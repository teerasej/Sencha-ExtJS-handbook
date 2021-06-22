
# สร้าง Contact Form

## 1. สร้าง Contact Form 

```js
// src/views/ContactForm.js
import React from "react";
import {
  Button,
  Container,
  EmailField,
  FormPanel,
  TextField,
  TitleBar,
  Toolbar,
} from "@sencha/ext-react-modern";

export default function ContactForm() {
  return (
    <FormPanel padding='20'>
      <FieldSet title="New Contact" defaults={{labelAlign: "placeholder"}}>
        <TextField label='First name' required />
        <TextField label='Last name' required />
        <EmailField label='Email' placeholder='me@sencha.com' />
      </FieldSet>
      <Toolbar shadow={false} docked="bottom" layout={{ pack: 'right' }}>
        <Button text="Add"/>
      </Toolbar>
    </FormPanel>
  );
}

```

## 2. แสดงใน ContactView 

```js
// src/views/ContactView.js


import React from 'react'
import { Container, Panel } from "@sencha/ext-react-modern";
import ContactForm from './ContactForm';

export default function ContactView() {
    return (
        <Container layout="hbox">
            <Panel flex='1' layout='fit' padding='10'>
                <ContactForm />
            </Panel>
        </Container>
    )
}

```