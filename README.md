# React-Interview-questions

Here’s a comprehensive list of **React.js interview questions** categorized by difficulty level to help you prepare:

---

## **🟢 Basic Level (For Beginners)**
---
## 1. **What is React.js and What are the key features of React?**  
---

**React.js** is an **open-source JavaScript library** developed by **Facebook** for building **user interfaces (UI)**, especially for **single-page applications (SPA)** where UI updates dynamically. React is designed to create fast, scalable, and interactive web applications.

---

## **🔹 Key Features of React.js**
1. **Declarative Syntax:**  
   - React allows developers to describe the UI state, and it efficiently updates and renders the right components when data changes.  
   - Example:  
   ```jsx
   const App = () => <h1>Hello, React!</h1>;
   ```

2. **Component-Based Architecture:**  
   - React encourages building reusable UI components that manage their own state.  
   - Example:  
   ```jsx
   function Greeting({ name }) {
     return <h2>Hello, {name}!</h2>;
   }
   ```

3. **Virtual DOM (VDOM):**  
   - React creates a **lightweight copy** of the **real DOM** called the **Virtual DOM**.  
   - When state changes, React compares the Virtual DOM with the previous version (using **diffing algorithm**) and updates only the changed parts in the **real DOM**.

4. **JSX (JavaScript XML):**  
   - JSX is a syntax extension that allows you to write HTML-like code directly in JavaScript.  
   - Example:  
   ```jsx
   const element = <h1>Welcome to React!</h1>;
   ```

5. **One-Way Data Binding:**  
   - Data flows in a **single direction**, making the application more predictable and easier to debug.

6. **React Hooks:**  
   - Hooks like `useState()`, `useEffect()`, and `useContext()` simplify state management in functional components.

7. **React Native Support:**  
   - React can also be used to build **cross-platform mobile applications** with **React Native**.

---

## **🔹 Why Use React.js?**
✅ **Fast Performance** thanks to the Virtual DOM.  
✅ **Reusable Components** improve code maintainability.  
✅ **Rich Ecosystem** with tools like **React Router**, **Redux**, and **Next.js**.  
✅ **Strong Community Support** with plenty of resources and libraries.

---

## **🔹 Example Code – Counter with `useState()`**
```jsx
import React, { useState } from 'react';

function Counter() {
  const [count, setCount] = useState(0);

  return (
    <div>
      <h1>Count: {count}</h1>
      <button onClick={() => setCount(count + 1)}>Increment</button>
      <button onClick={() => setCount(count - 1)}>Decrement</button>
    </div>
  );
}

export default Counter;
```

✅ **Key Concepts in Action:**  
- **Functional Component** using JSX  
- **State Management** via `useState()`  
- **Event Handling** with `onClick`  

---

## **🔹 Who Uses React.js?**##
Popular companies using React include:  
Facebook, Instagram, Neflix, Airbnb, Whatsapp
  
---

## **🔹 When to Use React.js?**
✔️ When building **dynamic web applications**  
✔️ When your project requires **complex UI interactions**  
✔️ When aiming for **code reusability** through components  

---
## 2. **What is JSX and how does it differ from HTML?**
---
  ### **🟦 What is JSX (JavaScript XML)?**

**JSX** stands for **JavaScript XML**. It’s a **syntax extension** for JavaScript used with **React** that allows developers to write HTML-like code directly inside JavaScript.

JSX simplifies writing UI components by combining HTML structure and JavaScript logic in one place.

---

## **🔹 Key Characteristics of JSX**
✅ Looks similar to HTML but is not exactly the same.  
✅ Must be transpiled into **React.createElement()** function calls using **Babel** before browsers can interpret it.  
✅ JSX can include **JavaScript expressions** inside `{}`.  
✅ Requires components to return **one parent element**.  

---

## **🔹 Example of JSX vs. Traditional JavaScript**
**JSX Code:**
```jsx
import React from 'react';

function Greeting() {
  const name = 'Kinshuk';
  return <h1>Hello, {name}!</h1>;
}

export default Greeting;
```

