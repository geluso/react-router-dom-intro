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

These controls make total sense as you traditionally browse the web. It makes
sense to go **back** and **forward** between search results, Yelp, and
some cafe's official website. Browser history mechanics are built for going
between lots of different pages.

Pages can be all on the same site, or on many different sites. Browsing pages on
different sites is like using a search engine as above. Browsing pages on one
site is like viewing different articles on Wikipedia, or viewing different movie
pages on IMDB.

## Modern Single Page Applications
Modern web applications let you do lots of things on just one page. Websites
that serve up only one page and change the content of the page dynamically
without reload the page are called **Single Page Applications**.

Imagine using Gmail:

* You load Gmail and see your inbox
* You start instant messaging a friend in a sidebar
* You start to compose a new email to your manager to request time off
* You search for an email with flight information
* You browse through more email to make sure you've talked your manager about
  getting time off before

This all happens on one page! The page never refreshes. The chat bar with your
friend never disappears as you compose an email and search through your inbox.

Modern web applications like Gmail are called **Single Page Applications**. A
Single Page Application serves up just one webpage and that web page is
configured to display all sorts of different content.

Gmail has one web page that shows you your inbox, shows you individual emails,
and lets you search through all your email.
 
Single Page Applications break the initial design of Browser History Mechanics.
The **back** and **forward** actions were built specifically to go back and
forth between different pages. These modern web pages keep you all on
just one page view many different views. When users press the **back** button
they go entirely off the page, completely out of the Single Page Application.

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
 
## Modern Browser History Mechanics
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
for us developers to build Single Page Applications. We're not going to be
using these new features directly ourselves. Instead, we'll use a tool
called **React Router** that bundles these modern features together for us
and allows us to create our own Single Page Applications extremely easily.

**React Router** makes it easy for us to swap out different content on the same
page  and it saves us from  having to manually manipulate browser history
mechanics.

# React Router Overview
React Router is designed to handle several common patterns that come with
creating Single Page Applications. React Router is actually a **third-party**
library. Third Party just means it's not built by React and it's not built by
ourselves. It's been written by some other "third-party" group of developers.
Even though React Router is third-party software it's extremely useful,
trustworthy, and popular.

Here's what React Router provides:

* **Routing:** easily define what content is associated with what URLs.
* **History:** automatically manage browser history when navigating between
  content.

## Routing Example
**Routing** is the act of displaying certain content when users navigate to
certain URLs. Let's take at an example of how content is routed by URLs by
looking at the General Assembly homepage.

Go to <https://generalassemb.ly/>. Interact with the menu in the top bar on
the right. You should see options for things like "On Campus," "Locations," and
"About." Click on the different links to pages and notice the URLs that you end
up at.

This table shows the **path** for each URL. The path of a URL is everything
after the domain name. In this case the path is everything that appears
after "https://generalassemb.ly" in the location bar of the browser. The `/`
path is a special path called the root.

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

# Installing React Router
Let's see how to actually install `react-router` and use it in a React app.
Let's build a simple Single Page App with a few different pages of content
for an imaginary dentist website.

1. Create a new React app.
2. Install React Router.
3. Import dependencies into your app.

```
create-react-app dentist-website
cd dentist-website
npm install --save react-router
npm start
```

**app.js**
```
const Router = require('react-router').Router
const Route = require('react-router').Route
const browserHistory = require('react-router').browserHistory;
```  

# Creating Routes

# Recap


## Licensing
All content is licensed under a CC­BY­NC­SA 4.0 license.
All software code is licensed under GNU GPLv3. For commercial use or alternative licensing, please contact legal@ga.co.
