
# สร้าง TileLayer สำหรับใช้งาน

```js
// src/views/map/layers/TileLayer.js

import { useContext, useEffect } from "react";
import MapContext from "../MapContext";
import OLTileLayer from "ol/layer/Tile";

const TileLayer = ({ source, zIndex = 0 }) => {

  // เข้าถึง map object ของ Open Layer จาก Context
  const { map } = useContext(MapContext); 

  // ทำการรันโค้ดหลังจาก component render เรียบร้อยแล้ว

  useEffect(() => {

    // ถ้าไม่ได้กำหนด map object ของ open layer ให้หยุดการทำงานลงตรงนี้
    if (!map) return;
    
    // สร้าง TileLayer instance ของ Open Layer
    let tileLayer = new OLTileLayer({
      source,
      zIndex,
    });

    // เพิ่ม Tile Layer เข้า Map object
    map.addLayer(tileLayer);

    // กำหนดค่า index 
    tileLayer.setZIndex(zIndex);

    return () => {
      if (map) {
        map.removeLayer(tileLayer);
      }
    };
  }, [map]);

  return null;
};
export default TileLayer;
```