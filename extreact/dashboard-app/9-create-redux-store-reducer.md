
# เตรียม Redux store และ reducer

## 1. ติดตั้ง package 

```bash
npm i redux react-redux

// หรือ

yarn add redux react-redux
```

## 2. สร้าง Reducer 

```js
// src/redux/reducer.js
const initialState = {

}

export default (state = initialState, { type, payload }) => {
    switch (type) {

    case 'typeName':
        return { ...state, ...payload }

    default:
        return state
    }
}

```

## 3. สร้าง Store 

```js
// src/redux/store.js

import { createStore } from "redux";
import reducer from "./reducer";

export default function configureStore() {
    const store = createStore(reducer);
    return store;
}
```

## 4. สร้าง Store เข้ากับ App 

```js
// src/App.js

import React, { Component } from 'react';
import { Button, Container, ExtGrid, Panel, Titlebar, TreeList } from "@sencha/ext-react-modern";
import { ExtColumn } from "@sencha/ext-react-modern";
import { Route, Switch, useHistory } from 'react-router-dom';
import ContactView from './views/ContactView'

// Provider component จาก redux 
import { Provider } from "react-redux";

// import function มาจาก store.js
import configureStore from "./redux/store";

// สร้าง object ของ store
const store = configureStore();

const Ext = window['Ext'];

export default function App() {

  const history = useHistory();

  const onTreeMenuClick = (sender, info) => {
    let path = sender.info.node.getId()
    history.push(path)
  }


  return (
    {/* ครอบ Provider */}
    <Provider store={store}>
      <Container viewport="true" fullscreen layout="fit">
        <Titlebar title="Dashboard" docked="top">
        <Panel scrollable docked="left" shadow zIndex={2}>
          <TreeList
            ui="nav"
            expanderFirst={false}
            onItemclick={onTreeMenuClick}
            selection={'/'}
            store={{
              root: {
                children: [
                  { id: '/', text: 'Home', iconCls: 'x-fa fa-home', leaf: true },
                  { id: '/form', text: 'Form', iconCls: 'x-fa fa-file-signature', leaf: true }
                ]
              }
            }}
          />
        </Panel>
        <Switch>
          <Route path="/" exact>
            <Panel padding="10">
              <p>home</p>
            </Panel>
          </Route>
          <Route path="/form" exact>
            <ContactView />
          </Route>
        </Switch>
      </Container>
    </Provider>
  )
}



```