**How JSX Transpiles into JavaScript:**
```javascript
import React from 'react';

function Greeting() {
  const name = 'Kinshuk';
  return React.createElement('h1', null, `Hello, ${name}!`);
}

export default Greeting;
```

---

## **🔹 Key Differences Between JSX and HTML**
| Aspect            | JSX                                       | HTML                            |
|:------------------|:------------------------------------------|:--------------------------------|
| **Syntax**          | Uses **camelCase** for attribute names (e.g., `className`, `onClick`) | Uses standard **lowercase** attributes (e.g., `class`, `onclick`) |
| **JavaScript Integration** | Allows embedding JavaScript expressions inside `{}` | No JavaScript logic directly in tags |
| **Self-Closing Tags** | Requires self-closing tags for elements like `<img />`, `<input />` | Closing tags are optional in HTML |
| **Event Handling** | Uses **camelCase** event handlers (e.g., `onClick`, `onChange`) | Uses lowercase handlers (e.g., `onclick`, `onchange`) |
| **Comments**         | Written as `{/* Comment */}`            | Written as `<!-- Comment -->` |

---

## **🔹 Examples of Key Differences**
### 1️⃣ **Attribute Naming**
**JSX:**
```jsx
<div className="container">Content here</div>
```

**HTML:**
```html
<div class="container">Content here</div>
```

---

### 2️⃣ **JavaScript Logic Inside JSX**
**JSX:**
```jsx
const isLoggedIn = true;

return (
  <div>
    {isLoggedIn ? <p>Welcome back!</p> : <p>Please log in</p>}
  </div>
);
```

**HTML (not possible without JavaScript logic separately):**
```html
<div>
  <p>Welcome back!</p>
</div>
```

---

### 3️⃣ **Event Handling**
**JSX:**
```jsx
<button onClick={() => console.log('Clicked!')}>Click Me</button>
```

**HTML:**
```html
<button onclick="console.log('Clicked!')">Click Me</button>
```

---

### 4️⃣ **Comments**
**JSX:**
```jsx
{/* This is a comment in JSX */}
```

**HTML:**
```html
<!-- This is a comment in HTML -->
```

---

## **🔹 Why Use JSX?**
✅ Provides a **cleaner, more readable syntax**.  
✅ Reduces the need to use `React.createElement()` manually.  
✅ Makes UI development faster and more intuitive.  
✅ Enables **component-based architecture** by combining structure and logic in one place.  

---
3. **How does React’s Virtual DOM work?**
---
### **🔹 What is the Virtual DOM in React?**

The **Virtual DOM (VDOM)** is a **lightweight JavaScript representation** of the **real DOM** in memory. React uses the Virtual DOM to efficiently update the user interface by minimizing direct manipulation of the **actual DOM**, which is slow and resource-intensive.

Instead of updating the real DOM directly, React creates a **Virtual DOM** to track changes and apply only the necessary updates — improving performance significantly.

---

## **🔹 How Does the Virtual DOM Work?**
The Virtual DOM process follows a **3-step cycle**:

### **1️⃣ Rendering (Initial Render)**
- When you create a React component, React builds a **Virtual DOM tree** representing the initial UI structure.  
- This VDOM is then converted into real DOM elements and rendered in the browser.

✅ **Example Initial Render:**  
```jsx
function App() {
  return <h1>Hello, Kinshuk!</h1>;
}
```

⏩ The Virtual DOM creates this structure:
```
<div>
  <h1>Hello, Kinshuk!</h1>
</div>
```

---

### **2️⃣ Diffing (Detecting Changes)**
- When the state or props change, React creates a **new Virtual DOM** reflecting the updated UI.  
- React then compares the **new VDOM** with the **previous VDOM** using a highly efficient **diffing algorithm**.

✅ **Example with Change:**
```jsx
import React, { useState } from 'react';

function Counter() {
  const [count, setCount] = useState(0);

  return (
    <div>
      <h1>Count: {count}</h1>
      <button onClick={() => setCount(count + 1)}>Increment</button>
    </div>
  );
}
```

