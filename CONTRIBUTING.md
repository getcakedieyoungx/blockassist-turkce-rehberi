# 🤝 Katkıda Bulunma Rehberi

BlockAssist Türkçe rehberine katkıda bulunmak için bu rehberi takip et.

---

## Katkı Türleri

### 📝 Dokümantasyon İyileştirmeleri

- Yazım hataları düzelt
- Açıklamaları netleştir
- Örnekler ekle
- Çeviri iyileştir

### 🐛 Hata Raporları

- Kurulum hatası
- Çalıştırma sorunu
- Yanlış talimat
- Çevirme hatası

### ✨ Yeni İçerik

- Yeni rehberler
- Video bağlantıları
- İpuçları ve püf noktaları
- Platform-spesifik rehberler

---

## Nasıl Katkıda Bulunur?

### 1. Repository'i Fork Et

```bash
# GitHub'da Fork butonuna tıkla
```

### 2. Klonla

```bash
git clone https://github.com/SENIN_KULLANICI_ADI/blockassist-turkce-rehberi.git
cd blockassist-turkce-rehberi
```

### 3. Branch Oluştur

```bash
git checkout -b ozellik/aciklama
# Örn: git checkout -b docs/wsl-kurulum
```

### 4. Değişiklikleri Yap

- Dosyaları düzenle
- Testler geçtiğinden emin ol
- Markdown formatını kontrol et

### 5. Commit Et

```bash
git add .
git commit -m "Açıklama: değişiklik türü"
# Örn: "docs: WSL kurulum rehberi eklendi"
```

### 6. Push Et

```bash
git push origin ozellik/aciklama
```

### 7. Pull Request Aç

- GitHub'da Pull Request sekmesine git
- "New Pull Request" tıkla
- Değişiklikleri açıkla
- Submit et

---

## Stil Rehberi

### Türkçe Yazım

- ✅ Doğru Türkçe kullan
- ✅ Teknik terimleri İngilizcede tut (Python, Java, vb)
- ✅ Özel adları büyük harfle yaz (BlockAssist, HuggingFace, vb)

### Markdown Formatı

```markdown
# Başlık 1
## Başlık 2
### Başlık 3

- Madde 1
- Madde 2

1. Sıra 1
2. Sıra 2

**Kalın** ve *İtalik*

`kod`

\`\`\`bash
kod bloğu
\`\`\`
```

### Kod Örnekleri

```markdown
# Doğru
\`\`\`bash
git clone https://...
\`\`\`

# Yanlış
git clone https://...
```

---

## Commit Mesajı Formatı

```
<tür>: <açıklama>

<detaylı açıklama (isteğe bağlı)>
```

### Tür

- `docs`: Dokümantasyon
- `fix`: Hata düzeltme
- `add`: Yeni içerik
- `update`: Güncelleme
- `remove`: Silme

### Örnekler

```
docs: WSL kurulum rehberi eklendi
fix: Python version hatasını düzelt
add: Leaderboard açıklaması
update: Java kurulum talimatları
remove: Eski macOS rehberi
```

---

## Kılavuzlar

### Dosya Yapısı

```
blockassist-turkce-rehberi/
├── README.md (Ana rehber)
├── QUICKSTART.md (Hızlı başlangıç)
├── SORUN-GIDERME.md (Sorun giderme)
├── CONTRIBUTING.md (Bu dosya)
├── LICENSE (MIT)
└── docs/ (İsteğe bağlı, ek rehberler)
    ├── WSL-kurulum.md
    ├── Linux-kurulum.md
    └── macOS-kurulum.md
```

### Yeni Rehber Eklerken

1. `docs/` klasörü içinde dosya oluştur
2. README.md içinde referans ekle
3. Detaylı ve açık yazı
4. Kod örnekleri ekle
5. Bağlantıları kontrol et

---

## Hata Raporlama

### Issue Template

```markdown
## Açıklama
[Sorunu açıkla]

## Adımlar
1. [Adım 1]
2. [Adım 2]
3. [Adım 3]

## Beklenen Sonuç
[Ne olması gerektiğini yaz]

## Gerçek Sonuç
[Ne olduğunu yaz]

## Sistem Bilgisi
- OS: [Windows/Linux/macOS]
- Sürüm: [Örn: Ubuntu 22.04]
- Python: [3.10, 3.11, vb]
```

---

## Gözden Geçirme Süreci

1. PR'nı gönder
2. Bakı alanı tarafından incelenir
3. Değişiklikler istenebilir
4. Onaylanınca merge edilir
5. Teşekkürler! 🎉

---

## Davranış Kuralları

- ✅ Saygılı ve profesyonel ol
- ✅ Yapıcı geri bildirim ver
- ✅ Diğerleri dinle
- ❌ Ayrımcılık yapma
- ❌ Spam yapma
- ❌ Yasa dışı içerik

---

## Sorular?

- 💬 [Discord](https://discord.com/invite/gensyn)
- 📧 Bu repo'da Issue aç
- 🎬 [YouTube](https://www.youtube.com/watch?v=Ab2tEsuJX2w)

---

**Katkılara açığız! Teşekkürler! 🙏**

*Son Güncelleme: 17 Kasım 2025*
