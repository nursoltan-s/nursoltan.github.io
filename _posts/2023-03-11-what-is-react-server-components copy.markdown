---
layout: post
title: What is React server components
date: 2023-03-11 13:32:20 +0300
description: You’ll find this post in your `_posts` directory. Go ahead and edit it and re-build the site to see your changes. # Add post description (optional)
img: react-logo.png # Add image post (optional)
fig-caption: # Add figcaption (optional)
tags: [react, front-end, javascript]
---

### Overview

React Server Components is a new feature in the React ecosystem that allows developers to write components that are rendered on the server and streamed to the client. This feature has the potential to improve the performance of web applications by reducing the time to first paint and the amount of JavaScript that needs to be downloaded and executed by the client.

Traditionally, web applications have been built using client-side rendering, where the application logic runs on the client and the server sends HTML, CSS, and JavaScript assets to the client for rendering. This approach has its limitations, such as slow initial loading times, poor performance on slow devices, and difficulties in implementing server-side rendering.

React Server Components aims to address these limitations by allowing developers to write components that can be rendered on the server and streamed to the client. The server components are similar to regular React components, but they have a few key differences. For example, server components cannot have any side effects, such as accessing the DOM or making API calls. This is because they are rendered on the server, where there is no access to the client's browser environment.

When a user visits a website that uses React Server Components, the server renders the initial content and sends it to the client. As the user interacts with the website, the client sends requests to the server for additional content, which is then streamed back to the client. This approach reduces the amount of JavaScript that needs to be downloaded and executed by the client, which can lead to faster page load times and improved performance on slower devices.

One of the key benefits of React Server Components is that they can be used with existing React applications without requiring a complete rewrite. Developers can gradually introduce server components to their application and take advantage of the performance benefits without disrupting the existing application logic.

Overall, React Server Components represent a significant step forward in the evolution of web application development. By allowing developers to write components that can be rendered on the server and streamed to the client, React Server Components have the potential to improve the performance and user experience of web applications, especially for users on slower devices or with limited network connectivity.

### Example

#### server.js

```jsx
// server.js
import { createServer } from "http";
import { renderToNodeStream } from "react-dom/server";
import App from "./App.server";

const server = createServer((req, res) => {
  res.setHeader("Content-Type", "text/html");

  const stream = renderToNodeStream(<App />);

  stream.pipe(res, { end: false });
  stream.on("end", () => {
    res.end();
  });
});

server.listen(3000);
```

#### App.server.jsx

```jsx
// App.server.jsx
import React from "react";

function App() {
  return (
    <html>
      <head>
        <title>Hello, world!</title>
      </head>
      <body>
        <h1>Hello, world!</h1>
      </body>
    </html>
  );
}

export default App;
```

In this example, we create a simple HTTP server that renders a React component called App to the client. The App component is defined in a separate file called App.server.jsx. The renderToNodeStream function is used to render the component to a stream that can be sent to the client.

When a client makes a request to the server, the server sends the HTML content for the App component to the client. As the client interacts with the application, additional requests can be made to the server for additional content.

This is a very simple example, but it illustrates the basic concepts of React Server Components. In practice, server components can be used to build complex web applications that are faster and more efficient than traditional client-side rendered applications.
