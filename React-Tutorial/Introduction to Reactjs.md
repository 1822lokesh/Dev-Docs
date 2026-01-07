# Introduction to React.js

## 1. What is React?
React is an open-source JavaScript library used for building user interfaces (UI), specifically for single-page applications. It was created by Meta (Facebook) and is maintained by a large community of developers.

Unlike traditional web development where you build entire pages, React allows you to build **Components**—small, isolated pieces of code that represent parts of the interface (like a button, a search bar, or a navigation menu).

## 2. Why Use React?
React is currently the most popular front-end library in the world. Here is why:

* **Component-Based:** You write code once and reuse it everywhere.
* **Declarative:** You describe what the UI should look like based on the current data, and React handles the "how" (updating the DOM).
* **Virtual DOM:** React is fast because it uses a "Virtual DOM" to minimize expensive operations in the actual browser.
* **Huge Ecosystem:** Since it's so popular, there are endless libraries for routing, styling, and state management.

## 3. Core Concepts for Beginners

### A. The Virtual DOM
In standard JavaScript, if you change one item in a list of ten, the browser often re-renders the whole list. React creates a lightweight copy of the UI (the Virtual DOM), compares it to the real UI, and only updates the specific part that changed.

### B. JSX (JavaScript XML)
JSX is a syntax extension that allows you to write HTML-like code directly inside your JavaScript. It makes the code easier to read and write.

```javascript
// This is JSX
const element = <h1>Hello, React!</h1>;

```

### C. Components

Think of components like LEGO bricks. You build small bricks (Button, Input, Header) and stack them together to create a house (the Application).

## 4. Setting Up Your First Project

To start a React project today, the industry standard is to use **Vite** because it is incredibly fast.

**Prerequisites:** You must have Node.js installed on your computer.

**Steps to create a project:**

1. Open your terminal.
2. Run the creation command:
```bash
npm create vite@latest my-react-app -- --template react

```


3. Move into the folder:
```bash
cd my-react-app

```


4. Install dependencies:
```bash
npm install

```


5. Start the server:
```bash
npm run dev

```
# Framework vs. Library

In software development, we rarely write everything from scratch. We use external code to help us. Two common types of external code are **Libraries** and **Frameworks**.

## 1. What is a Library?
A library is a collection of pre-written code (functions, classes, or components) that you can use to perform specific tasks.

* **Key Characteristic:** You are in control. You decide when to call the library and where to use it in your code.
* **Analogy:** A Library is like going to a **supermarket**. You pick the ingredients you want (vegetables, spices, meat) and you decide how to cook them and what dish to make.
* **Example:** React, jQuery, Lodash.

## 2. What is a Framework?
A framework is a comprehensive platform that provides a foundation for building software. It includes libraries, but it also dictates how your project should be structured.

* **Key Characteristic:** The Framework is in control. It provides a skeleton, and you fill in the blanks. The framework calls your code when it needs to.
* **Analogy:** A Framework is like ordering a **HelloFresh meal kit**. The menu is decided, the ingredients are pre-measured, and you must follow the specific recipe card to get the result.
* **Example:** Angular, Vue (often considered a progressive framework), Next.js, Django.

## 3. The Key Difference: "Inversion of Control" (IoC)
The technical difference between the two is called **Inversion of Control**.

* **With a Library:** Your application code calls the library.
    * `Your Code -> calls -> Library`
* **With a Framework:** The framework calls your application code.
    * `Framework -> calls -> Your Code`

[Image of Inversion of Control Diagram Framework vs Library]

## 4. Comparison Table

| Feature | Library | Framework |
| :--- | :--- | :--- |
| **Control** | You control the flow (You call the code). | The Framework controls the flow (It calls your code). |
| **Flexibility** | High. You can swap libraries easily. | Low. You are stuck with the framework's rules. |
| **Opinionated?** | No. It doesn't care how you structure files. | Yes. It enforces specific file structures and patterns. |
| **Replacement** | Easy to replace or upgrade specific parts. | Hard. Rewriting the app is often required to switch frameworks. |
| **Example** | React.js (UI only) | Angular (UI + Routing + HTTP + State) |

## 5. Why is React considered a Library?
React is a library because it only cares about one thing: **The User Interface** (rendering views).

* React doesn't tell you how to handle routing (navigating between pages).
* React doesn't tell you how to make HTTP requests (fetching data).
* React doesn't force a specific folder structure.

Because of this, you have to choose other libraries to work with React (like `react-router-dom` for pages or `axios` for API calls).