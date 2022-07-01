1. Do you need to keepIs all component states in Redux store?
   - You need to keep your application state as small as possible. You don't have to push everything in there. Only do it makes a lot of sense to keep something there Or if it makes your life easier when using Dev Tools. But we shouldn't overload its importance too much.
2. What is Redux ?
   - Redux is a predictable state container for JavaScript apps based on the Flux design pattern. Redux can be used together with ReactJS, or with any other view library. It is tiny (about 2kB) and has no dependencies.
3. What is Flux ?
   - Flux is an application design paradigm used as a replacement for the more traditional mvc pattern. It is not a framework or a library but a new kind of architecture that complements React and the concept of Unidirectional Data Flow. Facebook used this pattern internally when working with React The workflow between dispatcher, stores and views components with distinct inputs and outputs as follows:
4. What is Redux DevTools ?
   - Redux DevTools is a live-editing time travel environment for redux with hot reloading, action replay, and customizable UI. If you don’t want to bother with installing Redux DevTools and integrating it into your project, consider using Redux DevTools Extension for Chrome and Firefox.
5. What is the difference between Component and Container in Redux ?
   - Component is part of the React API. A Component is a class or function that describes part of a React UI.
   - Container is an informal term for a React component that is connected to a redux store. Containers receive Redux state updates and dispatch actions, and they usually don't render DOM elements; they delegate rendering to presentational child components.
6. What are reducers in redux ?
   - The reducer is a pure function that takes the previous state and an action, and returns the next state.
   ```js
   (previousState, action) => newState;
   ```
   - It's called a reducer because it's the type of function you would pass to `Array.prototype.reduce(reducer, ?initialValue)`. It's very important that the reducer stays pure. Things you should never do inside a reducer:
   1. Mutate its arguments;
   2. Perform side effects like API calls and routing transitions;
   3. Call non-pure functions, e.g. `Date.now()` or `Math.random()`.
7. What is redux-saga ?
   - redux-saga is a library that aims to make side effects (i.e. asynchronous things like data fetching and impure things like accessing the browser cache) in React/Redux applications easier and better. It is available in NPM as
   ```
   npm install --save redux-saga
   ```
8. How to set initial state in Redux ?

   - You need to pass initial state as second argument to createStore

   ```js
   const rootReducer = combineReducers({
     todos: todos,
     visibilityFilter: visibilityFilter,
   });

   const initialState = {
     todos: [{ id: 123, name: "sudheer", completed: false }],
   };

   const store = createStore(rootReducer, initialState);
   ```

9. What is the difference between React context and React redux ?
   - You can use Context in your application directly and is going to be great for passing down data to deeply nested components which what it was designed for. Whereas Redux is much more powerful and provides a large number of features that the Context Api doesn't provide.
   - Also, React Redux uses context internally but it doesn’t expose this fact in the public API. So you should feel much safer using context via React Redux than directly because if it changes, the burden of updating the code will be on React Redux instead developer responsibility.
10. What is Redux Thunk ?
    - Redux Thunk middleware allows you to write action creators that return a function instead of an action. The thunk can be used to delay the dispatch of an action, or to dispatch only if a certain condition is met. The inner function receives the store methods dispatch and getState() as parameters.
11. How to add multiple middlewares to Redux ?
    - You can use applyMiddleware where you can pass each piece of middleware as a new argument. So you just need to pass each piece of middleware you'd like. For example, you can add Redux Thunk and logger middlewares as an argument as below,
    ```js
    import { createStore, applyMiddleware } from "redux";
    const createStoreWithMiddleware = applyMiddleware(
      ReduxThunk,
      logger
    )(createStore);
    ```
12. What are the features of Redux DevTools ?
    - Below are the major features of Redux devTools
      1. Lets you inspect every state and action payload
      2. Lets you go back in time by “cancelling” actions
      3. If you change the reducer code, each “staged” action will be re-evaluated
      4. If the reducers throw, you will see during which action this happened, and what the error was
      5. With `persistState()` store enhancer, you can persist debug sessions across page reloads
