********************************
React JS
********************************

ComponentLifeCycle
====================
There are three main phases in the React lifecycle: Mounting, Updating and Unmounting.

Mounting Phase: 

    1. constructor(props)
        - The constructor gets called before anything else and is a good spot to initialize state and other values.
        - The constructor is called with the props argument and should also call super(props), this will initiate the parents constructor and allow the component to inherit methods from its parent.

    2. getDerivedStateFromProps(props, state)
        - Gets called right before rendering the elements in the DOM

    3. render()
        - Outputs HTML to the DOM
    
    4. componentDidMount()
        - Called after the component is rendered
        - Good time to do stuff that rely on the component being in the DOM

Updating Phase:  

    1. getDerivedStateFromProps(props, state)

    2. shouldComponentUpdate()
        - You can return a boolean from this function to determine whether React should continue rendering or not, default is true

    3. render()
        - re-render the new HTML to the DOM

    4. getSnapShotBeforeUpdate(prevProps, prevState)
        - Gives you access to the props and state before the update occurred to that you can check what the old values were
        - If you have this function present, you must also have the componentDidUpdate() lifecycle method or else you will get an error
    
    5. componentDidUpdate()
        - This function is called right when the component has been updated in the DOM

Unmounting Phase:

    1. componentWillUnmount()
        - This function is called when the component is about to be removed from the DOM
        - Could be used to do any final tear down or save any unsaved progress
    
    
In order from first to last:

1. componentWillMount - LEGACY
    * Immediately before initial rendering

2. componentDidMount
    * Immediately after initial rendering

3. componentWillRecieveProps - LEGACY
    * When component recieved new props (ex. new props due to parent state change)

4. shouldComponentUpdate
    * Before rendering, after recieving new props or state. Can return false to prevent rerendering

5. componentWillUpdate - LEGACY
    * Before rendering, after receiving new props or state

6. componentDidUpdate
    * After component's update are flushed to DOM

7. componentWillUnMount
    * Immediately before removing component from DOM

Built-in Components
====================
Pure Components
-------------------------
A pure component is a React component which implements shouldComponentUpdate() with a shallow prop and state comparison.
The shallow comparison will only update the component if the values of state of props have actually changed.
It should also be noted that all childern of a pure component should also be pure.

A pure component can offer a performance increase as the component is not being re-rendered if it does not need to be.

.. code-block:: javascript

    class Pure extends React.PureComponent {}

Fragments
-------------------------
A fragment allows you to group a list of childern without adding extra nodes to the DOM.
A good example of this is if you have a HTML list or table and want to populate it with elements from a custom component.

.. code-block:: javascript

    class Table extends React.Component {
        render() {
            return (
            <table>
                <tr>
                <Columns />
                </tr>
            </table>
            );
        }
    }

    class Columns extends React.Component {
        render() {
            return (
            <div>
                <td>Hello</td>
                <td>World</td>
            </div>
            );
        }
    }

The above example would be invalid because <div> in Columns is not a valid child of <table>. To solve this, you can use a fragment to wrap your elements rather than an HTML element like a div.

.. code-block:: javascript

    class Columns extends React.Component {
        render() {
            return (
            <React.Fragment>
                <td>Hello</td>
                <td>World</td>
            </React.Fragment>
            );
        }
    }


Profiler
-------------------------
A Profiler is a React component that can be inserted anywhere in the tree to measure the cost of rendering that specific part of the tree.
It is a great tool for determining rendering speeds and optimizing applications.
It takes an onRender prop which requires a callback function.

.. code-block:: javascript

    render(
        <App>
            <Profiler id="Navigation" onRender={callback}>
            <Navigation {...props} />
            </Profiler>
            <Main {...props} />
        </App>
    );

Then, we can create the callback function to handle the Profiler measurements.

    function onRenderCallback(
        id, // the "id" prop of the Profiler tree that has just committed
        phase, // either "mount" (if the tree just mounted) or "update" (if it re-rendered)
        actualDuration, // time spent rendering the committed update
        baseDuration, // estimated time to render the entire subtree without memoization
        startTime, // when React began rendering this update
        commitTime, // when React committed this update
        interactions // the Set of interactions belonging to this update
    ) {
        // Aggregate or log render timings...
    }

