# Model-as-a-Service with Flask & Docker

โปรเจกต์นี้เป็นตัวอย่างการสร้าง **Model-as-a-Service** โดยใช้ **Flask** เป็น backend และทำให้รันง่ายด้วย **Docker**

---

## สิ่งที่มีในโปรเจกต์
- `app.py` : Flask API สำหรับเรียกใช้งานโมเดล
- `model/` : โฟลเดอร์เก็บโมเดลที่เทรนไว้
- `Dockerfile` : ไฟล์สำหรับ build Docker image
- `requirements.txt` : ไลบรารี Python ที่ต้องใช้

---

## วิธีใช้งาน

### 1. Clone โปรเจกต์
```bash
git clone https://github.com/Mindcha58/Model-as-a-Service_Flask-Docker.git
cd Model-as-a-Service_Flask-Docker
```

### 2. Build Docker image
```bash
docker build -t model-service .
```

### 3. รัน Docker container
```bash
docker run -p 5000:5000 model-service
```

หลังจากรันแล้ว Flask API จะเปิดที่ `http://localhost:5000`

---

## การใช้งาน API
คุณสามารถใช้ Postman หรือ curl ส่ง request ไปที่ API เพื่อเรียกใช้งานโมเดล ตัวอย่างเช่น:

```bash
curl -X POST http://localhost:5000/predict \
     -H "Content-Type: application/json" \
     -d '{"input": [ค่าอินพุตของโมเดล]}'
```

API จะส่งผลลัพธ์การทำนายกลับมาเป็น JSON

---

## หมายเหตุ
- ก่อนรัน Docker ต้องติดตั้ง Docker ในเครื่อง
- โมเดลที่ใช้ต้องอยู่ในโฟลเดอร์ `model/` เพื่อให้ Flask โหลดได้
- เหมาะสำหรับการทดลองหรือทำโปรเจกต์เล็ก ๆ

