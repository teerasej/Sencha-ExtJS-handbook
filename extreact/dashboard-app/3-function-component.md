

# แปลง class component เป็น function component

```js

// src/App.js

import React, { Component } from 'react';

// เรียกใช้ Container component
import { Container, ExtGrid } from "@sencha/ext-react-modern";
import { ExtColumn } from "@sencha/ext-react-modern";
import { Route, Switch } from 'react-router-dom';

// สังเกตว่ามีการเรียกใช้ ExtJS library ตรงจุดนี้
const Ext = window['Ext'];

export default function App() {

  // กำหนด Container
  // ใช้งาน Switch และ Router 
  return (
    <Container viewport="true" fullscreen layout="fit">
      <p>Main</p>
      <Switch>
        <Route path="/" exact>
          <p>home</p>
        </Route>
      </Switch>
    </Container>
  )
}




```