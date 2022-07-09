1. What are native apps ?

- Native mobile apps are the most common type of app.
- They are built for specific platforms and are written in languages that the platform accepts. For example, `Swift` and `Objective-C` for native iOS apps and `Java` or `Kotlin` for native Android apps.
- Native apps are also built using the specific Integrated Development Environment (IDE) for the selected operating systems

2. List some benefits of using React Native for building mobile apps ?

- Some benefits of React Native are:
  1. Known for Optimal Performance
  2. Can Reuse the Codes and Pre-Developed Components
  3. Large Community of Developers
  4. Advantage of Live and Hot Reloading
  5. Cost Effective Solution
  6. Offers Simple User Interface
  7. Support for Third-Party Plugins
  8. Modular Architecture
  9. Providing Handy Solutions and Libraries

3. Why do we use curly brace while importing some library ?

- Consider:

```js
import { Text, StyleSheet } from "react-native";
```

- Curly braces are used to import small pieces of library. In above example we just want to make use of Text and StyleSheet component from react-native, so they are put in curly braces.

4. What are the advantages of hybrid apps over native apps ?

- Works across multiple platforms.
- Unified development.
- Faster build and lower cost of development.
- Easier to make changes and update.

5. What are hybrid apps ?

- Hybrid mobile apps are applications that are installed on a device, just like any other app.
- Hybrid apps are deployed in a native container that uses a mobile WebView object. When the app is used, this object displays web content thanks to the use of web technologies (CSS, JavaScript, HTML).

6. What is React Native ?

- `React Native` is a mobile app development framework that enables the development of multi-platform Android and iOS apps using native UI elements.
- It is based on the JavaScriptCore runtime and Babel transformers. With this setup react native supports new `JavaScript` (ES6+) features, e.g. arrow functions, async/await etc.
- This famous framework for mobile app development started in the summer of 2013 as Facebook’s internal hackathon project.
- Its first public preview was released in January of 2015 at `Reactjs` Conference and in March of 2015, Facebook made React Native open and available on GitHub.

7. How do you dismiss the keyboard in react native ?

- Using `Keyboard.dismiss()`

```js
import { Keyboard } from "react-native";
// Hiding the keyboard
Keyboard.dismiss();
```

8. What is JSX ?

- `JSX` is an XML/HTML-like syntax used by `React` that extends ECMAScript so that XML/HTML-like text can co-exist with `JavaScript/React` code.
- The syntax is intended to be used by preprocessors (i.e., transpilers like Babel) to transform HTML-like text found in JavaScript files into standard JavaScript objects that a JavaScript engine will parse.

```jsx
const nav = (
  <ul id="nav">
    <li>
      <a href="#">Home</a>
    </li>
    <li>
      <a href="#">About</a>
    </li>
    <li>
      <a href="#">Clients</a>
    </li>
    <li>
      <a href="#">Contact Us</a>
    </li>
  </ul>
);
```

9. What are props in React Native ?

- The properties of React Native components are simply pronounced as props.
- In React Native, most of the components can be customized at the time of their creation with different parameters. These parameters are known as props.
- They are immutable, and they cannot be changed.

```jsx
import React, { Component } from "react";
import { Platform, StyleSheet, Image, Text, View } from "react-native";

export default class App extends Component<{}> {
  render() {
    let imagePath = {
      uri: "https://facebook.github.io/react-native/img/header_logo.png",
    };
    return (
      <View style={styles.container}>
        <Text style={styles.welcome}>Welcome to React Native!</Text>
        <Image source={imagePath} style={{ width: 250, height: 250 }} />
      </View>
    );
  }
}

const styles = StyleSheet.create({
  container: {
    flex: 1,
    justifyContent: "center",
    alignItems: "center",
    backgroundColor: "#a7a6a9",
  },
  welcome: {
    fontSize: 30,
    textAlign: "center",
    margin: 20,
  },
});
```

10. Tell us some options of storing persisting data in a react native app ?

- Some popular options are:
  1. Async Storage ("built-in" to React Native)
  2. SQLite
  3. Realm
  4. Firebase
  5. MongoDB

11. Will this piece of code work ?