Error Boundaries
====================
`Error Boundaries <https://reactjs.org/docs/error-boundaries.html>`_

Runtime errors during rendering will break the app, we can prevent this using error boundaries.
Consists of two lifecycle methods:

* static getDerivedStateFromError(error)

    * Used to render a fallback UI after an error is thrown
    * Can set error state to true and conditionally render a specific UI

* componentDidCatch(error, info)

    * Used to log the error and information

Create an ErrorBoundary component which has the two lifecycle methods above. You can then wrap any
component in this ErrorBoundary component if you wish to enable the error boundaries for it.

Redux State Management
========================
A popular state management library that keeps all state information in a central location called a 'store'.
Redux models the applications state as a single JS Object

Action
    
    * A POJO that must have a key called 'type' and a string value
    * Can have any number of additional keys

Reducer

    * A function that accepts the state and an action and returns a new state

Store

    * One bug POJO that represents the entire state of the application

Refs
========================
Refs provide a way to access DOM nodes or React class elements created in the render method.
A few good use cases of refs are:
    - Managing focus, text selection or media playback
    - Triggering imperative animations
    - Intergrating with third-party DOM libraries

Using Refs
-------------------------
You can create a ref using React.createRef();
If you use a ref on a HTML element, it recieves the DOM element as its current property.
If you use a ref on a custom class component, it recieves the mounted instance of the component as its current.
You cannot use refs on functional components because they do not have instances.

.. code-block:: javascript

    class CustomTextInput extends React.Component {
        constructor(props) {
            super(props);
            // create a ref to store the textInput DOM element
            this.textInput = React.createRef();
            this.focusTextInput = this.focusTextInput.bind(this);
        }

        focusTextInput() {
            // Explicitly focus the text input using the raw DOM API
            // Note: we're accessing "current" to get the DOM node
            this.textInput.current.focus();
        }

        render() {
            // tell React that we want to associate the <input> ref
            // with the `textInput` that we created in the constructor
            return (
            <div>
                <input
                type="text"
                ref={this.textInput} />
                <input
                type="button"
                value="Focus the text input"
                onClick={this.focusTextInput}
                />
            </div>
            );
        }
    }

Forwarding Refs
-------------------------
Ref forwarding is an opt-in feature that lets some components take a ref they recieve and pass it further down (forward) it to a child.
An example:

.. code-block:: javascript

    const FancyButton = React.forwardRef((props, ref) => (
        <button ref={ref} className="FancyButton">
            {props.children}
        </button>
    ));

    // You can now get a ref directly to the DOM button:
    const ref = React.createRef();
    <FancyButton ref={ref}>Click me!</FancyButton>;

Forwarding refs is not necessary for most components in the application, however can be useful in some cases.

Composition / Containment
===========================
A common pattern used to re-use code between components.
Instead of just inserted a components like: <MyComponent />, you can insert html, or other components inside of it.

In the example below, we see a WelcomeDialog component where all the HTML is within the FancyBorder JSX tag. 

.. code-block:: javascript

    function WelcomeDialog() {
        return (
            <FancyBorder color="blue">
                <h1 className="Dialog-title">
                    Welcome
                </h1>
                <p className="Dialog-message">
                    Thank you for visiting our spacecraft!
                </p>
            </FancyBorder>
        );
    }

Now, in the FancyBorder component we have a div that renders {props.childern}. props.childern will refer to all of the child elements within FancyBorder in the above snippet.

.. code-block:: javascript

    function FancyBorder(props) {
        return (
            <div className={'FancyBorder FancyBorder-' + props.color}>
                {props.children}
            </div>
        );
    }

Higher Order Components (HOC)
==============================
Higher order component is a function which takes a component and returns a new component

Hooks
===========================
Hooks are new addition to React 16.8 and they let you use state or other React features within a functional component
......