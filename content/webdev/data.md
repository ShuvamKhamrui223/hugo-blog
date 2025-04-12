---
authors: 
- John Doe
date: 2025-01-20
type: "blog"
title: "current page link styling in react js with tailwind css"
description: "Steps to Style Current Page NavLink in react js with tailwind css"
categories: ["Web Development"]
tags: ["web development", "technology", "future"]
draft: false
featured: true
---

## current page link styling

You can style the current page NavLink differently in a React application using React Router and Tailwind CSS by utilizing the isActive property provided by the NavLink component. Here's how to do it:

Steps to Style Current Page NavLink

• Use NavLink Component: React Router's NavLink provides an isActive boolean property that indicates whether the link corresponds to the current route.

• Apply Tailwind Classes Dynamically: Use a function to apply conditional Tailwind classes based on the isActive property.

Code Example

```js
import { NavLink } from "react-router-dom";
const Navbar = () => {
  return (
    <nav className="bg-gray-800 p-4">
      <ul className="flex space-x-4">
        <li>
          <NavLink
            to="/"
            className={({ isActive }) =>
              isActive
                ? "text-white font-bold border-b-2 border-white"
                : "text-gray-400 hover:text-white"
            }
          >
            {" "}
            Home{" "}
          </NavLink>{" "}
        </li>{" "}
        <li>
          {" "}
          <NavLink
            to="/about"
            className={({ isActive }) =>
              isActive
                ? "text-white font-bold border-b-2 border-white"
                : "text-gray-400 hover:text-white"
            }
          >
            {" "}
            About{" "}
          </NavLink>{" "}
        </li>{" "}
        <li>
          {" "}
          <NavLink
            to="/contact"
            className={({ isActive }) =>
              isActive
                ? "text-white font-bold border-b-2 border-white"
                : "text-gray-400 hover:text-white"
            }
          >
            {" "}
            Contact{" "}
          </NavLink>{" "}
        </li>{" "}
      </ul>{" "}
    </nav>
  );
};
export default Navbar;
```

Explanation

• className Prop:

• The className prop of NavLink accepts a function that receives an isActive property.

• You can return a string of Tailwind classes based on whether isActive is true or false.

• Active Styles:

• When isActive is true, apply specific styles (e.g., text-white font-bold border-b-2 border-white).

• When isActive is false, apply default styles (e.g., text-gray-400 hover:text-white).

• Tailwind Classes:

• text-white: White text for the active link.

• font-bold: Bold text for the active link.

• border-b-2 border-white: Adds a white underline for the active link.

• text-gray-400: Gray text for inactive links.

• hover:text-white: Changes text color to white on hover.

Result

• The current page's navigation link will have distinct styles (e.g., bold text, underline).

• Inactive links will have a default appearance but change on hover.

Additional Tips

• Dynamic Styling: If you have a lot of links and need reusable logic, extract the className logic into a function:

```js
const navLinkClass = (isActive: boolean) =>
  isActive
    ? "text-white font-bold border-b-2 border-white"
    : "text-gray-400 hover:text-white";
```

Then use it in your NavLink:

```js
<NavLink to="/" className={({ isActive }) => navLinkClass(isActive)}>
  {" "}
  Home{" "}
</NavLink>
```

• Mobile Navigation: Use responsive utilities like sm:hidden or lg:flex to style links differently for mobile and desktop views.

Let me know if you need further assistance!

If you have general styles that should always be applied to your NavLink components, irrespective of whether they are active or not, you can combine the general styles with the conditional active styles. Here's how you can do it:

Code Example with General Styles

```js
import { NavLink } from "react-router-dom";
const Navbar = () => {
  //   Define the base styles
  const baseStyles = "px-4 py-2 text-sm rounded transition-all";
  return (
    <nav className="bg-gray-800 p-4">
      {" "}
      <ul className="flex space-x-4">
        {" "}
        <li>
          {" "}
          <NavLink
            to="/"
            className={({ isActive }) =>
              `${baseStyles} ${
                isActive
                  ? "text-white font-bold border-b-2 border-white"
                  : "text-gray-400 hover:text-white"
              }`
            }
          >
            {" "}
            Home{" "}
          </NavLink>{" "}
        </li> <li>
          {" "}
          <NavLink
            to="/about"
            className={({ isActive }) =>
              `${baseStyles} ${
                isActive
                  ? "text-white font-bold border-b-2 border-white"
                  : "text-gray-400 hover:text-white"
              }`
            }
          >
            {" "}
            About{" "}
          </NavLink>{" "}
        </li> <li>
          {" "}
          <NavLink
            to="/contact"
            className={({ isActive }) =>
              `${baseStyles} ${
                isActive
                  ? "text-white font-bold border-b-2 border-white"
                  : "text-gray-400 hover:text-white"
              }`
            }
          >
            {" "}
            Contact{" "}
          </NavLink>{" "}
        </li>{" "}
      </ul>{" "}
    </nav>
  );
};
export default Navbar;
```

Explanation

• Base Styles:

• The baseStyles variable contains general styles (px-4 py-2 text-sm rounded transition-all) that are applied to all links, regardless of their active state.

• These include padding, text size, rounded corners, and transitions for smooth hover effects.

• Active and Inactive Styles:

• Conditional styles (isActive ? ... : ...) are appended to the base styles.

• Active links get specific styles (e.g., text-white font-bold border-b-2 border-white).

• Inactive links get default styles (e.g., text-gray-400 hover:text-white).

• Combining Styles:

• The ${baseStyles} ensures the general styles are always applied.

• ${isActive ? ... : ...} dynamically adds active or inactive styles.

Result

• All NavLink components will have the base styles (e.g., padding, rounded corners).

• The current page's link will have distinct active styles (e.g., bold text, underline).

• Inactive links will retain their default appearance with hover effects.

Reusable Function for Styling

If you want to make the styling reusable across multiple components, create a helper function:

const getNavLinkClass = (isActive: boolean) => `px-4 py-2 text-sm rounded transition-all ${ isActive ? "text-white font-bold border-b-2 border-white" : "text-gray-400 hover:text-white" }`;

Then use it in your NavLink components:

<NavLink to="/" className={({ isActive }) => getNavLinkClass(isActive)}> Home </NavLink>

This approach keeps your code clean and DRY (Don't Repeat Yourself). Let me know if you need more enhancements!
