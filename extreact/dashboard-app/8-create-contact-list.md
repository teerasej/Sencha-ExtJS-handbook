
# สร้าง Contact List


## 1. สร้าง Contact List 

```js
// src/views/ContactList.js

import React from 'react'
import { List, Panel } from "@sencha/ext-react-modern"

const Ext = window['Ext'];

export default function ContactList() {

    // สร้าง store สำหรับ feed ข้อมูลให้ List Component
    const store = Ext.create('Ext.data.Store', {
        data: [{
                firstName: "Suzanna",
                lastName: "Lounds"
            }, {
                firstName: "Deidre",
                lastName: "West-Frimley"
            }, {
                firstName: "Theo",
                lastName: "Spyvye"
            }]
    })

    // สร้าง template สำหรับ list item 
    // สังเกตว่ารับข้อมูลเข้ามาเป็น object
    const itemTemplate = data => (
        <div>
            <div style={{ fontSize: '16px', marginBottom: '5px' }}>{data.firstName} {data.lastName}</div>
        </div>
    )

    // ใช้งาน list item
    return (
        <Panel title='Contacts' shadow scrollable>
            <List
                store={store}
                itemTpl={itemTemplate}
            />
        </Panel>
    )
}

```

## 2. แสดงใน ContactView 

```js
// src/views/ContactView.js


import React from 'react'
import { Container, Panel } from "@sencha/ext-react-modern";
import ContactForm from './ContactForm';
import ContactList from './ContactList';

export default function ContactView() {
    return (
        <Container layout="hbox">
            <Panel flex='1' padding='10'>
              <ContactForm />
            </Panel>
            <Panel flex='2' layout='fit' padding='10'>
              <ContactList />
            </Panel>
        </Container>
    )
}



```