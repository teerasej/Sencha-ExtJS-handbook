
# เรียกใช้ Reducer กับ Store ของ Contact List

## 1. แยกข้อมูล users ไปไว้ที่ reducer

```js
// src/redux/reducer.js

const initialState = {
    // ย้ายข้อมูลเริ่มต้นมาใว้ใน Redux state
    users: [{
        firstName: "Suzanna",
        lastName: "Lounds"
    }, {
        firstName: "Deidre",
        lastName: "West-Frimley"
    }, {
        firstName: "Theo",
        lastName: "Spyvye"
    }]
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

## 2. เรียกใช้ข้อมูลจาก users จาก reducer ในการสร้าง store

```js
// src/views/ContactList.js


import React from 'react'
import { List } from "@sencha/ext-react-modern"
import { useSelector } from 'react-redux';

const Ext = window['Ext'];

export default function ContactList() {

    // ใช้ useSelector ดึงข้อมูลจาก Redux มาใช้งาน
    const users = useSelector(state => state.users)
    
    const store = Ext.create('Ext.data.Store', {

        // กำหนดข้อมูลที่ได้จาก reducer เข้า Store
        data: users
    })

    const itemTemplate = data => (
        <div>
            <div style={{ fontSize: '16px', marginBottom: '5px' }}>{data.first_name} {data.last_name}</div>
        </div>
    )

    return (
        <List
            store={store}
            itemTpl={itemTemplate}
        />
    )
}

```