# Frontend Build Tools ve Development Sunumu

Bu proje, modern frontend geliştirme süreçlerinde kullanılan build araçları, monorepo ve mikrofrontend mimarileri, karşılaştırmalar ve workflow optimizasyonları hakkında kapsamlı bir Marp sunumu içerir. Sunumda canlı demolar, araçların avantajları ve geliştirme sürecini hızlandırmaya yönelik pratik ipuçları yer alır.

---

## Sunum Linki

Sunumun güncel haline buradan ulaşabilirsin:  
👉 [https://trkaplan.github.io/frontend-build-araclari-sunum/](https://trkaplan.github.io/frontend-build-araclari-sunum/)

> **Not:** Sunumu konuşmacı notlarıyla birlikte görmek için, sayfanın altındaki **Presenter** butonuna tıklayabilirsin.

--- 

## İçerik

- Sunumun Amacı ve Gündem
- Frontend'de Build Kavramı ve Modern Build Süreci
- Modern Uygulama Framework'leri (Next.js, Vite, vs.)
- Vite ve Demo
- Micro-Frontend Mimarisi ve Webpack Module Federation
- Monorepo ve Mikrofrontend: Modern Alternatifler
- Monorepo vs Mikrofrontend Karşılaştırması
- Turborepo'nun Avantajları ve Demo
- pnpm: Hızlı ve Disk Dostu Paket Yöneticisi
- Geliştirme Sürecini Optimize Etmek İçin Neler Yapılabilir?
    - Monorepo ve Build/CI Optimizasyonu
    - Kod Kalitesi ve Otomasyon
    - Hızlı Local Geliştirme ve CI/CD İpuçları
- Sonuç ve Seçim Kriterleri
- Sorular & Cevaplar
- İletişim
- Kaynaklar   

---

## Gereksinimler

- [Node.js](https://nodejs.org/) (v14+ önerilir)
- [Marp CLI](https://github.com/marp-team/marp-cli) (npx ile otomatik çalışır)

---

## Canlı Önizleme (Watch Mode)

Sunumu VS Code'a yüklenen [Marp VSCode](https://marketplace.visualstudio.com/items?itemName=marp-team.marp-vscode) eklentisi ile önizlemesini bir panelde görebilirsiniz. Yaptığınız değişiklikleri anlık olarak tarayıcıda görmek için aşağıdaki komutu kullanabilirsiniz:

```bash
npx @marp-team/marp-cli@latest -w slide-deck.md --template bespoke --bespoke.progress
```

- `-w` veya `--watch`: Dosyada değişiklik oldukça otomatik olarak sunumu günceller ve tarayıcıda canlı önizleme sağlar.
- `--template bespoke`: Marp'ın interaktif HTML template'ini kullanır.
- `--bespoke.progress`: Slaytların altında ilerleme çubuğu (progress bar) gösterir.

Sunumu düzenlerken bu komutu çalıştırıp, oluşan `slide-deck.html` dosyasını tarayıcıda açık tutarsanız, her kaydettiğinizde değişiklikler otomatik olarak yansır.

---

## Sunumu Dışa Aktarmak

### HTML Olarak

```bash
npx @marp-team/marp-cli@latest slide-deck.md --template bespoke --bespoke.progress -o slide-deck.html
```

### PDF Olarak

```bash
npx @marp-team/marp-cli@latest slide-deck.md --pdf
```

---

## Sunumu Açmak

- İzleme modunda veya HTML çıktısı aldıktan sonra, `slide-deck.html` dosyasını tarayıcıda açabilirsin.
- PDF çıktısı doğrudan paylaşılabilir.

---

## Görseller

- Sunumda kullanılan görseller `slide-images/` klasöründe yer alır.
- Footer'da veya slaytlarda görsel kullanmak için Markdown veya HTML `<img>` etiketi kullanılabilir.

---

## Notlar

- Sunumun içeriğini `slide-deck.md` dosyasından güncelleyebilirsin.
- Marp ile ilgili daha fazla bilgi için: [Marp Documentation](https://marpit.marp.app/)

### MARP Bespoke Teması Hakkında

Bu sunum, Marp'ın Bespoke temasını kullanmaktadır. Bespoke teması aşağıdaki özellikleri sağlar:

- Modern ve şık bir görünüm
- Klavye kısayolları ile kolay navigasyon (sağ/sol ok tuşları, space)
- İlerleme çubuğu (`--bespoke.progress` parametresi ile aktifleştirilir)
- Responsive tasarım - farklı ekran boyutlarında uyumlu görüntüleme
- Otomatik slayt geçişleri ve animasyonlar
- Koyu tema desteği

Bespoke temasını kullanırken, sunumunuzu tarayıcıda görüntülerken F tuşuna basarak tam ekran moduna geçebilirsiniz. Ayrıca P tuşu ile sunum modunu, N tuşu ile notları görüntüleyebilirsiniz.

---

## Katkı ve Lisans

Bu sunum açık kaynaklıdır. Dilediğin gibi kullanabilir, geliştirebilir veya paylaşabilirsin.

## Otomatik Sunum Yayınlama (GitHub Actions + Pages)

Bu repoda, sunumun Markdown kaynağı (`slide-deck.md`) her güncellendiğinde GitHub Actions otomatik olarak Marp CLI ile HTML sunum (`index.html`) üretir ve GitHub Pages üzerinden yayınlar.

### Nasıl Çalışır?
- Her push'ta workflow tetiklenir.
- `slide-deck.md` dosyasından `index.html` otomatik olarak üretilir.
- Üretilen HTML, `gh-pages` branch'ine deploy edilir.
- GitHub Pages ayarlarından `gh-pages` branch ve root klasör seçilidir.

### Sunuma Erişim
Sunumun güncel haline şu adresten ulaşabilirsin:

```
https://<kullanici-adi>.github.io/<repo-adi>/
```

(Adresini kendi kullanıcı ve repo adına göre güncelle!)
