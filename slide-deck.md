---
marp: true
paginate: true
backgroundColor: #111827
theme: gaia
html: true
color: #f3f4f6
center: true

---

<!-- _class: lead -->

<style>
  h1 {
    font-size: 56px;
  }
  ul + ul {
    margin-top: 0;
  }
  ul:has(+ ul) {
    margin-bottom: 0;
  }

  .box-rounded {
    text-align:center;
    p {
      display: inline-block;
      font-size: 36px;
      margin-bottom: 28px;
      margin-top: 12px;
      background: #1e598b;
      padding: 0 21px;
      box-shadow: #646464 8px 7px 0px 0px;
    }
    &.demo {
      color:white; 
      margin-top: 128px;
      p {
        background-color: #517e16
      } 
    }
  }
  
  .box-content {
    text-align:center
  }
  .wrapper {
    display:flex;
    height:100%;
    h2 {
      width:666px;
      margin-bottom:64px;
      text-align:left;
    }
    h4 {
      text-align:left;
    }
    .left {
      flex:1;
    }
    .qr {
      width:70%;
    }
    .right {
      flex-basis: 40%;
      display: flex;
      flex-direction: column;
      align-items: end;
      p {
        margin-top:0;
      }
      a {
        display:block;
        text-align:center
      }
      img {
        margin-top:36px;
        width:100%;
        margin-left:12px;
      }
      
    }
  }
  .icon-box {
  text-align:center;
  img {
    width: 72px;
    height: auto;
  }
}
.smaller-bullet-font {
  font-size: 34px; 
}
.table-small-font {
  font-size: 28px;
}

</style>

<div class="wrapper">
  <div class="left">
    <h2>Frontend'de Build Araçları ve Geliştirme Ortamı</h2>
    <h4> Konuşmacı: Tuncay Kaplan</h4>
  </div>
  <div class="right">
    <div class="qr">
      <img src="./slide-images/ss-linkedin-qr.jpg"/>
      <a href="https://linkedin.com/in/trkaplan">Linkedin</a>
    </div>
  </div>
</div>

<!-- 
Konuşmacı Notları:

Hoşgeldiniz, sorularınız olursa lütfen söyleyin. Ufak demolar da olacak.
Takdim
Frontend deneyimleriniz ne durumda?
// proje kurdum, konfigüre ettim, mevcut projede geliştirme yaptım, aktif olarak frontend yazmıyorum vs.

30-40 dakika sunum + Soru-Cevap

-->
---


<div class="wrapper">
  <div class="left">
    <h2>Ben Kimim - Deneyimler</h2>

- Telekom sektörü
* Kamu (Gelir İdaresi, İç İşleri Bakanlığı)
* Banka (Finans Bank / eFinans)
* Özel üniversite
* Blokzincir tabanlı DAO (Merkeziyetsiz Otonom Organizasyon) Projesi

  </div>
  <div class="right">
    <div class="qr">
      <img src="./slide-images/ss-linkedin-qr.jpg"/>
      <a href="https://linkedin.com/in/trkaplan">Linkedin</a>
    </div>
  </div>
</div>

<!-- 
Konuşmacı Notları:
- Arayüz geliştirme, frontend alt yapı kurulumu, yükseltmeleri, performans optimizasyonu
- AI dönüşümü ve otomasyon olanakları güncel ilgi alanım.
- Innova'da kurumsal projeler, TT Bireysel Müşteri Self Servis Portalı React migrasyonu ve UI yenileme projesi ve SARP
- Build süresi optimizasyonu ve bundle boyutu küçültme konularında çalıştım
- Öncesinde ePlatform'da e-Defter Beyan Sistemi için frontend geliştirme yaptım
- CityDAO'da geliştirme ekibini koordine ettim ve frontend geliştirme yaptım
- Rollerskating, buz pateni, kitesurfing, windsurfing, yüzme gibi hobilerle ilgileniyorum
.
-->
---

# 🎯 Sunumun Amacı

- Modern frontend build sürecinin aşamalarını ve otomasyonunu göstermek
- Monorepo ve mikrofrontend mimarilerinin avantajlarını ve farklarını açıklamak
- Vite, Turborepo, Module Federation, pnpm gibi güncel araçların pratikteki katkılarını ve karşılaştırmalarını sunmak
- Canlı demolar ve örneklerle, geliştirme sürecini nasıl optimize edebileceğimizi göstermek

---

# Frontend dünyasında "build" kavramı

Projenin kaynak kodlarının, çalıştırılabilir ve dağıtılabilir hale getirilmesi için yapılan tüm işlemler bütünüdür.

