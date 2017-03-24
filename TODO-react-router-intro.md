* [TODO] Installing React Router
  * [TODO] clarify `npm install --save react-router-dom`
  * [TODO] clarify what `--save` does
* [TODO] Importing React Router
  * [TODO] clarify the import statement
    * is it always required? (router/route: yes, Link: no)
* [TODO] clarify component imports
  * these are files defined in the project
  * these are components, just like we're used to
  * each component represents one page on our website
  * React Router allows us to define the pages in components in different
    files, then we use <Router> and <Route> to define how they fit into
    our page and React Router bundles it all into a single page app when
    we put it online.
* [ ] meet Sunday Night Deadline

Under the Installing section: you have the import components section (home,
procedures, contact). You haven't explained what these are - they aren't by
default added when you do create-react-app. Are they added by install
react-router-DOM? Are they files in the dentist repo, but you said to create a
new app. If we're building them, include in the codealong here a really basic
framework of these - they aren't going to do anything unless you also do it!

So after "app.js", you can be like, "We'll also have base components that we can
pull in, so let's quickly make components that are just the same as the ones
we're used to." and then just show the code for those.

"Import dependencies into your app. This will be React and a css file as per
usual, but make sure to import any components you plan on having the user see,
and then everything we require from Router.... <now have the explanation of the
things from Router>"

In your breakdown bullets beneath Creating Routes, just add the code as a 'to
show'. like, leave it all as is :)

under the path and component definitions, have another sentence of explanation
before the link bullet. Something like, The syntax for this is  <Route
path="<your URL>" component={<the Component to load} /> . For example, <Route
path="/procedures" component={Procedures} /> tells our app "when someone wants
to go to the /procedures page, load the Procedures component."

And then the same - under the to definition,
The syntax for this is
<li><Link to="<your URL>">Your Displayed Text</Link></li>.

For example,
<li><Link to="/procedures">Procedures</Link></li> tells our app "There's a link,
display "Procedures."
When someone clicks this, it will call the right Route
path call on the page (the previous bullet we just saw!)."

Question: Where does this render?
  Is there still a render call in Index.js?
  Will this go where the nav bar is?
  explain (I know it's in the example repo, but explain also).
  
Maybe make a super simple sketch of a nav bar with a block div under it
and "different components will render here." Thanks!

What's 'exact path' and why is that one different?
Do you always need an exact path?

Maybe add, "now you can build this out and try it in the browser
see how it just reloads the components?
And your browser history doesn't update."

Ah a thought on one of those bullets -

My bullet was, " you have the import components section (home, procedures,
contact). You haven't explained what these are - they aren't by default added
when you do create-react-app. Are they added by install react-router-DOM? Are
they files in the dentist repo, but you said to create a new app. If we're
building them, include in the codealong here a really basic framework of these -
they aren't going to do anything unless you also do it! So after "app.js",

you can be like,

"We'll also have base components that we can pull in, so let's
quickly make components that are just the same as the ones we're used to." and
then just show the code for those." But these are made in your dentist repo. So
I would say recommend something like this,

"We're importing the components home,
procedures, and contact. These are just regular components that you're used to,
so create three new files - contact.js, home.js, and procedure.js. Remember,
they'll have the syntax of

import React, { Component } from 'react';
class <ClassName> extends Component {
  render () {
    return (
      <div>
        <div>Whatever you'd like this component to display! </div>
        <div>Really, anything!</div>
        <div>Just make sure there's only one top-level div!</div>
      </div>
    );
  }
}
module.exports = Home;

You can look in the dentist solution repo for the full code of these."
