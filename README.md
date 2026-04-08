Thai Image Captioning - Super AI Engineer SS6
โปรเจกต์นี้เป็นการสร้างระบบบรรยายภาพเป็นภาษาไทย (Image Captioning) สำหรับการแข่งขัน Super AI Engineer Season 6 โดยใช้โมเดล BLIP ร่วมกับเทคนิคการแปลภาษาและการปรับสำนวน (Refinement) เพื่อให้สอดคล้องกับโครงสร้างประโยคในภาษาไทยตามฐานข้อมูล COCO และ IPU

📊 Performance
Best Score: 39.73059

Public Score: 39.06728

Baseline Status: ✅ Passed (Approaching 40.0)

🛠 Tech Stack
Model: Salesforce/blip-image-captioning-base

Translation: deep-translator (Google Translator API)

Framework: PyTorch, Transformers

Environment: Google Colab / Kaggle (GPU Accelerated)

💡 Key Strategies (Optimization)
เพื่อให้ได้คะแนน Sacrebleu สูงสุด เราได้ใช้เทคนิคดังนี้:

In-Context Refinement: ไม่เพียงแค่แปลตรงตัว แต่มีการทำ Post-processing โดยอิงจากสถิติคำศัพท์ใน train.json และ val.json

Vocab Mapping: ปรับเปลี่ยนคำศัพท์จากภาษาทางการ (AI-generated) เป็นภาษาธรรมชาติที่ใช้ใน Dataset เช่น:

สุนัข ⮕ หมา

จักรยานยนต์ ⮕ มอเตอร์ไซค์

รับประทาน ⮕ กิน

Structure Cleaning: ตัดคำเกริ่นนำที่ฟุ่มเฟือยออก เช่น "รูปภาพของ", "ภาพระยะใกล้ของ" เพื่อให้ประโยคกระชับตรงกับเฉลยมากที่สุด

Stable Translation Pipeline: ออกแบบฟังก์ชัน final_clean_translate แบบวนลูปทีละบรรทัดเพื่อป้องกันปัญหา API Timeout และรักษาโครงสร้างประโยคให้สมบูรณ์

📂 Project Structure
notebook.ipynb: โค้ดหลักสำหรับการทำ Inference และ Translation

submission_final_val_style.csv: ไฟล์ผลลัพธ์ล่าสุดที่ใช้ส่งคะแนน

capgen_v1.0_val.json: ไฟล์อ้างอิงสำหรับการปรับแต่งสำนวน (Validation Set)

📝 How to Use
โหลดไฟล์ภาพจาก Competition Dataset ไปไว้ที่ Path ที่กำหนด

รันโมเดล BLIP เพื่อสร้าง Caption ภาษาอังกฤษ (English Base)

ใช้ฟังก์ชัน final_clean_translate ในการแปลงเป็นภาษาไทยพร้อมปรับสำนวนอัตโนมัติ

ตรวจสอบ image_id ให้เป็น Format 5 หลัก (zfill(5)) ก่อนทำการ Submit