---

# Frontend dünyasında "build" kavramı

Modern build araçları, sadece çıktı üretmekle kalmaz; geliştirme sürecinde de canlı önizleme ve hızlı güncelleme (HMR), otomatik test, linting, formatlama gibi otomasyonlarla geliştirici deneyimini artırır.

---

# Frontend Build Sürecinde Neler Olur?
<style scoped>
  p {
    font-size:56px;
    margin-left: 132px;
    margin-top: 92px;
  }
  img {
    width: 1.5em;
    margin-left: -54px;
    height: auto;
  }
  img:nth-child(odd) {
    position: relative;
    top: 194px;
  }
</style>
🔁  📦  ✂️  🖼️  ⚙️  ⚡  🤖

---

# Frontend Build Sürecinde Neler Olur?

<div class="icon-box">

🔁 

</div>
<div class="box-rounded">

Kodun Dönüştürülmesi

</div>
<div class="box-content">TypeScript, JSX, SCSS </br>
          ↓</br>
    HTML, JS, CSS
</div>


<!-- 
Notlar:
- Transpile: TypeScript, JSX, SCSS gibi modern dillerin, tarayıcılar tarafından desteklenmeyen kodlarının, çalıştırılabilir hale getirilmesi için derlenmesi.
-->


---

# Frontend Build Sürecinde Neler Olur?

<div class="icon-box">

🔁 

</div>
<div class="box-rounded">

Kodun Dönüştürülmesi (CSS)

</div>

<div class="smaller-bullet-font">

- SCSS/SASS/LESS gibi ön işlemcilerin derlenmesi
* PostCSS ile otomatik vendor prefix eklenmesi (autoprefixer)
* Minifikasyon
* CSS modülleri ile scope'lama
* CSS-in-JS çözümleri*
* Critical CSS extraction (önemli stillerin ayrı çıkarılması)

