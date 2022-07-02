1. How does React work?
   - React creates a virtual DOM. When state changes in a component it firstly runs a "diffing" algorithm, which identifies what has changed in the virtual DOM. The second step is reconciliation, where it updates the DOM with the results of diff.
2. What is Content API in ReactJS ?

   - Context provides a way to pass data through the component tree without having to pass props down manually at every level. Context is designed to share data that can be considered “global” for a tree of React components, such as the current authenticated user, theme, or preferred language. Using context, we can avoid passing props through intermediate elements.

   ```js
   const ThemeContext = React.createContext("light");
   class App extends React.Component {
     render() {
       return (
         <ThemeContext.Provider value="dark">
           <Toolbar />
         </ThemeContext.Provider>
       );
     }
   }

   function Toolbar() {
     return (
       <div>
         <ThemedButton />
       </div>
     );
   }

   class ThemedButton extends React.Component {
     static contextType = ThemeContext;
     render() {
       return <Button theme={this.context} />;
     }
   }
   ```

3. What are props in React ?

   - Props are inputs to a React component. They are single values or objects containing a set of values that are passed to React Components on creation using a naming convention similar to HTML-tag attributes. i.e, They are data passed down from a parent component to a child component.

   - The primary purpose of props in React is to provide following component functionality:

   1. Pass custom data to your React component.
   2. Trigger state changes.
   3. Use via this.props.reactProp inside component's render() method.

   For example, let us create an element with reactProp property,

   ```jsx
   <Element reactProp="1" />
   ```

   This reactProp (or whatever you came up with) name then becomes a property attached to React's native props object which originally already exists on all components created using React library.

   ```jsx
   props.reactProp;
   ```

4. What is the use of refs ?

   - Refs provide a way to access DOM nodes or React elements created in the render method. They should be avoided in most cases, however, they can be useful when we need direct access to DOM element or an instance of a component.

   - There are a few good use cases for refs:

     1. Managing focus, text selection, or media playback.
     2. Triggering imperative animations.
     3. Integrating with third-party DOM libraries.

   - Refs are created using React.createRef() and attached to React elements via the ref attribute. Refs are commonly assigned to an instance property when a component is constructed so they can be referenced throughout the component.

     ```jsx
     class MyComponent extends React.Component {
       constructor(props) {
         super(props);
         this.myRef = React.createRef();
       }
       render() {
         return <div ref={this.myRef} />;
       }
     }
     ```

5. What are the advantages of ReactJS ?
   - Blow are the advantages of ReactJS:
     1. Increases the application’s performance with Virtual DOM
     2. JSX makes code is easy to read and write
     3. It renders both on client and server side
     4. Easy to integrate with other frameworks (Angular, BackboneJS) since it is only a view library
     5. Easy to write UI Test cases and integration with tools such as JEST.
6. What are React Hooks ?
   - Hooks are a new addition in React 16.8. They let you use state and other React features without writing a class. With Hooks, you can extract stateful logic from a component so it can be tested independently and reused. Hooks allow you to reuse stateful logic without changing your component hierarchy. This makes it easy to share Hooks among many components or with the community.
7. How would you write an inline style in React ?
   - For example:
   ```jsx
   <div style={{ height: 10 }}>
   ```
8. What is React ?
   - React is an open-source JavaScript library created by Facebook for building complex, interactive UIs in web and mobile applications. React’s core purpose is to build UI components; it is often referred to as just the “V” (View) in an “MVC” architecture.
9. What are the major features of ReactJS ?
   - The major features of ReactJS are as follows,
     1. It uses VirtualDOM instead RealDOM considering that RealDOM manipulations are expensive.
     2. Supports server-side rendering
     3. Follows Unidirectional data flow or data binding
     4. Uses reusable/composable UI components to develop the view
10. What are the differences between a Class component and Functional component ?
    - Class Components
      1. Class-based Components uses ES6 class syntax. It can make use of the lifecycle methods.
      2. Class components extend from React.Component.
      3. In here you have to use this keyword to access the props and functions that you declare inside the class components.
    - Functional Components
      1. Functional Components are simpler comparing to class-based functions.
      2. Functional Components mainly focuses on the UI of the application, not on the behavior.
      3. To be more precise these are basically render function in the class component.
      4. Functional Components can have state and mimic lifecycle events using Reach Hooks
