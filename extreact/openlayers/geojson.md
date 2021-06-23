
# แสดงข้อมูลจาก GeoJSON

-โหลดไฟล์ **countries.json** ที่อยู่ในโฟลเดอร์ data ของแบบฝึกหัด open layers ไปวางไว้ในโฟลเดอร์ src ขอโปรเจค

```js

import React, { useState } from 'react'
import { Panel } from '@sencha/ext-react-modern';

import { fromLonLat, toLonLat } from 'ol/proj';
import GeoJSON from "ol/format/GeoJSON";
import "ol/ol.css";
import { RMap, ROSM, RControl, MapBrowserEvent, RLayerVector } from 'rlayers';

// ดึงข้อมูล GeoJSON มาใช้งาน
import geojsonFeatures from "../../data/countries.json";

export default function MapView() {

    const firstLocation = fromLonLat([0, 0]);


    return (
        <Panel padding='10'>
            <RMap
                className="example-map"
                noDefaultControls={true}
                width={"100%"} height={"80vh"}
                initial={{ center: firstLocation, zoom: 2 }}>
                <ROSM />

                {/* โหลดข้อมูล GeoJSON มาแสดงเป็น Vector Layer */}
                <RLayerVector
                    zIndex={10}
                    features={new GeoJSON({
                        featureProjection: "EPSG:3857",
                    }).readFeatures(geojsonFeatures)}>

                </RLayerVector>
            </RMap>
        </Panel>
    )
}

```