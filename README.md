# Intro to React Router

## Objectives
* Understand browser history mechanics
* Introduce Single Page Applications
* Understand how React Router is designed to work
* Use React Router to map URIs to components

# Browser History Mechanics
Browsers have built in history mechanics. You can go **back** and **forward**
between pages you've been been to and you can **reload** the page you're on.

Imagine checking out a cafe using a search engine:

* Go to google.com
* Search for "cafe allegro seattle"
* Click on the first Yelp result to check out reviews
* Go **back** to the search results page
* Click on the official Cafe Allegro website
* **Reload** the page to see if they've announced their new coffee yet.

These controls make total sense as you traditionally browse web pages. It makes
sense to go **back** and **forward** between pages for search results, Yelp, and
some cafe's official website. Browser history mechanics are built for going
between different pages.

Pages can be all on the same site, or on many different sites. Browsing pages on
different sites is like using a search engine as above. Browsing pages on one
site is like viewing different articles on Wikipedia, or viewing different movie
pages on IMDB.

It's important to specifically note what a "page" is. A page is a whole HTML
file that your browser downloads and displays. You know you're navigating
between two different pages when you see your browser screen go blank, then
slowly load in a totally new page.

We're going into detail about what a page is in order to draw contrast to how
modern web applications don't use multiple pages like they used to. Modern web
applications are now often what we call **Single Page Applications**.

## Modern Single Page Applications
Modern web applications let you do lots of things on just one page. They try to
minimize how often you have to go to a new page where you see your browser go
blank and load everything over again. Instead, modern web apps serve just one
page and they change parts of the *contents* of the page dynamically, without
having to reload the entire page or send users to another page.

Websites that serve up only one page and change the content of the page
dynamically without reload the page are called **Single Page Applications**.

Imagine using Gmail:

* You load Gmail and see your inbox
* You start instant messaging a friend in a sidebar
* You start to compose a new email to your manager to request time off
* You search for an email with flight information
* You browse through more email to make sure you've talked your manager about
  getting time off before

This all happens on one page! The page never refreshes. The chat bar with your
friend never disappears as you compose an email and search through your inbox.

Gmail fits the definition of a **Single Page Applications**. Gmail loads one
page just once and that page replaces content dynamically to show you many
different things. That single page changes it's content dynamically without
reloading or sending you to another page. It's great!

Consider the benefits of a single page application:
* It's fast. Users don't have to wait for a page to reload over and over.
* It's persistent. You can have a chat window open in one corner and keep
  talking to a friend as the rest of Gmail switches between showing you your
  inbox, an email, or email search results.

## Single Page Apps Break Old History Mechanics!
Single Page Applications break the initial design of Browser History Mechanics.
The **back** and **forward** actions were built specifically to go back and
forth between different pages. Since single page apps only change the content
of themselves without actually sending users to different web pages the notion
of **back** and **forward** is lost.

When users press the **back** button in a Single Page Application they go back
off the one page, completely out of the Single Page Application.

Imagine being on Facebook, going to Gmail, going through several views of
different email inboxes, search results and then pressing the back button.

* Go to facebook.com
* Type in www.gmail.com to check your email
* Click on one email
* Search your email for plane tickets
* Click on on email to see ticket information
* Click **back** to go back to plane ticket search results
* The user ends up back at facebook.com

Since Gmail is a Single Page Application pressing the back button will take
the user all the way back to Facebook! Really, the user just wanted to go back
to their email search results.
 
## Introducing Modern Browser History Mechanics
Web Developers, users, and browser vendors all love Single Page Applications.
They're a great experience that the Internet community should embrace. At one
point people got together in committees and devised a way to upgrade the old
browser history mechanics to accommodate modern Single Page Applications.

The modern HTML5 specification (published October 2014) introduced new browser
history mechanics to make Single Page Applications easier to browse **back** and
**forward** even through they actually stay on the same page.

