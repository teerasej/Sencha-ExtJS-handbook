
# สร้าง CSS สำหรับใช้งานกับ div map

```css
/* src/views/map/Map.css */

/* กำหนด style ของแผนที่ */
.ol-map {
    min-width: 600px;
    min-height: 500px;
    margin: 50px;
    height: 500px;
    width: "100%";
  }

  /* กำหนด style ของ control */
  .ol-control {
    position: absolute;
    background-color: rgba(255,255,255,0.4);
    border-radius: 4px;
    padding: 2px;
  }

  /* กำหนด style ของ fullscreen control */
  .ol-full-screen {
    top: .5em;
    right: .5em;
  }
```