11. Whar are the advantages of using React ?
    - It is easy to know how a component is rendered, you just need to look at the render function.
    - JSX makes it easy to read the code of your components. It is also really easy to see the layout, or how components are plugged/combined with each other.
    - You can render React on the server-side with Nextjs. This enables improves SEO and performance.
    - It is easy to test.
    - You can use React with any framework (Backbone.js, Angular.js) as it only a view layer.
12. What is the differrence between state and props ?
    - The state is a data structure that starts with a default value when a Component mounts. It may be mutated across time, mostly as a result of user events.
    - Props (short for properties) are a Component's configuration. They are received from above and immutable as far as the Component receiving them is concerned. A Component cannot change its props, but it is responsible for putting together the props of its child Components. Props do not have to just be data - callback functions may be passed in as props.
13. What is the difference between a Presentational component and a Container component ?
    - Presentational components are concerned with how things look. They generally receive data and callbacks exclusively via props. These components rarely have their own state, but when they do it generally concerns UI state, as opposed to data state.
    - Container components are more concerned with how things work. These components provide the data and behavior to presentational or other container components. They call Flux actions and provide these as callbacks to the presentational components. They are also often stateful as they serve as data sources.
14. What are refs used for in React ?

    - Refs are an escape hatch which allow you to get direct access to a DOM element or an instance of a component. In order to use them you add a ref attribute to your component whose value is a callback function which will receive the underlying DOM element or the mounted instance of the component as its first argument.

    ```jsx
    class UnControlledForm extends Component {
      handleSubmit = () => {
        console.log("Input Value: ", this.input.value);
      };
      render() {
        return (
          <form onSubmit={this.handleSubmit}>
            <input type="text" ref={(input) => (this.input = input)} />
            <button type="submit">Submit</button>
          </form>
        );
      }
    }
    ```

    - Above notice that our input field has a ref attribute whose value is a function. That function receives the actual DOM element of input which we then put on the instance in order to have access to it inside of the handleSubmit function.
    - It’s often misconstrued that you need to use a class component in order to use refs, but refs can also be used with functional components by leveraging closures in JavaScript.

    ```jsx
    function CustomForm({ handleSubmit }) {
      let inputElement;
      return (
        <form onSubmit={() => handleSubmit(inputElement.value)}>
          <input type="text" ref={(input) => (inputElement = input)} />
          <button type="submit">Submit</button>
        </form>
      );
    }
    ```

15. What's the difference between a Controlled component and an Uncontrolled one in React ?

    - This relates to stateful DOM components (form elements) and the React docs explain the difference:
      1. A Controlled Component is one that takes its current value through props and notifies changes through callbacks like onChange. A parent component "controls" it by handling the callback and managing its own state and passing the new values as props to the controlled component. You could also call this a "dumb component".
      2. A Uncontrolled Component is one that stores its own state internally, and you query the DOM using a ref to find its current value when you need it. This is a bit more like traditional HTML.
    - Most native React form components support both controlled and uncontrolled usage:

    ```jsx
    // Controlled:
    <input type="text" value={value} onChange={handleChange} />

    // Uncontrolled:
    <input type="text" defaultValue="foo" ref={inputRef} />
    // Use `inputRef.current.value` to read the current value of <input>
    // In most (or all) cases you should use controlled components.
    ```

16. What are Controlled components in ReactJS ?
    - A Controlled Component is one that takes its current value through props and notifies changes through callbacks like onChange. A parent component "controls" it by handling the callback and managing its own state and passing the new values as props to the controlled component. You could also call this a "dumb component".
    ```jsx
    // Controlled:
    <input type="text" value={value} onChange={handleChange} />
    ```
17. What is state in React ?

    - State of a component is an object that holds some information that may change over the lifetime of the component. We should always try to make our state as simple as possible and minimize the number of stateful components.
    - Consider:

    ```jsx
    class User extends React.Component {
      constructor(props) {
        super(props);

        this.state = {
          message: "Welcome to React world",
        };
      }
      render() {
        return (
          <div>
            <h1>{this.state.message}</h1>
          </div>
        );
      }
    }
    ```

18. What does it mean for a component to be mounted in React ?
    - It has a corresponding element created in the DOM and is connected to that.
