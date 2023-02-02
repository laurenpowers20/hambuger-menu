# React Hamburger Menu

Standard hamburger menu in React.js.
[Try it here](https://rococo-creponne-b55eb4.netlify.app/)

## References

- [React Icons](https://react-icons.github.io/react-icons/)

# How'd you do that?

1. First, create a new React app.

```bash
npx create-react-app hamburger-menu
```

2. After deleting the boiler-plate React files that we don't need, create a `HamburgerMenu.jsx` file.

3. Create a regular blank JSX function in the new file.

```javascript
function HamburgerMenu() {}
export default HamburgerMenu;
```

4. We're going to need to import a few things here. Since we're here, lets bring in our useState like so:

```javascript
import { useState } from "react";
```

5. Icons! You're gonna need a menu and an exit icon. You can use whatever icons you like, but I used this cute hamburger logo ![](./src/images/readmeLogo.png) in lieu of the traditional 3 lined one ![](./src/images/readmeLogolines.png). I used [React Icons](https://react-icons.github.io/react-icons/)

```bash
npm install react-icons --save
```

Import those icons on the top of your page with your useState

```javascript
import { GiHamburger } from "react-icons/gi";
import { GrClose } from "react-icons/gr";
import { useState } from "react";
```

6. Mmmk, we are getting there. Now, lets add our destructed array for our useState. Set him to false. Your JSX function should look like this thang so far.

```javascript
import { useState } from "react";
import { GiHamburger } from "react-icons/gi";
import { GrClose } from "react-icons/gr";

function HamburgerMenu() {
  const [navbarOpen, setNavbarOpen] = useState(false);
}
export default HamburgerMenu;
```

7. Lets set up our return within our HamburgerMenu function.

```javascript
return (
  <nav className="nav-bar">
    <button>
      <GrClose /> //icon
      <GiHamburger /> //icon
    </button>
    <nav className="nav-bar">
    <ul>
      <li>Burger One</li>
      <li>Burger Two</li>
      <li>Burger Three</li>
    </ul>
  </nav>
);
```

8. I'm going to use [React-Router](https://reactrouter.com/en/main) for this. I use Browser Router all the time. It's the best. Go to your terminial and install it.

```bash
npm install react-router-dom
```

9. Go to your `index.js` file and put this up top

```javascript
import { BrowserRouter as Router } from "react-router-dom";
```

10. Now wrap your `<App />` with the `<Router>` tags. Should look like this:

```javascript
mport React from "react";
import ReactDOM from "react-dom/client";
import "./index.css";
import App from "./App";
import reportWebVitals from "./reportWebVitals";
import { BrowserRouter as Router } from "react-router-dom";

const root = ReactDOM.createRoot(document.getElementById("root"));
root.render(
  <React.StrictMode>
    <Router>
      <App />
    </Router>
  </React.StrictMode>
);

// If you want to start measuring performance in your app, pass a function
// to log results (for example: reportWebVitals(console.log))
// or send to an analytics endpoint. Learn more: https://bit.ly/CRA-vitals
reportWebVitals();
```

11. Create your JSX files that we'll be navigating to. I just used `PageOne.jsx`, `PageTwo.jsx`, etc. Make 'em whatever they need to be.

12. Navigate to App.js and import the following up top:

```javascript
import { Routes, Route } from "react-router-dom";
```

13. Import all your pages that you want to navigate to like so:

```javascript
import PageOne from "./PageOne";
import PageTwo from "./PageTwo";
import PageThree from "./PageThree";
```

15. In the return statement in the App.js function, put your routes in:

```javascript
return (
  <Routes>
    <Route path="/pageone" element={<PageOne />} />
    <Route path="/pagetwo" element={<PageTwo />} />
    <Route path="/pagethree" element={<PageThree />} />
  </Routes>
);
```

16. Navigate back to Hamburger.jsx. Import

```javascript
import { NavLink } from "react-router-dom";
```

17. Link up your NavLink routes in those <li> tags. I keep the <li> tags becuase that's how you make a <nav> by convention. Some CSS will take the bullet points off. Do what ya want though!

```javascript
<li>
    <NavLink to="/pageone">
       Burger One
    </NavLink>
<li>

<li>
  <NavLink to="/pagetwo">
     Burger Two
  </NavLink>
</li>
```

18. Ok let's add some functionality to these fugazi buttons we got here. I used arrow functions. In the end, it's all just logic we use from our magical useState. The "handleToggle" is top open the menu and the "closeMenu" we'll add on the close icon.

```javascript
const [navbarOpen, setNavbarOpen] = useState(false);
const handleToggle = () => {
  setNavbarOpen(!navbarOpen);
};
const closeMenu = () => {
  setNavbarOpen(false);
};
```

19. And now...[ternary operators](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Conditional_Operator). Just read through it slowly and you'll understand what's happening. I like to say it out loud sometimes. "Is the nav bar open? If yes show close button. If not, show hamburger menu icon."

```javascript
<button onClick={handleToggle}>
          {navbarOpen ? (
            <GrClose  /> //close icon
          ) : (
            <GiHamburger  />// hamburger menu icon
          )}
        </button>
        <ul className={`menu-nav ${navbarOpen ? " show-menu" : ""}`}>
```

We can make some classNames using the ternary operator in the `<ul>` tag using interpolation. Yeah you can do that, React is so cool. Notice we put it in curly braces since it's JavaScript.

20. When you click on your NavLinks, you'll probably want the menu to close back up. So stick that closeMenu functions we defined on top right in NavLinks

```javascript
<li>
<NavLink
   to="/pageone"
    onClick={closeMenu}>
    Burger One
</NavLink>
  </li>
  <li>
<NavLink
    to="/pagetwo"
    onClick={closeMenu}>
    Burger Two
</NavLink>
  </li>
```



....instructions are still in progress! I gotta go be a human being so I'll finish later. Come back soon.

```

```
