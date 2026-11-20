# GitHub Portfolio — Public Repository Showcase Modernization

## 1. Amaç

GitHub hesabım `hakdogan1` üzerinde bulunan public repository'leri uluslararası QA Automation Engineer / SDET iş başvurularında kullanılabilecek profesyonel bir proje vitrini haline getir.

GitHub profilini ziyaret eden bir kişi ilk 30 saniyede şunları anlayabilmeli:

- Hangi projeleri geliştirdiğimi
- Projelerin ne işe yaradığını
- Hangi teknolojileri kullandığımı
- Hangi mühendislik problemlerini çözdüğümü
- Test otomasyonu ve QA çalışmalarımı
- CI/CD, deployment ve kalite güvence yaklaşımımı
- Çalışan uygulamaları nereden inceleyebileceğini

Public repository'ler birer **engineering case study** niteliğinde olmalı.

Private uygulama kaynak kodlarını public yapma.

## 2. Repository kapsamı

GitHub hesabı: `hakdogan1`

| Mevcut repository | Önerilen isim |
|---|---|
| `qa-practice-platform` | `qa-testing-platform-showcase` |
| `portfolio-engineering` | `qa-portfolio-engineering` |
| `hakdogan1` | Aynı kalacak |

Önerilen isimleri GitHub üzerinde kontrol et. İsimlerin uygunluğunu, açıklayıcılığını ve mevcut bağlantılara etkisini değerlendir.

**Henüz repository isimlerini değiştirme.** Önce değerlendirme ve etki analizi hazırla.

## 3. QA Practice README

Repository: `hakdogan1/qa-practice-platform`

Canlı uygulama: https://qapractice.hakdogan.com/

Mevcut README oldukça kapsamlıdır. Teknik içeriği kaybetmeden daha profesyonel, görsel destekli ve kolay anlaşılır hale getir.

README dili İngilizce olacak.

### Korunacak teknik içerikler

- Next.js 15, React 19, TypeScript, Tailwind CSS v4
- 27 UI modülü ve 10 form senaryosu
- 24 çok adımlı test senaryosu
- 15 kasıtlı hata içeren Bug Playground
- 20 locator dersi
- 50 locator challenge
- 12 iframe / Shadow DOM senaryosu
- API Testing Lab ve simüle REST servisleri
- Fault Injection / QA Test Mode
- Playwright + TypeScript
- Selenium + Java
- Framework blueprint
- Mimari kararlar
- Test stratejisi
- Teknik sorunlar ve çözümler
- Kişisel katkılarım

Bu sayıları mevcut kaynaklarla yeniden doğrula. Farklılık varsa raporla.

### Test sonuçları konusunda doğruluk

Mevcut dokümantasyonda 21 Node tabanlı doğrulama script'i bulunuyor.

Bunları gerçek Playwright E2E testleri olarak gösterme.

Script Practice uygulamasındaki simülasyonu gerçek Playwright veya Selenium driver çalıştırması olarak tanıtma.

Çalıştırılmamış testlere PASS yazma.

Planlanan otomasyon framework'ünü tamamlanmış gibi gösterme.

## 4. QA Practice ekran görüntüleri

Gerçek production sitesinden aşağıdaki ekran görüntülerini al:

1. Ana sayfa — desktop
2. UI Elements
3. Bug Playground
4. Locator Practice Hub
5. Automation Framework
6. Ana sayfa — mobile

Önerilen viewport değerleri:

- Desktop: 1440×900
- Mobile: 390×844

Görselleri WebP formatına optimize et.

Dosya konumu:

`docs/screenshots/`

Örnek dosyalar:

- `homepage-desktop.webp`
- `ui-elements.webp`
- `bug-playground.webp`
- `locator-challenges.webp`
- `framework.webp`
- `homepage-mobile.webp`

Ekran görüntülerinin gerçekten ilgili sayfalara ait olduğunu kontrol et.

Görselde kişisel bilgi, oturum verisi, erişim anahtarı veya hassas içerik bulunmamalı.

README'ye açıklayıcı alt metinlerle ekle.

Görselleri sadece en alta toplama; ilgili özellik bölümlerine yerleştir.

Ana sayfa görüntüsü README'nin ilk ekranında bulunmalı.

## 5. Portfolio Engineering README

Repository: `hakdogan1/portfolio-engineering`

Canlı site: https://www.hakdogan.com/

Bu repository benim QA Engineering portföy web sitemin teknik case study dokümantasyonunu içeriyor.

Mevcut README'yi incele ve geliştirilmiş İngilizce sürümünü hazırla.

Özellikle şu alanları koru ve vurgula:

- PHP
- TypeScript
- Vite
- Playwright
- Python
- GitHub Actions
- Interactive QA Labs
- QA Handbook
- Test Automation
- CI/CD
- Güvenli production deployment
- SHA-256 dosya bütünlüğü kontrolü
- Backup ve rollback
- 43 deployment safeguard testi
- İzole release rehearsal
- Release verification

