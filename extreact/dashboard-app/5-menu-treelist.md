
# สร้าง Menu ด้วย TreeList

## 1. สร้าง menu ทางฝั่งซ้าย และครอบ panel ไว้ทางฝั่งขวา

```js
// src/App.js

import React, { Component } from 'react';
import { Button, Container, ExtGrid, Panel, Titlebar, TreeList } from "@sencha/ext-react-modern";
import { ExtColumn } from "@sencha/ext-react-modern";
import { BrowserRouter as Router, Route, Switch } from 'react-router-dom';
const Ext = window['Ext'];

export default function App() {

  return (
      <Container viewport="true" fullscreen layout="fit">
        <Titlebar title="Dashboard" docked="top">
        </Titlebar>

        {/* ใช้ panel เป็นตัวแทนของพื้นที่ Menu */}
        <Panel scrollable docked="left" shadow zIndex={2}>

          {/* ใช้ TreeList เป็นตัวแทนของ menu */}
          <TreeList
            ui="nav"
            expanderFirst={false}

            // กำหนดค่า Store เป็น Menu Item
            store={{
              root: {
                children: [
                  { id: '/', text: 'Home', iconCls: 'x-fa fa-home', leaf: true }
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
        </Switch>
      </Container>
  )
}

```

## 2. จับการเลือกคลิก menu ดึง id ของ menu มาใช้งานเป็น path

**เวลาดู document ให้สังเกตการใช้งานจาก code ตัวอย่าง หลีกเลี่ยงการ copy ชื่อ property หรือ event มาโดยตรง**

```js
// src/App.js

import React, { Component } from 'react';
import { Button, Container, Panel, Titlebar, TreeList } from "@sencha/ext-react-modern";
import { Route, Switch } from 'react-router-dom';
const Ext = window['Ext'];

export default function App() {

  // สร้าง function รับ id ของ menu item ที่ถูกเลือก
  const onTreeMenuClick = (sender, info) => {
    let path = sender.info.node.getId()
  }


  return (
      <Container viewport="true" fullscreen layout="fit">
        <Titlebar title="Dashboard" docked="top">
        </Titlebar>
        <Panel scrollable docked="left" shadow zIndex={2}>
          <TreeList
            ui="nav"
            expanderFirst={false}

            // กำหนด function ให้ onItemclick
            onItemclick={onTreeMenuClick}
            selection={'/'}
            store={{
              root: {
                children: [
                  { id: '/', text: 'Home', iconCls: 'x-fa fa-home', leaf: true },
                  
                  // สร้าง menu item ที่ 2
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

          {/* สร้าง Route ที่ 2 */}
          <Route path="/form" exact>
            <Panel padding="10">
              <p>form</p>
            </Panel>
          </Route>
        </Switch>
      </Container>
  )
}



```