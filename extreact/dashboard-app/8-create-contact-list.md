
# สร้าง Contact List


## 1. สร้าง Contact List 

```js
// src/views/ContactList.js

import React from 'react'
import { List } from "@sencha/ext-react-modern"

const Ext = window['Ext'];

export default function ContactList() {

    // สร้าง store สำหรับ feed ข้อมูลให้ List Component
    const store = Ext.create('Ext.data.Store', {
        data: [{
            id: 1,
            first_name: "Suzanna",
            last_name: "Lounds",
            phone: "180-809-4642"
        }, {
            id: 2,
            first_name: "Deidre",
            last_name: "West-Frimley",
            phone: "667-456-4774"
        }, {
            id: 3,
            first_name: "Theo",
            last_name: "Spyvye",
            phone: "704-602-1020"
        }]
    })

    // สร้าง template สำหรับ list item 
    // สังเกตว่ารับข้อมูลเข้ามาเป็น object
    const itemTemplate = data => (
        <div>
            <div style={{ fontSize: '16px', marginBottom: '5px' }}>{data.first_name} {data.last_name}</div>
            <div style={{ fontSize: '12px', color: '#666' }}>{data.title}</div>
        </div>
    )

    // ใช้งาน list item
    return (
        <List
            shadow
            store={store}
            itemTpl={itemTemplate}
        />
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
            <Panel flex="1" layout="fit">
                <ContactForm />
            </Panel>
            <Panel flex="2" layout="fit">
                <ContactList />
            </Panel>
        </Container>
    )
}



```