HTML5 introduced `.pushState` and `.replaceState` functions that allow web pages
to save custom history data to the browser. Now applications like Gmail can use
these functions to manually save custom browser history. When someone goes from
their inbox to a specific email Gmail can use `.pushState` to save information
about what the user is currently doing in the application. Now when the user
presses the **back** button the browser gives the saved information back to
Gmail and Gmail brings back the content the user was last looking at.

It's good that HTML5 introduced new browser history mechanics to make it easier
for us developers to build Single Page Applications. We're actually not going to
be using these new features directly ourselves. Instead, we'll use a tool called
**React Router** that bundles many concepts together and allows us to create our
own Single Page Applications extremely easily. So even though we won't use the
new history mechanics firsthand ourselves it's still important to know that our
framework is taking care of that for us under the hood.

# What is URL Routing?
Before we take a look at **React Router** let's see what **routing** means.

**Routing** defines what content is displayed when someone visits a certain a
URL. If I go to `http://github.com/` I would expect to see GitHub's homepage.
If I got to `http://github.com/login` I would expect to see a login page. Each
of these URLs is a **route**. A route pairs a URL with the content that should
be displayed for that URL. You should be able to visit a webpage, copy the URL
to a friend, and they should end up viewing the same page.

Let's take at an example of how content is routed by URLs by looking at the
General Assembly homepage.

Go to <https://generalassemb.ly/>. Interact with the menu in the top bar on
the right. You should see options for things like "On Campus," "Locations," and
"About." Click on the different links to pages and notice the URLs that you end
up at. Hover over the links to see their URL to save yourself from actually
navigating off the page.

This table shows the **path** for each URL. The path of a URL is everything
after the domain name. In this case the path is everything that appears
after "https://generalassemb.ly" in the location bar of the browser. The `/`
path is a special path called the root. It's the homepage.

Compare the paths in the URLs and get a sense for how URLs are routed to
content. Websites URLs are general split into succinct, descriptive,
hierarchical categories. Notice how going to `/locations` takes you to a page
showing all campus locations, then each specific location is in a hierarchy
under that, like `/locations/london` and `/locations/singapore`.

| **URL Route**                       | **Content**                                              |
|-------------------------------------|----------------------------------------------------------|
| /                                               | Homepage                                     |
| /about                                          | General Information                          |
| /education                                      | Shows all local upcoming courses             |
| /education/web-development-immersive            | WDI course details                           |
| /education/user-experience-design-immersive     | UX course details                            |
| /locations                                      | Shows all global GA locations                |
| /locations/london                               | Shows London-specific location information   |
| /locations/singapore                            | Shows London-specific location information   |

You can see that URLs *route* users to content. When someone types in a URL
they are ultimately shown content associated with that URL. It's also important
that someone should be able to copy a URL, send it to someone else, and everyone
should end up seeing the same thing.

Have you ever tried to send someone a link to what you're looking at on Google
Maps and then when they click on your link they end up looking at something
completely different? That's a great example of bad URL routing. (Google Maps
is actually much better about this these days.) URLs should represent the
main content of the page you're looking at!

# React Router Overview
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

### Single Page Applications and Browser History Mechanics
* Single Page Applications are websites that serve only one web page, then
  change the content of that page dynamically, without refreshing.
* Old browser history mechanics support **back** and **forward** operations that
  traditionally keep track of history as users move between different pages.
* Since modern Single Page Applications keep the user on one page without
  refreshing old browser history **back** and **forward** mechanics don't work
  well with modern applications.

### React Router
* Single Page Applications have specific URLs that are routed to display
  different content.
* React Router is a third-party library that we can install and use with React.
* React Router makes it easy to define how URLs are routed to different
  components.

## Licensing
All content is licensed under a CC­BY­NC­SA 4.0 license.
All software code is licensed under GNU GPLv3. For commercial use or alternative licensing, please contact legal@ga.co.
