# ⚡ BlockAssist - 5 Dakika Hızlı Başlangıç

**BlockAssist'i en hızlı şekilde başlatmak için bu rehberi takip et!**

---

## 🚀 Adım 1: Deposu Klonla

```bash
git clone https://github.com/gensyn-ai/blockassist.git
cd blockassist
```

---

## 🛠️ Adım 2: Bağımlılıkları Yükle

### macOS
```bash
./setup.sh  # Java'yı yükler
brew install pyenv
pyenv install 3.10
pyenv exec pip install psutil readchar rich
```

### Linux
```bash
./setup.sh  # Java'yı yükler
curl -fsSL https://pyenv.run | bash
source ~/.bashrc
pyenv install 3.10
pip install psutil readchar rich
```

### Windows (WSL2)
[README.md](README.md) dosyasında detaylı kurulumu gör.

---

## 🎮 Adım 3: BlockAssist'i Çalıştır

### macOS
```bash
pyenv exec python run.py
```

### Linux
```bash
python run.py
```

---

## 🔑 Adım 4: HuggingFace Token

**Terminal şu soracak:**
```
HuggingFace token:
```

**Token Alma (2 dakika):**
1. https://huggingface.co/settings/tokens aç
2. "Create New Token" tıkla
3. "Write" seçeneğini işaretle
4. Token'ı kopyala ve yapıştır

---

## 🌐 Adım 5: Gensyn Girişi

Tarayıcı otomatik açılır: `http://localhost:3000`

- Email ile giriş yap VEYA
- Google hesabı kullan

---

## 🎮 Adım 6: Minecraft'ta Oyna

1. Minecraft penceresi açılır
2. **Terminal'de ENTER'a bas**
3. Minecraft penceresine tıkla
4. **Tekrar Terminal'de ENTER'a bas**
5. İnşa görevini tamamla (struct inşa et)
6. **Terminal'de ENTER'a bas (seçim bitmesi için)**

---

## 🤖 Adım 7: Model Eğitimi

**Otomatik başlar - bekleme süresi:**
```
5-15 dakika (sistem specs'e bağlı)
```

**Başarı göstergesi:**
```
✅ Successfully uploaded model to HuggingFace
✅ Transaction confirmed on Gensyn Testnet
```

---

## ✅ Tamamlandı!

Tebrik ederiz! 🎉

**Kazandıklarınız:**
- ✅ 1 Participation Puanı
- ✅ Eğitilmiş Model (HuggingFace'de)
- ✅ Blockchain Kaydı (Gensyn Testnet)

---

## 📊 Sonrasında

### Tekrar Çalıştır
```bash
python run.py  # Aynı komutu çalıştır
```

### İlerlemeyi Takip Et
```
https://dashboard.gensyn.ai/
```

### Leaderboard
```
https://dashboard.gensyn.ai/
```

---

## 🆘 Sorun Mu?

| Sorun | Çözüm |
|-------|-------|
| Java bulunamıyor | `brew install java` (macOS) \| `sudo apt install default-jdk` (Linux) |
| Python sürümü yanlış | `pyenv global 3.10` |
| pyenv bulunamıyor | [README.md](README.md#pyenv-bulunamıyor-linux) |
| Minecraft açılmıyor (WSL) | [README.md](README.md#minecraft-penceresi-açılmıyor-wsl) |

---

**Detaylı rehber için:** [README.md](README.md)

*Son Güncelleme: 17 Kasım 2025*
