<p align="center"><img src="http://infernojs.org/img/inferno.png" width="150px"></p>
<p>&nbsp;</p>
[![Build Status](https://img.shields.io/travis/trueadm/inferno/master.svg?style=flat-square)](https://travis-ci.org/trueadm/inferno/branches)
[![Coverage Status](https://img.shields.io/coveralls/trueadm/inferno/master.svg?style=flat-square)](https://coveralls.io/github/trueadm/inferno?branch=master)
[![Dependencies](https://img.shields.io/david/trueadm/inferno.svg?style=flat-square)](https://david-dm.org/trueadm/inferno)
[![devDependency Status](https://david-dm.org/trueadm/inferno/dev-status.svg?style=flat-square)](https://david-dm.org/trueadm/inferno#info=devDependencies)
[![MIT](https://img.shields.io/npm/l/inferno.svg?style=flat-square)](https://github.com/trueadm/inferno/blob/master/LICENSE.md)
[![NPM Version](https://img.shields.io/npm/v/inferno.svg?style=flat-square)](https://www.npmjs.com/package/inferno)
[![npm downloads](https://img.shields.io/npm/dm/inferno-dom.svg?style=flat-square)](https://www.npmjs.org/package/inferno-dom)
[![Slack Status](https://inferno-slack.herokuapp.com/badge.svg)](https://inferno-slack.herokuapp.com/)

Inferno is an insanely fast, `8kb` React-like library for building high-performance user interfaces on both the client and server.

To quote a member of the React core team at Facebook:
> Inferno 1.0 is really well written. It's how I would've rewritten React. I'd recommend reading its source to learn.

Inferno aims to provide all the great benefits that React does, plus other great features for people already familiar with the React ecosystem, such as: lifecycle events on functional components, server side render streams, better real-world performance, lower memory consumption and faster parse/load times. Furthermore, Inferno allows people to switch their **existing React projects** to Inferno in a few lines of code using [`inferno-compat`](https://github.com/trueadm/inferno/tree/master/packages/inferno-compat).

For those not familiar with React, Inferno is a JavaScript library for building user interfaces in a **declarative** manner. Rather than working with MVC/MVVM style patterns, Inferno uses a **component-based** approach where data flows in one direction, making coding predictable, re-usable and highly testable. Based on the concept of *learn once, write anywhere*, Inferno doesn't impose any restrictions on how you create components. You literally write JavaScript to state how you'd like your UI to look – Inferno does all the rest. Inferno also renders content on the server via `inferno-server` and NodeJS, so you can write awesome UIs that get rendered full-stack.

In terms of performance, Inferno is currently the **fastest** JavaScript UI library there is – both in benchmarks and actual real-world scenarios. It excels on the browser at initial page load, parse times, render times and update times. Inferno's server-side rendering is around 10x faster than React, 7x faster than Preact and around 5x faster than Vue and Angular 2.

## But why?

Inferno started as an idea two years ago, to see if a UI library could really improve the experience, battery, memory usage and performance on mobile devices. At the time we really struggled to get good performance on *any* UI library/framework at the time – it simply wasn't happening, we spent a huge amount of time writing lots of vanilla JavaScript code and it did the job – but it was a mess.

Since then, things haven't really improved much in the mobile space. Libraries have gotten smaller, but the time to parse a 2mb app can result in 5+ seconds time before the user can even see anything. Frameworks and libraries need to lose bloat, they need to care about performance. Developing on a MacBook Pro and seeing animations, routing, complex UIs instantly appear is *not* going to happen on an average mobile device (especially in emerging countries).

Inferno proves that it is possible to be fast on mobile. Parse-time, load-time, rendering complex UIs and all the normal things you'd expect to just work. How Inferno does that is based on many factors, but ultimately Inferno's code is much better understood by modern JavaScript engines and can be highly optimised to perform far better than other libraries/frameworks.

## Summary

- Component driven + one-way data flow architecture
- One of the fastest front-end frameworks for rendering UI in the DOM
- React-like API, concepts and component lifecycle events
- Partial synthetic event system, providing delegation to certain events for better performance
- Inferno's [`linkEvent`](https://github.com/trueadm/inferno/blob/master/README.md#linkevent-package-inferno) feature removes the need to use arrow functions or binding event callbacks (for delegated events)
- Lightweight filesize of only 8kb
- Isomorphic rendering on both client and server with `inferno-server`
- Highly modular with very few opinions on how things should be done
- Unlike React and Preact, Inferno has lifecycle events on functional components
- Supports asynchronous component rendering using `requestIdleCallback`
- Unlike Preact and other React-like libraries, Inferno has controlled components for input/select/textarea elements

## Benchmarks

- [Virtual DOM Benchmark](http://vdom-benchmark.github.io/vdom-benchmark/)
- [UI Bench](https://localvoid.github.io/uibench/)
- [dbmonster](http://infernojs.org/benchmarks/dbmonster/)
- [dbmonster (lazy optimisation)](http://infernojs.org/benchmarks/dbmonster-lazy/)
- [Angular Test Table](http://infernojs.org/benchmarks/angular-test-table/infernojs/index.html)
- [JS Web Frameworks Benchmark - Round 4](http://stefankrause.net/js-frameworks-benchmark4/webdriver-ts/table.html)

## Code Example

Let's start with some code. As you can see, Inferno intentionally keeps the same, good, design ideas as React regarding components: one-way data flow and separation of concerns.

In these examples, JSX is used via the [Inferno JSX Babel Plugin](https://github.com/infernojs/babel-plugin-inferno) to provide a simple way to express Inferno virtual DOM. You do not need to use JSX, it's completely **optional**, you can use [hyperscript](https://github.com/trueadm/inferno/tree/master/packages/inferno-hyperscript) or [createElement](https://github.com/trueadm/inferno/tree/master/packages/inferno-create-element) (like React does).

```jsx
import Inferno from 'inferno';

const message = "Hello world";

Inferno.render(
  <MyComponent message={ message } />,
  document.getElementById("app")
)
```
Furthermore, Inferno also uses ES6 components like React:

```jsx
import Inferno from 'inferno';
import Component from 'inferno-component';

class MyComponent extends Component {
  constructor(props) {
    super(props);
    this.state = {
      counter: 0
    }
  }
  render() {
    return (
      <div>
        <h1>Header!</h1>
        <span>Counter is at: { this.state.counter }</span>
      </div>
    )
  }
}

Inferno.render(<MyComponent />, document.body);
```

### More Examples

- [**Simple Clock** (@JSFiddle)](https://jsfiddle.net/o01mvsyn/)

## Getting Started

The best way to start to use Inferno is by using [Create Inferno App](https://github.com/infernojs/create-inferno-app). You can get setup and running within a few minutes.

Alternatively, you can get started with Inferno using the [Inferno Boilerplate](https://github.com/infernojs/inferno-boilerplate) for a very simple setup. For a more advanced example demonstrating how Inferno might be used, we recommend trying out [Inferno Starter Project](https://github.com/nightwolfz/inferno-starter) by [nightwolfz](https://github.com/nightwolfz/).

Core package:

```sh
npm install --save inferno@beta32
```

Addons:

```sh
# ES2015 stateful components
npm install --save inferno-component@beta32
# server-side rendering
npm install --save inferno-server@beta32
# routing
npm install --save inferno-router@beta32
```

Pre-bundled files for browser consumption can be found on [our cdnjs](https://cdnjs.com/libraries/inferno):

```
https://cdnjs.cloudflare.com/ajax/libs/inferno/1.0.0-beta32/inferno.min.js
```

### Creating Virtual DOM

#### JSX:
```sh
npm install --save-dev babel-plugin-inferno@beta13
```

#### Hyperscript:
```sh
npm install --save inferno-hyperscript@beta32
```

#### createElement:
```sh
npm install --save inferno-create-element@beta32
```

### Compatibility with existing React apps
```sh
npm install --save-dev inferno-compat@beta32
```

Note: Make sure you read more about [`inferno-compat`](https://github.com/trueadm/inferno/tree/master/packages/inferno-compat) before using it.

## Third-party state libraries

Inferno now has bindings available for some of the major state management libraries out there:

- [Redux](https://github.com/trueadm/inferno/tree/dev/packages/inferno-redux) via `inferno-redux`
- [MobX](https://github.com/trueadm/inferno/tree/dev/packages/inferno-mobx) via `inferno-mobx`
- [Cerebral](https://github.com/cerebral/cerebral-view-inferno) via `cerebral-view-inferno`

## JSX

Inferno has its own [JSX Babel plugin](https://github.com/trueadm/babel-plugin-inferno).

## Differences from React

- Inferno is much smaller in size, `8kb` vs `45kb` gzip. This means Inferno is faster to transfer over the network but more importantly, is *much* faster to parse – this makes a big impact on mobile.
- Inferno is considerably faster than React. This doesn't apply to only benchmarks, but real-world applications that companies have converted to Inferno from React. Ranging from 40% - 110% performance improvement with Inferno `1.0`. No other React-like library gets close to this performance gain over React.
- Inferno doesn't have a fully synthetic event system like React does. Inferno has a partially synthetic event system, instead opting to only delegate certain events (such as `onClick`).
- Inferno doesn't support React Native. Inferno was only designed for the browser/server with the DOM in mind.
- Inferno doesn't support string refs – although this can be enabled using `inferno-compat`. We don't recommend using them, they are the source of many memory leaks and performance issues in real-world apps. Stick with function callback refs instead.
- Inferno includes `render` on the main core package, rather than have a `InfernoDOM` package like React does. We used to do it that way, but we found people simply didn't like it given we don't support native. Furthermore, by not splitting them, we improved performance and bundle sizes.
- Inferno provides lifecycle events on stateless components. This is a major win for people who prefer lightweight components rather than bloated ES2015 classes.
- Inferno has its own devtools debugger (still in development) that differs from the React implementation. Inferno's debugger is on average, 4x faster – fixing lots of the issues with slow, laggy interfaces when developers are debugging.

## Differences from Preact

- Inferno is larger in size, `8kb` vs `3kb` gzip. This means that Preact should parse faster than Inferno – if only slightly.
- Inferno has a partial synthetic event system, resulting in better performance via delegation of certain events.
- Inferno is *much* faster than Preact in rendering, updating and removing elements from the DOM. Inferno diffs against virtual DOM, rather than the real DOM (except for when loading from server-side rendered content) which means it can make drastic improvements. Unfortunately, diffing against the real DOM has a 30-40% overhead cost in operations.
- Inferno fully supports controlled components for `input`/`select`/`textarea` elements. This prevents lots of edgecases where the virtual DOM is not the source of truth (it should always be). Preact pushes the source of truth to the DOM itself.
- Inferno provides lifecycle events on stateless components. This is a major win for people who prefer lightweight components rather than bloated ES2015 classes.
- Inferno has its own devtools debugger (still in development) that differs from the Preact (React bound) implementation. Inferno's debugger is on average, 4x faster – fixing lots of the issues with slow, laggy interfaces when developers are debugging.

## Event System

Like React, Inferno also uses a light-weight synthetic event system in certain places (although both event systems differ massively). Inferno's event system provides highly efficient delegation and an event helper called [`linkEvent`](https://github.com/trueadm/inferno/blob/master/README.md#linkevent-package-inferno). 


As this is feature is a very recent addition to Inferno, there are only a handful of events that use Inferno's event system. They are outlined below:
- `onClick`
- `onMouseMove`
- `onMouseDown`
- `onMouseUp`

More events are expected to be supported in future versions.

## Inferno Top-Level API

### `render` (package: `inferno`)

```javascript
import Inferno from 'inferno';

Inferno.render(<div />, document.body);
```

Render a virtual node into the DOM in the supplied container given the supplied virtual DOM. If the virtual node was previously rendered
into the container, this will perform an update on it and only mutate the DOM as necessary, to reflect the latest Inferno virtual node.

Warning: If the container element is not empty before rendering, the content of the container will be overwritten on the initial render.

### `createRenderer` (package: `inferno`)

`createRenderer` allows for functional composition when rendering content to the DOM. An example of this is shown below:

```javascript
import Inferno from 'inferno';
import { scan, map } from 'most';

...
const model$ = scan(update, 0, actions$);
const vNodes$ = map(view(actions$), model$);
const renderer = Inferno.createRenderer();
const runApp = () => scan(renderer, container, vNodes$).drain();

runApp();
```

### `createElement` (package: `inferno-create-element`)

Creates an Inferno VNode using a similar API to that found with React's `createElement()`

```javascript
import Component from 'inferno-component';
import createElement from 'inferno-create-element';

class BasicComponent extends Component {
    render() {
        return createElement('div', {
               className: 'basic'
           },
           createElement('span', {
               className: this.props.name
           }, 'The title is ', this.props.title)
       )
    }
}

Inferno.render(createElement(BasicComponent, { title: 'abc' }), document.body);
```

### `Component` (package: `inferno-component`)

**Stateful component:**

```javascript
import Component from 'inferno-component';

class MyComponent extends Component {
  render() {
    ...
  }
}
```

This is the base class for Inferno Components when they're defined using ES6 classes.

**Stateless component:**

```javascript
import Inferno from 'inferno';

const MyComponent = ({ name, age }) => (
  <span>My name is: { name } and my age is: {age}</span>  
);
```

Stateless components are first-class functions where their first argument is the `props` passed through from their parent.

### `createVNode` (package: `inferno`)
```js
Inferno.createVNode(
  flags,
  type,
  [props],
  [...children],
  [events],
  [key],
  [ref],
  [isNormalized]
)
```

Create a new Inferno `VNode` using `createVNode()`. A `VNode` is a virtual DOM object that is used to
describe a single element of the UI. Typically `createElement()` (package: `inferno-create-element`), `h()` (package: `inferno-hyperscript`) or JSX are used to create
`VNode`s for Inferno, but under the hood they all use `createVNode()`. Below is an example of using
of `createVNode` usage:

```javascript
import Inferno from 'inferno';

const vNode = Inferno.createVNode(2, 'div', { className: 'example' }, 'Hello world!');

Inferno.render(vNode, container);
```

The first argument for `createVNode()` is a value from [`VNodeFlags`](https://github.com/trueadm/inferno/tree/master/packages/inferno-vnode-flags), this is numerical value that used to tell Inferno what the VNode is meant to describe on the page.

### `cloneVNode` (package: `inferno`)
```js
Inferno.cloneVNode(
  vNode,
  [props],
  [...children]
)
```

Clone and return a new Inferno `VNode` using a `VNode` as the starting point. The resulting `VNode` will have the original `VNode`'s props with the new props merged in shallowly. New children will replace existing children. key and ref from the original `VNode` will be preserved.

`cloneVNode()` is almost equivalent to:
```jsx
<VNode.type {...VNode.props} {...props}>{children}</VNode.type>
```

An example of using `cloneVNode`:

```javascript
import Inferno from 'inferno';

const vNode = Inferno.createVNode(2, 'div', { className: 'example' }, 'Hello world!');
const newVNode = Inferno.cloneVNode(vNode, { id: 'new' }); // we are adding an id prop to the VNode

Inferno.render(newVNode, container);
```

If you're using JSX:

```jsx
import Inferno from 'inferno';

const vNode = <div className="example">Hello world</div>;
const newVNode = Inferno.cloneVNode(vNode, { id: 'new' }); // we are adding an id prop to the VNode

Inferno.render(newVNode, container);
```

### `enableFindDOMNode` (package: `inferno`)

This enables `findDOMNode()`. We strongly recommend against using this API as it introduces a significant impact to performance. In the future this API command will be removed, along with `findDOMNode()`;

### `findDOMNode` (package: `inferno`)

Once enabled via `enableFindDOMNode()` at the start of an application, `findDOMNode()` is enabled.

Note: we recommend using a `ref` callback on a component to find its instance, rather than using `findDOMNode()`. `findDOMNode()` cannot be used on functional components and it introduces a significant impact to performance.

If a component has been mounted into the DOM, this returns the corresponding native browser DOM element. This method is useful for reading values out of the DOM, such as form field values and performing DOM measurements. 
In most cases, you can attach a ref to the DOM node and avoid using `findDOMNode()` at all. When render returns null or false, `findDOMNode()` returns null.

### `linkEvent` (package: `inferno`)

`linkEvent()` is a helper function that allows attachment of `props`/`state`/`context` or other data to events without needing to `bind()` them or use arrow functions/closures. It works by hooking into Inferno's event system (so make sure the event you are using will use Inferno's event system). This is extremely useful when dealing with events in functional/stateless components. Below is an example:

```jsx
import Inferno, { linkEvent } from 'inferno';

function handleClick(props, event) {
	props.validateValue(event.target.value);
}

function MyComponent(props) {
	return <div><input type="text" onClick={ linkEvent(props, handleClick) } /><div>;
}
```

This is an example of using it with ES2015 classes:


```jsx
import Inferno, { linkEvent } from 'inferno';
import Component from 'inferno-component';

function handleClick(instance, event) {
	instance.setState({ data: event.target.value });
}

class MyComponent extends Component {
	render () {
		return <div><input type="text" onClick={ linkEvent(this, handleClick) } /><div>;
	}
}
```

`linkEvent()` offers better performance than binding an event in a class constructor and using arrow functions, so where possible, it should be used.

### `renderToString` (package: `inferno-server`)

```javascript
import Inferno from 'inferno';
import InfernoServer from 'inferno-server';

InfernoServer.renderToString(<div />);
```

Render a virtual node into an HTML string, given the supplied virtual DOM.

## Stateless component hooks

| Name                      | Triggered when                                                 | Arguments to callback           |
| -----------               | --------------                                                 | -----------------------         |
| `onComponentWillMount`    | a stateless component is about to mount                        |                                 |
| `onComponentDidMount`     | a stateless component has mounted successfully                 | `domNode`                       |
| `onComponentShouldUpdate` | a stateless component has been triggered to updated            | `lastProps, nextProps`          |
| `onComponentWillUpdate`   | a stateless component is about to perform an update            | `lastProps, nextProps`          |
| `onComponentDidUpdate`    | a stateless component has performed an updated                 | `lastProps, nextProps`          |
| `onComponentWillUnmount`  | a stateless component is about to be unmounted                 |                                 |

### Using hooks

It's simple to implicitly assign hooks to both DOM nodes and stateless components.
Please note: stateful components (ES2015 classes) from `inferno-component` **do not** support hooks.

```javascript
function mounted(domNode) {
    // [domNode] will be available for DOM nodes and components (if the component has mounted to the DOM)
}

Inferno.render(<div onCreated={ createdCallback } />, document.body);

function StatelessComponent({ props }) {
	return <div>Hello world</div>;
}

Inferno.render(<StatelessComponent onComponentDidMount={ mounted } />, document.body);
```

Hooks provide powerful lifecycle events to stateless components, allowing you to build components without being forced to use ES2015 classes.

## Browser Support

Inferno supports IE11+, Edge, Chrome, Firefox and Safari 8+. In order to support IE8+, Inferno requires polyfills for the following JavaScript features:

- [Map object](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Map)
- [WeakMap object](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/WeakMap)
- [Object.keys](https://developer.mozilla.org/en/docs/Web/JavaScript/Reference/Global_Objects/Object/keys)
- [Object.assign](https://developer.mozilla.org/en/docs/Web/JavaScript/Reference/Global_Objects/Object/assign)

Potential solutions including using the [es5-shim](https://github.com/es-shims/es5-shim) for ES5 features and [es6-shim](https://github.com/paulmillr/es6-shim) from ES2015 features.

### Custom namespaces

Inferno wants to always deliver great performance and in order to do so, it has to make intelligent assumptions about the state of the DOM and the elements available to mutate. Custom namespaces conflict with this idea and change the schema of how different elements and attributes might work; so Inferno makes no attempt to support namespaces. Instead, SVG namespaces are automatically applied to elements and attributes based on their `tag name`.

## Community

There is an [Inferno Slack](https://infernojs.slack.com). You can join via [inferno-slack.herokuapp.com](https://inferno-slack.herokuapp.com).

### Inferno is supported by BrowserStack

<img src="http://infernojs.org/browserstack.svg" height="50px" alt="Supported by Browserstack" />