➡️ Suppose `count = 0` initially, and you click the **Increment** button.  
➡️ React generates a new Virtual DOM tree where the `<h1>` content changes to `"Count: 1"`.

---

### **3️⃣ Reconciliation (Efficient Update)**
- React compares the **new VDOM** with the **previous VDOM**.  
- It identifies the **minimal set of changes** needed to update the real DOM efficiently.  
- Only the modified elements are updated — not the entire page.

✅ In the above example:  
- React will only update the `<h1>` content, leaving other elements untouched.

---

## **🔹 Visual Representation of Virtual DOM Process**
```
1. Initial VDOM       2. New VDOM            3. Updated DOM
------------------------------------------------------------
<div>                  <div>                  <div>
  <h1>Count: 0</h1>     <h1>Count: 1</h1>      <h1>Count: 1</h1> ✅ (Updated)
  <button>Increment</button> <button>Increment</button> <button>Increment</button> (No Change)
</div>                 </div>                 </div>
```

---

## **🔹 Why Does the Virtual DOM Improve Performance?**
1. **Minimized DOM Manipulations:**  
   - Directly updating the real DOM is slow. React's Virtual DOM efficiently calculates the **minimal number of changes** and applies them in bulk.  

2. **Batch Updates:**  
   - React batches multiple updates into a **single repaint**, reducing performance overhead.  

3. **Efficient Diffing Algorithm:**  
   - React's diffing algorithm efficiently compares old and new VDOM trees by:  
     - Comparing element types.  
     - Tracking changes based on unique `key` props (important for lists).

---

## **🔹 Key Advantages of the Virtual DOM**
✅ Improved performance with minimal DOM updates.  
✅ Faster UI rendering and better responsiveness.  
✅ Efficiently handles complex UI updates.  
✅ Provides a **predictable state management flow**.  

---

## **🔹 When Does the Virtual DOM Update?**
🔄 Whenever:  
- **`setState()`** is called in class components.  
- **`useState()`** or **`useReducer()`** updates state in functional components.  
- **Props** change in child components.  

---

## **🔹 Pro Tip:** To boost performance further, you can use:
✅ **`React.memo()`** to prevent unnecessary re-renders.  
✅ **`useCallback()`** and **`useMemo()`** to memoize functions and data.  

---
6. **What is the purpose of `useState()` hook? Provide an example.**
---
### **🔹 What is `useState()` in React?**

The **`useState()`** hook is a **React Hook** that allows functional components to manage **state**.  

Since functional components don’t have a `this` keyword (like class components), React introduced `useState()` to handle state management in them.

---

## **🔹 Syntax of `useState()`**
```jsx
const [state, setState] = useState(initialState);
```

### **Parameters:**
- **`state`** → The current state value.  
- **`setState`** → A function that updates the state.  
- **`initialState`** → The initial value assigned to the state (can be any data type — string, number, object, array, etc.).

---

## **🔹 Example: Counter with `useState()`**
```jsx
import React, { useState } from 'react';

function Counter() {
  // Declare a state variable 'count' with an initial value of 0
  const [count, setCount] = useState(0);

  return (
    <div>
      <h1>Count: {count}</h1>
      <button onClick={() => setCount(count + 1)}>Increment</button>
      <button onClick={() => setCount(count - 1)}>Decrement</button>
      <button onClick={() => setCount(0)}>Reset</button>
    </div>
  );
}

export default Counter;
```

### **🔍 How It Works:**
✅ `count` → Tracks the current state (initialized as `0`).  
✅ `setCount()` → Updates the `count` value.  
✅ Clicking the **Increment** or **Decrement** button modifies the state.  

---

## **🔹 Key Concepts of `useState()`**
### **1️⃣ State Persistence**
- The state persists between re-renders.  
- React automatically re-renders the component when the state updates.

---

### **2️⃣ State Initialization**
- `useState()` only initializes the state **once** — on the **initial render**.  
- Changing the state later won’t re-initialize it.

