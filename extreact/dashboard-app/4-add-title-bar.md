
# สร้าง TitleBar

```js
import React, { Component } from 'react';
import { Container, Titlebar, Panel } from "@sencha/ext-react-modern";
import {  Route, Switch } from 'react-router-dom';
const Ext = window['Ext'];

export default function App() {

  return (

      <Container viewport="true" fullscreen layout="fit">

        {/* 
          - เรียกใช้ title bar 
          - docked="top": กำหนดให้ใช้พื้นที่ด้านบนของ Container ทั้งหมด
        */} 
        <Titlebar title="Dashboard" docked="top"/>
        <Switch>
          <Route path="/" exact>
            {/* 
              ครอบ panel เพื่อให้ Container สามารถคำนวนพื่นที่ของ Layout ได้
            */} 
            <Panel padding="10">
              <p>home</p>
            </Panel>
          </Route>
        </Switch>
      </Container>
    
  )
}
```