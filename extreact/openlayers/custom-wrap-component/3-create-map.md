
# สร้าง map component สำหรับแสดงแผนที่และ control ทั้งหมด

```js
// src/views/map/Map.js

import React, { useRef, useState, useEffect } from "react"
import "./Map.css";
import MapContext from "./MapContext";
import * as ol from "ol";

const Map = ({ children, zoom, center }) => {
    
    const mapRef = useRef();

    // สร้าง state สำหรับเก็บข้อมูลแผนที่
    const [map, setMap] = useState(null);

    // ทำการสร้าง instance map ของ open layer
    useEffect(() => {

        // กำหนด View option
        let options = {
            view: new ol.View({ zoom, center }),
            layers: [],
            controls: [],
            overlays: []
        };

        // สร้าง map instance ของ openlayer
        let mapObject = new ol.Map(options);

        // กำหนดตำแหน่งอ้างอิงของ div สำหรับการวาดแผนที่ให้ map ของ open layer
        mapObject.setTarget(mapRef.current);

        // เก็บค่า map ไว้ใน state
        setMap(mapObject);
        return () => mapObject.setTarget(undefined);
    }, []);

    // รองรับการเปลี่ยนค่า zoom
    useEffect(() => {
        if (!map) return;
        map.getView().setZoom(zoom);
    }, [zoom]);

    // รองรับการเปลี่ยนค่า location
    useEffect(() => {
        if (!map) return;
        map.getView().setCenter(center)
    }, [center])

    // ใช้ MacContext ผูกเข้ากับ map ของ open layer
    // div เป็นส่วนที่ใช้วาดแผนที่ของ openlayer
    return (
        <MapContext.Provider value={{ map }}>
            <div ref={mapRef} className="ol-map">
                {children}
            </div>
        </MapContext.Provider>
    )
}
export default Map;
```