19. What are Fragments in React ?
    - It's common pattern in React which is used for a component to return multiple elements. Fragments let you group a list of children without adding extra nodes to the DOM.
    ```jsx
    render() {
        return (
            <React.Fragment>
            <ChildA />
            <ChildB />
            <ChildC />
            </React.Fragment>
        );
    }
    ```
    - There is also a shorter syntax:
    ```jsx
    render() {
        return (
        <>
            <ChildA />
            <ChildB />
            <ChildC />
        </>
        );
    }
    ```
20. When rendering a list what is a key and what is it's purpose ?
    - Keys help React identify which items have changed, are added, or are removed. Keys should be given to the elements inside the array to give the elements a stable identity. The best way to pick a key is to use a string that uniquely identifies a list item among its siblings.
    ```jsx
    render () {
        return (
            <ul>
            {this.state.todoItems.map(({task, uid}) => {
                return <li key={uid}>{task}</li>
            })}
            </ul>
        )
    }
    ```
    - Most often you would use IDs from your data as keys. When you don't have stable IDs for rendered items, you may use the item index as a key as a last resort. It is not recommend to use indexes for keys if the items can reorder, as that would be slow.
21. How to create refs in React ?
    - Refs are created using React.createRef() method and attached to React elements via the ref attribute. In order to use refs throughout the component, just assign the ref to the instance property with in constructor.
    ```jsx
    class MyComponent extends React.Component {
      constructor(props) {
        super(props);
        this.myRef = React.createRef();
      }
      render() {
        return <div ref={this.myRef} />;
      }
    }
    ```
    And:
    ```jsx
    class UserForm extends Component {
      handleSubmit = () => {
        console.log("Input Value is: ", this.input.value);
      };
      render() {
        return (
          <form onSubmit={this.handleSubmit}>
            <input type="text" ref={(input) => (this.input = input)} /> //
            Access DOM input in handle submit
            <button type="submit">Submit</button>
          </form>
        );
      }
    }
    ```
    We can also use it in functional components with the help of closures.
22. What is `useState()` in React ?

    - Explain what is the use of useState(0) there:

    ```jsx
    ...
    const [count, setCounter] = useState(0);
    const [moreStuff, setMoreStuff] = useState(...);
    ...

    const setCount = () => {
        setCounter(count + 1);
        setMoreStuff(...);
        ...
    };
    ```

    - `useState` is one of build-in react hooks. `useState(0)` returns a tuple where the first parameter count is the current state of the counter and setCounter is the method that will allow us to update the counter's state.
    - We can use the `setCounter` method to update the state of count anywhere - In this case we are using it inside of the setCount function where we can do more things; the idea with hooks is that we are able to keep our code more functional and avoid class based components if not desired/needed.

23. What are Stateful components in React ?

    - If the behaviour of a component is dependent on the state of the component then it can be termed as stateful component. These Stateful components are always class components and have a state that gets initialized in the constructor.

    ```jsx
    class App extends Component {
      constructor(props) {
        super(props);
        this.state = { count: 0 };
      }

      render() {
        // omitted for brevity
      }
    }
    ```

24. What is JSX ?
    - JSX is a syntax notation for Javascript XML (XML-like syntax extension to ECMAScript).It stands for JavaScript XML. It provides expressiveness of JavaScript along with HTML like template syntax. For example, the below text inside h1 tag return as javascript function to the render function,
    ```jsx
       render(){
    	return(
         <div>
            <h1> Welcome to React world!!</h1>
         </div>
    	);
     }
    ```
25. What are the limitations of React ?
    - Belows are the list of limitations:
      1. React is just a view library, not a full-blown framework
      2. There is a learning curve for beginners who are new to web development.
      3. Integrating React.js into a traditional MVC framework requires some additional configuration
      4. The code complexity increases with inline templating and JSX.
      5. Too many smaller components leading to over-engineering or boilerplate
26. What are Stateless components in React ?
    - If the behaviour is independent of its state then it can be a stateless component. You can use either a function or a class for creating stateless components. But unless you need to use a lifecycle hook in your components, you should go for stateless functional components.
    ```jsx
    // Stateful/Container/Smart component:
    class Main extends Component {
      constructor() {
        super();
        this.state = {
          books: [],
        };
      }
      render() {
        <BooksList books={this.state.books} />;
      }
    }
    // Stateless/Presentational/Dumb component:
    const BooksList = ({ books }) => {
      return (
        <ul>
          {books.map((book) => {
            return <li>book</li>;
          })}
        </ul>
      );
    };
    ```
    - There are a lot of benefits if you decide to use stateless functional components here; they are:
      1. easy to write, understand, and test, and
      2. you can avoid the this keyword altogether.