```jsx
<View>
  <Text>Hey there!</Text>
  <Text style={{ fontsize: 40 }}>Example of inline style</Text>;
</View>
```

- No. An error will be thrown as `Text` strings must be rendered within `Text` component. Because here semi-colon in third line will be treated as text, and in React native all texts needs to be rendered inside `Text` tag.

12. What are the advantages of native apps over hybrid apps ?

- They work efficiently as they are built for that specific platforms
- Native apps are responsive on all the platform-specific devices
- They are very fast and the best in the app performance
- Native apps better integrate with mobile hardware
- They have interactive and intuitive User Interface (UI) and User Experience (UX) as per the user expectations based on specific platforms
- Some of the Native mobile apps work even without the Internet connection
- Native apps are secured and reliable
- They can easily access or utilize the other device-specific capabilities like GPS, Camera, Contacts, etc.

13. What are Refs used for in React Native ?

- Refs provide you direct access to a DOM element or a components instance.

14. What are the types of data that control a component ?

- There are two types of data that control a component: `props` and `state`.
- `props` are set by the parent and they are fixed throughout the lifetime of a component. For data that is going to change, we have to use `state`.

15. What does the Gesture Responder System do ?

- The gesture responder system manages the lifecycle of gestures in an app.

16. What determines the size of a component and what are the ways ?

- The height and width determine the size of component on the screen.
- Two different ways to set height and width. - Fixed Dimensions - Flex Dimensions

17. What are some ways of styling a react native component ?

- we can use:
  1. Inline styling
  2. StyleSheet
  3. Styled Components

18. What are components ?

- Components are the building blocks of any `React` application.
- Components let you split the UI into `independent`, `reusable` pieces, and think about each piece in isolation.
- React Native provides a number of built-in components. Some are:- - Basic Components - User Interface - List Views - iOS-specific - Android-specific

19. When would you use ScrollView over FlatList or vice-versa ?

- Do you need to render a list of similar items from an array or the data is very big? Use `FlatList`
- Do you need to render generic content in a scrollable container and the data is small? Use ScrollView

20. How is React Native different from ReactJS ?

- ReactJS React has as its main focus Web Development.
  1. React’s virtual DOM is faster than the conventional full refresh model, since the virtual DOM refreshes only parts of the page.
  2. We use div, p, span, etc. HTML tags to build the UI of the web application.
  3. You can reuse code components in React, saving you a lot of time. (You can in React Native too.)
  4. As a business: The rendering of your pages completely, from the server to the browser will improve the SEO of your web app.
  5. It improves the debugging speed making your developer’s life easier.
  6. You can use hybrid mobile app development, like Cordova or Ionic, to build mobile apps with React, but is more efficiently building mobile apps with React Native from many points.

21. Explain the use of Flexbox in React Native ?

- `flex` defines how much of a view will fill the screen. Available values are integers greater than or equal to 0.
- `flexDirection` determines in which direction—vertically or horizontally—the children are laid out. Available values include `column`, `row`, `column-reverse`, and `row-reverse`.
- `justifyContent` determines how an item should render along the primary axis (determined by the `flexDirection` property). Available values are `flex-start`, `flex-end`, `center`, `space-between`, `space-around`, and `space-evenly`.
- `alignItems` determines how an item should be rendered along the secondary axis (determined by the `flexDirection` property). Available values are `flex-start`, `flex-end`, `center`, and `baseline`.
- `alignSelf` determines how a child should align itself and overrides `alignItems`. Available values are `flex-start`, `flex-end`, `center`, and `baseline`
- `flexWrap` determines what happens when the children of a container overflow outside the container. By default, they are forced to fit into a single line, which consequently shrinks them.
- When the `flexWrap` property is set to `wrap`, children of the container can spill over into multiple lines.

22. What is flex dimension and how is it different from fixed dimension ?

- The flex property styles the component to expand and shrink it dynamically according to available space unlike fixed dimension where a specific height, width is specified.
- Setting `flex: 1` will fill all the available space to the component, and shared evenly among the other components of same as the parent.
- Higher the flex value, occupy component higher ratio of space compared to its siblings.

23. How are props and state different ?

- Props:
  1. are immutable which lets React to fast reference checks
  2. are used to pass data down from your view-controller for top level component
  3. have better performance which use this to pass data to child components