13. How to structure Redux top level directories ?
    - Most of the applications has several top-level directories as below:
      1. Components Used for “dumb” React components unaware of Redux
      2. Containers Used for “smart” React components connected to Redux
      3. Actions Used for all action creators, where file name corresponds to part of the app
      4. Reducers Used for all reducers, where file name corresponds to state key
      5. Store Used for store initialization This structure works well for small and mid-level size apps
14. What are Redux selectors and Why to use them ?
    - Selectors are functions that take Redux state as an argument and return some data to pass to the component. For example, to get user details from the state:
    ```js
    const getUserData = (state) => state.user.data;
    ```
15. What are the core principles of Redux ?
    - Redux follows three fundamental principles:
      1. Single source of truth: The state of your whole application is stored in an object tree within a single store. The single state tree makes it easier to keep track of changes over time and debug or inspect the application.
      2. State is ready only: The only way to change the state is to emit an action, an object describing what happened. This ensures that neither the views nor the network callbacks will ever write directly to the state.
      3. Changes are made with pure functions: To specify how the state tree is transformed by actions, you write pure reducers(Reducers are just pure functions that take the previous state and an action, and return the next state).
16. What is a store in Redux ?
    - A store is an immutable object tree in Redux. A store is a state container which holds the application’s state. Redux can have only a single store in your application. Whenever a store is created in Redux, you need to specify the reducer.
    ```js
    import { createStore } from "redux";
    import reducer from "./reducers/reducer";
    const store = createStore(reducer);
    createStore(reducer, [preloadedState], [enhancer]);
    ```
17. What are typical middleware choices for handling asynchronous calls in Redux ?
    - Redux thunk is a very easy way of introducing a middleware to Redux. It’s even mentioned as the solution for async operations in Redux in the official redux documentation.
    - The saga middleware exposes a set of helper functions to create declarative effects (plain JavaScript objects) that can be yielded by our sagas. The middleware will then handle the objects yielded behind the scenes.
    - The promise middleware returns a promise to the caller in order to wait for the async operation to be completed. This is useful for server-side rendering. There are few packages that can be used as promise based middleware (E.g.- redux-promise-middleware ).
18. Are there any similarities between Redux and RxJS ?
    - Redux uses the Reactive paradigm just a little bit: the Store is reactive. You do not set its content from a distance. That's why there is no store.set() in Redux. The Store observes actions from a distance, and changes itself. And the Store allows others to observe its data from a distance.
    - RxJS also uses the Reactive paradigm, but instead of being an architecture, it gives you basic building blocks, Observables, to accomplish this "observing from a distance" pattern.
19. How to access redux store outside a react component ?

    - Export the store from the module you called createStore with. Then you are assured it will both be created and will not pollute the global window space.

    ```js
    //in store.js
    //this
    const store = createStore(myReducer);
    export store;
    // or this
    const store = createStore(myReducer);
    export default store;
    ```

    ```js
    // in client.js
    import {store} from './MyStore'
    store.dispatch(...)
    ```

    ```js
    // for multiple use cases
    async function getUserStore (userId) {
    // check if user store exists and return or create it.
    }
    export getUserStore
    //
    import {getUserStore} from './store'

    const joeStore = await getUserStore('joe')
    ```

20. What is Redux form ?
    - redux-form is a great way of managing forms that are powered by Redux. It is a Higher-Order-Component (HOC) that uses react-redux to make sure HTML forms in React use Redux to store all of its state.
    - redux-form has the following components to help you build your applications:
      1. `formReducer()`: This is a function that tells how to update the Redux store based on changes coming from the application; those changes are described by Redux actions. `formReducer` has to be mounted on the Redux state at `form`.
      2. `reduxForm()`: The `reduxForm()` function is a higher-order component takes a configuration object and it always returns a new function. It is used to wrap the form component and bind user interaction to the Redux dispatch actions.
      3. The `<Field/>` component: A component that lives inside your wrapped form component. It serves as a way to connect the input elements in a form to the `redux-form logic`. In other words, it’s the way we get the input from what users type.
21. What are the main features of Redux Form ?
    - Field values persistence via Redux store.
    - Validation (sync/async) and submission.
    - Formatting, parsing and normalization of field values.
