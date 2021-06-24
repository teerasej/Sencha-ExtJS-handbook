
# เรียกใช้งาน component ทั้งหมด

```jsx


import React, { useEffect, useRef, useState } from 'react'
import { Panel } from '@sencha/ext-react-modern';

import { OSM } from 'ol/source';
import { fromLonLat } from 'ol/proj';

import Map from './Map';
import Layers from './layers/Layers';
import TileLayer from './layers/TileLayer';
import Controls from './controls/Controls';
import FullScreenControl from './controls/FullScreenControl';

export default function MapView() {


    const [center, setCenter] = useState([100, 13]);
    const [zoom, setZoom] = useState(6);


    return (
        <Panel layout='fit'>
            {/* กำหนดพิกัด และระดับการ zoom */}
            <Map center={fromLonLat(center)} zoom={zoom}>
                 {/* ใช้ tile layer กับ open street map */}
                <Layers>
                    <TileLayer source={new OSM()} zIndex={0} />
                </Layers>
                 {/*  ใส่ full screen control */}
                <Controls>
                    <FullScreenControl />
                </Controls>
            </Map>
        </Panel>
    )
}

```