- state:
  1. should be managed in your view-controller for top level component
  2. is mutable
  3. has worse performance
  4. should not be accessed from child components which pass it down with props instead

24. What happens if you edit modules with exports that aren't React components in Fast Refresh ?

- Fast Refresh will re-run both that module, and the other modules importing it.
- So if both Button.js and Modal.js import Theme.js, editing Theme.js will update both components.

25. How is flexbox different in React Native and browser ?

- Flexbox works the same way in React Native as it does in CSS on the web, with a few exceptions. The defaults are different, with flexDirection defaulting to column instead of row, and the flex parameter only supporting a single number.

26. How are Hot Reloading and Live Reloading in React Native different ?

- Live reloading reloads or refreshes the entire app when a file changes. For example, if you were four links deep into your navigation and saved a change, live reloading would restart the app and load the app back to the initial route.
- Hot reloading only refreshes the files that were changed without losing the state of the app. For example, if you were four links deep into your navigation and saved a change to some styling, the state would not change, but the new styles would appear on the page without having to navigate back to the page you are on because you would still be on the same page.

27. What is AppRegistry ? Why is it required early in "require" sequence ?

- `AppRegistry` is the JS entry point to running all React Native apps.
- App root components should register themselves with `AppRegistry.registerComponent`, then the native system can load the bundle for the app and then actually run the app when it's ready by invoking `AppRegistry.runApplication`.
- `AppRegistry` should be required early in the `require` sequence to make sure the JS execution environment is setup before other modules are required.

28. What does StyleSheet.create do and why is it useful ?

- StyleSheet.create function validates the keys and register them to react
- creates a stylesheet style reference from the specified object
- allows you to send the style only once through the bridge while referring to all subsequent users through ID.
- styleSheet.create useful because it similiar to React styled component syntax, lesser learning curve for web dev.

29. How do you re-render a FlatList ?

- Use the `extraData` property on FlatList component passing the state value to it. Whenever state is change, the FlatList will re-render itself. Without a state, FlatList is just a PureComponent.

30. What is the use of ScrollView component ?

- The `ScrollView` is a generic scrolling container that can contain multiple components and views. The scrollable items can be heterogeneous, and you can scroll both vertically and horizontally (by setting the `horizontal` property).
- ScrollViews can be configured to allow paging through views using swiping gestures by using the pagingEnabled props. Swiping horizontally between views can also be implemented on Android using the ViewPager component.
- The ScrollView works best to present a small number of things of a limited size. All the elements and views of a ScrollView are rendered, even if they are not currently shown on the screen. If you have a long list of items which cannot fit on the screen, you should use a FlatList instead. So let's learn about list views next.

31. In Fast Refresh, what will happen if you edit files imported by modules outside of the React Tree ?

- Fast fresh will fall back to doing a full reload.
- For a file which renders a React component but also exports a value that is imported by a non-React component, consider migrating the query to a separate file and importing it into both files. This will re-enable Fast refresh to work.

32. What is Lifting State up ?

- Lifting state up meaning when you have parent component and child component, you could put the state at parent level and child level just get pass props or state or function in it.

33. What happens if you edit a module that only exports React components in Fast Refresh ?

- Fast Refresh will update the code only for that file, and re-render your component. You can edit anything in that file, including styles, rendering logic, event handlers, or effects.

34. What is the use of FlatList ?

- The FlatList component is an efficient way to display items in a scrollable list view. This component has many supported features such as Scroll Loading, header/footer views support, horizontal mode, pull to refresh.
- FlatList is used to render the items in a scrollable list view.
- Large Data: When we have a large list of data and the number of data can change over time we can use FlatList as large data affect rendering speed and using FlatList won't affect the rendering speed.
- FlatList is used when we want to render only those elements that are currently being displayed on the screen(default: 10 items)
- For automatic memory management and to handle data changes in list we use a flat list.
- FlatList can be used when we want the separator between the list items with ItemSeparatorComponent prop.

35. What is State in react native ?

- State is the place where the data comes from. We should always try to make our state as simple as possible and minimize the number of stateful components. If we have, for example, ten components that need data from the state, we should create one container component that will keep the state for all of them.

