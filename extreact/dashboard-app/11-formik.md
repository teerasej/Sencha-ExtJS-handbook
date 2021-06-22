
# การใช้ Formik กับ ExtJS

## 1. ติดตั้ง package

รันคำสั่งใน Terminal ของโปรเจค

```bash
npm i yup formik

// หรือ

yarn add yup formik
```

## 2. สร้าง Custom TextField ของ ExtJS เพื่อให้ทำงานกับ Formik ได้ 

```js
// สร้างอีก component หนึ่งแยก src/views/WrapTextField.js


import { TextField } from '@sencha/ext-react-modern'
import React from 'react'

export default function WrapTextField({ field, form, label }){

  // ถ้ามีการเปลี่ยนแปลงค่าใน TextField เราจะอัพเดตให้กับ formik โดยตรง
  const onValueChange = ({textField, newValue, OldValue}) => {
    form.handleChange(field.name)
    form.setFieldValue(field.name, newValue)
  }
 
  // ถ้าเกิด blur event ให้ส่งใช้งานกับ formik ด้วย
  const onFieldBlur = () => {
    form.handleBlur(field.name)
  }

  return (
    <TextField 
    name={field.name} 
    label={label} 
    value={field.value}
    onChange={onValueChange} 
    onBlur={onFieldBlur}/>
  )
}

```

## 3. สร้างตัวรับข้อมูลด้วย formik และ validate ด้วย yup

```js
// src/views/ContactForm.js

import React from "react";
import {
  Button,
  Displayfield,
  EmailField,
  FieldSet,
  FormPanel,
  TextField,
  Toolbar,
} from "@sencha/ext-react-modern";

// เรียกใช้งาน Yup และ Formik
import * as yup from 'yup'
import { Field, Formik } from "formik";

// นำเอา Custom TextField เข้ามาใช้
import WrapTextField from './WrapTextField'


export default function ContactForm() {

  // กำหนด validation rule ด้วย yup
  const validationSchema = yup.object({
    firstName: yup.string()
      .required('Fill something...'),
    lastName: yup.string()
      .required('Fill something...')
  })


  return (
    <Formik
      initialValues={{
        firstName: '',
        lastName: ''
      }}
      validationSchema={validationSchema}
      onSubmit={(values, { resetForm, setErrors }) => {
        console.log('ok',values)
        resetForm();
        setErrors({});
      }}
    >
      {
        ({handleSubmit, errors }) => (
          <FormPanel padding='20' shadow title='New Contact'>
            <FieldSet >
              <Field
                id="firstName"
                name="firstName"
                component={WrapTextField}
                label="First Name"
              />
              {Boolean(errors.firstName) ?
                (<Displayfield value={errors.firstName}/>) : null
              }
              <Field
                id="lastName"
                name="lastName"
                component={WrapTextField}
                label="Last Name"
              />
              {Boolean(errors.lastName) ?
                (<Displayfield value={errors.lastName}/>) : null
              }
            </FieldSet>
            <Toolbar shadow={false} docked="bottom" layout={{ pack: 'right' }}>
              <Button text="Add" handler={handleSubmit}/>
            </Toolbar>
          </FormPanel>
        )
      }
    </Formik>
  );
}

```

