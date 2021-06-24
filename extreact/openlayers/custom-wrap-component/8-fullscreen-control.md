
# สร้าง full screen control

```js
// src/views/map/controls/FullScreenControl.js

import React, { useContext, useEffect, useState } from "react";
import { FullScreen } from "ol/control";
import MapContext from "../MapContext";

const FullScreenControl = () => {

  const { map } = useContext(MapContext);

  useEffect(() => {
    if (!map) return;
    let fullScreenControl = new FullScreen({});
    map.controls.push(fullScreenControl);
    
    return () => map.controls.remove(fullScreenControl);
  }, [map]);

  return null;
};
export default FullScreenControl;
```