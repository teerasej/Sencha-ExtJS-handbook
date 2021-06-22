
# ส่งข้อมูลจาก Form เข้า Contact List

## 1. กำหนด action type ใน reducer

```js
// src/redux/reducer.js

const initialState = {
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
    
    // กำหนด action type และอัพเดต state
    case 'ADD':
        console.log(type,payload)
        return { ...state, users: [...state.users, payload ] }

    default:
        return state
    }
}

```

## 2. dispatch ข้อมูลเข้า redux จาก Contact Form 

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

import * as yup from 'yup'
import { Field, Formik } from "formik";

import WrapTextField from './WrapTextField'
import { useDispatch } from "react-redux";

export default function ContactForm() {

  // เรียกใช้งาน dispatch
  const dispatch = useDispatch()

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

        // ส่ง action เข้า redux
        dispatch({ type:'ADD', payload: values})
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