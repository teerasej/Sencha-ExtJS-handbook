
# กำหนด Router ให้พร้อมใช้งาน

```js
// src/index.js

//import '@sencha/ext-modern-enterprise';
//import '@sencha/ext-modern-material';
import React from 'react';
//import ReactDOM from 'react-dom';
import ExtReactDOM from '@sencha/ext-react-modern';
import './index.css';
import App from './App';
import * as serviceWorker from './serviceWorker';

// เรียกใช้งาน Router
import { BrowserRouter as Router } from 'react-router-dom';

// ครอบ App ด้วย Router 
// สังเกตว่าในที่นี้เราใช้ ExtReactDOM แทน ReactDOM
ExtReactDOM.render(<Router><App /></Router>, document.getElementById('root'));


serviceWorker.unregister();

```