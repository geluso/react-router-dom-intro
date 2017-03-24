# Intro to React Router

## Objectives
* Review how websites use URLs to route content
* Introduce React Routers main features: routing, components, history
* Use React Router to map URLs to components
* Use React Router to create links to different pages

# Intro to React Router
Now let's see see how we can use **React Router** to route URLs to content. In
our React apps, our content will be associated with a component. Once we define
what URLs route to which components **React Router** will handle replacing the
content and keeping track of browser history all automatically.

Here's what React Router provides:

* **Routing:** easily define what content is associated with what URLs.
* **History:** automatically manage browser history when navigating between
  content.

React Router is actually a **third-party** library. Third Party just means it's
not built by React and it's not built by ourselves. It's been written by some
other "third-party" group of developers. Even though React Router is third-party
software it's extremely useful, trustworthy, and popular.

# Installing React Router
Full Repo: <https://github.com/geluso/react-router-simple-dentist-site>
Live Site: <https://react-router-dentist.herokuapp.com/>

Let's see how to actually install `react-router-dom` and use it in a React app.
We'll build a simple Single Page App with a few different pages of content
for an imaginary dentist website.

1. Create a new React app with `create-react-app`
2. Install `react-router-dom`
3. Import `Home`, `Procedures`, and `Contact` components
4. Import `BrowserRouter as Router`, `Route`, and `Link`
5. Wrap `<Route>` components with `<Router>` component
6. Use `<Route>` components to map URLs to `Home`, `Procedure`, and `Contact`
  Components

Create the new React app and install `react-router-dom`:

```
create-react-app dentist-website
cd dentist-website
npm install --save react-router-dom
npm start
```

Import our `Home`, `Procedures`, and `Contact` components and import the
React Router components too:

**app.js**
```
import React, { Component } from 'react';
import './App.css';

import Home from './home';
import Procedures from './procedures';
import Contact from './contact';

import {
  BrowserRouter as Router,
  Route,
  Link
} from 'react-router-dom'
```

# Creating Routes
React Router uses three of it's own components to define how URLs are routed
to components, and to create links to those routes. Let's look at each of the
three in summary:

* **<Router>** - this component is a container component that all the other
  React Router components must be wrapped inside of.
* **<Route>** - this component creates a definition routing one URL to a
  component. This component has two attributes:
  * **path** - defines the URL path that leads to the component. If someone
    types in the URL defined here then the site will display the component as
    the content of the page.
  * **component** - a reference to the component to show as content when
    someone navigates to the URL.
* **<Link>** - This component creates `<a>` tags and automatically integrates
  modern HTML5 browser history mechanics for the Single Page Application. It
  has one attribute:
  * **to** - this attribute defines what path to navigate to.
    
Here's what the components all look like together. The `<Router>` component is
wrapped around everything. There's a `<nav>` section that contains several
`<Link>` components that link to the different pages. After the `<nav>` section
the `<Route>` components define how the URL paths are actually associated with
each component.

**app.js**
```
class App extends Component {
  render() {
    return (
      <Router>
        <div>
          <nav>
            <ul>
              <li><Link to="/">Home</Link></li>
              <li><Link to="/procedures">Procedures</Link></li>
              <li><Link to="/contact">Contact</Link></li>
            </ul>
          </nav>
          <Route exact path="/" component={Home} />
          <Route path="/procedures" component={Procedures} />
          <Route path="/contact" component={Contact} />
        </div>
      </Router>
    );
  }
}

export default App;
```  

# Recap
Here's a summary of what we've learned today:

### React Router
* Single Page Applications have specific URLs that are routed to display
  different content.
* React Router makes it easy for us to route URLs to components.
* React Router automatically manipulates modern browser history mechanics.
* React Router is a third-party library that we can install and use with React.

## Licensing
All content is licensed under a CC­BY­NC­SA 4.0 license.
All software code is licensed under GNU GPLv3. For commercial use or alternative licensing, please contact legal@ga.co.
