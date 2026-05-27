# Week 8 - React Routing, State Management & CORS

---

# Routing in React

Routing is very important for **Single Page Applications (SPA)**.

It allows us to navigate between different views or pages without reloading the entire page.

We can use libraries like:

```bash
react-router-dom
```

to handle routing in React applications.

---

# Steps to Set Up Routing in React

## 1. Design the Root Layout

Create the main layout structure of the application.

Example:
- Navbar
- Sidebar
- Footer
- Main content area

---

## 2. Install React Router

Install the routing package using npm:

```bash
npm install react-router-dom
```

---

## 3. Create Components

Create separate components for each page or view.

Example:

```text
Home.jsx
About.jsx
Contact.jsx
Dashboard.jsx
```

---

## 4. Configure Routing

Connect the components to paths using routes.

Example:

```jsx
import { BrowserRouter, Routes, Route } from "react-router-dom";

<BrowserRouter>
  <Routes>
    <Route path="/" element={<Home />} />
    <Route path="/about" element={<About />} />
  </Routes>
</BrowserRouter>
```

---

# React Router Hooks

React Router provides hooks for navigation and accessing location data.

---

# useNavigate

`useNavigate` is used for programmatic navigation.

Example:

```jsx
import { useNavigate } from "react-router-dom";

const navigate = useNavigate();

navigate("/home");
```

### Uses
- Redirect after login
- Move between pages
- Navigate dynamically

---

# useLocation

`useLocation` always knows the location from where we are coming from.

It provides information about the current URL.

Example:

```jsx
import { useLocation } from "react-router-dom";

const location = useLocation();

console.log(location.pathname);
```

### Uses
- Track current page
- Access route state
- Conditional rendering based on URL

---

# State Management in React

State management is very important in React.

Without state management, we cannot build complex applications properly.

It helps us:
- Manage data
- Share data across components
- Synchronize UI updates
- Keep components updated automatically

---

# Problem with Multi-Level Components

When many nested components are involved, it becomes difficult to pass data between components.

This creates a problem called:

## Prop Drilling

Prop drilling means passing props through multiple component levels just to send data from one component to another.

### Problems with Prop Drilling

- Messy code
- Hard to maintain
- Difficult debugging
- Unnecessary complexity

---

# Ways to Manage State in React

There are several approaches:

| Method | Best For |
|---|---|
| Context API | Small to Medium Applications |
| Redux | Medium to Large Applications |

---

# Context API

Context API is a built-in feature of React.

It allows us to create shared state that can be accessed by multiple components without passing props manually through every level.

---

# Uses of Context API

Useful for:
- Authentication state
- Theme settings
- Language preferences
- Shared counters
- User information

---

# How Context API Solves Prop Drilling

Context API provides a direct way to share data between components.

Instead of passing props through intermediate components, components can directly access the shared state.

This makes the code:
- Cleaner
- Easier to maintain
- More scalable

---

# Important Note About Context

It is not completely correct to call Context a "global state".

It is only available to components wrapped inside the Context Provider.

So it is:
- Shared state
- Not truly global

---

# Steps to Use Context API

---

## 1. Create a Context Object

Example:

```jsx
import { createContext } from "react";

const CounterContext = createContext();
```

---

## 2. Context Provider

Every context object has a:

- Provider
- Consumer

The Provider supplies the state to components.

Example:

```jsx
<CounterContext.Provider value={value}>
  {children}
</CounterContext.Provider>
```

---

## 3. Context Consumer

Components consume the provided state.

Usually done using the `useContext` hook.

Example:

```jsx
import { useContext } from "react";

const data = useContext(CounterContext);
```

---

# Example Folder Structure

Create a folder:

```text
src/context
```

Inside it create:

```text
CounterContext.js
```

In this file:
- Create the context
- Create the provider
- Manage the state

Then:
- Wrap components using the provider in `App.jsx`
- Consume state where needed

---

# Context as a Pipeline

We can think of Context like a pipeline.

It allows data to move between components without manually passing props through every level.

This improves:
- Readability
- Maintainability
- Scalability

---

# Best Practice for Context API

## One Context = One State

Avoid storing too many states inside one context.

### Why?

Multiple states inside one context can cause:
- Unnecessary re-renders
- Performance issues
- Slower applications

---

# Recommended Approach

Create separate contexts for separate states.

Example:

```text
AuthContext
ThemeContext
CounterContext
LanguageContext
```

This improves performance and keeps state management organized.

---

# Reference Project

For the Context API example:

```text
/learding/2-context-demo
```

In this project:
- A Counter Context is created
- The Provider wraps components
- Multiple components share the same counter state

---

# CORS (Cross-Origin Resource Sharing)

CORS is a security feature implemented by web browsers.

It prevents malicious websites from making unauthorized requests to other websites.

---

# Why CORS Exists

Browsers follow the:

## Same-Origin Policy

This means:
- A website can only access resources from the same origin by default.

Origin includes:
- Protocol
- Domain
- Port

Example:

```text
http://localhost:3000
```

and

```text
http://localhost:5000
```

are considered different origins because the ports are different.

---

# What CORS Does

CORS allows servers to specify:

- Which origins are allowed
- Which HTTP methods are allowed
- Which headers are allowed

---

# Example

Backend server response:

```http
Access-Control-Allow-Origin: *
```

This allows requests from all origins.

---

# Common HTTP Methods in CORS

- GET
- POST
- PUT
- DELETE

---

# Example in Express.js

```bash
npm install cors
```

Example setup:

```jsx
import cors from "cors";

app.use(cors());
```

Specific origin example:

```jsx
app.use(
  cors({
    origin: "http://localhost:3000",
  })
);
```

---

# Summary

This README covered:

- React Routing
- react-router-dom
- useNavigate
- useLocation
- State Management
- Prop Drilling
- Context API
- Context Provider & Consumer
- useContext Hook
- CORS
- Same-Origin Policy

These concepts are essential for building modern React applications.
