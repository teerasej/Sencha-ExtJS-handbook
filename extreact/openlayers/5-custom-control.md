
# 

```js


import React from 'react'
import { Panel } from '@sencha/ext-react-modern';

import { fromLonLat } from 'ol/proj';
import "ol/ol.css";
// import control มาใช้งาน
import { RMap, ROSM, RControl } from 'rlayers';

export default function MapView() {

    const center = fromLonLat([100.5103341, 13.7078748]);

    return (
        <Panel padding='10'>
            <RMap
                {/* ปิด control ปกติ */}
                noDefaultControls={true}
                className="example-map"
                width={"100%"} height={"80vh"} initial={{ center: center, zoom: 11 }}>
                <ROSM />
                 {/* กำหนด control ของแผนที่เอง */}
                <RControl.RScaleLine />
                <RControl.RAttribution />
                <RControl.RZoom />
                <RControl.RZoomSlider />
                <RControl.RFullScreen />
            </RMap>
        </Panel>
    )
}

```