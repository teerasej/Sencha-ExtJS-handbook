
# แสดงพิกัดจากการคลิกบนแผนที่

```js


import React, { useState } from 'react'
import { Panel } from '@sencha/ext-react-modern';

import { fromLonLat,toLonLat } from 'ol/proj';
import "ol/ol.css";
import { RMap, ROSM, RControl, MapBrowserEvent } from 'rlayers';

export default function MapView() {

    const firstLocation = fromLonLat([100.5103341, 13.7078748]);

    // กำหนด state
    const [location, setLocation] = useState(firstLocation)

    // สร้าง function
    const onMapClick = (e:MapBrowserEvent) => {
        const coords = e.map.getCoordinateFromPixel(e.pixel);

        // แปลงค่าพิกัดออกมาเป็น ลองจิจูด ละติจูด
        const lonlat = toLonLat(coords);
        setLocation(lonlat)
    }

    return (
        <Panel padding='10'>
            {/* แสดงค่าที่ได้จากการคลิกแผนที่ */}
            <div>
                <p>click position (lat,lng): {location[1]}, {location[0]}</p>
            </div>
            <RMap
                noDefaultControls={true}
                className="example-map"

                 {/* จับการคลิก event */}
                onClick={onMapClick}
                width={"100%"} height={"80vh"} 
                initial={{ center: firstLocation, zoom: 11 }}>
                <ROSM />
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