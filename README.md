# 🎮 BlockAssist - Türkçe Rehberi

**BlockAssist**, Gensyn AI'nin Minecraft'ta oynanan eylemlerinizden öğrenen yapay zeka asistanıdır.

> 💡 **Nedir?** Minecraft'ta inşa ederken, AI asistan sizin hareketlerinizi izleyerek öğrenir ve size yardımcı olmaya başlar.

---

## 📋 İçindekiler

1. [BlockAssist Nedir?](#blockassist-nedir)
2. [Sistem Gereksinimleri](#sistem-gereksinimleri)
3. [Hızlı Başlangıç (5 Dakika)](#hızlı-başlangıç-5-dakika)
4. [Detaylı Kurulum Rehberi](#detaylı-kurulum-rehberi)
5. [BlockAssist Nasıl Çalışır?](#blockassist-nasıl-çalışır)
6. [Model Eğitimi ve Gönderi](#model-eğitimi-ve-gönderi)
7. [Sorun Giderme](#sorun-giderme)
8. [Sıkça Sorulan Sorular](#sıkça-sorulan-sorular)

---

## BlockAssist Nedir?

### Temel Konsept

BlockAssist, basitçe şöyle çalışır:

1. **Siz Minecraft'ta inşa yaparsınız** - oyunun içinde bir görev verilir (mesela bir ev, köprü ya da depo yapmak)
2. **AI izler** - her hareketinizi, blok yerleştirmenizi, araç seçiminizi göz önünde tutar
3. **Model eğitilir** - oyun bittikten sonra, AI sizin stiliyle inşa etmeyi öğrenen bir model eğitilir
4. **Model kaydedilir** - bu model Hugging Face'te saklanır ve Gensyn testnetine kaydedilir

Sonuç olarak, siz Minecraft'ta oynarken ve inşa ederken, eğer bir problemi çözüyorsanız, o problemi çözüş tarzınızı öğrenen bir asistan oluşturmuş olursunuz.

### Neden Önemli?

Bu sistem, "yardım öğrenmesi" (assistance learning) adı verilen yeni bir AI paradigmasının pratik örneğidir. Geleneksel AI sistemleri statik veri setleriyle eğitilirken, BlockAssist doğrudan sizin eylemleri gözlemleyerek öğrenir. Bu da AI'ı daha uyumlu ve insan tercihlerine daha yakın hale getiriyor.

### Özellikler

✅ **Gerçek Verilerden Öğrenme:** Bot komutları değil, gerçek insan davranışı  
✅ **Yerel Model:** Tüm veriler bilgisayarınızda işlenir, kimseyle paylaşılmaz  
✅ **Kendi Modeliniz:** Eğittiğiniz model tamamen sizin mülkiyetinizdir  
✅ **Desentralize Sistem:** Gensyn ağında kaydedilir, merkezi sunucuya bağımlı değildir  
✅ **Şeffaf:** Ne öğrendiği, nasıl eğitildiği hep görünür  

---

## Sistem Gereksinimleri

### Minimum Spesifikasyonlar

| Gereksinim | Minimum | Tavsiye |
|-----------|---------|----------|
| **İşletim Sistemi** | Windows 10/11 (WSL2) veya Ubuntu 22.04+ | Ubuntu 22.04+, macOS 12+ |
| **RAM** | 8 GB | 16 GB |
| **Disk Alanı** | 10 GB | 20 GB |
| **CPU** | Dual-core 2.0 GHz | Quad-core 2.5 GHz+ |
| **GPU** | Yok (isteğe bağlı) | NVIDIA RTX 3090, 4090 |

### Yazılım

- **Python:** 3.10+
- **Java:** 1.8.0_152+
- **Git:** En güncel sürüm
- **pyenv:** Python sürüm yönetimi için (macOS/Linux)

### GPU Desteği (İsteğe Bağlı)

Eğer NVIDIA GPU'nuz varsa, eğitim hızı 3-5 kata çıkar:

```bash
# GPU kullanılıyor mu kontrol et
nvidia-smi
```

---

## Hızlı Başlangıç (5 Dakika)

### 1. Deposu Al

```bash
git clone https://github.com/gensyn-ai/blockassist.git
cd blockassist
```

### 2. Bağımlılıkları Kur

Hangi sistemde olduğunuza göre komutu seçin:

**macOS:**
```bash
./setup.sh
brew install pyenv
pyenv install 3.10
pyenv exec pip install psutil readchar rich
```

**Linux (Ubuntu 22.04+):**
```bash
./setup.sh
curl -fsSL https://pyenv.run | bash
# ~/.bashrc'yi güncelle ve source'la
pyenv install 3.10
pip install psutil readchar rich
```

### 3. Çalıştır

```bash
# macOS
pyenv exec python run.py

# Linux
python run.py
```

### 4. HuggingFace Token

Terminal soracak. Token almak için:
1. https://huggingface.co/settings/tokens sayfasına git
2. "Create New Token" → "Write" seçeneğini işaretle → Oluştur
3. Token'ı terminale yapıştır

### 5. Oyun Başlasın

- Gensyn login sayfası açılır (email veya Google)
- Minecraft penceresi açılır
- Görev verilir, inşa edersin
- Bitince `ENTER` tuşu

### 6. Model Eğitilir

5-15 dakika içinde model otomatik eğitilir ve HuggingFace'e yüklenir. Bitti! ✅

---

## Detaylı Kurulum Rehberi

### Windows (WSL2)

Windows'ta BlockAssist çalıştırmak biraz fazladan çalışma gerektiriyor çünkü GUI uygulaması grafik çıktı bekliyor. WSL2 ve VcXsrv (Windows X Server) kombinasyonu bu problemi çözer.

**Adım 1: WSL2 Kur**

PowerShell'i yönetici olarak aç ve çalıştır:

```powershell
wsl --install
```

Bilgisayarı yeniden başlat.

**Adım 2: Ubuntu 22.04 Seç**

```powershell
wsl --install -d Ubuntu-22.04
wsl -s Ubuntu-22.04
```

**Adım 3: VcXsrv Kur (X Server)**

Windows'ta Minecraft penceresinin görünebilmesi için bir X11 sunucusu gerekir.

1. [VcXsrv'i indir](https://sourceforge.net/projects/vcxsrv/) ve kur
2. VcXsrv'i açarken şu ayarları kullan:
   - ✅ Multi-window
   - ✅ Start no client
   - ✅ Disable access control
   - ❌ Native OpenGL (işaretlemeyin)

**Adım 4: WSL Terminali Aç ve Devam Et**

WSL terminal'de Linux kurulumunu takip et (aşağıda).

**Adım 5: DISPLAY Ayarı**

Her BlockAssist çalıştırışında, WSL'de:

```bash
export DISPLAY=<WINDOWS_IP>:0
# Örnek: export DISPLAY=192.168.1.10:0
```

Windows IP'nizi bulmak için `ipconfig` komutunu PowerShell'de çalıştırın.

---

### Linux (Ubuntu 22.04+)

Linux kurulumu en basit olanıdır.

**Adım 1: Deposu Klonla**

```bash
git clone https://github.com/gensyn-ai/blockassist.git
cd blockassist
```

**Adım 2: Java Kur**

```bash
./setup.sh
```

**Adım 3: System Paketleri**

```bash
sudo apt update && sudo apt upgrade -y

# Temel araçlar
sudo apt install -y build-essential libssl-dev zlib1g-dev \
  libbz2-dev libreadline-dev libsqlite3-dev curl git \
  libncursesw5-dev xz-utils tk-dev libxml2-dev \
  libxmlsec1-dev libffi-dev liblzma-dev
```

**Adım 4: pyenv Kur**

```bash
curl -fsSL https://pyenv.run | bash

# ~/.bashrc'ye ekle
echo 'export PYENV_ROOT="$HOME/.pyenv"' >> ~/.bashrc
echo 'export PATH="$PYENV_ROOT/bin:$PATH"' >> ~/.bashrc
echo 'eval "$(pyenv init -)"' >> ~/.bashrc

source ~/.bashrc
```

**Adım 5: Python 3.10 Kur**

```bash
pyenv install 3.10
pyenv global 3.10
pip install psutil readchar rich
```

---

### macOS

macOS kurulumu en düzgün olanıdır (geriye uyumluluğu en iyi).

**Adım 1: Homebrew (Varsa Atla)**

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

**Adım 2: Deposu Klonla**

```bash
git clone https://github.com/gensyn-ai/blockassist.git
cd blockassist
```

**Adım 3: Java Kur**

```bash
./setup.sh
```

**Adım 4: pyenv Kur**

```bash
brew install pyenv

# ~/.zshrc'ye ekle (macOS Catalina+)
echo 'eval "$(pyenv init -)"' >> ~/.zshrc
source ~/.zshrc
```

**Adım 5: Python 3.10 Kur**

```bash
pyenv install 3.10
pyenv global 3.10
pip install psutil readchar rich
```

---

## BlockAssist Nasıl Çalışır?

### Episode Nedir?

Bir **episode** = Bir oyun oturumu

Siz BlockAssist'i başlattığınızda:
1. Minecraft penceresinde bir görev belirlenir (sırasıyla daha zor görevler)
2. Siz o görevde inşa etmeye başlarsınız
3. Her seçim, hareket, blok yerleştirme, araç değişikliği kaydedilir
4. Görev bittiğinde (ya da istediğiniz zaman) `ENTER` tuşu ile bitirebilirsiniz
5. Kayıtlar model eğitimi için toplanır
6. Model eğitilir (5-15 dakika)
7. Model HuggingFace'e yüklenir
8. Gensyn testnetine kaydedilir

### AI Ne Öğreniyor?

AI, gözlemlediği şeyler:
- **Hareket Desenleri:** Nereden başladığınız, nasıl hareket ettiğiniz
- **Blok Seçimi:** Hangi bloklara tercih ettiniz
- **İnşa Tarzı:** Kare mı, dikdörtgen mi, çapraz mı yapıyorsunuz
- **Problem Çözme:** Engele karşılaştığında nasıl davrandığınız

Bu bilgilerden yola çıkarak, "eğer benzer bir görev verilseydi nasıl davranırdı?" sorusuna cevap veren bir model yaratılıyor.

### Görev Seviyeleri

İlk başladığınızda kolay görevlerle başlarsınız, ilerledikçe biraz daha zorluyorlar:

| Seviye | Örnek | Tahmini Zaman |
|-------|--------|---------------|
| **Kolay** | Basit bir kutu veya platform | 5-10 dakika |
| **Orta** | Biraz daha detaylı yapı | 10-20 dakika |
| **Zor** | Kompleks görevler | 20+ dakika |

**İpucu:** Başlangıçta zorluk seviyeleriyle deneme yapın. Bazen kolay görevlerde bile iyi eğitim verilerir.

---

## Model Eğitimi ve Gönderi

### Tam Süreç

```
Episode Başlat
    ↓
Minecraft'ta Inşa Et (kendi tarzında)
    ↓
Ctrl + C (veya "ENTER" tuşu)
    ↓
Model Eğitimi Başlar (5-15 dakika)
    ↓
HuggingFace'e Yüklenir
    ↓
Gensyn Testnet'e Kaydedilir
    ↓
Blockchain Doğrulandı ✓
```

### Eğitim Sırasında

Eğitim süreci tamamen otomatiktir. Yapmanız gereken:

1. Bilgisayarı uyku moduna almamak
2. İnternet bağlantısını kapalı tutmamak (model yüklenirken)
3. Birkaç dakika beklemek

Günlükleri takip etmek isterseniz:

```bash
tail -f logs/blockassist.log
```

### Başarı Göstergesi

Eğitim başarılı ise, log dosyasında şunu göreceksiniz:

```
Successfully uploaded model to HuggingFace:
h-grieve/blockassist-bc-bellowing_pouncing_horse_1753675374
```

Ardından blockchain işlemi kaydedilir:

```
Transaction confirmed on Gensyn Testnet
```

### Modelinizi Bulma

HuggingFace profilinizde tüm modellerinizi görebilirsiniz:

```
https://huggingface.co/PROFILINIZ/models
```

Her biri bir episode'ı temsil eder. Modeller şuna benzer isimlere sahip olur:

```
blockassist-bc-bellowing_pouncing_horse_1753675374
blockassist-bc-agile_dancing_llama_1753675401
```

---

## Sorun Giderme

### Java Hatası

**Hata:**
```
Java not found
command not found: java
```

**Çözüm:**

macOS:
```bash
brew install java
java -version
```

Linux:
```bash
sudo apt install default-jdk
java -version
```

---

### Python Sürümü

**Hata:**
```
Python 3.10 required
```

**Çözüm:**

```bash
pyenv global 3.10
python --version
```

---

### Minecraft Penceresini Açılamıyor (WSL)

**Çözüm:**

1. VcXsrv'in açık olduğundan emin ol
2. DISPLAY'i doğru şekilde ayarla:
   ```bash
   export DISPLAY=<WINDOWS_IP>:0
   ```
3. Test et:
   ```bash
   xeyes
   ```

---

### HuggingFace Token Hatası

**Hata:**
```
Invalid HuggingFace token
```

**Çözüm:**

1. https://huggingface.co/settings/tokens sayfasına git
2. Token'ın "Write" iznine sahip olduğundan emin ol
3. Yeni bir token oluştur
4. Terminale yapıştır

---

### Model Eğitimi Başlamıyor

**Kontrol Listesi:**

1. Disk alanı yeterli mi? (min 2 GB)
   ```bash
   df -h
   ```

2. RAM yeterli mi? (min 4 GB)
   ```bash
   free -h
   ```

3. Log hatası ne?
   ```bash
   tail -100 logs/blockassist.log
   ```

---

## Sıkça Sorulan Sorular

**S: Minecraft satın almam gerekiyor mu?**

C: Hayır, BlockAssist zaten dahili bir Minecraft versiyonuyla geliyor. Kendi Minecraft'ınızı satın almış olsanız bile, BlockAssist kendi kopya'sını kullanır.

---

**S: Tek Episode'da ne kadar zaman geçer?**

C: Genellikle 30-40 dakika. İnşa 10-20 dakika, eğitim 5-15 dakika, yükleme 2-5 dakika.

---

**S: Modeller nereye kaydediliyor?**

C: HuggingFace'te (bulutta) ve Gensyn Testnet'te (blockchain). İkisi de güvenle saklanır.

---

**S: Bilgisayarı kapatabilir miyim?**

C: Episode bitene kadar hayır. Ama eğitim bittiğinde sorun yok.

---

**S: Hangi GPU önerilir?**

C: NVIDIA kartları önerilir (RTX 3090, 4090, A100). CPU ile de çalışır ama yavaş.

---

**S: Başka biri modeli görebilir mi?**

C: HuggingFace linkini paylaşmadığınız sürece hayır. Özel kalır.

---

## Kaynaklar

- 📖 [Resmi Gensyn Dokumentasyonu](https://docs.gensyn.ai/testnet/blockassist/)
- 🎮 [BlockAssist GitHub Deposu](https://github.com/gensyn-ai/blockassist)
- 💬 [Gensyn Discord Topluluğu](https://discord.com/invite/gensyn)
- 🔗 [HuggingFace Token Ayarları](https://huggingface.co/settings/tokens)
- 📊 [Leaderboard](https://dashboard.gensyn.ai/)

---

## İletişim ve Yardım

Sorun çıkarsa veya soru sor:

- **Discord:** Gensyn resmi topluluğu (hızlı cevap)
- **GitHub Issues:** https://github.com/gensyn-ai/blockassist/issues
- **Bu Rehber:** Bu sayfada sorun giderme bölümü

---

**BlockAssist ile eğlenceleri çıkar! 🎮✨**

*Son güncelleme: 17 Kasım 2025*