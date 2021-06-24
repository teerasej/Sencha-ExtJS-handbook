
# สร้าง control component สำหรับใข้ใส่ control อื่นๆ

```js
// src/views/map/controls/Controls.js

import React from "react";

const Controls = ({ children }) => {
  return <div>{children}</div>;
};

export default Controls;
```