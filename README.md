PCB-Defected-Detected

💡 Drive İndirme Linki : https://drive.google.com/drive/folders/15SdTuzhOsE5LtvSSjJcqdYyCiyC7-AM6?usp=drive_link


🔍 Proje Amacı
Bu proje, PCB (Printed Circuit Board - Baskılı Devre Kartı) üzerindeki lehim hatalarını tespit etmek amacıyla geliştirilmiştir. YOLOv8 mimarisi kullanılarak, görsel veriler üzerinde hızlı ve doğru hata analizi yapılması hedeflenmiştir. Proje, üretim hatalarının otomatik tespiti sayesinde kalite kontrol süreçlerini kolaylaştırmayı amaçlamaktadır.

🧠 Kullanılan Teknolojiler
Python 
Görüntü işleme (preprocessing)
Derin öğrenme ile nesne tespiti (YOLOv8)
PyQt5 (arayüz desteği)


📁 Klasör Yapısı

PCB-defected-detected/
├── data/
│   ├── images/          # Alternatif görsel klasörü
│   └── labels/          # Alternatif label klasörü
│
├── dataset/
│   ├── images/          # YOLO eğitim/test görselleri
│   ├── labels/          # YOLO formatında anotasyonlar
│   └── data.yaml        # YOLO eğitim konfigürasyonu
│
├── runs/detect/         # YOLO çıktıları
│   ├── predict/         # Tahmin görselleri
│   ├── train/           # Eğitim 1
│   ├── train2/          # Eğitim 2
│   ├── train3/...       # Devam eden eğitim klasörleri
│
├── bolum.py             # Görsel bölme işlemleri (belirli bölge analizi)
├── data.py              # Dataset yönetimi veya yardımcı fonksiyonlar
├── ui1.py               # Arayüz 1 (PyQt5)
├── ui3.py               # Arayüz 3 (alternatif UI tasarımı)
│
├── yolov11n.pt          # YOLOv8 model dosyası (v11 custom ağırlıklar)
├── yolov8n.pt           # Orijinal YOLOv8n model ağırlıkları
🖼️ Veri Seti
📂 Görüntü ve etiket dosyaları bu klasörde yer almakta

Görseller: dataset/images/
Etiketler: dataset/labels/ (YOLO formatı)
Konfigürasyon: dataset/data.yaml

⚙️ Kullanım Adımları
1️⃣ Gerekli Paketleri Yükle

2️⃣ YOLOv8 eğitimini başlat:
yolo task=detect mode=train model=yolov8n.pt data=dataset/data.yaml epochs=50 imgsz=640

3️⃣ Eğitilen modeli kullanarak test yap:
yolo task=detect mode=predict model=runs/detect/train/weights/best.pt source=dataset/images/

4️⃣ Arayüzü başlatmak için:
python ui3.py

5️⃣ Görüntü üzerinde bölme işlemi yapmak için:
python bolum.py


📈 Model Performansı
Eğitim çıktıları runs/detect/trainX/ klasörlerinde saklanır.

Her eğitimde oluşan results.png, confusion_matrix.png, F1_curve.png gibi dosyalar sayesinde modelin başarısı görsel olarak incelenebilir.

🛠️ Notlar
yolov11n.pt, senin eğittiğin özel YOLOv8 modeli olabilir. Onu model= parametresinde kullanabilirsin.

.yaml dosyasındaki train, val, nc, names gibi alanların doğru olduğundan emin ol.
.labels klasöründeki dosyalar YOLO formatına (class x_center y_center width height) uygun olmalı.


👤 Katkıda Bulun
Pull request gönderebilir veya issue açarak destek olabilirsin. Proje açık kaynak olup, katkıya açıktır 🛠️
