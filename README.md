# RocketNative Snippets
## React Native code snippets for Sublime Text

## Summary

- [Installation](#installation)
- [Usage](#usage)
    - [Component](#component)
    - [ESLint](#eslint)
    - [Redux](#redux)
    - [Reactotron](#reactotron)
    - [Babel](#babel)
    - [Apisauce](#apisauce)

![Demo](https://raw.githubusercontent.com/diego3g/rocketnative-sublime-snippets/master/demo.gif)

### Installation
To install through [Package Control](http://wbond.net/sublime_packages/package_control),
search for **RocketNative Snippets**. If you still don't have Package Control in Sublime Text, [go get it](http://wbond.net/sublime_packages/package_control/installation).
It's pure awesomeness.

## Usage
### Component
#### [component] - Create react-native component
```javascript
/* Core */
import React, { Component } from 'react';

/* Presentational */
import { View } from 'react-native';

// import styles from './styles';

export default class MyComponent extends Component {
  render() {
    return (
      <View />
    );
  }
}
```

#### [proptypes] - Create component propTypes
```javascript
static propTypes = {

};
```

#### [defaultprops] - Create component defaultProps
```javascript
static defaultProps = {

};
```

#### [render] - Create render method
```javascript
render() {
  return (
    <View />
  );
}
```

### ESLint
#### [eslint] - Create eslint file config
```json
{
  "parser": "babel-eslint",
  "env": {
    "browser": true,
    "jest": true
  },
  "plugins": [
    "react-native",
    "jsx-a11y",
    "import"
  ],
  "extends": [
    "airbnb",
    "plugin:react-native/all"
  ],
  "rules": {
    "react/jsx-filename-extension": ["error", { "extensions": [".js", ".jsx"] }],
    "global-require": "off",
    "no-console": "off",
    "import/prefer-default-export": "off",
    "no-unused-vars": ["error", {"argsIgnorePattern": "^_"}]
  },
  "settings": {
    "import/resolver": {
      "babel-module": {}
    }
  },
  "globals": {
    "__DEV__": true
  }
}
```

### Redux
#### [reduxSetup] - Create Redux Setup file
```javascript
import { combineReducers } from 'redux';

/* Reducers */
// import navReducer from 'navigation/reducer';

import configureStore from './configureStore';
// import rootSaga from './sagas';

export default () => {
  const rootReducer = combineReducers({
    // nav: navReducer,
  });

  return configureStore(rootReducer, rootSaga);
};
```

#### [configureStore] - Create configureStore file
```javascript
import { createStore, applyMiddleware, compose } from 'redux';

export default (rootReducer) => {
  const middleware = [];
  const enhancers = [];

  /* Saga */
  // const sagaMonitor = __DEV__ ? console.tron.createSagaMonitor() : null;
  // const sagaMiddleware = createSagaMiddleware({ sagaMonitor });
  // middleware.push(sagaMiddleware);

  enhancers.push(applyMiddleware(...middleware));

  /* Store */
  const createAppropriateStore = __DEV__ ? console.tron.createStore : createStore;
  const store = createAppropriateStore(rootReducer, compose(...enhancers));

  /* Run Saga */
  // sagaMiddleware.run(rootSaga);

  return store;
};
```

#### [reduxComponent] - Create react-native Redux component
```javascript
/* Core */
import React, { Component } from 'react';

/* Presentational */
import { View } from 'react-native';

/* Redux */
import { connect } from 'react-redux';

// import styles from './styles';

class  extends Component {
  render() {
    return (
      <View />
    );
  }
}

const mapStateToProps = state => ({

});

const mapDispatchToProps = dispatch => ({

});

export default connect(mapStateToProps, mapDispatchToProps)();
```

#### [mapStateToProps] - Create redux mapStateToProps
```javascript
const mapStateToProps = state => ({

});
```

#### [mapDispatchToProps] - Create redux mapDispatchToProps
```javascript
const mapDispatchToProps = dispatch => ({

});
```

#### [duck] - Create react-native duck module
```javascript
import { createReducer, createActions } from 'reduxsauce';
import Immutable from 'seamless-immutable';

/* Types & Action Creators */

const { Types, Creators } = createActions({
  // actionType: ['dataPassed'],
});

export const TesteTypes = Types;
export default Creators;

/* Initial State */

export const INITIAL_STATE = Immutable({
  // data: [],
});

/* Reducers */

// export const reducer = state =>
//   state.merge({ data: [] });

/* Reducers to types */

export const reducer = createReducer(INITIAL_STATE, {
  // [Types.ACTION_TYPE]: reducer,
});
```

### Reactotron
#### [reactotronconfig] - Create Reactotron Config
```javascript
import Reactotron from 'reactotron-react-native';

if (__DEV__) {
  const tron = Reactotron
    .configure()
    .useReactNative()
    .connect();

  tron.clear();

  console.tron = tron;
}
```

### Babel
#### [moduleResolver] - Create Module Resolver config
```json
"plugins": [
  [
    "module-resolver",
    {
      "root": ["./src"],
      "extensions": [".js", ".ios.js", ".android.js"]
    }
  ]
]
```

### Apisauce
#### [apisauce] - Create APISauce Config
```javascript
import { create } from 'apisauce';

const api = create({
  baseURL: 'http://localhost:3000',
});

export default api;
```