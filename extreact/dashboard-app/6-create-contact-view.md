
# สร้าง Contact View

## 1. สร้าง ContactView Component

```js
// src/views/ContactView.js
import React from 'react'

export default function ContactView() {
    return (
        <Container layout="hbox">
        </Container>
    )
}

```

## 2. นำ ContactView มาใส่ใน App.js 

```js
// src/App.js

  return (
      
      //...

        <Switch>
          <Route path="/" exact>
            <Panel padding="10">
              <p>home</p>
            </Panel>
          </Route>
          <Route path="/form" exact>
            <ContactView/>
          </Route>
        </Switch>
//...
  )

```