```jsx
import React, { Component } from "react";
import { Text, View, Button, Alert } from "react-native";

class App extends Component {
  constructor(props) {
    super(props);
    this.state = { isToggle: true };
  }

  render(props) {
    return (
      <View style={{ flex: 1, justifyContent: "center", margin: 15 }}>
        <Button
          onPress={() => {
            this.setState({ isToggle: !this.state.isToggle });
          }}
          title={this.state.isToggle ? "ON" : "OFF"}
          color="green"
        />
      </View>
    );
  }
}
export default App;
```

36. What are Touchable Interactions in React Native ?

- React Native provides components to handle all sorts of common gestures, as well as a comprehensive gesture responder system to allow for more advanced gesture recognition, but the one component you will most likely be interested in is the basic Button.
- The "Touchable" components provide the capability to capture tapping gestures, and can display feedback when a gesture is recognized. These components do not provide any default styling, however, so you will need to do a bit of work to get them looking nicely in your app.

37. What is "Fast Refresh" ?

- Fast Refresh is a React Native feature that allows you to get near-instant feedback for changes in your React components. Fast Refresh is enabled by default, and you can toggle "Enable Fast Refresh" in the React Native developer menu. With Fast Refresh enabled, most edits should be visible within a second or two.
- If you edit a module that only exports React component(s), Fast Refresh will update the code only for that module, and re-render your component. You can edit anything in that file, including styles, rendering logic, event handlers, or effects.
- If you edit a module with exports that aren't React components, Fast Refresh will re-run both that module, and the other modules importing it. So if both Button.js and Modal.js import Theme.js, editing Theme.js will update both components.
- Finally, if you edit a file that's imported by modules outside of the React tree, Fast Refresh will fall back to doing a full reload. You might have a file which renders a React component but also exports a value that is imported by a non-React component. For example, maybe your component also exports a constant, and a non-React utility module imports it. In that case, consider migrating the constant to a separate file and importing it into both files. This will re-enable Fast Refresh to work. Other cases can usually be solved in a similar way.

39. How do you style a component in react native ?

- Using Inline Styles: Using inline styles is preferred only for small very small components. For large-scale production applications, it becomes cumbersome and inefficient to use inline styles.
- Using StyleSheet: As a component grows in complexity, it is much cleaner and efficient to use StyleSheet.create to define several styles in one place.

40. How do you perform logging in React native ?

- using console.log()

```jsx
console.log("App executed");
```

- using console.warn()

```jsx
console.warn("Hi Geek!! Lets code together!");
```

- using react-native-logs:

```jsx
import React from "react";
import { Text, View } from "react-native";
import { logger } from "react-native-logs";

export default function App() {
  var log = logger.createLogger();

  log.debug("I am a Debug log");
  log.info("I am a Info log");
  log.warn("I am a Warning log");
  log.error("I am a Error log");
}
```

41. What does TouchableHighlight do and when do you use it ?

- A wrapper for making views respond properly to touches. On press down, the opacity of the wrapped view is decreased, which allows the underlay color to show through, darkening or tinting the view.
- When to use it: On iOS for touchable elements or buttons that have a solid shape or background, and on ListView items.

42. What is View and how important is it ?

- The most fundamental component for building a UI, View is a container that supports layout with flexbox, style, some touch handling, and accessibility controls.
- View maps directly to the native view equivalent on whatever platform React Native is running on, whether that is a UIView, `<div>`, android.view, etc.

43. What is `autolinking` in react-native ?

- Autolinking is a mechanism that allows your project to discover and use this code.
- Each platform defines its own platforms configuration. It instructs the CLI on how to find information about native dependencies. This information is exposed through the config command in a JSON format. It's then used by the scripts run by the platform's build tools. Each script applies the logic to link native dependencies specific to its platform.

44. What are some features of Fast Refresh ?

- If you edit a module that only exports React component(s), Fast Refresh will update the code only for that module, and re-render your component. You can edit anything in that file, including styles, rendering logic, event handlers, or effects.
- If you edit a module with exports that aren't React components, Fast Refresh will re-run both that module, and the other modules importing it. So if both Button.js and Modal.js import Theme.js, editing Theme.js will update both components.
- Finally, if you edit a file that's imported by modules outside of the React tree, Fast Refresh will fall back to doing a full reload. You might have a file which renders a React component but also exports a value that is imported by a non-React component. For example, maybe your component also exports a constant, and a non-React utility module imports it. In that case, consider migrating the constant to a separate file and importing it into both files. This will re-enable Fast Refresh to work. Other cases can usually be solved in a similar way.

