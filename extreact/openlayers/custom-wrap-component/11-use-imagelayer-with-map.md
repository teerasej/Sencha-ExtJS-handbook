
# นำมาใช้งานกับ ImageWMS

```js
// src/views/map/MapView.js


import React, { useEffect, useRef, useState } from 'react'
import { Panel } from '@sencha/ext-react-modern';

import GeoJSON from "ol/format/GeoJSON";
import Map from './Map';
import { fromLonLat } from 'ol/proj';
import Layers from './layers/Layers';
import TileLayer from './layers/TileLayer';
import { ImageWMS, OSM } from 'ol/source';
import Controls from './controls/Controls';
import FullScreenControl from './controls/FullScreenControl';
import ImageLayer from './layers/ImageLayer';

export default function MapView() {


    const [center, setCenter] = useState([100, 13]);
    const [zoom, setZoom] = useState(6);


    return (
        <Panel layout='fit'>
            <Map center={fromLonLat(center)} zoom={zoom}>
                <Layers>
                    <TileLayer source={new OSM()} zIndex={0} />
                    
                    {/* กำหนดใช้ image layer โดยดึงมาจาก WMS */}
                    <ImageLayer
                        source={new ImageWMS({
                            url: "https://floodtiles.gistda.or.th/geoserver/FloodOnline/wms?",
                            params: {
                                LAYERS: "FloodOnline:RepeatFloodRaster",
                            },
                        })}
                        zIndex={10} />
                </Layers>
                <Controls>
                    <FullScreenControl />
                </Controls>
            </Map>
        </Panel>
    )
}

```