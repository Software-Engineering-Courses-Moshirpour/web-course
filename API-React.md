# React and REST API

## React

React is a JavaScript library for creating user intefaces built by Facebook. It is currently the most popular JavaScript framework, and that's why we have decided to talk about it in this course.

There are two past workshops about React which I encourage everyone to see. One of them is just a beginner course on React, while the other one goes in some depth and explains intermediate concepts in React. You can find the workshops on D2L.

Here, I will link to the subjects discussed in the workshops in case you want to study more and get a better sense of them.

### Creating a React application

There are different ways for creating and starting with a React application. Three of the most popular ones are as follows, as you can see [on this webpage as well](https://reactjs.org/docs/create-a-new-react-app.html):

- Use the `create-react-app` module
- Use a static framework like Gatsby
- Use a dynamic framework like Next.js

In both workshops, we used the first approach. But just so you know, [Gatsby](https://www.gatsbyjs.com/) is a React-based framework for creating static websites. And [Next.js](https://nextjs.org/) is a React-based framework for creating dynamic websites using Node.js.

You can refer to [this page](https://reactjs.org/docs/create-a-new-react-app.html) to learn more about each approach.

### JSX

You combine HTML tags and JavaScript and you get yourself JSX. That's basically it. Here's a quick example:

```jsx
const name = "Josh Perez";
const element = <h1>Hello, {name}</h1>;
```

Browsers don't support JSX right out of the box, so we need libraries to compile JSX into plain JavaScript so that browsers can understand it. But don't worry. You don't need to be concerned about those libraries. All the approaches I mentioned above for creating a React application come with pre-installed libraries, so everything is ready for you from the very beginning. You just need to write your code and push it to your repository. Hopefully, at the end of this course, we will also talk about CI/CD methods and how you can link your repository to a pipeline so that every time you push a new version, it fires up and deploys a new version for you.

For now, just note that we use JSX for writing React application. You can go [here](https://reactjs.org/docs/introducing-jsx.html) to get more info on JSX and how it works.

### Components

React uses components. Basically, you break your application (and by application I mean the front-end of your application, since, as I mentioned at the beginning, React is a JavaScript framework for building user interfaces). It's always a good idea to spend some good time on designing your application and breaking it into different components before writing your React code. If you watch the workshops, especially the longer one, I first spend some time to just figure out the components and what I want to do in terms of React components and then I start builging the applications.

There are many ways to build a user interface with React. In one of the previous semesters, we gave the students the same project but they all submitted a completely different design at the end. Not 2 applications were the same. That's the beauty of React that you can build your application in many ways. However, not every design is good and efficient. I always say that the more time you spend in the designing and analyzing phase of your application, the more efficient your final application will be; the performance will be better and the whole process will go much smoother. If you jump into the editor and start coding right away, you might think that you are saving time, but in big projects, you will see how important the designing and analyzing phase is.

Since React is a JavaScript framework for creating user interfaces, the way you design your UI has a direct impact on your components and the way the communicate with each other. You can lear more about thinking in React on [this page](https://reactjs.org/docs/thinking-in-react.html).

You can consider Components as classes. In fact, in previous versions of React, the components were all JavaScript classes. You can still use classes for writing React applications, but it is considered a past approach. The newer approach is using functions. If you hear somewhere about Functional React, that's just React with using functions as components instead of classes.

But it's safe to still think of components as classes. I assume that you have already passes some programming courses and are familiar with Object Oriented Programming. An application (let's say a Java application), is usually consisted of multiple classes. And these classes are talking to each other. So, there's always a way for classes to communicate with one another. Components in React are not an exception. React Components, too, need to talk to each other, and the way we accomplish that is with a concept called Props (short for Properties). So, basically, if you want to send something to another Component, you will do so by putting your stuff in Props and then pass the Props to the target class and vice versa.

Here's an example of passing Props to another component:

```jsx
function Welcome(props) {
  return <h1>Hello, {props.name}</h1>;
}

const element = <Welcome name="Sara" />;
```

You can read more about Props and Components [here](https://reactjs.org/docs/components-and-props.html).

### States

States are what keeps your React application alive. And by alive, I mean an application that reacts (pun intented) to users' actions. States are different from normal JavaScript variables. For one, we don't update React states directly by the equal sign (`=`). There are functions coming from the React library that take care of that for us.

But how we can decide between creating a JavaScript variable or a React state? So, basically, if you have a variable that meets the following conditions, you need to create a React state for it:

- It's value changes over time (without refreshing your browser)
- Its value has an impact on the UI (it changes something in the UI)

So, with that definition, if I have a key that I use for calling an API endpoint, I don't need to create a React state for that. It never changes during the lifetime of a webpage. But, if I have a number showing the total number of users registered in my application and the number changes asynchronously (without refreshing the webpage), I should create a React state for that. Why? Because

1. It changes
2. Its change affect the UI (you're watching the page and then the number goes from 120 to 125. That's a visible change in the UI. You can see it!)

Again, please refer to the workshops in D2L and I discussed the concept of states in React.

If you want to learn more about React states, please refer to [here](https://reactjs.org/docs/state-and-lifecycle.html).

### Hooks

When it was just classes in React, there was no Hook. Hooks are a new addition to React and if you want to write functional React (which we want in this course), you need to learn them. Basically, they are a way to deal with the states of your applications (defining them, changing them, handling them) without using classes.

For example, we use `useState` to create React states. Take a look at the following example:

```jsx
import React, { useState } from "react";

function Example() {
  // Declare a new state variable, which we'll call "count"
  const [count, setCount] = useState(0);

  return (
    <div>
      <p>You clicked {count} times</p>
      <button onClick={() => setCount(count + 1)}>Click me</button>
    </div>
  );
}
```

`useState` accepts one argument which is the default value of the state being declared (`count` in the above example), and returns an array of two:

1. The state itself
2. And a function to change the value of the state

The above example uses JavaScript destructuring to get the two values and put them in two variables: `count` and `setCount`. We talked about the JavaScript destructuring capability in previous chapters.

This is a [video](https://reactjs.org/docs/hooks-intro.html) of the React conference where Hooks were introduced for the first time. It's a bit long (1:30 hour), but worth watching.

In the workshops, especially the longer one, I talked about another useful hook that we can use to change a React state. That is the `useReducer` hook. So, basically, if you have a complicated logic to change your state, you might be better off with using `useReducer`. But if you have a pretty simple logic, like if I click on this button, incremet the value of a counter, then using `useState` is enough, although nothing stops you from using `useReducer` even in this situations. In the workshop I talk about these two methods in detail.

Here's an example of using `useReducer`:

```jsx
const initialState = { count: 0 };

function reducer(state, action) {
  switch (action.type) {
    case "increment":
      return { count: state.count + 1 };
    case "decrement":
      return { count: state.count - 1 };
    default:
      throw new Error();
  }
}

function Counter() {
  const [state, dispatch] = useReducer(reducer, initialState);
  return (
    <>
      Count: {state.count}
      <button onClick={() => dispatch({ type: "decrement" })}>-</button>
      <button onClick={() => dispatch({ type: "increment" })}>+</button>
    </>
  );
}
```

You can learn more about `useReducer` in [here](https://reactjs.org/docs/hooks-reference.html#usereducer). In addition, you can learn more about all React Hooks on the [React website](https://reactjs.org/docs/hooks-intro.html).

### REST API

A REST API (also known as RESTful API) is an application programming interface (API or web API) that conforms to the constraints of REST architectural style and allows for interaction with RESTful web services. REST stands for representational state transfer and was created by computer scientist Roy Fielding.

An API is a set of definitions and protocols for building and integrating application software. It’s sometimes referred to as a contract between an information provider and an information user—establishing the content required from the consumer (the call) and the content required by the producer (the response). For example, the API design for a weather service could specify that the user supply a zip code and that the producer reply with a 2-part answer, the first being the high temperature, and the second being the low.

You can watch [this video](https://www.youtube.com/watch?v=lsMQRaeKNDk&ab_channel=IBMCloud) from Microsoft. It's less than 10 minutes and gives you a good understanding of REST APIs.

A RESTful API uses HTTP/HTTPS endpoints to the followings:

- Retrieve something with `GET`
- Update something with `PUT`
- Create new things with `POST`
- Remove stuff with `DELETE`

There are other HTTP methods, such as `OPTIONS`, which you can learn more about [here](https://developer.mozilla.org/en-US/docs/Web/HTTP/Methods).

RESTful APIs are the fundamental of most web applications nowadays. There are different ways to create a RESTful API, like for instance, using and application like [Postman](https://www.postman.com/). But these are just temporary solutions. At the end, you want to build an actual backend (Serverless or otherwise) for your API endpoints. In future lessons we will talk more about backend technologies like Django where you can learn about building your own APIs.

## Additional Resources

- [React website](https://reactjs.org/)
- [W3School on React](https://www.w3schools.com/react/)
- [Dan Abramov's Blog on React](https://overreacted.io/)
- [Free Code Camp Video](https://www.youtube.com/watch?v=DLX62G4lc44&ab_channel=freeCodeCamp.org)
- [MDN's REST Documentation](https://developer.mozilla.org/en-US/docs/Glossary/REST)
- [Traversy Media on RESTful APIs](https://www.youtube.com/watch?v=Q-BpqyOT3a8&ab_channel=TraversyMedia)