45. What is Component Driven Development (CDD) ?

- Component-Driven Development (CDD) is a development methodology that anchors the build process around components. It is a process that builds UIs from the “bottom up” by starting at the level of components and ending at the level of pages or screens.

46. What are Container/Smart components ?

- Smart components (or container components) on the other hand have a different responsibility. Because they have the burden of being smart, they are the ones that keep track of state and care about how the app works.
- Using the container design pattern, the container components are separated from the presentational components and each handles their own side of things. The container components do the heavy lifting and pass the data down to the presentational components as props.
- These components also often contain other callback functions that are used to update the state and get passed down to their child components as props.
- The root component off an app is a good example of a smart component. It is often responsible for maintaining several pieces of state for the entire app and needs to pass down additional functions to its child components so that the state can be updated when a user interacts with the site.

47. What are Presentational/Dumb Components ?

- Dumb components are also called ‘presentational’ components because their only responsibility is to present something to the DOM. Once that is done, the component is done with it. No keeping tabs on it, no checking in once in a while to see how things are going. Nope. Put the info on the page and move on.
- The components themselves only have a render() method (they don’t need any others) and are often just Javascript functions. They don’t have internal state to manage. They wouldn’t know how to change the data they are presenting if they were asked. Ignorance is bliss.

```jsx
const Footer = (props) => {
  return (
    <div>
      <ul>
        <li>Footer Information</li>
      </ul>
    </div>
  );
};
```

48. What does React Native Packager do in the React Native ?

- A React Native app is a compiled app that is running some Javascript. Whenever you build and run your React Native project, a packager starts up called Metro.
- The packager does a few things:
  1. Combines all your Javascript code into a single file, and translates any Javascript code that your device won’t understand (like JSX or some of the newer JS syntax).
  2. Converts assets (e.g. PNG files) into objects that can be displayed by an Image component.

49. What is Higher Order Component or HOC ?

- A higher-order component (HOC) is an advanced element for reusing logic in React components. Components take one or more components as arguments, and return a new upgraded component. Sounds familiar, right? They are similar to higher-order functions, which take some functions as an argument and produce a new function.
- HOCs are commonly used to design components with certain shared behavior in a way that makes them connected differently than normal state-to-props pattern.
- HOCS do not modify or mutate component, just create new one.
- HOCS letting the code reusable.
- HOCS are just pure function, do not have any side effects and return only new component.
- etc. react-redux `connect(mapStateToProps, mapDispatchToProps)(UserPage)`, react-router `withRouter(UserPage)`, material-ui `withStyles(styles)(UserPage)`

50. What Javascript engine does React native use ?

- In most cases, React Native will use JavaScriptCore, the JavaScript engine that powers Safari. Note that on iOS, JavaScriptCore does not use JIT due to the absence of writable executable memory in iOS apps.
- When using Chrome debugging, all JavaScript code runs within Chrome itself, communicating with native code via WebSockets. Chrome uses V8 as its JavaScript engine.

51. Are libraries such as Typescript that compile to Javascript compatible with React Native ?

- Languages that compile to javascript are generally compatible with React Native.
- React Native uses Babel to transform javascript into a form that is consumable by the native OS's javascript runtime, using the `react-native` Babel plugin.
- As long as Bebel can compile your javascript, and your code does not rely on web or Node.js-specific dependencies, it will run in React Native.

52. What are features of presentational/dumb components ?

- Focus on the UI: Dumb components mainly focus on how things look. So almost all UI components like buttons, inputs, modals, etc should be considered dumb components.
- Accepting props: Dumb components accept props to receive data and the callback function from the parent component. This makes them dynamic and reusable.
- The state is rarely included: Dumb component does not include state, the only time it includes state is to manipulate the UI itself not the data.
- No dependencies: Dumb components do not require any dependencies on the rest of the app.
- Easy Testing: It is easy to test dumb components as it only takes props and returns the UI. It does not have any complex logic or state for data.

