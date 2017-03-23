# React Router Simple Dentist Website
This website is a simple example of how to route URLs to different components
using `react-router-dom`. 

Here's how you can hook up a nav bar to each component, and route URLs to
each component in your main `App.js` file:

```js
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

## Licensing
All content is licensed under a CC­BY­NC­SA 4.0 license.
All software code is licensed under GNU GPLv3. For commercial use or alternative licensing, please contact legal@ga.co.

