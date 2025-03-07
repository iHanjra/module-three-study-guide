# Intro to React

## Key Terms

| Term | Definition |
| ---- | ---------- |
| __React__ | An open-source third-party front-end framework built on JavaScript and used for building and maintaining large and robust front-end applications. |
| __Create React App__ | A tool used to quickly set up a new React project with pre-configured settings and features. |
| __UI__ | User Interface: The visual and interactive elements of a website or application that users interact with. |
| __Front-end__ | The part of a software application or website that users directly interact with. |
| __DOM__ | Document Object Model: A programming interface that represents the structure and content of a web page as objects, allowing manipulation and modification of the page. |
| __Virtual DOM__ | A virtual representation of the actual DOM in memory that React uses to efficiently update and render components. |
| __Components__ | Independent and reusable building blocks in React that encapsulate the UI and behavior of a part of a web page. |
| __JSX__ | JavaScript XML: A syntax extension for JavaScript that allows you to write HTML-like code in JavaScript, used in React to define the structure and appearance of components. |
| __Boilerplate code__ | Pre-written code that serves as a starting point for development, often providing basic setup and configurations. |
| __npx__ | A command-line tool that is bundled with npm which allows you to execute Node.js packages without the need to install them globally on your system. It stands for "Node Package eXecutor."

---

## React Folders & Files
| Folder / File | Purpose |
| ---- | ---------- |
| __README.md__ | There is some boilerplate information about Create React App in this file. If you create your own project that you want to share with people, you should replace most or all of the content here with information about your project. |
| __node_modules/__ | This folder contains many folders containing all of the code to run Create React App. You can peek inside, but you won't need to change any code here.|
| __package-lock.json__ | This file keeps track of the files and folders inside the node_modules/ folder. This file is automatically generated and maintained. You won't need to change any code here. |
| __package.json__ | A file used in Node.js projects to store metadata and configuration information about the project. It includes details such as the project name, version, dependencies, scripts, and more. |
| __.gitignore__ | This is a file that tells git which files to ignore. Not every file should be tracked or stored on GitHub. |
| __public/__ | A place to store static assets that are publicly accessible by the client-side of your application. This folder often serves as the root of your web application when it is deployed and will contain HTML files, images, fonts, and other static resources. |
| __src__ | The `src/` folder (short for source) is where you will build your React application. All the code in this folder will be bundled to build your React application. If you try to add code or assets outside of this folder, they will not be able to be loaded into your React application (which will be loaded inside the `div` with the id of `root` from `public/index.html`). |
| __index.js__ | This is the file that is the entry point for the application. This will be the starting point of what is loaded into `index.html`. |
| __App.js__ | The `App.js` component is responsible for rendering the overall structure of your application and acts as a container for other components. It defines the layout, routing, and any global state management that your application might require. |

---

## Setting Up a New Create React App Project

- How would you give this a different name, like `the-ultimate-react-portfolio`, instead? Replace my-social-media-app with whatever you want.

```bash
npx create-react-app my-social-media-app
```

## Starting the React App

- What is `cd my-social-media-app` doing? Change directory to correct folder before starting.
- Where would you find the `npm start` script? package.json

```bash
cd my-social-media-app
npm start
```

## A Simple __App.js__ Structure
The following code should give you a blank but functional web page.

- What is `import "./App.css";` doing? Styles explicity for the component with the same name.
- Why are we using `className` instead of `class` on our `div`? Class is a reserved keyword in html. So is for(forHTML).
- Why is the page blank? There's nothing in the app.
- What does `export default` do? Exporting the default component of the file

```js
import "./App.css";

function App() {
  return <div className="App"></div>;
}

export default App;
```

## Using JSX
This code calls a function, formatName, in the embedded expression. The return value of this function, My Name, is then added to the h1 element after Hello.

- Why does the function use `user.firstName` and `user.lastName` instead of just `firstName` and `lastName`? Because user is an object
- What's the difference between the `user` in the function `formatName(user)` and the `const user`? The first is a variable and the second is an argument that's passed as a paramater.
- What data type is the `user` variable? Object
- Why are there brackets around our function call `{formatName(user)}`? Curly braces are used to pass a dynamic value into JSX or HTML.

```js
function formatName(user) {
  return user.firstName + " " + user.lastName;
}

const user = {
  firstName: "My",
  lastName: "Name",
};

const hello = <h1>Hello, {formatName(user)}!</h1>;
```

## Child Components

- What is the purpose of the empty brackets `<></>`? What are they called? React fragments. Group elements together without additional elements like div. React components can only return one element in the DOM.
- If you removed the parenthesis from `return (...);` would the code still work? Why or why not? No because it needs to encapsulate the return statement unless it's one line.

```js
// src/ContactList.js
export default function ContactList() {
  return (
    <>
      <p>Contacts</p>
      <ul>
        <li>Andrew Clark</li>
        <li>Brian Vaughn</li>
        <li>Dan Abramov</li>
        <li>Flarnie Marchan</li>
      </ul>
    </>
  );
}
```

- Does the `import` name `ContactList` need to match the name of the component? No because it's a default export.
- Why isn't the import name `ContactList` inside curly brackets? Because its's a default export. Curly braces are used for named exports, where you import specific members of a module.
- Why is the implementation of the component `<ContactList />` self-closed? When should it not be self-closed? In JSX, self-closing syntax is used when a component does not have any children. If a component has children elements or content, it should not be self-closed.

```js
// src/App.js
import ContactList from "./ContactList";

function App() {
  return (
    <div className="App">
      {hello}
      <ContactList />
    </div>
  );
}

export default App;
```

## Duplicating Components

- What would happen if we replaced all the dynamic data in `Post.js` with static data? It would be two of the same exact post.
- What would show on the page if we duplicated the `<ContactList />` component? There would be two contactlists with the same information.

```js
// src/Post.js
import postInfo from "./data.js";

export default function Post() {
  return (
    <div>
      <p>{postInfo.title}</p>
      <img src={postInfo.imageLink} alt="post" width="200" height="200" />
      <p>{postInfo.description}</p>
    </div>
  );
}

// src/App.js
function App() {
  return (
    <div className="App">
      {hello}
      <h2>Feed</h2>
      <Post />
      <Post />
      <ContactList />
    </div>
  );
}
```