22. What are the downsides of Redux over Flux ?
    - You'll need to learn to avoid mutations. Flux is unopinionated about mutating data, but Redux doesn't like mutations and many packages complementary to Redux assume you never mutate the state. You can enforce this with dev-only packages like redux-immutable-state-invariant, use Immutable.js, or trust yourself and your team to write non-mutative code, but it's something you need to be aware of, and this needs to be a conscious decision accepted by your team.
    - You're going to have to carefully pick your packages. While Flux explicitly doesn't try to solve “nearby” problems such as undo/redo, persistence, or forms, Redux has extension points such as middleware and store enhancers, and it has spawned a young but rich ecosystem. This means most packages are new ideas and haven't received the critical mass of usage yet. You might depend on something that will be clearly a bad idea a few months later on, but it's hard to tell just yet.
23. How to use connect from react redux ?

    - Before converting a regular React component to a container component using connect(), you have to specify the Redux store to which the component will be connected.

    ```js
    import React from "react";
    import { connect } from "react-redux";
    class NewComment extends React.Component {
      input = null;
      writeComment = (evt) => {
        evt.preventDefault();
        const comment = this.input.value;

        comment && this.props.dispatch({ type: "WRITE_COMMENT", comment });
      };
      render() {
        const { id, content } = this.props.comment;

        return (
          <div>
            <input
              type="text"
              ref={(e) => (this.input = e)}
              placeholder="Write a comment"
            />
            <button type="button" onClick={this.writeComment}>
              Submit Comment
            </button>
          </div>
        );
      }
    }
    export default connect()(NewComment);
    ```

24. What is the purpose of the constants in Redux ?

    - constants come into the picture, it provides a way to define the type of actions and reducers at one file or one place.
    - Type of the actions and reducers are being used at two different files. Constants help to import them and use them from a single page.
    - Readability of code increases because all constants are listed in one file and gives info in one read.
    - It helps to reduce small typing issues bugs while writing.

25. What are the differences between redux-saga and redux-thunk ?
    - Redux-Thunk has less boilerplate code than Redux-Saga
    - Redux-Thunk is easy-to-understand than Redux-Saga
    - Redux-Thunk is hard-to-scale than Redux-Sage
    - Redux-Thunk holds more async logic in action creators than Redux-Saga has pure creators
    - Redux-Thunk is hard to test than Redux-Saga
26. What is a Reducer ?

    - In Redux, a reducer is a pure function that takes an action and the previous state of the application and returns the new state. The action describes what happened and it is the reducer's job to return the new state based on that action.

    ```js
    (previousState, action) => newState;
    ```

    - The reducer takes two parameters: state and action. You need to have an initial value so that when Redux calls the reducer for the first time with undefined, it will return the initialState. Then the function uses a switch statement to determine which type of action it's dealing with. If there is an unknown action, then it should return the state, so that the application doesn't lose its current state.

    ```js
    const initialState = {
      username: "",
      messages: [],
    };

    function reducer(state = initialState, action) {
      switch (action.type) {
        case CHANGE_USERNAME:
          return {
            ...state,
            username: action.username,
          };
        default:
          return state;
      }
    }
    ```

27. How to reset state in redux ?

    - write a root reducer in application, for example:

    ```js
    const rootReducer = combineReducers({
      /* your app’s top-level reducers */
    });
    const appReducer = combineReducers({
      /* your app’s top-level reducers */
    });

    const rootReducer = (state, action) => {
      if (action.type === "USER_LOGOUT") {
        const { routing } = state;
        state = { routing };
      }
      return appReducer(state, action);
    };
    ```

28. How to make Ajax request in Redux ?

    - apply redux-thunk middleware which allows you to define async actions.

    ```js
    export function fetchBook(id) {
      return (dispatch) => {
        dispatch(setLoadingBookState()); // Show a loading spinner
        fetch(`/book/${id}`, (response) => {
          dispatch(doneFetchingBook()); // Hide loading spinner
          if (response.status == 200) {
            dispatch(setBook(response.json)); // Use a normal function to set the received state
          } else {
            dispatch(someError);
          }
        });
      };
    }

    function setBook(data) {
      return { type: "SET_BOOK", data: data };
    }
    ```

