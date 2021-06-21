
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
    <FormPanel shadow padding='20' title='New Contact'>
      <TextField label='Name' required />
      <EmailField label='Email' placeholder='me@sencha.com' />
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
            <Panel flex="1" layout="fit">
                <ContactForm />
            </Panel>
        </Container>
    )
}

```