53. Differentiate ScrollView and FlatList ?

- memory management: ScrollView does not provide; FlatList automatic provides.
- content loading: ScrollView loads content at once; FlatList load content as window scroll.
- render speed: ScrollView has slow rendering speed and will increase memory usage; FlatList does not affect the rendering speed.
- state maintain: ScrollView does maintains component state; FlatList does not maintain component state.
- render type: ScrollView render content as scrollable container; FlatList renders a list of items.

54. How would you implement animations on events ?

- Gestures, like panning or scrolling, and other events can map directly to animated values using Animated.event(). This is done with a structured map syntax so that values can be extracted from complex event objects. The first level is an array to allow mapping across multiple args, and that array contains nested objects.
- Animated.event()
- For example, when working with horizontal scrolling gestures, you would do the following in order to map event.nativeEvent.contentOffset.x to scrollX (an Animated.Value):

```jsx
 onScroll={Animated.event(
   // scrollX = e.nativeEvent.contentOffset.x
   [{ nativeEvent: {
        contentOffset: {
          x: scrollX
        }
      }
    }]
 )}
```

55. How many threads run in a React Native app ?

- There are three threads that mainly run a React Native app:
  1. The UI thread — this is the native thread used to run Swift/Objective C in iOS devices and Java/Kotlin in Android devices, an application’s UI is manipulated solely on this thread. Here the application’s Views are rendered and users of the app can interact with the OS. Most of the heavy lifting in this thread is performed by React Native
  2. The JavaScript thread — this is the thread that executes JavaScript separately via a JavaScript engine. An application’s logic – including which Views to display and in what manner they are displayed — is usually configured here
  3. The bridge — React Native’s bridge enables communication between the UI and JS thread

56. State the lifecycle of Gesture Responder System ?

- There are three steps what define any gesture, it defines as below:
- onStartShouldSetResponder: Does this view want to become responder on the start of a touch?

```jsx
onStartShouldSetResponder: (event) => true | false;
```

- onMoveShouldSetResponser: Called for every touch move on the View when it is not the responder. Does this view want to “claim” touch responsiveness?

```jsx
onMoveShouldSetResponder: (event) => true | false;
```

- onResponderGrant: The View is now responding for touch events.
- onResponderReject: Something else is the responder right now.
- onResponderMove: The user is moving their finger.
- onResponderRelease: Fired at the end of the touch.

57. What are the features of Container/Smart components ?

- Manipulates Data Smart components can fetch, capture changes and pass down application data.
- Call Redux, Lifecycle methods, APIs, Libraries, etc These components are called smart for a reason! They are responsible for calling libraries and functionality.
- Manage state Smart components are responsible for managing state and knowing when to re-render a component.
- Rarely includes styling Since dumb components focus on styling, it allows the smart component to focus on functionality without the clutter of styles too.

58. What are some limitations of using react-native-cli for instantiating a project ?

- Needs Android Studio and/or XCode to run the projects
- Can't not develop for IOS without having a mac
- Device has to be connected via USB to use it for testing
- Fonts need to be imported manually in XCode
- If you want to share the app you need to send the whole .apk /.ipa file
- Does not provide JS APIs out of the box, e.g. Push-Notifications, Asset Manager, they need to be manually installed and linked with npm for example
- Setting up a working project properly(including device configuration) is rather complicated and can take time.

59. What is AsyncStorage and how do you use it ?

- AsyncStorage is React Native’s API for storing data persistently over the device. It’s a storage system that developers can use and save data in the form of key-value pairs. If you are coming from a web developer background, it resembles a lot like localStorage browser API.
- use case:

```jsx
// set item to async storage
const userId = "8ba790f3-5acd-4a08-bc6a-97a36c124f29";
const saveUserId = async (userId) => {
  try {
    await AsyncStorage.setItem("userId", userId);
  } catch (error) {
    // Error retrieving data
    console.log(error.message);
  }
};
// retrieve value from AsyncStorage
const getUserId = async () => {
  let userId = "";
  try {
    userId = (await AsyncStorage.getItem("userId")) || "none";
  } catch (error) {
    // Error retrieving data
    console.log(error.message);
  }
  return userId;
};
// Delete value from AsyncStorage
const deleteUserId = async () => {
  try {
    await AsyncStorage.removeItem('userId');
  } catch (error) {
    // Error retrieving data
    console.log(error.message);
  }
}
// with redux
import {AsyncStorage} from 'react-native';
const initialState = {
  id: null,
  sessionId: null,
  username: null,
  password: null
};
export default (state = initialState, action) => {
  switch (action.type) {
    case 'SAVE_USER':
      // save sessionId & userId in AsyncStorage
      if (action.user.sessionId) {
        AsyncStorage.setItem('sessionId', action.user.sessionId);
      }
      if (action.user.id) {
        AsyncStorage.setItem('userId', action.user.id);
      }
      return {
        ...state,
        id: action.user.id || state.id,
        sessionId: action.user.sessionId || state.sessionId,
        username: action.user.username || state.username,
        password: action.user.password || state.password
      });
    default:
      return state;
  }
};
```

60. What are some advantages of Component Driven Development ?

- Reusability: In Component Driven Development, the development process is in place, components once created can be easily used across as many modules as needed. Reusability helps to provide the development efforts and cost across applications.
- Repetition: An application is often an interface made up of repeating components. Repetition in component developments provides developers to maintain and scale their code on large. Repetition provides familiarity which makes the user feel the symmetric design and helps them to make informed decisions.
- Scalability: Component Driven Development allows for extending the benefits of a modular architecture to the frontend as well. As the React application scales, more no components for the features can be easily added without changing the entire codebase.
- Simpler maintenance: Component Driven Development models in software engineering keep you away from such unwanted situations. CDD decomposes the frontend files into smaller and easily manageable components which are easy to handle, making any upgrade or modification become an easy task.
- Faster development: Component Driven Development reduces development time a lot, furthermore the relationship with the codebase. With the use of shared library accessible, working teams no longer need to build the solutions from scratch. They can use components from this library without worrying about non-functional requirements such as security, usability, performance, etc.

61. Does React Native compile Javascript into Java for android ?