29. Whats the purpose of at @ symbol in the redux connect decorator ?
    - it is equal to below example, @ it is just high order function prefix.
    ```js
    // normal connect
    class MyApp extends React.Component {
    // ...define your main app here
    }
    export default connect(mapStateToProps, mapDispatchToProps)(MyApp);
    // with @ prefix
    @connect(mapStateToProps, mapDispatchToProps)
    export default class MyApp extends React.Component {
    // ...define your main app here
    }
    ```
30. What are the differences between `call` and `put` in redux-saga ?

    - Both `call()` and `put()` are effect creator functions. `call()` function is used to create effect description, which instructs middleware to call the promise. `put()` function creates an effect, which instructs middleware to dispatch an action to the store.

    ```js
    function* fetchUserSaga(action) {
      // `call` function accepts rest arguments, which will be passed to `api.fetchUser` function.
      // Instructing middleware to call promise, it resolved value will be assigned to `userData` variable
      const userData = yield call(api.fetchUser, action.userId);

      // Instructing middleware to dispatch corresponding action.
      yield put({
        type: "FETCH_USER_SUCCESS",
        userData,
      });
    }
    ```

31. Why are Redux state functions called as reducers ?
    - Reducers do not just return default values. They always return the accumulation of the state (based on all previous and current actions).
    - Therefore, they act as a reducer of state. Each time a redux reducer is called, the state is passed in with the action (state, action). This state is then reduced (or accumulated) based on the action, and then the next state is returned. This is one cycle of the classic fold or reduce function.
32. What is the proper way to access Redux store ?
    - The best way to access your store in a component is to use the connect() function, that creates a new component that wraps around your existing one. This pattern is called Higher-Order Components, and is generally the preferred way of extending a component's functionality in React. This allows you to map state and action creators to your component, and have them passed in automatically as your store updates.
    ```js
    import { connect } from "react-redux";
    import { setVisibilityFilter } from "../actions";
    import Link from "../components/Link";
    const mapStateToProps = (state, ownProps) => ({
      active: ownProps.filter === state.visibilityFilter,
    });
    const mapDispatchToProps = (dispatch, ownProps) => ({
      onClick: () => dispatch(setVisibilityFilter(ownProps.filter)),
    });
    const FilterLink = connect(mapStateToProps, mapDispatchToProps)(Link);
    export default FilterLink;
    ```
33. What is Redux Thunk used for ?

    - Redux Thunk is a middleware that lets you call action creators that return a function instead of an action object. That function receives the store’s dispatch method, which is then used to dispatch regular synchronous actions inside the function’s body once the asynchronous operations have been completed.

    ```js
    import {
      ADD_TODO_SUCCESS,
      ADD_TODO_FAILURE,
      ADD_TODO_STARTED,
      DELETE_TODO,
    } from "./types";

    import axios from "axios";

    export const addTodo = ({ title, userId }) => {
      return (dispatch) => {
        dispatch(addTodoStarted());

        axios
          .post(`https://jsonplaceholder.typicode.com/todos`, {
            title,
            userId,
            completed: false,
          })
          .then((res) => {
            dispatch(addTodoSuccess(res.data));
          })
          .catch((err) => {
            dispatch(addTodoFailure(err.message));
          });
      };
    };

    const addTodoSuccess = (todo) => ({
      type: ADD_TODO_SUCCESS,
      payload: {
        ...todo,
      },
    });

    const addTodoStarted = () => ({
      type: ADD_TODO_STARTED,
    });

    const addTodoFailure = (error) => ({
      type: ADD_TODO_FAILURE,
      payload: {
        error,
      },
    });
    ```

34. What is the mental model of redux-saga ?
    - Saga is like a separate thread in your application, that's solely responsible for side effects. `redux-saga` is a redux middleware, which means this thread can be started, paused and cancelled from the main application with normal Redux actions, it has access to the full Redux application state and it can dispatch Redux actions as well.
35. How Relay is different from Redux ?
    - Relay is similar to Redux in that they both use a single store. The main difference is that relay only manages state originated from the server, and all access to the state is used via GraphQL queries (for reading data) and mutations (for changing data). Relay caches the data for you and optimizes data fetching for you, by fetching only changed data and nothing more.
