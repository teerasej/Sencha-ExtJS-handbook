
# สร้าง MapContext สำหรับแชร์ใช้งานใน Map Component

```js
// src/views/map/MapContext.js

import React from "react";

// สร้าง MapContext เพื่อใช้อ้างอิงตัว Map ของ OpenLayer ใน component อื่น
const MapContext = new React.createContext();
export default MapContext;
```