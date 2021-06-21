
# 

```js
import React, { Component } from 'react';
import { Button, Container, Titlebar } from "@sencha/ext-react-modern";
import {  Route, Switch } from 'react-router-dom';
const Ext = window['Ext'];

export default function App() {

  return (

      <Container viewport="true" fullscreen layout="fit">

        // เรียกใช้ title bar
        <Titlebar title="Dashboard" docked="top">
        </Titlebar>
        <Switch>
          <Route path="/" exact>
            <p>home</p>
          </Route>
        </Switch>
      </Container>
    
  )
}
```