
# การตั้งชื่อ Namespaces 

หลักการตั้งชื่อ Namespace คือ **<ชื่อ Application>.<ชื่อโฟลเดอร์>.<ชื่อ Class>**

เช่น ถ้าใน class MainView ในโปรเจคมีรูปแบบนี้ 

```
app
  L desktop 
         L src
             L Application.js // ที่กำหนดชื่อ Application 
             L view
                  L main
                       L MainView.js
```

- ที่อยู่ของไฟล์ในโปรเจคคือ **app/desktop/src/view/main/MainView.js** 
- สมมติว่าในไฟล์ Application.js มีการกำหนดชื่อ Application เป็น **CounterApp**

```js
// Application.js

Ext.define('CounterApp.Application', {
  extend: 'Ext.app.Application',
  name: 'CounterApp',  // กำหนดชื่อ Application
  //...
})
```

- เวลาอ้างอิงที่อยู่ class เราจะอ้างอิงกับที่อยู่ของ ไฟล์ **Application.js** ทำให้ได้เป็น **view/main/MainView.js** 

ดังนั้นตอนตั้งชื่อ namespace ให้ class ในโค้ด JavaScript จะเป็น 

```js
// MainView.js
//        | ชื่อแอพ     | ชื่อโฟลเดอร์| ชื่อ Class
Ext.define('CounterApp.view.main.MainView', {
  //...
})

```

