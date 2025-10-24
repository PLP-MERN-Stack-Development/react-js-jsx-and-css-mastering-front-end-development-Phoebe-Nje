# React Week 3 Project

## Project Overview
This project, **React Week 3 Project**, demonstrates the use of React components, routing, and API integration using **Vite** as the build tool.  
It fetches and displays data from an external API and allows navigation between different pages using **React Router DOM**.

---

## Objectives
1. Create a React project using **Vite**.
2. Set up **React Router** for navigation between pages.
3. Fetch and display API data from **https://jsonplaceholder.typicode.com/posts**.
4. Implement reusable components.
5. Style the project using **Tailwind CSS**.
6. Document the entire process with screenshots.

---

## Project Structure

```
src/
 ┣ components/
 ┣ pages/
 ┃ ┣ Home.jsx
 ┃ ┣ TasksManager.jsx
 ┃ ┗ APIData.jsx
 ┣ App.jsx
 ┗ main.jsx
```

---

## Step-by-Step Implementation

### Step 1: Create a React App
Use **Vite** to create a new React project.

```bash
npm create vite@latest react-week3-project
cd react-week3-project
npm install
npm run dev
```


---

### Step 2: Setup Project Structure
Inside the `src` folder, create:
- `pages` → contains page components (`Home.jsx`, `TasksManager.jsx`, `APIData.jsx`)
- `components` → for reusable UI components


---

### Step 3: Install Dependencies
Install the required dependencies for React Router and Tailwind CSS.

```bash
npm install react-router-dom
npm install -D tailwindcss postcss autoprefixer
npx tailwindcss init -p
```


---

### Step 4: Configure Tailwind CSS
In `tailwind.config.cjs`, add the following:

```javascript
content: [
  "./index.html",
  "./src/**/*.{js,ts,jsx,tsx}",
],
```

Then, add Tailwind directives in your `index.css`:

```css
@tailwind base;
@tailwind components;
@tailwind utilities;
```


---

### Step 5: Create Pages

#### Home.jsx
Displays a welcome message and links to other pages.

#### TasksManager.jsx
Displays a simple task list or message placeholder.

#### APIData.jsx
Fetches data from the API and displays it in a list format.


---

### Step 6: Setup Routing
In `App.jsx`, import **BrowserRouter** and define routes:

```jsx
import { BrowserRouter as Router, Routes, Route, Link } from "react-router-dom";
import Home from "./pages/Home";
import TasksManager from "./pages/TasksManager";
import APIData from "./pages/APIData";

function App() {
  return (
    <Router>
      <nav className="p-4 bg-gray-800 text-white flex gap-4">
        <Link to="/">Home</Link>
        <Link to="/tasks">Tasks</Link>
        <Link to="/api-data">API Data</Link>
      </nav>
      <Routes>
        <Route path="/" element={<Home />} />
        <Route path="/tasks" element={<TasksManager />} />
        <Route path="/api-data" element={<APIData />} />
      </Routes>
    </Router>
  );
}

export default App;
```


---

### Step 7: Fetch API Data
In `APIData.jsx`, fetch data from the API and display it.

```jsx
import { useEffect, useState } from "react";

function APIData() {
  const [posts, setPosts] = useState([]);

  useEffect(() => {
    fetch("https://jsonplaceholder.typicode.com/posts")
      .then((res) => res.json())
      .then((data) => setPosts(data.slice(0, 10)));
  }, []);

  return (
    <div className="p-4">
      <h1 className="text-2xl font-bold mb-4">API Data</h1>
      <ul className="space-y-3">
        {posts.map((post) => (
          <li key={post.id} className="p-3 bg-gray-100 rounded-lg shadow">
            <h2 className="font-semibold">{post.title}</h2>
            <p>{post.body}</p>
          </li>
        ))}
      </ul>
    </div>
  );
}

export default APIData;
```


---

### Step 8: Run and Test the Application

```bash
npm run dev
```

Visit **http://localhost:5173/** in your browser to see the app running.



## Author
**Phoebe Njeri Muriuki**