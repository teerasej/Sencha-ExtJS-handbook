
# สร้าง menu และ Map View

## 1. สร้าง Map View 

สร้างไฟล์ MapView ใหม่ 

```js
// src/views/map/MapView.js

import React from 'react'
import { Panel } from '@sencha/ext-react-modern';

export default function MapView() {


    return (
        <Panel padding='10'>
           
        </Panel>
    )
}

```

## 2. เพิ่มเมนูใน App.js 

```js
// src/App.js

import React from 'react';
import { Container, Panel, Titlebar, TreeList } from "@sencha/ext-react-modern";
import { Route, Switch, useHistory } from 'react-router-dom';
import ContactView from './views/ContactView'

// Import map view
import MapView from './views/map/MapView'

import { Provider } from "react-redux";

import configureStore from "./redux/store";

const store = configureStore();


export default function App() {

  const history = useHistory();

  const onTreeMenuClick = (sender, info) => {
    let path = sender.info.node.getId()
    history.push(path)
  }


  return (
    <Provider store={store}>
      <Container viewport="true" fullscreen layout="fit">
        <Titlebar title="Dashboard" docked="top">
        </Titlebar>
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
                  { id: '/form', text: 'Form', iconCls: 'x-fa fa-file-signature', leaf: true },

                  // เพิ่ม map view ใน menu
                  { id: '/map', text: 'Map', iconCls: 'x-fa fa-map-marker', leaf: true }
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

          // เพิ่ม map view
          <Route path="/map" exact>
            <MapView />
          </Route>
        </Switch>
      </Container>
    </Provider>
  )
}



```