27. How is React different from AngularJS (1.x)?

    - For example, AngularJS (1.x) approaches building an application by extending HTML markup and injecting various constructs (e.g. Directives, Controllers, Services) at runtime. As a result, AngularJS is very opinionated about the greater architecture of your application — these abstractions are certainly useful in some cases, but they come at the cost of flexibility.

    - By contrast, React focuses exclusively on the creation of components, and has few (if any) opinions about an application’s architecture. This allows a developer an incredible amount of flexibility in choosing the architecture they deem “best” — though it also places the responsibility of choosing (or building) those parts on the developer.

28. What is the difference between state and props ?
    - Both props and state are plain JavaScript objects. While both of them hold information that influences the output of render, they are different in their functionality with respect to component. i.e,
      1. Props get passed to the component similar to function parameters
      2. State is managed within the component similar to variables declared within a function.
29. What are two types of components in ReactJS ?
    - There are two possible ways to create ReactJS Components.
      1. Functional components: This is the simplest way to create ReactJS components. It accepts props as an Object and returns ReactJS elements. We call it as “functional” because those are pure JavaScript functions.
      ```jsx
      function Greeting(props) {
        return <h1> Hello, {props.message}</h1>;
      }
      ```
      2. Class components: You can also use Es6 class to define component. The above functional component can be written as below,
      ```jsx
      class Greeting extends React.Component {
        render() {
          return <h1>Hello, {this.props.message}</h1>;
        }
      }
      ```
30. What is the purpose of callback function as an argument of setState ?
    - The callback function is invoked when setState finished and the component gets rendered. Since setState is asynchronous the callback function is used for any post action.
    - Note: It is recommended to use lifecycle method rather this callback function.
    ```jsx
    setState({ name: "sudheer" }, () =>
      console.log("The name has updated and component re-rendered")
    );
    ```
31. What are portals in React and when do we need them ?
    - Portals provide a first-class way to render children into a DOM node that exists outside the DOM hierarchy of the parent component.
    - Sometimes it’s useful to insert a child into a different location in the DOM:
    - A typical use case for portals is when a parent component has an overflow: hidden or z-index style, but you need the child to visually “break out” of its container.
    ```jsx
    render() {
    // React does *not* create a new div. It renders the children into `domNode`.
    // `domNode` is any valid DOM node, regardless of its location in the DOM.
    return ReactDOM.createPortal(
        this.props.children,
        domNode  );
    }
    ```
32. What are advantages of using React Hooks ?
    - Primarily, hooks in general enable the extraction and reuse of stateful logic that is common across multiple components without the burden of higher order components or render props. Hooks allow to easily manipulate the state of our functional component without needing to convert them into class components.
    - Hooks don’t work inside classes (because they let you use React without classes). By using them, we can totally avoid using lifecycle methods, such as componentDidMount, componentDidUpdate, componentWillUnmount. Instead, we will use built-in hooks like useEffect .
33. What happens during the lifecycle of a React component ?
    - At the highest level, React components have lifecycle events that fall into three general categories:
      1. Initialization
      2. State/Property Updates
      3. Destruction
    - ![image info](./../images/react-33.png)
34. What is the difference between Component and Container in Redux ?
    - Component is part of the React API. A Component is a class or function that describes part of a React UI.
    - Container is an informal term for a React component that is connected to a redux store. Containers receive Redux state updates and dispatch actions, and they usually don't render DOM elements; they delegate rendering to presentational child components.
35. What are inline conditional expressions in ReactJS ?
    - You can use either if statements or ternary expressions which are available from JS to conditionally render expressions. Apart from these approaches, you can also embed any expressions in JSX by wrapping them in curly braces and then followed by JS logical operator(&&).
    ```jsx
    if (this.state.mode === "view") {
      return <button onClick={this.handleEdit}>Edit</button>;
    } else {
      return <button onClick={this.handleSave}>Save</button>;
    }
    // or
    {
      view ? null : (
        <p>
          <input onChange={this.handleChange} value={this.state.inputText} />
        </p>
      );
    }
    ```
36. What is Reconciliation in ReactJS?
    - When a component’s props or state change, React decides whether an actual DOM update is necessary by comparing the newly returned element with the previously rendered one. When they are not equal, React will update the DOM. This process is called reconciliation.
