# 🎮 BlockAssist - Türkçe Rehberi

**BlockAssist**, Gensyn AI'nin Minecraft'ta oynanan eylemlerinizden öğrenen yapay zeka asistanıdır.

> 💡 **Nedir?** Minecraft'ta inşa ederken, AI asistan sizin hareketlerinizi izleyerek öğrenir.

---

## 📋 İçindekiler

1. [BlockAssist Nedir?](#blockassist-nedir)
2. [Sistem Gereksinimleri](#sistem-gereksinimleri)
3. [Hızlı Başlangıç (5 Dakika)](#hızlı-başlangıç-5-dakika)
4. [Detaylı Kurulum Rehberi](#detaylı-kurulum-rehberi)
5. [BlockAssist Nasıl Çalışır?](#blockassist-nasıl-çalışır)
6. [Model Eğitimi ve Gönderimi](#model-eğitimi-ve-gönderimi)
7. [Leaderboard ve Para Kazanma](#leaderboard-ve-para-kazanma)
8. [Sorun Giderme](#sorun-giderme)

---

## BlockAssist Nedir?

### Kısaca Açıklaması

```
┌──────────────────────────────────────────┐
│                                          │
│  1. Minecraft'ta inşa yaparsınız         │
│     ↓                                    │
│  2. AI asistan sizin hareketleri izler  │
│     ↓                                    │
│  3. Model eğitilir (5-15 dakika)       │
│     ↓                                    │
│  4. Model HuggingFace'e yüklenir        │
│     ↓                                    │
│  5. Gensyn Testnet'e kaydedilir         │
│     ↓                                    │
│  6. Participation kazanırsınız!         │
│                                          │
└──────────────────────────────────────────┘
```

### Özellikleri

✅ **Assistance Learning:** AI doğrudan insan eylemlerinden öğrenir  
✅ **Yerel Çalışma:** Tüm veriler bilgisayarınızda kalır  
✅ **Model Sahibi:** Eğittiğiniz model tamamen sizin  
✅ **Desentralize:** Gensyn Testnet'e kayıt edilir  
✅ **Para Kazanma:** Gelecekte reward programı açılacak  

---

## Sistem Gereksinimleri

### Minimum Gereksinimler

| İşletim Sistemi | Sürüm |
|-----------------|-------|
| Windows | 10/11 (WSL2) |
| Linux | Ubuntu 22.04+ |
| macOS | 12+ |

### Yazılım

- **Python:** 3.10+
- **Java:** 1.8.0_152+
- **Git:** En güncel sürüm
- **pyenv:** Python sürüm yönetimi

### Donanım

- **CPU:** Dual-core 2.0 GHz+
- **RAM:** 8GB (16GB önerilir)
- **Disk:** 10GB boş alan
- **GPU:** İsteğe bağlı (NVIDIA hızlandırması için)

---

## Hızlı Başlangıç (5 Dakika)

### 1. Deposu Klonla

```bash
git clone https://github.com/gensyn-ai/blockassist.git
cd blockassist
```

### 2. Bağımlılıkları Yükle

**macOS:**
```bash
./setup.sh  # Java'yı yükler
brew install pyenv
pyenv install 3.10
pyenv exec pip install psutil readchar rich
```

**Linux:**
```bash
./setup.sh  # Java'yı yükler
curl -fsSL https://pyenv.run | bash
# ~/.bashrc'yi güncelle: export PATH="$HOME/.pyenv/bin:$PATH"
pyenv install 3.10
pip install psutil readchar rich
```

### 3. BlockAssist'i Çalıştır

```bash
# macOS
pyenv exec python run.py

# Linux
python run.py
```

### 4. HuggingFace Token Gir

Terminal şu soracak:
```
HuggingFace token: (yapıştır)
```

**Token Alma:**
1. https://huggingface.co/settings/tokens aç
2. "Create New Token" → "Write" seçeneğini işaretle
3. Token'ı kopyala ve yapıştır

### 5. Gensyn'e Giriş Yap

Tarayıcı açılır: `http://localhost:3000`
- Email veya Google hesabı ile giriş yap

### 6. Minecraft'ta Oyna

- Minecraft penceresi açılır
- İnşa görevini tamamla (struktur inşa et)
- Terminal'de `ENTER`'a bas

### 7. Model Eğitilsin

```
Eğitim süresi: 5-15 dakika
Model otomatik olarak HuggingFace'e yüklenir
Gensyn'e kaydedilir
```

**Yapıldı! ✅**

---

## Detaylı Kurulum Rehberi

### Windows (WSL2)

**Adım 1: WSL2 Kur**
```powershell
wsl --install
```

**Adım 2: Ubuntu 22.04 Kur**
```powershell
wsl --install -d Ubuntu-22.04
wsl -s Ubuntu-22.04
```

**Adım 3: WSL'de Devam Et**
```bash
sudo apt update && sudo apt upgrade -y
sudo apt install -y python3.10 git curl build-essential
```

**Adım 4: VcXsrv (X Server) Kur**
- Windows'ta indir: [VcXsrv](https://sourceforge.net/projects/vcxsrv/)
- Yükle: Multi-window + "Disable access control" seçeneklerini işaretle
- DISPLAY'i ayarla: `export DISPLAY=<WINDOWS_IP>:0` (komut: `ipconfig`)

**Adım 5: BlockAssist Kurulumu**
Linux kurulumunu takip et (aşağıda)

### Linux (Ubuntu 22.04+)

**Adım 1: Deposu Klonla**
```bash
git clone https://github.com/gensyn-ai/blockassist.git
cd blockassist
```

**Adım 2: Java Yükle**
```bash
./setup.sh
```

**Adım 3: pyenv Kur**
```bash
curl -fsSL https://pyenv.run | bash
export PYENV_ROOT="$HOME/.pyenv"
export PATH="$PYENV_ROOT/bin:$PATH"
eval "$(pyenv init -)"
source ~/.bashrc
```

**Adım 4: Python 3.10 Kur**
```bash
sudo apt install -y make build-essential libssl-dev zlib1g-dev libbz2-dev libreadline-dev libsqlite3-dev curl git libncursesw5-dev xz-utils tk-dev libxml2-dev libxmlsec1-dev libffi-dev liblzma-dev

pyenv install 3.10
pyenv global 3.10
```

**Adım 5: Bağımlılıkları Yükle**
```bash
pip install psutil readchar rich
```

### macOS

**Adım 1: Homebrew Kur** (eğer yoksa)
```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

**Adım 2: Deposu Klonla**
```bash
git clone https://github.com/gensyn-ai/blockassist.git
cd blockassist
```

**Adım 3: Java Yükle**
```bash
./setup.sh
```

**Adım 4: pyenv Kur**
```bash
brew install pyenv
echo 'eval "$(pyenv init -)"' >> ~/.zshrc
source ~/.zshrc
```

**Adım 5: Python 3.10 Kur**
```bash
pyenv install 3.10
pyenv global 3.10
```

**Adım 6: Bağımlılıkları Yükle**
```bash
pip install psutil readchar rich
```

---

## BlockAssist Nasıl Çalışır?

### Episode Nedir?

Bir **episode** = Bir Minecraft oturumu

```
1. BlockAssist başlatılır
2. Minecraft penceresi açılır
3. Size bir görev verilir (struktur inşa et)
4. Siz inşa edersiniz, AI izler
5. ENTER'a basarak oturum bitirirsiniz
6. Model eğitilir
7. Model HuggingFace'e yüklenir
8. Participation kazanırsınız
```

### AI Ne Öğreniyor?

AI sizin:
- Blok yerleştirme konumlarını
- Hareket hareketlerini
- Araç seçimlerini
- Hedef oluşturmayı

**gözlemleyerek** öğrenir.

### Görev Türleri

| Görev | Açıklama | Zaman |
|-------|----------|-------|
| Kolay | Basit yapılar | 5-10 dk |
| Orta | Biraz karmaşık | 10-20 dk |
| Zor | Kompleks yapılar | 20+ dk |

**İpucu:** Başlangıç için "Kolay"dan başlayın.

---

## Model Eğitimi ve Gönderimi

### Eğitim Süreci

```
┌─────────────────────────────────┐
│ 1. Episode Bitir (Ctrl + C)     │
│    Süresi: Anında               │
└──────────────┬──────────────────┘
               ↓
┌─────────────────────────────────┐
│ 2. Model Eğitilir              │
│    Süresi: 5-15 dakika          │
│    CPU/GPU kullanılır           │
└──────────────┬──────────────────┘
               ↓
┌─────────────────────────────────┐
│ 3. HuggingFace'e Yüklenir      │
│    Süresi: 2-5 dakika           │
│    İnternet hızına bağlı        │
└──────────────┬──────────────────┘
               ↓
┌─────────────────────────────────┐
│ 4. Gensyn'e Kaydedilir         │
│    Blockchain işlemi            │
│    Participation +1             │
└─────────────────────────────────┘
```

### Günlükleri Kontrol Et

```bash
# Tüm log dosyalarını görmek için
ls logs

# Belirli bir logu takip etmek için
tail -f logs/blockassist.log
```

### Başarı Göstergesi

**Başarılı oldu:**
```
Successfully uploaded model to HuggingFace:
h-grieve/blockassist-bc-bellowing_pouncing_horse_1753675374
```

**Blockchain'de Kaydedildi:**
```
Transaction confirmed on Gensyn Testnet
```

---

## Leaderboard ve Para Kazanma

### Leaderboard'u Görüntüle

```
https://dashboard.gensyn.ai/
```

Burada görebilirsiniz:
- ✅ Toplam Participation
- ✅ Sıralama
- ✅ Diğer oyuncular
- ✅ İstatistikler

### Participation Nedir?

**1 Episode = 1 Participation Puanı**

```
100 P = ~$1-5 (tahmini)
1000 P = ~$10-50 (tahmini)
```

**Tahminen:**
```
1 saat = 3-5 episode
30 saat = 100-150 episode
30 saat = 100-150 P = $100-750 (2026'da)
```

### Para Kazanma (2026)

**Mevcut Durum:**
- ❌ Şu anda para kazanma aktif değil
- ✅ Participation biriktirilmektedir
- ✅ 2026'da reward programı açılacak
- ✅ Erken katılımcılar avantajlı

---

## Sorun Giderme

### Java Bulunamıyor

```bash
# macOS
brew install java

# Linux
sudo apt install default-jdk

# Kontrol et
java -version
```

### Python Sürümü Yanlış

```bash
python3.10 --version

# Eğer 3.10 yüklü değilse:
pyenv install 3.10
pyenv global 3.10
```

### pyenv Bulunamıyor (Linux)

```bash
curl -fsSL https://pyenv.run | bash

# Şunları ~/.bashrc'ye ekle:
export PYENV_ROOT="$HOME/.pyenv"
export PATH="$PYENV_ROOT/bin:$PATH"
eval "$(pyenv init -)"

# Kaydet
source ~/.bashrc
```

### Minecraft Penceresi Açılmıyor (WSL)

**Çözüm: VcXsrv'i Kontrol Et**

1. VcXsrv'in açık olduğundan emin ol
2. Windows IP'ni bul: `ipconfig` (IPv4 Address)
3. WSL'de ayarla: `export DISPLAY=<IP>:0`
4. Test et: `xeyes` (göz simülasyonu görüntülensin)

### HuggingFace Token Hatası

```bash
# Token doğru mu kontrol et
huggingface-cli login

# Yeni token oluştur
# https://huggingface.co/settings/tokens
```

### Port Çakışması

```bash
# Linux/macOS: Port 3000 kullanımda
lsof -i :3000

# Prosesi kapat
kill -9 <PID>

# Windows
netstat -ano | findstr :3000
taskkill /PID <PID> /F
```

### Model Eğitimi Başarısız

```bash
# Disk alanını kontrol et
df -h

# RAM'ı kontrol et
free -h

# Log dosyasını kontrol et
tail -f logs/blockassist.log
```

---

## İpuçları ve Best Practices

✅ **Yapınız:**
- Farklı görev türleri deneyin
- Tutarlı olun (günde 1-2 episode)
- Log dosyalarını takip edin
- Leaderboard'u kontrol edin
- Topluluğa katılın

❌ **Yapmayınız:**
- Bot kullanmayın (otomatikleştirme)
- Token'ı paylaşmayın
- Spam episode göndermeyin
- Bilgisayarı uyku moduna almayın

---

## Kaynaklar

- 📖 [Resmi Dokumentasyon](https://docs.gensyn.ai/testnet/blockassist/)
- 🎬 [YouTube Rehberi](https://www.youtube.com/watch?v=Ab2tEsuJX2w)
- 💬 [Discord Topluluğu](https://discord.com/invite/gensyn)
- 🎮 [BlockAssist GitHub](https://github.com/gensyn-ai/blockassist)
- 📊 [Leaderboard](https://dashboard.gensyn.ai/)
- 🔗 [HuggingFace Tokens](https://huggingface.co/settings/tokens)

---

## Sık Sorulan Sorular

**S: Minecraft'ı satın almam gerekiyor mu?**
C: Hayır! BlockAssist kendi Minecraft ortamını içerir.

**S: Kaç Participation kazanabilirim?**
C: Günde 3-5 episode = 3-5 P. Ayda 100-150 P.

**S: Model nereye kaydediliyor?**
C: HuggingFace profilinizde saklanır (örn: h-grieve/blockassist-bc-...)

**S: Bilgisayarı kapatabilir miyim?**
C: Eğitim bitene kadar, ağır hesaplama olduğu için kapatmayın.

**S: Hangi GPU önerilir?**
C: NVIDIA RTX 3090, 4090, A100 ideal. CPU ile de çalışır (biraz yavaş).

---

## Lisans

MIT License - Özgürce kullanabilirsiniz.

---

**Hazır mısınız? Başlayın:** `git clone https://github.com/gensyn-ai/blockassist.git`

*Son Güncelleme: 17 Kasım 2025*
