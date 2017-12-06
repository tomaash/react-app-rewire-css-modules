# react-app-rewire-css-modules

Add [CSS Module](https://github.com/css-modules/css-modules) loaders to your [create-react-app](https://github.com/facebookincubator/create-react-app) via [react-app-rewired](https://github.com/timarney/react-app-rewired).

CSS Module styles can be written in CSS (including PostCSS)
Unlike codebandits/react-app-rewire-css-modules this fork does NOT contain any SASS. Enough problems with the node-sass lib already.

## Installation

This package is not yet published to the npm registry. Install from GitHub:

```
yarn add --dev tomaash/react-app-rewire-css-modules 
```

OR

```
npm install --save-dev tomaash/react-app-rewire-css-modules 
```

## Usage

Use the following file extensions for any CSS Modules styles:

- `*.module.css`

Files with the following file extensions will load normally, without the CSS Modules loader:

- `*.css`

### Example

In your react-app-rewired configuration:

```javascript
/* config-overrides.js */

const rewireCssModules = require('react-app-rewire-css-modules');

module.exports = function override(config, env) {
    // ...
    config = rewireCssModules(config, env);
    // ...
    return config;
}
```

In your React application:

```css
// src/App.module.css

.app {
  color: aqua;
  
  &:hover {
    color: lawngreen;
  }
}
```

```jsx harmony
// src/App.js

import React from 'react';
import styles from './App.module.css';

export default ({text}) => (
    <div className={styles.app}>{text}</div>
)
```