✅ Example:  
```jsx
const [value, setValue] = useState(Math.random()); 
```
➡️ The random number is generated **once** and won’t change on subsequent renders unless updated via `setValue()`.

---

### **3️⃣ Functional Updates (Best Practice for State Updates)**
When updating state based on the **previous state**, always use the **callback syntax** to ensure correct behavior.

✅ Example:
```jsx
setCount((prevCount) => prevCount + 1);
```

This is important because state updates in React are **asynchronous**.

---

### **4️⃣ Multiple `useState()` Calls**
You can use multiple `useState()` hooks for managing different state variables.

✅ Example:
```jsx
const [name, setName] = useState('Kinshuk');
const [age, setAge] = useState(25);
```

---

### **5️⃣ Complex State (Objects & Arrays)**
`useState()` can also manage **objects** and **arrays**.

✅ Example (Managing Object State):
```jsx
const [user, setUser] = useState({ name: 'Kinshuk', age: 25 });

function updateAge() {
  setUser((prevUser) => ({ ...prevUser, age: prevUser.age + 1 }));
}
```

---

## **🔹 Common Mistakes with `useState()`**
❌ **Directly modifying the state**  
```jsx
count++;         // ❌ Wrong - React won't re-render
user.name = 'John'; // ❌ Wrong - React won't track the change
```

✅ **Correct Way:**
```jsx
setCount(count + 1);         // ✅ Correct
setUser({ ...user, name: 'John' });  // ✅ Correct
```

---

## **🔹 When to Use `useState()`**
✅ For managing **simple** or **component-specific** states.  
✅ For handling **form inputs**, **UI toggles**, **counters**, etc.  

For **complex** state logic or **global state management**, tools like `useReducer()` or **Redux** may be better options.

---

## **🔹 Key Takeaway**
The `useState()` hook simplifies state management in functional components, making them cleaner, more concise, and easier to maintain.

---
4. **Explain the difference between `props` and `state`.**
---

Both **`props`** and **`state`** are essential for managing data in React, but they serve different purposes and behave in distinct ways. Here's a detailed comparison:

---

## **🔸 Key Differences Between `props` and `state`**

| Aspect        | `props`                         | `state`                         |
|:---------------|:--------------------------------|:---------------------------------|
| **Definition**  | Short for **properties**; used to pass data **from parent to child** components. | Used to manage **internal component data** that can change over time. |
| **Mutability**  | **Immutable** (cannot be modified directly by the component receiving them). | **Mutable** (can be updated using `setState()` or `useState()`). |
| **Control**     | Controlled by the **parent component**. | Managed **within the component** itself. |
| **Purpose**      | Used for **passing data** (e.g., text, numbers, functions) to child components. | Used for **managing dynamic data** that may change due to user actions or events. |
| **Initialization** | Defined when the component is **instantiated** (rendered). | Initialized within the component using `useState()` or `this.state`. |
| **Re-rendering** | Changes in `props` trigger a **re-render** of the component. | Changes in `state` also trigger a **re-render**. |

---

## **🔹 Example to Demonstrate `props` and `state`**
### **Parent Component (`App`) Using `props`**
```jsx
import React from 'react';
import Greeting from './Greeting';

function App() {
  return <Greeting name="Ram" />;
}

export default App;
```

---

### **Child Component (`Greeting`) Using `props`**
```jsx
import React from 'react';

function Greeting({ name }) {
  return <h1>Hello, {name}!</h1>;
}

export default Greeting;
```

✅ Here, `props` passes `"Ram"` from the `App` component to the `Greeting` component.  
✅ Since `props` are **read-only**, the `Greeting` component **cannot modify** the `name`.

---

### **Component Using `state`**
```jsx
import React, { useState } from 'react';

function Counter() {
  const [count, setCount] = useState(0);

  return (
    <div>
      <h2>Count: {count}</h2>
      <button onClick={() => setCount(count + 1)}>Increment</button>
      <button onClick={() => setCount(count - 1)}>Decrement</button>
    </div>
  );
}

export default Counter;
```