Tüm test ve production iddialarını mevcut kanıtlarla karşılaştır.

### Portfolio ekran görüntüleri

Canlı siteden uygun görüntüler hazırla:

1. Portfolio ana sayfa — desktop
2. QA Handbook
3. Test Automation
4. Interactive QA Lab
5. Portfolio ana sayfa — mobile

Gerçek sitede bulunmayan ekran veya özelliği üretme.

Görselleri `docs/screenshots/` altında sakla.

## 6. GitHub Profile README

Repository: `hakdogan1/hakdogan1`

Profil README'sini güncelle.

Öne çıkan projeler bölümünde QA Practice ve Portfolio Engineering repolarına görünür bağlantılar ekle.

Her proje için:

- Proje adı
- Tek cümlelik açıklama
- Kullanılan temel teknolojiler
- Live Demo
- GitHub repository
- Uygunsa küçük ekran görüntüsü

Profilin mevcut QA Automation Engineer odağını koru.

Teknoloji listesine gerçekte kullanmadığım araçları ekleme.

Profilde gereksiz animasyon, aşırı badge veya kalabalık görsel kullanma.

## 7. Repository Description ve Topics

GitHub repository açıklamalarını da profesyonel hale getirmek için öneri hazırla.

QA Practice için önerilen description:

"Interactive QA testing platform featuring UI testing, bug hunting, locator challenges, API simulations, and Playwright/Selenium learning exercises."

Portfolio Engineering için önerilen description:

"QA engineering portfolio case study featuring interactive testing labs, Playwright regression testing, CI/CD, and secure production deployment."

Uygun GitHub Topics öner.

Description ve Topics değişikliklerini onay almadan uygulama.

## 8. Teknik ve güvenlik kuralları

- Private repository'leri public yapma.
- Private kaynak kodunu public repository'lere kopyalama.
- Parola, API key, token veya private configuration ekleme.
- Production uygulamalarında değişiklik yapma.
- Production deployment gerçekleştirme.
- Mevcut mimari belgelerini silme.
- Mevcut README içeriğini kontrol etmeden değiştirme.
- Doğrulanamayan teknik iddiaları gerçekmiş gibi sunma.
- Eski bağlantıların yeni repository isimlerine etkisini analiz et.
- Gereksiz dosya ve büyük boyutlu görsel ekleme.
- Public repo işlemlerini mümkünse ayrı feature branch'lerde hazırla.
- Ana repository'lerin çalışma durumunu bozma.
- Başka projelerin worktree'lerine dokunma.

## 9. Doğrulama

Değişikliklerden sonra:

- README Markdown bağlantılarını kontrol et.
- Görsel yollarının doğru olduğunu doğrula.
- Bozuk bağlantıları raporla.
- Görsellerin GitHub üzerinde render edilebilir olduğunu kontrol et.
- Dosya boyutlarını kontrol et.
- İngilizce yazım ve teknik terminolojiyi gözden geçir.
- README içindeki proje metriklerini kaynaklarla karşılaştır.
- Mevcut teknik dokümantasyonun korunup korunmadığını denetle.
- Private bilgilerin public içeriğe sızmadığını kontrol et.

Test sonuçlarını PASS / FAIL / SKIP olarak raporla.

## 10. Çalışma ve onay sınırları

Önce salt okunur inceleme yap.

Mevcut branch, HEAD, Git durumu, README içerikleri ve repository yapılarını doğrula.

Ardından yalnızca güvenli, izole çalışma alanlarında değişiklikleri hazırla.

**Aşağıdaki işlemler için ayrıca açık onayımı al:**

- Commit
- Push
- Pull Request oluşturma
- Merge
- Repository yeniden adlandırma
- Repository görünürlüğü değiştirme
- Production deployment

Bu işlemler için önceden verilmiş genel bir onay olduğunu varsayma.

## 11. Beklenen sonuç

Çalışma tamamlandığında şu raporu sun:

1. İncelenen repository'ler
2. Önerilen yeni repository isimleri
3. Güncellenen README bölümleri
4. Eklenen ekran görüntüleri
5. Korunan teknik bilgiler
6. Doğrulanan test sonuçları
7. Bağlantı kontrol sonuçları
8. Güvenlik incelemesi
9. Git diff özeti
10. Commit / Push / PR / Rename için onay bekleyen işlemler

**Hedef:** GitHub profilim, yalnızca teknolojileri listeleyen bir CV görünümünden çıkarak gerçek projeleri, mühendislik kararlarını ve QA Automation yetkinliğimi kanıtlayan profesyonel bir portföye dönüşsün.

Önce inceleme ve hazırlık aşamasını tamamla. Onayım olmadan GitHub üzerinde kalıcı değişiklik yapma.
