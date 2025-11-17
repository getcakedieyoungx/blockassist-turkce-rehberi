# 🛠️ BlockAssist - Sorun Giderme Rehberi

BlockAssist kullanırken en yaygın sorunlar ve çözümleri burada bulabilirsiniz.

---

## 📋 İçindekiler

1. [Kurulum Sorunları](#kurulum-sorunları)
2. [Çalıştırma Sorunları](#çalıştırma-sorunları)
3. [Minecraft Sorunları](#minecraft-sorunları)
4. [HuggingFace Sorunları](#huggingface-sorunları)
5. [Model Eğitimi Sorunları](#model-eğitimi-sorunları)
6. [Windows/WSL Sorunları](#windowswsl-sorunları)
7. [Performans Sorunları](#performans-sorunları)

---

## Kurulum Sorunları

### Java Bulunamıyor

**Hata Mesajı:**
```
Java not found
command not found: java
```

**Çözüm:**

**macOS:**
```bash
brew install java
# Kontrol et
java -version
```

**Linux:**
```bash
sudo apt install default-jdk
# Kontrol et
java -version
```

**Windows (WSL):**
```bash
sudo apt update
sudo apt install default-jdk
```

---

### pyenv Bulunamıyor (Linux)

**Hata Mesajı:**
```
command not found: pyenv
```

**Çözüm:**

```bash
# 1. pyenv'i indir
curl -fsSL https://pyenv.run | bash

# 2. ~/.bashrc'ye ekle
echo 'export PYENV_ROOT="$HOME/.pyenv"' >> ~/.bashrc
echo 'export PATH="$PYENV_ROOT/bin:$PATH"' >> ~/.bashrc
echo 'eval "$(pyenv init -)"' >> ~/.bashrc

# 3. Kaydet
source ~/.bashrc

# 4. Kontrol et
pyenv --version
```

---

### Python 3.10 Bulunamıyor

**Hata Mesajı:**
```
Python 3.10 not found
No such file or directory: python3.10
```

**Çözüm:**

```bash
# 1. Bağımlılıkları yükle (Linux)
sudo apt install make build-essential libssl-dev zlib1g-dev libbz2-dev libreadline-dev libsqlite3-dev curl git libncursesw5-dev xz-utils tk-dev libxml2-dev libxmlsec1-dev libffi-dev liblzma-dev

# 2. Python 3.10'u yükle
pyenv install 3.10

# 3. Globally ayarla
pyenv global 3.10

# 4. Kontrol et
python3.10 --version
```

---

## Çalıştırma Sorunları

### Permission Denied

**Hata Mesajı:**
```
Permission denied: './setup.sh'
```

**Çözüm:**

```bash
chmod +x setup.sh
./setup.sh
```

---

### Module Not Found

**Hata Mesajı:**
```
ModuleNotFoundError: No module named 'psutil'
```

**Çözüm:**

```bash
# Bağımlılıkları yükle
pip install psutil readchar rich

# Veya
pip3 install psutil readchar rich
```

---

### Port 3000 Zaten Kullanımda

**Hata Mesajı:**
```
Address already in use: ('127.0.0.1', 3000)
port 3000 already in use
```

**Çözüm:**

**Linux/macOS:**
```bash
# Kullanılan prosesi bul
lsof -i :3000

# PID'yi göreceksin, örn: 12345
# Prosesi kapat
kill -9 12345
```

**Windows PowerShell:**
```powershell
netstat -ano | findstr :3000
# PID göreceksin, örn: 12345
taskkill /PID 12345 /F
```

---

## Minecraft Sorunları

### Minecraft Penceresi Açılmıyor

**Hata Mesajı:**
```
Could not find or load the main class
Minecraft window failed to open
```

**Çözüm - Kurulum Hatası:**

```bash
# Bağımlılıkları kontrol et
pip install -e .

# Windows'ta karşılaştıksan, tekrar çalıştır
python run.py
```

**Çözüm - WSL Sorunları:**

[Windows/WSL Sorunları](#windowswsl-sorunları) bölümüne git.

---

### Minecraft Çöküyor

**Çözüm:**

1. **RAM yeterli mi kontrol et:**
```bash
free -h  # Linux
mem      # macOS (top komutunda)
```

2. **OpenGL Hatası (WSL):**
```bash
export LIBGL_ALWAYS_SOFTWARE=1
export MESA_LOADER_DRIVER_OVERRIDE=llvmpipe
export _JAVA_OPTIONS='-Xms512m -Xmx2g -Dorg.lwjgl.opengl.Display.allowSoftwareOpenGL=true'
```

---

### Keyboard/Mouse Girdisi Alınmıyor

**Çözüm:**

1. Minecraft penceresine tıkla
2. Terminal'de ENTER'a bas
3. Tekrar Minecraft penceresine tıkla
4. Oyna

---

## HuggingFace Sorunları

### Invalid HuggingFace Token

**Hata Mesajı:**
```
Invalid HuggingFace token
Authentication failed
```

**Çözüm:**

1. Token'ın doğru olduğunu kontrol et:
   ```bash
   huggingface-cli login
   ```

2. Token'ın "Write" iznine sahip olduğunu kontrol et:
   - https://huggingface.co/settings/tokens
   - Token'ı seç
   - "Permission" -> "Write" olmalı

3. Yeni token oluştur:
   - https://huggingface.co/settings/tokens
   - "Create New Token"
   - "Write" seçeneğini işaretle
   - Kopyala ve yapıştır

---

### Model HuggingFace'e Yüklenmiyor

**Hata Mesajı:**
```
Failed to upload model to HuggingFace
Connection timeout
```

**Çözüm:**

1. İnternet bağlantısını kontrol et:
   ```bash
   ping huggingface.co
   ```

2. Token'ı kontrol et (yukarıdaki çözümü gör)

3. Disk alanını kontrol et:
   ```bash
   df -h
   ```

4. Log dosyasını kontrol et:
   ```bash
   tail -f logs/blockassist.log
   ```

---

## Model Eğitimi Sorunları

### Eğitim Başlamıyor

**Çözüm:**

1. Log dosyasını kontrol et:
   ```bash
   tail -f logs/blockassist.log
   ```

2. Episode verisi var mı kontrol et:
   ```bash
   ls data/episodes/
   ```

3. RAM ve disk yeterli mi:
   ```bash
   free -h
   df -h
   ```

---

### Eğitim Çok Uzun Sürüyor

**Normal Davranış:** 5-15 dakika

**Çözüm:**

1. GPU hızlandırması var mı kontrol et:
   ```bash
   nvidia-smi
   ```

2. Sistem yükü:
   ```bash
   top  # q'ye basarak çık
   ```

3. Diğer programları kapat

---

### Model Eğitimi Başarısız

**Çözüm:**

1. Disk alanını kontrol et (min 2GB):
   ```bash
   df -h
   ```

2. RAM yeterli mi (min 4GB):
   ```bash
   free -h
   ```

3. Dosya izinleri:
   ```bash
   chmod -R 755 ~/.blockassist
   ```

4. Log hatası:
   ```bash
   tail -100 logs/blockassist.log
   ```

---

## Windows/WSL Sorunları

### VcXsrv Bağlantı Hatası

**Hata Mesajı:**
```
Cannot connect to X11
_XSERVTransmitConnect: Cannot open display
```

**Çözüm:**

1. VcXsrv'in açık olduğunu kontrol et

2. Windows IP'ni bul:
   ```powershell
   ipconfig
   # IPv4 Address'i bul
   ```

3. WSL'de ayarla:
   ```bash
   export DISPLAY=<WINDOWS_IP>:0
   # Örn: export DISPLAY=192.168.1.10:0
   ```

4. Test et:
   ```bash
   xeyes
   # Göz simülasyonu görüntülensin
   ```

---

### VcXsrv Ayarları

VcXsrv'i aç ve şu ayarları kullan:

```
✅ Multi-window
✅ Start no client  
✅ Disable access control
❌ Native OpenGL (işaretlemeyin)
```

---

### WSL'de Python Sürüm Sorunları

**Hata:**
```
Python 3.10 required
```

**Çözüm:**

```bash
# ~/.bashrc'ye ekle
echo 'alias python=python3.10' >> ~/.bashrc
source ~/.bashrc

# Kontrol et
python --version
```

---

## Performans Sorunları

### Düşük FPS (Minecraft)

**Çözüm:**

1. Graphics ayarları düşür
2. Render mesafesi azalt
3. İnternal resolution azalt
4. CPU/GPU sıcaklığını kontrol et

---

### CPU %100 Kullanımı

**Normal mi?** Eğitim sırasında evet

**Çözüm:**

```bash
# İşlemleri kontrol et
top

# Diğer programları kapat
```

---

### Disk Alanı Yetersiz

**Çözüm:**

1. Eski modelleri sil:
   ```bash
   rm -rf ~/.blockassist/models/*.old
   rm -rf data/episodes/*.old
   ```

2. Cache temizle:
   ```bash
   pip cache purge
   ```

3. Geçici dosyaları sil:
   ```bash
   rm -rf /tmp/*
   ```

---

## Debug Modunu Aç

```bash
export DISABLE_TELEMETRY=0
python run.py
```

---

## Log Dosyalarını Kontrol Et

```bash
# Mevcut logları görmek
ls logs/

# Belirli bir logu takip et
tail -f logs/blockassist.log

# Son 100 satırı görmek
tail -100 logs/blockassist.log

# Hata içeren satırları bulmak
grep ERROR logs/blockassist.log
```

---

## Hala Çözülemedi?

1. **Discord Topluluğuna Sor:** https://discord.com/invite/gensyn
2. **GitHub Issues:** https://github.com/gensyn-ai/blockassist/issues
3. **Resmi Docs:** https://docs.gensyn.ai/testnet/blockassist/

---

*Son Güncelleme: 17 Kasım 2025*
