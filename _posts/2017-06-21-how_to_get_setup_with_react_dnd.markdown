---
layout: post
title:  "How to get setup with React DnD"
date:   2017-06-21 04:23:12 +0000
---


  In this post I am going to show you how to easily it is to set up project using React DnD. React DnD was actually created by Dan Abramov, so it uses Redux internally, and while it may seem complicated at first its main concepts start to make more sense the more you play around with them.
	
  So starting off there are three High Order Components that you really need to understand when you first start with React DnD. They are the DragContext, the DragSource, and the DragTarget together they allow you to get setup with drag and drop functionally relatively fast. So I am going to try to explain these components as best I can and show you how easy it is to add basic drag and drop to a project using React DnD.

  First in order to install React DnD you actually have to install two packages, the first one installs React DnD while the second package installs the backend that will be used by React DnD. In these examples I am going to be showing the HTML5 drag and drop API but there are other backends. Such as the Touch backend in case you need to support touch device, the Test backend for testing without the DOM, or you can even write your own backend.

```
npm install — save react-dnd
npm install — save react-dnd-html5-backend
```

# DragContext / DragContextProvider
  After we have React DnD installed we can begin by wrapping our root component with either DragDropContext or DragDropContextProvider. Both will setup the share DnD state that functions behind the scenes and both will let you specify the backend. But the major advantage of DragDropContextProvider over DragDropContext is that it allows you to inject an optional Window instance, something that is required if you need to support iframes.

```
import HTML5Backend from ‘react-dnd-html5-backend’
import { DragDropContext } from ‘react-dnd’

class App extends Component {
 /* code here */
}

export default DragDropContext(HTML5Backend)(App)
```

# DragSource
  With DragDropContext setup on our root component, the next step is setting up DragSource on the components that we want to make draggable. Now DragSource accepts three parameters and all of them are required:
	
Type: This can be either a string, or an ES6 symbol but it has to uniquely identifies a class of items. This one is important because only DragSources (Draggable items) and DropTargets (Droppable containers) that have matching types will interact. In this way you can add multiple components with DragSources to your project but only have matching DropTargets respond to them.

Spec: A JS object with a few allowed methods, these describes how the draggable item reacts to drag and drop events. Only the `beginDrag()` method is actually required and this method returns a plain JS object that describes the item currently being dragged. This could be as simple as `{ id: 1 }`. You can also use the optional `endDrag()` method to call a function or anything else you want to do on a successful drop, Otherwise you can use DropTarget to handle successful drops..

Collect: This is a function that returns an object of props to be injected into the current component. This function basically connects the React DnD event handlers and also passes some knowledge about the current dragging state to the component. For instance you can use`isDragging()` to return whether an item is currently being dragged and have it passed into a prop to be used in your render function.
Be sure to check out the DragSource docs for a full list of the allowed methods in both Spec and Collect and some examples of their use.

Finally our class also has to return connectDragSource() to wrap the component.

```
import { DragSource } from ‘react-dnd’

const Types = {
 ITEM: ‘toy’
}

const itemSource = {
 beginDrag(props) {
   /code goes here /
   },
   endDrag(props) {
 /code goes here /
 }
}

function collect(connect, monitor) {
  return {
    connectDragSource: connect.dragSource(),
    isDragging: monitor.isDragging()
 }
}

class Toy extends Component {
  render() {
   const { isDragging, connectDragSource, src } = this.props
   return connectDragSource( <div> Toy </div>)
 }
}

export default DragSource(Types.ITEM, itemSource, collect)(Toy)
```

# DropTarget
  Now once we have our DragSource implemented our final step is simply to connect our DropTarget, to give our draggable items something to communicate with. DropTarget actually has a lot of the same setup as DragSource, the only main differences are the methods allowed in Spec. The same three parameters: Type, Spec, and Collect are all required for the DropTarget as well but now instead of returning connectDragSource, we return connectDropTarget.

```
import { DropTarget } from ‘react-dnd’

const Types = {
  ITEM: ‘toy’
}

function collect(connect, monitor) {
  return {
    connectDropTarget: connect.dropTarget()
  }
}

class Box extends Component {
   render() {
     const { connectDropTarget } = this.props
     return connectDropTarget( /code goes here /)
   }
}
export default DropTarget(Types.ITEM, {}, collect)(Box)
```

> Aside from using endDrag() in our DragSource Spec, we could use also use drop() in our DropTarget Spec to respond to a successful drop.

  And thats actually it for setting up our DropTarget, we now have a basic draggable item and a valid drop target using React DnD.
# In Conclusion…
  As I said at the beginning by using React DnD we can easy get started with drag and drop functions. To help illustrate this point even more I created a basic project that you can play around with at [ToyboxDnD](https://github.com/Alicekb/ToyboxDnD). This Toybox project has a simple set of Toy and Utensil components. The Toys will disappear as you drop them into the Box, while the Utensils can only be dragged and wont drop. This project is actually barebones but will show you the quickest way to get set up with React DnD so feel free to alter it and try the different methods in Spec.
Thanks for reading! Be on the look out for my next post that will go even more into depth with React DnD and hopefully show you some cool tricks you can use.