37. What is the purpose of using `super` constructor with `props` argument in React?

    - A child class constructor cannot make use of this reference until `super()` method has been called. The same applies for ES6 sub-classes as well. The main reason of passing props parameter to `super()` call is to access `this.props` in your child constructors.

    ```jsx
    // passing props:
    class MyComponent extends React.Component {
      constructor(props) {
        super(props);
        console.log(this.props); // Prints { name: 'sudheer',age: 30 }
      }
    }
    // Not passing props:
    class MyComponent extends React.Component {
      constructor(props) {
        super();
        console.log(this.props); // Prints undefined
        // But Props parameter is still available
        console.log(props); // Prints { name: 'sudheer',age: 30 }
      }

      render() {
        // No difference outside constructor
        console.log(this.props); // Prints { name: 'sudheer',age: 30 }
      }
    }
    ```

    - The above code snippets reveals that this.props behavior is different only with in the constructor. It would be same outside the constructor.

38. What happens when you call setState ?
    - The first thing React will do when setState is called is merge the object you passed into setState into the current state of the component. This will kick off a process called reconciliation. The end goal of reconciliation is to, in the most efficient way possible, update the UI based on this new state.
    - To do this, React will construct a new tree of React elements (which you can think of as an object representation of your UI). Once it has this tree, in order to figure out how the UI should change in response to the new state, React will diff this new tree against the previous element tree.
    - By doing this, React will then know the exact changes which occurred, and by knowing exactly what changes occurred, will able to minimize its footprint on the UI by only making updates where absolutely necessary.
39. What is the difference between Element and Component in ReactJS?
    - An element is a plain object describing what you want to appear on the screen in terms of the DOM nodes or other components. Elements can contain other elements in their props. Creating a React element is cheap. Once an element is created, it is never mutated. The object representation of React element would be as follows,
    ```jsx
    const element = React.createElement("div", { id: "login-btn" }, "Login");
    ```
    - The above createElement returns as object as below,
    ```js
    {
        type: 'div',
        props: {
            children: 'Login',
            id: 'login-btn'
        }
    }
    ```
    - And finally it renders to the DOM using ReactDOM.render as below,
    ```jsx
    <div id="login-btn">Login</div>
    ```
    - Whereas a component can be declared in several different ways. It can be a class with a render() method. Alternatively, in simple cases, it can be defined as a function. In either case, it takes props as an input, and returns an element tree as the output. JSX transpiled as createElement at the end.
    ```jsx
    function Button({ onLogin }) {
      return React.createElement(
        "div",
        { id: "login-btn", onClick: onLogin },
        "Login"
      );
    }
    ```
40. What are Higher-Order Components (HOC) in React?
    - A higher-order component (HOC) is a function that takes a component and returns a new component. Basically, it’s a pattern that is derived from React’s compositional nature We call them as “pure’ components” because they can accept any dynamically provided child component but they won’t modify or copy any behavior from their input components.
    ```jsx
    const EnhancedComponent = higherOrderComponent(WrappedComponent);
    ```
    - HOC can be used for many use cases as below,
      1. Code reuse, logic and bootstrap abstraction
      2. Render High jacking
      3. State abstraction and manipulation
      4. Props manipulation
41. How to call loading function with React `useEffect` only once?

    - If you only want to run the function given to `useEffect` after the initial render, you can give it an empty array `[]` as the second argument.
    - For example:

    ```jsx
    function MyComponent() {
      useEffect(() => {
        loadDataOnlyOnce();
      }, []);

      return <div> {/*...*/} </div>;
    }
    ```

42. How to access DOM elements in React?

    - One of the useful application of the `useRef()` hook is to access DOM elements. This is performed in 3 steps:
      1. Define the reference to access the element `const elementRef = useRef()`;
      2. Assign the reference to `ref` attribute of the element: `<div ref={elementRef}></div>`;
      3. After mounting, `elementRef.current` points to the DOM element.
    - Consider:

    ```jsx
    import { useRef, useEffect } from "react";

    function AccessingElement() {
      const elementRef = useRef();

      useEffect(() => {
        const divElement = elementRef.current;
        console.log(divElement); // logs <div>I'm an element</div>
      }, []);

      return <div ref={elementRef}>I'm an element</div>;
    }
    ```
