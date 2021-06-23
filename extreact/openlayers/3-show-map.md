

# แสดงแผนที่ 

```js
// src/views/map/MapView.js

import React from 'react'
import { Panel } from '@sencha/ext-react-modern';

// import function และ component
import { fromLonLat } from 'ol/proj';
import { RMap, ROSM } from 'rlayers';

export default function MapView() {

    // สร้างตำแหน่งอ้างอิงจากพิกัดละติจูด ลองจิจูด
    const center = fromLonLat([0,0]);

    return (
        <Panel padding='10'>
            {/* กำหนดขนาดแผนที่ พิกัดเริ่มต้น และ zoom level */}
            <RMap width={"100%"} height={"80vh"} initial={{ center: center, zoom: 2 }}>
                {/* ใช้ open street map เป็น background */}
                <ROSM />
            </RMap>
        </Panel>
    )
}

```

## 2. เปลี่ยนพิกัดเริ่มต้น

ทดสอบกำหนดศูนย์กลางเป็นกรุงเทพ

```js
const center = fromLonLat([100.5103341,13.7078748]);

<RMap width={"100%"} height={"80vh"} initial={{ center: center, zoom: 11 }}>
```