- Basically, you write Javascript. The Javascript communicates with native components (Java on Android, Objective C on iOS, C# on Windows).
- The communication occurs through the so-called "bridge". If at any time you feel that this communication slows things down too much, you can choose to implement the Javascript functionality in Java, Objective C, or C# respectively in order to run purely native. In this case, you are writing directly in native code, so there's no Javascript to native compilation.

62. How does the Fabric architecture work ?

- there are still three threads but designed in a way to make them as performant and efficient as possible. The first main concept that is used is, now the tasks are divided into sync and async instead of only async. It enables us to perform the important UI operations first and in sync with the frame rate of the mobile screen. In this way, absolute no frame is dropped as the tasks are executed in sync with the user interactions (high priority). Also as any thread can bring out the changes in the Shadow thread (synched with the main thread for priority tasks), it would have to be made immutable to have the consistency and avoid deadlocks.
- The other important concept which would greatly reduce the memory consumption is using references instead of a whole new copy of the DOM nodes. This is very helpful in having consistent and efficient DOM nodes. Also with the reference, we can perform any operation that we would have done with its copy but in a much quicker way.

63. What are some benefits of Container-Presentational pattern ?

- Better separation of concerns. You understand your app and your UI better by writing components this way.
- Better reusability. You can use the same presentational component with completely different state sources, and turn those into separate container components that can be further reused.
- Presentational components are essentially your app’s “palette”. You can put them on a single page and let the designer tweak all their variations without touching the app’s logic. You can run screenshot regression tests on that page.
- This forces you to extract “layout components” such as Sidebar, Page, ContextMenu and use this.props.children instead of duplicating the same markup and layout in several container components.

64. What is InterationManager and how is it used ?

- InteractionManager allows long-running work to be scheduled after any interactions/animations have completed. In particular, this allows JavaScript animations to run smoothly.

```jsx
const useMount = (func) => useEffect(() => func(), []);
const useFadeIn = (duration = 5000) => {
  const [opacity] = useState(new Animated.Value(0));
  useMount(() => {
    Animated.timing(opacity, {
      toValue: 1,
      duration,
    }).start();
  });
  return opacity;
};

const Ball = ({ onShown }) => {
  const opacity = useFadeIn();
  useMount(() => {
    const interactionPromise = InteractionManager.runAfterInteractions(() =>
      onShown()
    );
    return () => interactionPromise.cancel();
  });
  return <Animated.View style={[styles.ball, { opacity }]} />;
};

const App = () => {
  return (
    <View style={styles.container}>
      <Text>{instructions}</Text>
      <Ball onShown={() => Alert.alert("Animation is done")} />
    </View>
  );
};
export default App;
```

65. What is wrong with this code for querying a native API ?

```jsx
class GyroJs {
  setGyroPosition(pos) {
    if (pos === null || typeof pos === "undefined") {
      throw new Error("The position must be defined");
    }
    this.pos = pos;
  }
  constructor() {
    const gyroscopePosition = NativeModules.MyGyroModule.gyroPosition();
    this.setGyroPosition(gyroscopePosition);
  }
}
```

- This code will always throw an error because the value of gyroscopePosition will always be an unresolved Promise. It’s important to remember that the bridge that connects JavaScript and native code is asynchronous. We can either receive results from this side by passing in a callback (not done in this example), or by returning a Promise. In this case, we need to append a then() call to the gyroPosition() call and set the position inside it.

66. What is Fabric in React Native ?

- Fabric is React Native's new rendering system, a conceptual evolution of the legacy render system. The core principles are to unify more render logic in C++, improve interoperability with host platforms, and to unlock new capabilities for React Native. Development began in 2018 and in 2021, React Native in the Facebook app is backed by the new renderer.
- With improved interoperability between host views and React views, the renderer is able to measure and render React surfaces synchronously. In the legacy architecture, React Native layout was asynchronous which led to a layout “jump” issue when embedding a React Native rendered view in a host view.
- With support of multi-priority and synchronous events, the renderer can prioritize certain user interactions to ensure they are handled in a timely manner.
- Integration with React Suspense which allows for more intuitive design of data fetching in React apps.
- Enable React Concurrent Features on React Native.
- Easier to implement server side rendering for React Native.

67. Does React Native have a Virtual DOM ?

- yes, React Native use below strategy to produce similiar funcitionality to mobile with Virtual DOM.
  1. Yoga is a cross-platform layout engine written in C which implements Flexbox through bindings to the native views (Java Android Views / Objective-C iOS UIKit). All the layout calculations of the various views, texts and images in React-Native are done through yoga, this is basically the last step before our views get displayed on the screen.
  2. Shadow tree/Shadow nodes: When react-native sends the commands to render the layout, a group of shadow nodes are assembled to build shadow tree which represented the mutable native side of the layout (i.e: written in the corresponding native respective language, Java for Android and Objective-C for iOS) which is then translated to the actual views on screen (using Yoga).
  3. The ViewManger is an interface that knows how to translate the View Types sent from the JavaScript into their native UI components. The ViewManager knows how to create a shadow node, a native view node and to update the views. In the React-Native framework, there are a lot of ViewManager that enable the usage of the native components. If for example, you'd someday like to create a new custom view and add it to react-native, that view will have to implement the ViewManager interface
  4. The UIManager is the final piece of the puzzle, or actually the first. The JavaScript JSX declarative commands are sent to the native as Imperative commands that tell React-Native how to layout the views, step by step iteratively. So as a first render, the UIManager will dispatch the command to create the necessary views and will continue to send the update diffs as the UI of the app changes over time.

68. How is InteractionManager important ?

- The interaction Manager works on a long-running schedule after any interactions/animations have been completed. In particular, to run smoothly this allows Javascript animations.
- It is important because it creates an interaction 'handle' on animation start, and clearing it upon completion in applications to register animations.

69. What are the disadvantages of StyleSheet.create ?

- The key tradeoff with `StyleSheet.create` method is that recomputing styles based on external criteria (like screen rotation or even a user-selected viewing mode) needs some infrastructure built to determine which styles to use. If objects were passed in "raw" they could be recomputed on the fly every time, based on arbitrary criteria.
- You cannot make a comparison like this `styles.myNiceComponent.backgroundColor === 'blue'.(Need to flatten it first.)
