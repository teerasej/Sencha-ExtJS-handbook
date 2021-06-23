

## 1. Pull Docker ของ Geoserver

ดาวน์โหลด Docker ตัวอย่างของ Geoserver

```bash
docker pull kartoza/geoserver
```

## 2. 

รันโดยใช้คำสั่ง 

```
docker run -d -p 8600:8080 -e SAMPLE_DATA=true \
-e GEOSERVER_ADMIN_USER=admin \
-e GEOSERVER_ADMIN_PASSWORD=1234 \
--name geoserver kartoza/geoserver 
```

สังเกตว่า คำสั่ง -e SAMPLE_DATA=true จะเป็นการแสดงตัวอย่างข้อมูล ซึ่งปกติจะถูกปิดการทำงานไว้


เสร็จแล้วให้เข้ามาที่ dashboard: http://localhost:8600/geoserver/web/ 

