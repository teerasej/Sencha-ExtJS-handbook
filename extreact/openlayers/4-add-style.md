
#  ใส่ style ของ open layer

ปกติ open layer จะมี stylesheet เริ่มต้นมาให้เราเพื่อเลือกใช้งาน

```js
import React from 'react'
import { Panel } from '@sencha/ext-react-modern';

import { fromLonLat } from 'ol/proj';
import { RMap, ROSM } from 'rlayers';

// import Openlayer CSS
import "ol/ol.css";

export default function MapView() {


    const center = fromLonLat([100.5103341,13.7078748]);

    return (
        <Panel padding='10'>
            <RMap
                {/* ใส่ class name */}
                className="example-map" 
                width={"100%"} height={"80vh"} initial={{ center: center, zoom: 11 }}>
                <ROSM />
            </RMap>
        </Panel>
    )
}

```