✅ The `count` value is managed using `state` and updates when the button is clicked.  
✅ Since `state` is **mutable**, calling `setCount()` updates the value.

---

## **🔹 Key Use Cases**
✅ Use **`props`** when you need to pass **data from parent to child**.  
✅ Use **`state`** when data needs to **change dynamically** within the component.  

---

## **🔹 Quick Analogy for Better Understanding**
Imagine a **train**:
- **`props`** are like **train tickets** — once printed, they cannot change (fixed data).
- **`state`** is like **passenger count** — it can change as people board or leave the train.

---

## **🔹 Combining `props` and `state`**
Often, both are used together. For example:
- **`props`** → Passed from the parent for initial data.  
- **`state`** → Used to track changes in that data.  

### Example:
```jsx
function Profile({ initialAge }) {
  const [age, setAge] = useState(initialAge);

  return (
    <div>
      <h1>Age: {age}</h1>
      <button onClick={() => setAge(age + 1)}>Grow Older</button>
    </div>
  );
}
```

✅ `initialAge` is passed as a **`prop`**.  
✅ `age` is managed using **`state`** for updates.

---

## **🔹 Key Takeaway**
- Use **`props`** for **passing data**.  
- Use **`state`** for **managing dynamic data**.  

9. **What is a functional component vs. class component?**
10. **How does React handle events? Provide an example.**
11. **What is the purpose of `key` in React lists?**
12. **How do you conditionally render elements in React?**

---

## **🟠 Intermediate Level (For Experienced Developers)**
1. **Explain the lifecycle methods in class components.**
2. **What are React hooks? Name a few commonly used hooks.**
3. **How does `useEffect()` work and when should you use it?**
4. **Explain the concept of `context` in React. How does it simplify prop drilling?**
5. **What is the difference between `useMemo()` and `useCallback()`?**
6. **How do you manage global state in React? (e.g., Redux, Context API, Zustand)**
7. **What is React Router, and how does it handle navigation?**
8. **How would you optimize a React application’s performance?**
9. **What is lazy loading and how does `React.lazy()` improve performance?**
10. **How can you prevent unnecessary re-renders in React?**

---

## **🔴 Advanced Level (For Senior Developers)**
1. **Explain server-side rendering (SSR) vs. client-side rendering (CSR).**
2. **What is hydration in React? How does it improve performance?**
3. **Describe the reconciliation process in React.**
4. **What is `Suspense` and how does it work with `React.lazy()`?**
5. **How does error boundary work in React? Provide an example.**
6. **What are React Portals and when should you use them?**
7. **What is the difference between `useEffect()` and `useLayoutEffect()`?**
8. **How would you handle complex form management in React? (e.g., Formik, React Hook Form)**
9. **Explain the concept of custom hooks. Why and how would you create one?**
10. **How does React handle memoization and when should you use `React.memo()`?**

---

## **💼 Practical/Scenario-Based Questions**
1. **How would you design a to-do list app using React?**
2. **How would you implement dark mode in a React app?**
3. **How would you optimize a slow-rendering React component?**
4. **Explain how to integrate REST APIs in a React project.**
5. **How would you build a responsive UI using React and CSS-in-JS libraries like Emotion or Styled Components?**

---

## **🛠️ Coding Challenges**
1. **Implement a counter with increment, decrement, and reset buttons.**
2. **Create a dynamic search bar with real-time filtering.**
3. **Build a pagination component in React.**
4. **Implement a modal dialog box using React Portals.**
5. **Create a dynamic table with sorting and filtering functionality.**

---

## **🔥 Pro Tips for Interviews**
✅ Focus on explaining **why** you use certain patterns, not just **how**.  
✅ Practice coding on platforms like **LeetCode**, **CodeSandbox**, or **JSFiddle**.  
✅ Prepare a couple of **personal projects** to showcase practical skills.  
✅ Be ready to discuss **trade-offs** in design decisions (e.g., Context API vs Redux).  