</div>
<!-- 
Notlar:
- CSS Build Süreci: SCSS/SASS/LESS gibi ön işlemcilerin derlenmesi, PostCSS ile otomatik vendor prefix eklenmesi (autoprefixer), 
-  !!!! CSS-in-JS çözümleri (stillerin component içinde tanımlanması, class'ların otomatik ve benzersiz şekilde üretilmesi),
-  critical CSS extraction (önemli stillerin ayrı çıkarılması) gibi işlemler de bu aşamada yapılır.
-->

---


# Frontend Build Sürecinde Neler Olur?

<div class="icon-box">

📦

</div>
<div class="box-rounded">

Modül Birleştirme ve Ayırma </br> (Bundling & Code Splitting)

</div>
<div class="box-content">Bağımlılıkların ve modüllerin, birleştirilmesi ya da ayrılması.
</div>


<!-- 
Notlar:
- Bundling; ise sayfa, route veya bileşen bazında ayrı dosyalara bölünerek (code splitting) uygulamanın daha hızlı ve verimli yüklenmesinin sağlanması.
-->

---

# Frontend Build Sürecinde Neler Olur?

<div class="icon-box">

✂️

</div>
<div class="box-rounded">

Minifikasyon ve Optimizasyon:

</div>
<div class="box-content">Gereksiz boşluklar, açıklamalar, console.log'lar vs silinmesi
</div>


<!-- 
Notlar:
- Minifikasyon: Gereksiz boşluklar, açıklamalar, console.log'lar vs silinmesi
-->

---

# Frontend Build Sürecinde Neler Olur?

<div class="icon-box">

🖼️

</div>
<div class="box-rounded">

Asset Yönetimi

</div>
<div class="box-content">Görsellerin, fontlar vs gibi statik dosyaların optimize edilmesi klasörlere taşınması
</div>

---

# Frontend Build Sürecinde Neler Olur?

<div class="icon-box">

⚙️

</div>
<div class="box-rounded">

Ortam Konfigürasyonu

</div>
<div class="box-content">Farklı ortamlar için (development, staging, production) Konfigürasyon
</div>


---

# Frontend Build Sürecinde Neler Olur?

<div class="icon-box">

⚡

</div>
<div class="box-rounded">

Performans İyileştirmeleri

</div>
<div class="box-content">Code splitting, lazy loading, cache busting, bundle analizi gibi tekniklerle uygulamanın daha hızlı yüklenmesinin sağlanması
</div>

---

# Frontend Build Sürecinde Neler Olur?

<div class="icon-box">

🤖

</div>
<div class="box-rounded">

Test ve Otomasyon

</div>
<div class="box-content">Lint, test ve diğer kalite kontrollerinin build sürecine entegre edilmesi.
</div>

---
<style scoped>
  h1 {
    font-size: 56px;
  }
</style>
# 🏗️ Uygulama Framework'leri ile Hazır Konfigürasyon

- ### Next.js (React)
  - **Özellikler**: Server-side rendering, static generation, API routes
  - **Build Araçları**: Webpack + Turbopack (Beta)
* ### Nuxt.js (Vue) 
* ### SvelteKit (Svelte)
<!-- 
Notlar:
## 🏗️ Modern Uygulama Framework'leri
- Explain what meta-frameworks are (frameworks built on top of frameworks)
- Mention that Next.js is production-ready out of the box
- Share personal experience or example project
- Show the audience the bundle size comparison
- Ask if anyone has used Next.js before
- Time allocation: 5 minutes for this section

Alternatifler: 
### Nuxt.js (Vue)
- **Özellikler**: Universal app framework, auto-routing
- **Build Araçları**: Vite (default), Webpack desteği
- **Avantajlar**: Modüler mimari, strong TypeScript support

### SvelteKit (Svelte)
- **Özellikler**: Full-stack framework, file-based routing
- **Build Araçları**: Vite native entegrasyon
- **Avantajlar**: Minimal bundle size, excellent performance
-->

--- 

# Modern Build Araçları - ⚡ Vite

- Yeni nesil frontend build ve geliştirme aracı
* "Vite" Fransızca'da "hızlı" demek; odağı hız ve verimlilik
* Vue, React, Svelte gibi frameworklerle uyumlu

<!-- 
Konuşmacı Notları:
- Vite, Evan You (Vue.js'in yaratıcısı) tarafından geliştirildi.
- Klasik bundler'larda (Webpack, Parcel) dev server başlatmak ve dosya güncellemelerini görmek büyük projelerde yavaşlar.
- Vite, modern tarayıcıların native ES Modules (ESM) desteğini kullanarak, sadece ihtiyaç duyulan modülleri anında işler ve sunar.
- "Vite" kelimesi Fransızca'da "hızlı" anlamına gelir; projenin ana felsefesi de geliştirici deneyimini hızlandırmak ve sadeleştirmektir.
- Büyük projelerde bile cold start ve HMR çok hızlıdır.
- Vite, ekosistemdeki eski araçların yavaşlığına ve karmaşıklığına çözüm olarak doğdu.
- Kaynak: https://vite.dev/guide/why.html
-->

--- 

#  ⚡ Vite Ne Yapar?

- **Development (Geliştirme) Ortamı:**
  * Bundling yok, modüller ESM olarak ayrı ayrı ve anında tarayıcıya sunulur
  * Proje büyüklüğünden bağımsız, dev server anında başlar
  * Değişiklikler, uygulama büyüklüğünden bağımsız ve sabit hızda yansır (native ESM mimarisi sayesinde)
  * Bağımlılıklar (node_modules) bir kez pre-bundle edilir, tekrar tekrar işlenmez
<!-- 
Konuşmacı Notları:
- Vite, development ortamında klasik bundler'lardan farklı olarak modülleri ESM ile ayrı ayrı ve anında tarayıcıya sunar; bu sayede dev server başlatma ve değişikliklerin yansıması her zaman sabit hızda ve çok hızlıdır.
- Bağımlılıklar (node_modules) ilk başlatmada esbuild (GO İLE YAZILMIŞ ile pre-bundle edilir ve cache'lenir, tekrar tekrar işlenmez.
- Proje büyüklüğünden bağımsız olarak, geliştirme deneyimi her zaman akıcı ve hızlıdır.

-->

---

#  ⚡ Vite Ne Yapar?

- **Production Build:**
  - Arkaplanda Rollup'ı kullanır
  * Modülleri ve bağımlılıkları optimize şekilde bundle eder
  * Tree-shaking, code splitting, minification, common chunks gibi optimizasyonlar uygular

<!-- 
Konuşmacı Notları:
- Production build'de ise Rollup kullanılır; tüm kod ve bağımlılıklar optimize şekilde bundle edilir, tree-shaking ve code splitting gibi modern optimizasyonlar uygulanır.
- Vite'nin plugin ekosistemi Rollup ile uyumludur, bu sayede genişletilebilir ve framework agnostic bir yapı sunar.
- Kaynak: https://vite.dev/guide/why.html
-->

---

# ⚡ Vite Demo
<a href="https://stackblitz.com/edit/vitejs-vite-4cwredss?file=README.md" target="_blank">

<div class="box-rounded demo">

Demo 

</div>

</a>

<br/>
<br/>
<br/>

📂  <a href="https://stackblitz.com/edit/vitejs-vite-4cwredss?file=README.md" target="_blank">Demo:  Vite + React (Stackblitz)</a>

---


## 🔧 Micro-Frontend Mimarisi

- Büyük frontend uygulamalarının, bağımsız olarak geliştirilebilen ve deploy edilebilen küçük parçalara (micro-frontend'lere) bölünmesi yaklaşımıdır.
* Farklı ekipler, modülleri farklı teknolojilerle geliştirebilir.
* Shell / container kavramı
* Zorluklar: Ortak tasarım, entegrasyon, paylaşılan bağımlılıkların yönetimi.

<!-- 
Konuşmacı Notları:
- Büyük frontend uygulamalarının, bağımsız olarak geliştirilebilen ve deploy edilebilen küçük parçalara (micro-frontend'lere) bölünmesi yaklaşımıdır.
* Farklı ekipler, modülleri farklı teknolojilerle geliştirebilir.
* Ortak bir shell veya container uygulama içinde bu parçalar birleştirilir.
* Avantajları: Bağımsız geliştirme, ölçeklenebilirlik, teknoloji çeşitliliği, hızlı teslimat.
* Zorluklar: Ortak tasarım, entegrasyon, paylaşılan bağımlılıkların yönetimi.
-->

---

## 🔧 Micro-Frontend Mimarisi

### Webpack Module Federation Nedir?
<div class="smaller-bullet-font">

- Farklı uygulamaların veya micro-frontend'lerin, birbirlerinin modüllerini runtime'da (çalışma anında) dinamik olarak yükleyip kullanabilmesini sağlayan Webpack özelliğidir.
* Her micro-frontend bağımsız olarak build edilir ve deploy edilir.
*  Ortak bir shell/container uygulama, diğer micro-frontend'leri uzaktan (remote) yükleyebilir.
* Kod paylaşımı, bağımsız geliştirme ve incremental upgrade (kademeli güncelleme) imkanı sunar.
* Büyük ölçekli projelerde bağımsız ekiplerin iş akışını hızlandırır.
</div>

---
#### Webpack Module Federation


<a href="https://github.com/trkaplan/module-federation-demo-react-ssr-16-17-18" target="_blank">
<div class="box-rounded demo"> 
 
 Demo
</div>
 </a>



<br/>
<br/>
<br/>

📂 <a href="https://github.com/trkaplan/module-federation-demo-react-ssr-16-17-18" target="_blank"> Demo Repo Linki: React SSR with React 16, 17, 18</a>

📂 <a href="https://github.com/module-federation/module-federation-examples" target="_blank">Module Federation Örnekleri GitHub Reposu</a>

---

# Monorepo ve Mikrofrontend: Modern Alternatifler

- Monorepo araçları: Turborepo, Nx, Lerna
* Mikrofrontend araçları: Module Federation (Webpack/Nx/Turborepo ile), Single SPA, Bit
* <b>Not:</b> Sunuma dahil olmayan <b>Single SPA</b> ve <b>Bit</b> gibi alternatifleri de incelemenizde fayda olabilir.

<!-- 
Not: Nx ve Turborepo, monorepo içinde mikrofrontend mimarisi kurmak için altyapı ve otomasyon sağlar. Asıl entegrasyon için Module Federation veya Single SPA gibi çözümler kullanılır.
-->

---

# Monorepo vs Mikrofrontend Mimarisi

<div class="table-small-font">

| Özellik | Turborepo (Monorepo) | Module Federation (Mikrofrontend) |
|---------|----------------------|-----------------------------------|
| Kod Paylaşımı | Derleme zamanında (build-time) | Çalışma zamanında (runtime) |
| Bağımsız Deployment | Kısıtlı (paket bağımlılıkları nedeniyle) | Tam bağımsız |
| React Sürümleri | Genellikle tek sürüm | Farklı sürümler bir arada çalışabilir |
| Entegrasyon Seviyesi | Kod seviyesinde | Uygulama seviyesinde |
| Ekip Özerkliği | Orta seviye | Yüksek seviye |

</div>

---

# Ne Zaman Turborepo, Ne Zaman Module Federation?

- Turborepo: Tek repo, merkezi yönetim, hızlı build, ekip içi kod paylaşımı
* Module Federation: Bağımsız deploy, farklı teknoloji stack'leri, runtime entegrasyon

* **⚠️ Uyarı: Turborepo runtime remote import sağlamaz!**

<!-- 
Not:
Turborepo, farklı teknolojideki uygulamaları aynı repoda yönetebilir; ancak bir uygulamanın başka bir uygulamayı runtime'da (çalışma anında) remote olarak import etmesini doğrudan sağlamaz. Farklı framework'ler arası dinamik modül paylaşımı için Module Federation veya Single SPA gibi mikrofrontend çözümleri gerekir.
-->

---

# Turborepo'nun Avantajları

- Akıllı önbellek ve inkremental build
- Workspace'ler arası otomatik bağımlılık takibi
- Remote caching ile CI/CD hızlandırma

---

# Demo Turborepo
<a href="https://github.com/trkaplan/turborepo-nextjs-shared-ui-demo" target="_blank">

<div class="box-rounded demo">

Demo 

</div>

</a>

<br/>
<br/>
<br/>

📂  <a href="https://github.com/trkaplan/turborepo-nextjs-shared-ui-demo" target="_blank">Demo: Turborepo Monorepo </a><br/> (Next.js + Ortak UI Kütüphanesi)

---

# 📦 pnpm: Hızlı ve Disk Dostu Paket Yöneticisi

- Bağımlılıkları çok daha hızlı kurar (npm ve yarn'a göre 2-3 kat hızlı)
* Diskte çok daha az yer kaplar (tekil depolama, symlink ile paylaşım)
* Monorepo projelerde bağımlılık izolasyonu sağlar
* "Dependency hell" ve gizli bağımlılık sorunlarını azaltır
* Büyük projelerde CI/CD sürelerini kısaltır

---

# Geliştirme Sürecini Optimize Etmek İçin Neler Yapılabilir? (Monorepo ve Build/CI Özelinde)

- Monorepo ile birden fazla uygulama ve ortak paket yönetimi
* Turborepo/Nx ile hızlı ve cache'li build süreçleri
* pnpm ile hızlı bağımlılık kurulumu
* Ortak UI kütüphanesiyle kod paylaşımı
* CI/CD'de sadece değişen paketleri/testleri çalıştır, cache ve paralel task kullan

---

# Geliştirme Sürecini Optimize Etmek İçin Neler Yapılabilir?

- Kod formatı ve kalite standartlarını otomatize et (lint, format)
* Merge conflict ve gereksiz tekrarları önle
* Standart commit mesajları uygula
* Bundle boyutunu ve bağımlılıkları kontrol et
* Görselleri ve assetleri optimize et
* Circular dependency'leri tespit et
* Bundle analizi ve optimizasyon

<!-- 
Konuşmacı Notları:
- pnpm, klasik node_modules yerine symlink tabanlı bir yapı kurar.
- Özellikle çok sayıda proje ve bağımlılık içeren ortamlarda ciddi disk ve hız avantajı sağlar.
- Monorepo ve mikro frontend projelerinde pnpm ile workflow daha stabil ve hızlı olur.
- Farklı paket yöneticileriyle karışık kullanımda dikkatli olunmalı; install ve run işlemleri aynı araçla yapılmalı.
- Kaynak: https://pnpm.io/motivation
-->

---

# Sonuç

### Modern Araçların Avantajları
- **Hız**: Dramatik performans iyileştirmeleri
* **DX**: Geliştirilmiş geliştirici deneyimi  
* **Maintainability**: Daha kolay bakım ve güncelleme

---

# Sonuç

### Seçim Kriterleri
- Proje büyüklüğü ve karmaşıklığı
* Takımın hakim olduğu teknolojiler ve deneyimi
* Performans beklentisi
* Uzun vadeli bakım gereksinimleri

---

# 💬 Sorular & Cevaplar

- Frontend build araçları hakkında sorularınız
- Projeye özel zorluklar
- Uygulama detayları
- En iyi uygulamalar

--- 

### 📬 İletişim

🐙 [github.com/trkaplan](https://github.com/trkaplan)  
✖️ [x.com/trkaplan](https://x.com/trkaplan)  
💼 [linkedin.com/in/trkaplan](https://www.linkedin.com/in/trkaplan)

--- 
### Kaynaklar

- [Module Federation React SSR Örnekleri](https://github.com/module-federation/module-federation-examples/tree/master/react-16-17-18-ssr)
- [Turborepo Resmi Dokümantasyon](https://turbo.build/repo/docs)
- [Turborepo + Next.js + Ortak UI Demo](https://github.com/trkaplan/turborepo-nextjs-shared-ui-demo)
- [Vite Resmi Dokümantasyon](https://vitejs.dev/)
- [Single SPA Resmi Dokümantasyon](https://single-spa.js.org/)
- [Bit (bit.dev) Resmi Sitesi](https://bit.dev/)
- [pnpm Resmi Dokümantasyon](https://pnpm.io/)
