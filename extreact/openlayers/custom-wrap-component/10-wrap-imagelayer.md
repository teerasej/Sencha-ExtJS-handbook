
# สร้าง image layer สำหรับแสดงภาพ

```js
// src/views/map/layers/ImageLayer.js

import { useContext, useEffect } from "react";
import MapContext from "../MapContext";
import OLImageLayer from "ol/layer/Image";

const ImageLayer = ({ source, zIndex = 0 }) => {

  const { map } = useContext(MapContext); 

  useEffect(() => {
    if (!map) return;
    
    let imageLayer = new OLImageLayer({
      source,
      zIndex,
    });

    map.addLayer(imageLayer);

    imageLayer.setZIndex(zIndex);

    return () => {
      if (map) {
        map.removeLayer(imageLayer);
      }
    };
  }, [map]);

  return null;
};
export default ImageLayer;
```