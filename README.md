  <div align="center">

  # GNN Tabanlı Trafik Ağ Analizi


  </div>



  ##  İçindekiler

- [1. PROJEYE GİRİŞ](#1-projeye-giriş)
     - [1.1. Proje Nedir?](#11-proje-nedir)
     - [1.2. Sistem Mimarisi & Veri Akışı Diyagramı](#12-sistem-mimarisi--veri-akışı-diyagramı)
     - [1.3. Temel Kavramlar](#13-temel-kavramlar)
     - [1.4. Ne Yapabilirsiniz?](#14-ne-yapabilirsiniz)
- [2. SİSTEMİNİZDE NELER OLMALI](#2-sisteminizde-neler-olmali)
     - [2.1. Donanım Gereksinimleri](#21-donanım-gereksinimleri)
     - [2.2. Yazılım Gereksinimleri](#22-yazılım-gereksinimleri)
- [3. YAZILIMLARI NASIL EDİNEBİLİRİZ](#3-yazilimlari-nasil-edinebiliriz)
     - [3.1. Python](#31-python)
     - [3.2. Neo4j Desktop Kurulumu](#32-neo4j-desktop-kurulumu)
            - [3.2.1. Neo4j Desktop'ı İndirme](#321-neo4j-desktopı-indirme)
            - [3.2.2. Kurulum Sihirbazını Çalıştırma](#322-kurulum-sihirbazını-çalıştırma)
            - [3.2.3. Neo4j Desktop'ı İlk Kez Açma](#323-neo4j-desktopı-ilk-kez-açma)
            - [3.2.4. Kurulumun Doğru Çalıştığını Kontrol Etme](#324-kurulumun-doğru-çalıştığını-kontrol-etme)
            - [3.2.5. Neo4j Veritabanında Query'e Bağlanma](#325-neo4j-veritabanında-querye-bağlanma)
     - [3.3. Docker Desktop Kurulumu](#33-docker-desktop-kurulumu)
            - [3.3.1. Docker Desktop'ı İndirme](#331-docker-desktopı-indirme)
            - [3.3.2. Kurulum Sihirbazı ile Docker Desktop'ı Yükleme](#332-kurulum-sihirbazı-ile-docker-desktopı-yükleme)
            - [3.3.3. İlk Açılış ve WSL 2 Kontrolleri](#333-ilk-açılış-ve-wsl-2-kontrolleri)
            - [3.3.4. Kurulumun Doğru Çalıştığını Kontrol Etme](#334-kurulumun-doğru-çalıştığını-kontrol-etme)
     - [3.4. ArangoDB'nin Docker Üzerinden Kurulumu](#34-arangodbning-docker-üzerinden-kurulumu)
            - [3.4.1. ArangoDB Docker İmajını Çekme](#341-arangodb-docker-imajını-çekme)
            - [3.4.2. ArangoDB Container'ını Çalıştırma](#342-arangodb-containerını-çalıştırma)
            - [3.4.3. ArangoDB Web Arayüzüne Giriş](#343-arangodb-web-arayüzüne-giriş)
            - [3.4.4. Proje Veritabanını Oluşturma (traffic_db)](#344-proje-veritabanını-oluşturma-traffic_db)
     - [3.5. TigerGraph'ın Docker Üzerinden Kurulumu](#35-tigergraphın-docker-üzerinden-kurulumu)
            - [3.5.1. TigerGraph Docker imajını indirme](#351-tigergraph-docker-imajını-indirme)
            - [3.5.2. TigerGraph container'ını oluşturma](#352-tigergraph-containerını-oluşturma)
            - [3.5.3. TigerGraph servislerini başlatma](#353-tigergraph-servislerini-başlatma)
            - [3.5.4. İlk graph'ı ve GraphStudio arayüzünü hazırlama](#354-ilk-graphı-ve-graphstudio-arayüzünü-hazırlama)
            - [3.5.5. Kısa özet ve günlük kullanım](#355-kısa-özet-ve-günlük-kullanım)
     - [3.6. HERE Platform ve API Key Oluşturma](#36-here-platform-ve-api-key-oluşturma)
            - [3.6.1. HERE Hesabı Oluşturma](#361-here-hesabı-oluşturma)
            - [3.6.2. Proje (Project) Oluşturma](#362-proje-project-oluşturma)
            - [3.6.3. API Key Üretme](#363-api-key-üretme)
            - [3.6.4. API Key'i .env Dosyasına Yazma](#364-api-keyi-env-dosyasına-yazma)
- [4. PROJE KURULUMU](#4-proje-kurulumu)
     - [4.1. Projeyi İndirme](#41-projeyi-indirme)
     - [4.2. Gereksinimlerin Yüklenmesi](#42-gereksinimlerin-yüklenmesi)
     - [4.3. .env Yapılandırması](#43-env-yapılandırması)
- [5. PIPELINE KULLANIMI](#5-pipeline-kullanimi)
     - [5.1. Tek Seferlik Çalıştırma](#51-tek-seferlik-çalıştırma)
     - [5.2. Loop Modu (Belirli Aralıklarla Çalıştırma)](#52-loop-modu-belirli-aralıklarla-çalıştırma)
- [6. VERİTABANI YÖNETİMİ VE BAKIMI](#6-veritabani-yönetimi-ve-bakimi)
     - [6.1. Durum Kontrolü](#61-durum-kontrolü)
            - [6.1.1. Neo4j Durum Kontrolü](#611-neo4j-durum-kontrolü)
            - [6.1.2. ArangoDB Durum Kontrolü](#612-arangodb-durum-kontrolü)
            - [6.1.3. TigerGraph Durum Kontrolü](#613-tigergraph-durum-kontrolü)
     - [6.2. Veri Temizleme](#62-veri-temizleme)
- [7. GÖRSELLEŞTİRME](#7-görselleştirme)
     - [7.1. Web Viewer Kullanımı](#71-web-viewer-kullanımı)
            - [7.1.1. multi_db_viewer.py](#711-multi_db_viewerpy)
     - [7.2. Harita Anlamlandırma](#72-harita-anlamlandırma)
- [8. BENCHMARK & PERFORMANS](#8-benchmark--performans)
     - [8.1. Benchmark Çalıştırma](#81-benchmark-çalıştırma)
            - [8.1.1. Önkoşullar](#811-önkoşullar)
            - [8.1.2. Profil Seçimi (quick / standard / ultimate)](#812-profil-seçimi-quick--standard--ultimate)
            - [8.1.3. Benchmark Komutlarının Çalıştırılması](#813-benchmark-komutlarının-çalıştırılması)
     - [8.2. Sonuçları Okuma](#82-sonuçları-okuma)
            - [8.2.1. Metin Raporu (benchmark_results_readable.txt)](#821-metin-raporu-benchmark_results_readabletxt)
            - [8.2.2. HTML Dashboard (benchmark_dashboard.html)](#822-html-dashboard-benchmark_dashboardhtml)
     - [8.3. Karşılaştırma Analizi](#83-karşılaştırma-analizi)
            - [8.3.1. Ortalama Süre vs. P95 (Tail Latency)](#831-ortalama-süre-vs-p95-tail-latency)
            - [8.3.2. Test Kategorileri Arasında Denge](#832-test-kategorileri-arasında-denge)


## 1. PROJEYE GİRİŞ

  #### 1.1. Proje Nedir?

  Bu sistem, HERE Traffic Flow API v7 kullanarak gerçek zamanlı ve yakın gerçek zamanlı trafik
  verilerini otomatik olarak toplayan, işleyen ve bu verileri üç farklı graf veritabanında ( **Neo4j** ,
  **ArangoDB** , **TigerGraph** ) saklayan kapsamlı bir trafik veri pipeline’ıdır. Kurulan yapı sayesinde,
  seçilen bir bölgedeki yol ağı hem uzamsal (hangi yol hangi yola komşu?) hem de zamansal (zaman
  içinde hız ve yoğunluk nasıl değişiyor?) açıdan ayrıntılı olarak incelenebilir.
  Bu proje, hem pratik kullanım hem de akademik/AR-GE çalışmaları için tekrar kullanılabilir bir
  altyapı sunmayı hedefler. Pipeline, belirli aralıklarla HERE’den veri çekip bu veriyi işleyerek, farklı
  graf veritabanlarında karşılaştırılabilir bir biçimde saklar.

  **Projenin temel amaçları:**

  - Gerçek dünya trafik verilerini belirli aralıklarla sürekli toplamak ve arşivlemek
  - Yol ağını matematiksel bir graf yapısı (düğümler: yol segmentleri, kenarlar: komşuluk ilişkileri) olarak modellemek
  - Neo4j, ArangoDB ve TigerGraph üzerinde aynı veri ile performans karşılaştırması yapmak
  - İleride yapılacak zaman serisi trafik analizi (hız, yoğunluk, jamFactor değişimi vb.) için sağlam bir veri altyapısı oluşturmak
  - Graph Neural Network (GNN) ve benzeri yapay zeka modelleri için, temizlenmiş ve graf yapısına uygun hazır veri setleri oluşturmak
  Bu giriş bölümünün devamında, sistemin genel mimarisi, kullanılan temel bileşenler ve dokümanın
  ilerleyen bölümlerinde izlenecek kurulum/kullanım adımlarının genel çerçevesi özetlenecektir.


  ### 1.2. Sistem Mimarisi & Veri Akışı Diyagramı
  ![](docs/images/image.png)

  ### 1.3. Temel Kavramlar

  Bu projeyi anlamak için bilmeniz gereken temel kavramlar:

  #### **Segment (Yol Parçası)**
  - Bir yolun fiziksel bir kısmını temsil eder
  - Her segment'in benzersiz bir ID'si vardır (örn: edge:abc123)
  - Başlangıç ve bitiş koordinatları (lat/lon) içerir
  - Uzunluk, yol tipi, isim gibi özellikler barındırır

  #### **Measure (Trafik Ölçümü)**
  - Belirli bir zamanda bir segment üzerindeki trafik durumunu gösterir
  - Hız, serbest akış hızı, tıkanıklık faktörü (jamFactor) içerir
  - Her measure bir segment'e ve bir zamana bağlıdır

  #### **CONNECTS_TO (Komşuluk İlişkisi)**
  - İki segment'in fiziksel olarak birbirine bağlı olduğunu gösterir
  - Graf analizleri için kritik öneme sahiptir

  #### **AT_TIME (Zamansal İlişki)**
  - Bir segment'in belirli bir zamandaki measure'ını bağlar
  - Zaman serisi analizi için kullanılır
  ![](docs/images/image-1.png)
  **Görsel 1.1 - Örnek bir CONNECTS_TO bağlantısı**


  ### 1.4. Ne Yapabilirsiniz?

  #### **Veri Toplama & Arşivleme**
  - HERE API'den otomatik trafik verisi çekme
  - Her çalıştırmada GeoJSON snapshot'ı kaydetme
  - 500+ arşiv dosyası otomatik yönetimi

  #### **Graf Yapısı Modelleme**
  - Segment (node): Yol parçaları
  - CONNECTS_TO (edge): Komşuluk ilişkileri
  - AT_TIME (edge): Zamansal bağlantılar

  #### **Multi-Database Desteği**
  - Neo4j: Cypher sorguları ile graf analizi
  - ArangoDB: AQL ile multi-model sorgular
  - TigerGraph: GSQL ile yüksek performans

  #### **Görselleştirme**
  - Leaflet.js tabanlı interaktif haritalar
  - Trafik yoğunluğuna göre renk kodlaması
  - 3 farklı web viewer (her DB için ayrı)

  #### **Zaman Serisi Analizi**
  - Parquet formatında zaman serisi depolama
  - Snapshot bazlı karşılaştırma
  - Measure verilerinin birikimli tutulması

  #### **Performans Analizi**
  - 25 farklı kategori benchmark testi
  - Okuma/yazma/traversal karşılaştırması
  - Detaylı istatistiksel raporlar

  #### **Otomasyon**
  - Loop mode ile sürekli veri toplama
  - Configurable interval (varsayılan: 15 dakika)
  - Hata yönetimi ve logging


  ## 2. SİSTEMİNİZDE NELER OLMALI

  Bu kısımda, sistemi sorunsuz çalıştırmak için ihtiyaç duyacağınız minimum ve önerilen donanım ile
  temel yazılımları özetliyoruz. Bu gereksinimler, HERE trafik verisinin indirilmesi, işlenmesi ve üç
  farklı graf veri tabanında kullanılabilmesi için yeterli olacaktır.

  ### 2.1. Donanım Gereksinimleri

  #### **Minimum (Test & Öğrenme İçin)**

  | Bileşen | Gereksinim | Açıklama |
  |---|-----|----|
  | İşlemci | Intel Core i5 (4 çekirdek) | Pipeline ve tek db için yeterli |
  | RAM | 8 GB | Neo4J + Python için minimum |
  | Depolama | 50 GB boş alan (HDD) | 1 haftalık veri için yeterli |
  | İnternet | 10 Mbps | HERE API çağrıları için |

  #### **Önerilen (Production & Uzun Süreli Kullanım)**

  | Bileşen | Gereksinim | Açıklama |
  |---|-----|----|
  | İşlemci | Intel Core i7/i9 (8+ çekirdek) | 3 DB + benchmark için ideal |
  | RAM | 16-32 GB | TigerGraph için 16 GB önerilir |
  | Depolama | 100 GB SSD + 500 GB HDD | SSD: DB'ler, HDD: Arşiv |
  | İnternet | 50+ Mbps | Sürekli veri toplama için |

  ### 2.2. Yazılım Gereksinimleri

  #### **İşletim Sistemi**
  - Windows 10 veya üzeri (64-bit)

  #### **Gerekli Yazılımlar**

  1. Python 3.10 veya üzeri
  2. Neo4j Desktop (1.5 ve üzeri sürüm)
  3. ArangoDB Community Server (3.11 ve üzeri)
  4. Docker Desktop (4.25 ve üzeri, WSL2 etkin)
  5. TigerGraph Developer Edition (Docker üzerinde çalışacak)
  6. HERE hesabı ve geçerli bir HERE API Key

  Bu yazılımlar kurulduğunda; Python tarafında veri işleme ve pipeline çalıştırma, Neo4j/ArangoDB/TigerGraph üzerinde veri saklama ve sorgulama, HERE üzerinden trafik verisi alma ve Docker ile TigerGraph ortamını yönetme işlemlerini gerçekleştirebileceksiniz.

  ## 3. YAZILIMLARI NASIL EDİNEBİLİRİZ

  Bu bölümde, sistem için ihtiyaç duyacağınız temel yazılımların resmi indirme adreslerini toplu şekilde
  bulabilirsiniz. Tüm linkler, doğrudan resmi sitelere yönlendirecek şekilde seçilmiştir.

  ### 3.1. Python

  Python’u resmi sitesinden indireceksiniz:
  - İndirme adresi: https://www.python.org/downloads/
  - Önerilen sürüm: Python 3.11.
  - Kurulum sırasında özellikle **“** Add Python to PATH **”** kutucuğunu işaretlemeniz gerekir.
  - Kurulumdan sonra PowerShell’de python --version komutuyla kurulumu kontrol edebilirsiniz.
  ![](docs/images/image-2.png)
  **Görsel 3.1 - Python indirme adresinden bir görüntü**


  ### 3.2. Neo4j Desktop Kurulumu

  Neo4j Desktop, projede kullanacağımız grafik veritabanını yönetmek, verileri görmek ve sorgu
  çalıştırmak için kullanacağımız masaüstü uygulamadır. Aşağıdaki adımları takip ederek Neo4j
  Desktop’ı indirebilir ve ilk kez çalıştırabilirsiniz.

  #### 3.2.1. Neo4j Desktop’ı İndirme

  1. Herhangi bir tarayıcıdan aşağıdaki adrese gidin: https://neo4j.com/download/
  2. Sayfada “Neo4j Desktop” bölümünü bulun.
  3. “Download” veya “Download Neo4j Desktop” butonuna tıklayın.
  4. Kısa bir form açılabilir; isim, e-posta vb. bilgiler istenirse doldurun ve onaylayın.
  5. İndirme tamamlandığında elinizde Neo4jDesktop-Setup-...exe benzeri bir kurulum dosyası
          olacaktır.
                  ![](docs/images/image-3.png)
               **Görsel 3.2 - Neo4j web adresinden bir görüntü**
                  ![](docs/images/image-4.png)
                      **Görsel 3.3 - Doldurulması istenilen form**


  #### 3.2.2. Kurulum Sihirbazını Çalıştırma

  1. İndirilen Neo4jDesktop-Setup-...exe dosyasını bulun
  2. Dosyaya çift tıklayarak kurulum sihirbazını başlatın.
  3. Windows, “Bu uygulamaya izin vermek istiyor musunuz?” diye sorarsa Evet deyin.
  4. Kurulum ekranında sırasıyla:
            - Lisans sözleşmesini kabul edin (I agree / Accept).
            - Kurulum klasörünü varsayılan bırakabilirsiniz
               (genellikleC:\Users\KullanıcıAdı\AppData\Local\Neo4j altında).
            - “Next / İleri” butonlarına basarak kurulumu tamamlayın.
  5. Kurulum bittiğinde Finish diyerek sihirbazı kapatın.

  #### 3.2.3. Neo4j Desktop’ı İlk Kez Açma

  1. Kurulumdan sonra Başlat Menüsü’nden veya masaüstü kısayolundan Neo4j Desktop’ı
          çalıştırın.
  2. Uygulama ilk açılışta sizden:
            - Neo4j hesabınızla giriş yapmanızı, veya
            - Yeni bir hesap oluşturmanızı isteyebilir.
  3. Eğer daha önce Neo4j hesabınız yoksa, uygulama içinden veya web tarayıcısı üzerinden kısa
          bir kayıt formu doldurup hesap oluşturun.
  4. Kayıt sırasında verdiğiniz e-posta adresine gelen onay/aktivasyon mailini kontrol edin ve
          gerekirse hesabı doğrulayın.
  5. Neo4j Desktop, bazı sürümlerde aktivasyon anahtarı (activation key) alanı gösterebilir; e-posta
          ile gelen anahtarı bu alana yapıştırıp devam edebilirsiniz.
  6. Giriş işlemi tamamlandığında Neo4j Desktop ana ekranı açılacak ve “Projects” (Projeler)
          bölümünü göreceksiniz.

  ![](docs/images/image-5.png)
  **Görsel 3.4 - Neo4j arayüzünden bir görüntü**
  #### 3.2.4. Kurulumun Doğru Çalıştığını Kontrol Etme

  Bu aşamada henüz ayrıntılı veritabanı yapısını oluşturmayacağız; sadece Neo4j Desktop’ın sorunsuz
  çalıştığını kontrol edeceğiz.

  1. Neo4j Desktop ana ekranında New Project (Yeni Proje) butonuna tıklayın ve deneme amaçlı
          bir proje adı girin (örneğin: HEREv7).
  2. Projenin içinde Add →Local DBMS veya benzeri bir seçenek göreceksiniz. Buna tıklayıp:
            - Name (İsim) alanına örneğin test-db yazın,
            - Password (Şifre) alanına güçlü ama hatırlayabileceğiniz bir şifre girin (bu şifreyi proje
               boyunca kullanacağız).
                  ![](docs/images/image-6.png)
                      **Görsel 3.5 - Veritabanı örneği oluşturma ekranı**
  3. Create butonuna bastıktan sonra listede test-db isimli bir veritabanı göreceksiniz.
  4. Bu veritabanının yanındaki Start tuşuna basarak sunucuyu başlatın. Durum göstergesi yeşil
          olduğunda veritabanı ayağa kalkmış demektir.


  #### 3.2.5. Neo4j Veritabanında Query’e Bağlanma

  Aşağıdaki ekran görüntüsünde görüldüğü gibi, Neo4j Browser açıldığında üstte bir komut satırı ve
  altında “No instance connected” yazan bir alan yer alır. Bu durum, henüz hiçbir Neo4j
  sunucusuna/veritabanına bağlı olmadığımız anlamına gelir.
  ![](docs/images/image-7.png)
  **Görsel 3.6 - Neo4j Query Ekranı**
  Bu ekrandan bir veritabanına bağlanmak için şu adımları izleyin:

  **Önce Neo4j Desktop’tan veritabanını başlatın.**
  - Neo4j Desktop’ı açın.
  - Projenizdeki HEREv7 veya kullandığınız veritabanı adı satırını bulun.
  - Yanındaki Start butonuna tıklayın ve veritabanının yeşil duruma gelmesini bekleyin.


  **Query’deki “Connect to instance” bağlantısına tıklayın.**
  - Ekran görüntüsünde ortadaki gri kutuda “Connect to instance” yazan mavi linke tıklayın.
  - Karşınıza bir bağlantı penceresi çıkacaktır.
  ![](docs/images/image-8.png)
  **Görsel 3.7 - Bağlantı Penceresi**
  - Tüm alanları doldurduktan sonra penceredeki **Connect** butonuna tıklayın.
  ![](docs/images/image-9.png)
  **Görsel 3.8 - Veri tabanına bağlanma**


  - Bağlantı başarılı ise:
    - “No instance connected” uyarısı kaybolur.
    - Sol tarafta “Database information” bölümünde veritabanı ile ilgili bilgiler görünmeye
  başlar.
    - Ekranın üst kısmındaki komut satırına ( $ işaretinin olduğu yere ) artık Cypher
  sorguları yazabilirsiniz.
  ![](docs/images/image-10.png)
  Görsel 3.9 - Veri tabanına bağlanma
  ### 3.3. Docker Desktop Kurulumu

  ArangoDB ve TigerGraph’ı bu projede Docker container’ları içerisinde çalıştıracağımız için, önce
  Windows’a Docker Desktop kurmamız gerekir. Aşağıdaki adımlar Docker Desktop’ın indirilmesini,
  kurulmasını ve doğru çalıştığının kontrol edilmesini anlatır.

  #### 3.3.1. Docker Desktop’ı İndirme

  1. Herhangi bir tarayıcıdan aşağıdaki adrese gidin:
          https://www.docker.com/products/docker-desktop/
  2. Sayfada “Download Docker Desktop” butonunu göreceksiniz.
  3. İşletim sisteminiz otomatik algılanmış olmalıdır; değilse Windows seçili olduğundan emin
          olun.
  4. “Download for Windows” butonuna tıklayarak kurulum dosyasını indirin.
  İndirilen dosya genellikle Docker Desktop Installer.exe benzeri bir isimde olur.


  #### 3.3.2. Kurulum Sihirbazı ile Docker Desktop’ı Yükleme

  1. İndirilen Docker Desktop Installer.exe dosyasını bulun.
  2. Dosyaya çift tıklayarak kurulum sihirbazını başlatın.
  3. Windows, “Bu uygulamaya izin vermek istiyor musunuz?” penceresi açarsa Evet deyin.
  4. Kurulum ekranında genellikle şu adımlar gelir:
          a. Lisans ve kullanım şartlarını kabul edin.
          b. “Use WSL 2 instead of Hyper-V” seçeneği işaretli ise seçili kalmasına izin verin
               (Windows 10/11 için önerilen yöntem budur).
  5. “Install” butonuna tıklayarak kurulumu başlatın.
  6. Kurulum tamamlandığında sistem sizden bilgisayarı yeniden başlatmanızı isteyebilir;
          gerekirse Restart deyin.

  #### 3.3.3. İlk Açılış ve WSL 2 Kontrolleri

  1. Bilgisayar yeniden başladıktan sonra Docker Desktop otomatik açılabilir; açılmazsa Başlat
          menüsünden kendiniz başlatın.
  2. İlk açılışta kısa bir kurulum/başlangıç sihirbazı görebilirsiniz; varsayılan ayarlarla devam
          edebilirsiniz.
  3. Eğer WSL 2 ile ilgili bir uyarı alırsanız:
          - Windows’ta “Windows Features” (Windows Özelliklerini Aç veya Kapat)
               penceresinden
                        - “Virtual Machine Platform”
                        - “Windows Subsystem for Linux” (WSL)
                           seçeneklerinin işaretli olduğundan emin olun.
          - Değişiklik yaptıysanız bilgisayarı yeniden başlatın ve Docker Desktop’ı tekrar açın.
          ![](docs/images/image-11.png)
               **Görsel 3.10**
          ![](docs/images/image-12.png)
             **Görsel 3.11**


  #### 3.3.4. Kurulumun Doğru Çalıştığını Kontrol Etme

  1. PowerShell veya Windows Terminal açın.
  2. Aşağıdaki komutu yazıp Enter’a basın:
          a. docker --version
  3. Kurulum başarılıysa, ekranda Docker sürümünü gösteren bir çıktı görürsünüz (örneğin Docker
          version 27.0.3, build ...).
  4. Ek olarak, Docker’ın container çalıştırabildiğini test etmek için şu komutu da kullanabilirsiniz:
          a. docker run hello-world
          b. Bu komut küçük bir test imajı indirip çalıştırır; sonunda “Hello from Docker!” benzeri
               bir mesaj görürseniz Docker Desktop doğru şekilde çalışıyor demektir.


  ![](docs/images/image-13.png)
  Görsel 3.12
  ![](docs/images/image-14.png)
  Görsel 3.13
  ### 3.4. ArangoDB’nin Docker Üzerinden Kurulumu

  Bu projede ArangoDB’yi Windows’a doğrudan kurmak yerine Docker container içinde çalıştıracağız.
  Aşağıdaki adımlar, ArangoDB imajını çekmeyi, container’ı başlatmayı ve web arayüzü üzerinden
  traffic_db veritabanını oluşturmayı anlatır.

  #### 3.4.1. ArangoDB Docker İmajını Çekme

  1. Docker Desktop’ın çalıştığından emin olun.
          Sağ altta Docker simgesi görülmeli ve “Docker Desktop is running” yazmalıdır.
  2. PowerShell veya Windows Terminal’i açın.
  3. ArangoDB Enterprise imajını çekmek için, ArangoDB sitesinde de önerilen komutu çalıştırın:
          a. docker pull arangodb/enterprise:3.12.6.
          Bu komut, arangodb/enterprise:3.12.6.1 isimli imajı indirir.

  #### 3.4.2. ArangoDB Container’ını Çalıştırma

  İmaj indikten sonra, yine sitede verilen örneği temel alarak container’ı başlatacağız.

  1. Aynı terminal penceresinde şu komutu çalıştırın:


  docker run -d -e ARANGO_ROOT_PASSWORD="1234" -p 8529:
  arangodb/enterprise:3.12.6.

  Bu komut şunları yapar:
  - -d → Container’ı arka planda çalıştırır.
  - -e ARANGO_ROOT_PASSWORD="1234" → root kullanıcısının şifresini 1234
  olarak ayarlar.
  - -p 8529:8529 → Container içindeki 8529 portunu bilgisayarınızdaki 8529 portuna
  yönlendirir.
  - Son kısım (arangodb/enterprise:3.12.6.1) → Kullanılacak Docker imajının adıdır.
  Container’ın çalışıp çalışmadığını kontrol etmek için:
  **docker ps**
  Çıktıda arangodb/enterprise:3.12.6.1 kullanan bir satır ve STATUS kısmında Up ibaresini
  görmeniz gerekir.

  #### 3.4.3. ArangoDB Web Arayüzüne Giriş

  1. Tarayıcıyı açın (Chrome, Edge vb.).
  2. Adres çubuğuna şu adresi yazın:
          [http://localhost:](http://localhost:)
  3. ArangoDB giriş ekranı açılacaktır.
  4. Bilgileri şöyle doldurun:
          a. **Username:** root
          b. **Password:** ARANGO_ROOT_PASSWORD değişkeninde verdiğiniz şifre
               (ör.1234)
  5. Log in butonuna tıklayın.
  ![](docs/images/image-15.png)
          **Görsel 3.14 - ArrangoDB web arayüzü giriş ekranı**


  #### 3.4.4. Proje Veritabanını Oluşturma (traffic_db)

  1. Giriş yaptıktan sonra üst menüden “Databases” bölümüne geçin.
  2. Var olan sistem veritabanları arasında _system vb. kayıtları göreceksiniz.
  3. Kod ilk kez çalıştırıldıktan sonra traffic_db isimli veritabanını otomatik olarak oluşturacaktır.
  4. Listede sistem tarafından oluşturulan traffic_db isimli veritabanı görünmelidir.
          ![](docs/images/image-16.png)
          **Görsel 3.15**
  5. Üstteki veritabanı seçim menüsünden aktif veritabanı olarak traffic_db’yi seçin.
          Sol menüde **Collections** , **Queries** , **Graphs** sekmeleri bu veritabanı için görünecektir.
          ![](docs/images/image-17.png)
               **Görsel 3.16 - ArrangoDB arayüzünden bir görsel**


  Bu aşamada:
  - ArangoDB, Docker container’ı içinde çalışıyor,
  - root kullanıcısı ve belirlediğiniz şifre ile erişilebilir durumda,
  - Projede kullanacağımız traffic_db veritabanı hazır.
  Sonraki adımlarda Python script’leriyle bu veritabanına koleksiyonları ve graph yapısını yükleyeceğiz.

  ### 3.5 TigerGraph’ın Docker Üzerinden Kurulumu

  Bu bölümde, Docker Desktop üzerine TigerGraph Developer Edition kurup çalıştıracağız. Amaç;
  sonunda GraphStudio arayüzüne “http://localhost:14240” adresinden ulaşmak ve Python kodunun
  “localhost:9000” üzerinden TigerGraph’a bağlanabilmesi.

  **Önkoşul:** Docker Desktop kurulmuş ve çalışır durumda olmalı (Docker simgesi sağ altta görünmeli).

  #### 3.5.1 TigerGraph Docker imajını indirme

  1. PowerShell’i açın.
  2. Aşağıdaki komutu çalıştırın:

          a. docker pull docker.tigergraph.com/tigergraph-dev:4.1. 0

  3. Bu komut yaklaşık 4 GB boyutunda TigerGraph Developer Edition imajını indirir. İndirme
          bittiğinde, şu benzeri bir çıktı görmelisiniz: 

          Status: Downloaded newer image for
          docker.tigergraph.com/tigergraph-dev:4.1.0.
  4. İmajın gerçekten indiğini kontrol etmek için:
          a. docker images | findstr tigergraph
  5. Çıktıda docker.tigergraph.com/tigergraph-dev 4.1.0 satırını görüyorsanız imaj hazır demektir.

  #### 3.5.2 TigerGraph container’ını oluşturma

  Test ve geliştirme için basit kurulum yeterli. Veri kalıcılığına ihtiyacınız olursa ikinci seçeneği
  kullanabilirsiniz.

  **Yöntem 1 – Basit kurulum:**


  docker run -d `
  --name tigergraph `
  -p 14240:14240 `
  -p 9000:9000 `
  --ulimit nofile=1000000:1000000 `
  docker.tigergraph.com/tigergraph-dev:4.1.0


  - **--name tigergraph :** Container adımız
  - **-p 14240:14240 :** GraphStudio web arayüzü
  - **-p 9000:9000 :** REST API portu
  - **--ulimit nofile=1000000:1000000 :** TigerGraph için gerekli dosya tanıtıcı limiti

  **Yöntem 2 – Verilerin saklandığı kurulum:**

  1. Önce Windows’ta bir klasör oluşturun:

          a. mkdir 
          C:\TigerGraphData
  2. Sonra container’ı bu klasörle birlikte çalıştırın:

          docker run -d `
          --name tigergraph `
          -p 14240:14240 `
          -p 9000:9000 `
          --ulimit nofile=1000000:1000000 `
          -v C:\TigerGraphData:/home/tigergraph/mydata `
          docker.tigergraph.com/tigergraph-dev:4.1.0
  Bu şekilde container silinse bile verileriniz C:\TigerGraphData altında kalır.
  3. Container’ın gerçekten çalışıp çalışmadığını kontrol edin:

          a. docker ps
  Listede tigergraph ismini ve STATUS kısmında Up yazdığını görmelisiniz.

  #### 3.5.3 TigerGraph servislerini başlatma

  Container çalışıyor olsa bile içindeki TigerGraph servisleri ilk başta kapalı olur. Bunları gadmin ile
  açmamız gerekiyor.

  1. Container içine bağlanın:

          docker exec -it tigergraph bash
  2. Linux shell içinde aşağıdaki komutları çalıştırın:
  
          gadmin start all
          # 30–60 saniye bekledikten sonra
          gadmin status
  Çıktıda tüm servislerin Online olduğunu görmelisiniz (ADMIN, GSE, GPE, GUI, RESTPP,
  vb.). Bazıları “Warmup” görünüyorsa 30 saniye daha bekleyip gadmin status komutunu
  yeniden çalıştırın.
  3. İşiniz bittiğinde container içinden çıkmak için:


```bash
  exit
```
  #### 3.5.4 İlk graph’ı ve GraphStudio arayüzünü hazırlama

  1. Tarayıcınızda şu adresi açın:
          a. GraphStudio: [http://localhost:14240](http://localhost:14240)
          b. TigerGraph giriş ekranı açılacaktır. Developer imajında varsayılan kullanıcı genelde:
               i. **Username:** tigergraph
  ii. **Password:** tigergraph
  ![](docs/images/image-18.png)
  **Görsel 3.17 - TigerGraph giriş ekranı**
  2. Giriş yaptıktan sonra Graphstudio’yu seçin.
  ![](docs/images/image-19.png)
          **Görsel 3.18**


  3. Sol üst köşeden “Global View” yerine “TrafficGraph” seçelim.
          ![](docs/images/image-20.png)
          **Görsel 3.19**

  #### 3.5.5 Kısa özet ve günlük kullanım

  TigerGraph’ı açmak için:
  
  docker start tiger

  ### 3.6. HERE Platform ve API Key Oluşturma

  Bu projede trafik verisini HERE Traffic Flow API üzerinden alacağız. Bunun için önce HERE
  platformunda bir hesap açmanız, bir proje oluşturmanız ve bu proje için bir API key üretmeniz
  gerekiyor.

  #### 3.6.1. HERE Hesabı Oluşturma

  1. Tarayıcınızda şu adrese gidin: https://platform.here.com/
  2. Hesabınız varsa kayıtlı mail hesabınızı girebilirsiniz.
  3. HERE hesabınız yoksa “Create a free account” seçeneğini seçin.
  4. İsim, e-posta ve şifre bilgilerini doldurun, kullanım koşullarını kabul edin.
  5. E-posta adresinize gelen onay mailindeki linke tıklayarak hesabınızı doğrulayın.


  #### 3.6.2. Proje (Project) Oluşturma

  1. Hesabınızla giriş yaptıktan sonra HERE Platform ana sayfasında sağ üst köşede bulunan
          launcher butonuna basıp Projects Manager isimli bölüme geçin.
          ![](docs/images/image-21.png)
               **Görsel 3.20**
  2. “Create Project” butonuna tıklayın.
  3. Proje ismi olarak örneğin:
          a. **Name:** Traffic Flow Project
          b. **Description:** Traffic flow data collection and analysis for
               Neo4j/ArangoDB/TigerGraph pipeline
                  ![](docs/images/image-22.png)
                      **Görsel 3.21**
  4. “Create” diyerek projeyi oluşturun.


  #### 3.6.3. API Key Üretme

  1. Launcher (sol üst menü) üzerinden Access Manager’ı seçin.
  2. Üstteki sekmelerden Apps sekmesine geçin ve Register new app butonuna tıklayın.
          Açılan formda uygulama için bir ad yazın (örneğin: Traffic Flow App).
  3. Register butonuna tıklayın. HERE, bu uygulama için benzersiz bir app ID oluşturur.
  4. Uygulama detaylarındaki Credentials sekmesine geçin, burada API Keys bölümünü seçin ve
          Create API key butonuna tıklayın.
               a. En fazla iki API key oluşturabileceğinizi belirtir; bir tane key oluşturmanız yeterlidir.
               b. Oluşturulan API key ekranda gösterilir; bunu kopyalayın.

  #### 3.6.4. API Key’i .env Dosyasına Yazma

  1. Proje klasörünüzdeki config/.env.example dosyasını kopyalayın ve adını config/.env yapın.
  2. config/.env dosyasını açın ve şu satırı bulun:
          HERE_API_KEY=
  3. Eşittir işaretinden sonra HERE’den aldığınız anahtarı yapıştırın:
          HERE_API_KEY=BURAYA_API_KEY_GELECEK
  4. Dosyayı kaydedin.

  ## 4. PROJE KURULUMU

  Bu bölümde projeyi bilgisayarınıza indirip kuracak, Python bağımlılıklarını yükleyecek ve .env
  yapılandırmasını tamamlayacaksınız. Bu adımlar bittiğinde, 5. bölümdeki pipeline komutlarını
  çalıştırmaya hazır olacaksınız.

  ### 4.1. Projeyi İndirme

  1. Projeyi paylaşılan ZIP dosyasından indirin.
  2. Projeyi ZIP dosyasından çıkarın
  3. Klasör yapınız kabaca şöyle görünmelidir:

  ### 4.2. Gereksinimlerin Yüklenmesi

  Gerekli Python paketlerini kurun:
  pip install -r config\requirements.txt
  Bu komut; requests, pandas, geopandas, shapely, neo4j, python-arango, pyTigerGraph vb. paketleri
  yükleyecektir.


  ### 4.3. .env Yapılandırması

  Bu projede tüm gizli bilgiler (HERE API key, veritabanı şifreleri, bağlantı adresleri) .env dosyasında
  tutulur. Kodlar bu dosyayı otomatik okuyarak bağlantı ayarlarını kullanır.

  1. Örnek dosyayı kopyalayın.
          Proje kökünde şu dosyayı bulun:
               a. _config\.env.example_
                      Bunu kopyalayıp adını _config\.env_ olarak değiştirin.
  2. _config\.env_ dosyasını bir metin editörüyle açın.
          (VS Code, Notepad++ veya Not Defteri kullanabilirsiniz.)
  3. Temel alanları doldurun.
          Aşağıdaki satırlar örnek bir içerik gösterir; kendi şifrelerinize göre düzenleyin:
          
               # HERE Traffic Flow API
               HERE_API_KEY=BURAYA_HERE_API_KEY
               # Çalışılacak bbox (örnek: Eskişehir)
               BBOX=30.45,39.72,30.60,39.83
               # Neo4j bağlantısı
               NEO4J_URI=bolt://localhost:7687
               NEO4J_USER=neo4j
               NEO4J_PASSWORD=SENIN_NEO4J_SIFREN
               NEO4J_DATABASE=neo4j
               # ArangoDB bağlantısı
               ARANGO_HOST=http://localhost:8529
               ARANGO_USER=root
               ARANGO_PASSWORD=SENIN_ARANGO_SIFREN
               ARANGO_DB_NAME=traffic_db
               # TigerGraph bağlantısı
               TIGERGRAPH_HOST=http://localhost
               TIGERGRAPH_REST_PORT=9000
               TIGERGRAPH_USERNAME=tigergraph
               TIGERGRAPH_PASSWORD=tigergraph
               TIGERGRAPH_GRAPH_NAME=TrafficGraph
               # Pipeline genel ayarları
               PIPELINE_INTERVAL_MIN=15
               TIMEZONE=Europe/Istanbul
               CONNECT_THRESHOLD_METERS=12
               ACTIVE_DATABASES=neo4j,arangodb,tigergraph


```bash
  - HERE_API_KEY : Az önce HERE platformundan aldığınız anahtar.
  - NEO4J_PASSWORD : Neo4j Desktop’ta traffic-db için verdiğiniz şifre.
  - ARANGO_PASSWORD : ArangoDB Docker container’ını başlatırken verdiğiniz
  ARANGO_ROOT_PASSWORD.1
  - TIGERGRAPH_ * alanları: TigerGraph Developer’ın varsayılan kullanıcı ve port
  bilgileri.
```
  4. Dosyayı kaydedin.

  ## 5. PIPELINE KULLANIMI

  Bu bölümde:
  - Pipeline’ı tek seferlik nasıl çalıştıracağınızı,
  - Belirli aralıklarla veri toplamak için loop modunu nasıl kullanacağınızı,
  - Çalışma sırasında sık görülen hataları nasıl yorumlayacağınızı ve ilk neyi kontrol etmeniz
  gerektiğini anlatıyoruz.

  ### 5.1. Tek Seferlik Çalıştırma

  Tek seferlik çalıştırma, “şimdi bir kere veri çek, işle ve veritabanlarına yükle” senaryosu içindir. İlk
  denemeleri ve manuel veri toplama işlemlerini bu modla yapmanız tavsiye edilir.

  1. Pipeline’ı çalıştırın.
          python run_pipeline.py
  2. Komut başladıktan sonra terminalde sırasıyla şu adımlara benzer log satırları görürsünüz
          (örnek):

               Step 0/4 – Schema Oluşturma (İlk kez çalıştırma için gerekli)
               Step 1/4 – HERE API veri çekme
               Step 2/4 – Harita render & Arşivleme
               Step 3/4 – Timeseries oluşturma
               Step 4/4 – Multi-DB Yükleme + Topoloji (Neo4j + ArrangoDB + TigerGraph
               İşlemler Tamamlandı!
          Bu adımlar, .env içindeki ACTIVE_DATABASES alanına göre değişebilir (örneğin sadece
          neo4j aktifse diğerleri atlanır).


  3. Çıktıları hızlıca kontrol edin.

          data\raw\here_flow_raw.json
          data\processed\latest_flow.geojson
          archive\flow_YYYYMMDD_HHMMSS.geojson
          data\processed\timeseries.parquet

  ### 5.2. Loop Modu (Belirli Aralıklarla Çalıştırma)

  Loop modu, pipeline’ı aynı süreçle belirli dakikalık aralıklarla tekrar tekrar çalıştırır. Sürekli veri
  toplamak istediğinizde bu modu kullanabilirsiniz.

  1. Loop komutunu çalıştırın.
          Terminalde aşağıdakine benzer bir akış görürsünüz:

               python run_loop.py --interval 15
  2. Terminalde aşağıdakine benzer bir akış görürsünüz:

          Loop started. Interval: 15 minutes
          >>Yeni pipeline turu başlıyor (2025-11-28 14:00)...
          (run_pipeline adımları)
          Tur tamamlandı. Bir sonraki tur 15 dakika sonra başlayacak.
  3. Loop’tan çıkmak için terminalde Ctrl + C tuş kombinasyonuna basmanız yeterlidir.

  **Not:** Loop modu, HERE API kota limitlerini daha hızlı tüketir. Özellikle küçük BBOX’larda
  5–15 dakikalık aralıklar makul, büyük BBOX’larda süreyi artırmanız önerilir.


  ## 6. VERİTABANI YÖNETİMİ VE BAKIMI

  Bu bölümde üç veritabanının (Neo4j, ArangoDB, TigerGraph) durumunu nasıl kontrol edeceğinizi,
  gerektiğinde veriyi nasıl temizleyeceğinizi ve basit yedekleme/geri yükleme işlemlerini nasıl
  yapabileceğinizi özetliyoruz.

  ### 6.1. Durum Kontrolü

  Amaç: “Veriler gerçekten yüklendi mi, kaç node/edge var, veritabanı ayakta mı?” sorularına hızlı
  cevap alabilmek.

  #### 6.1.1. Neo4j Durum Kontrolü

  1. Sunucunun çalıştığını kontrol et:
  
          a. Neo4j Desktop’ı aç.
          b. traffic-db için Status ışığı yeşil olmalı (Start butonu yerine Stop gösteriyorsa çalışıyor
               demektir).
  2. Query sekmesinde temel sayımları al:
          Komut satırına aşağıdaki sorguları sırayla yazıp Enter’a bas:

               MATCH (s:Segment) RETURN count(s) AS segment_sayisi;
               MATCH (m:Measure) RETURN count(m) AS measure_sayisi;
               MATCH ()-[r:CONNECTS_TO]->() RETURN count(r) AS edge_sayisi;
          Bu değerler sıfırdan büyükse, pipeline Neo4j’e başarıyla veri yazmış demektir.

  #### 6.1.2. ArangoDB Durum Kontrolü

  1. Container çalışıyor mu?:

          docker ps
  Çıktıda arangodb/enterprise:3.12.6.1 içeren satırın STATUS kısmında Up yazmalı.

  2. Web arayüzüne gir:
  
          a. **Tarayıcıda:** [http://localhost:8529](http://localhost:8529)
          b. **Kullanıcı adı:** root
          c. **Şifre** : ARANGO_ROOT_PASSWORD’da verdiğin değer (ör. test veya kendi güçlü
               şifren).
  3. traffic_db seçili mi?:
          Üst menüden aktif veritabanını traffic_db olarak seç.
  4. Koleksiyon sayımlarını al:

          a. Soldan Queries bölümüne gir.
          b. Yeni bir AQL sorgusu oluştur ve şu komutları çalıştır:



  FOR s IN segments COLLECT WITH COUNT INTO c RETURN c

  FOR m IN measures COLLECT WITH COUNT INTO c RETURN c

  FOR e IN connects_to COLLECT WITH COUNT INTO c RETURN c
  #### 6.1.3. TigerGraph Durum Kontrolü

  1. Container çalışıyor mu?:

          docker ps
  Çıktıda tigergraph-dev:4.1.0 satırı Up olmalı.
  2. Servisler gerçekten ayakta mı?:

          docker exec -it tigergraph bash
          gadmin status
  Çıktıda ADMIN, RESTPP, GSE, GPE, GUI vb. servisler için Online görünmeli.
  Sonra exit yazarak container içinden çık.
  3. GraphStudio’dan vertex/edge sayıları:

          a. Tarayıcıda: [http://localhost:14240](http://localhost:14240)
          b. Kullanıcı: tigergraph / Şifre: tigergraph (değiştirmediysen)
          c. Sol üstten TrafficGraph graf’ını seç.
          d. “Graph Overview” panelinde vertex ve edge sayıları özet olarak görünür.
               (Segment, Measure ve CONNECTS_TO edge’leri burada listelenmelidir.)

  ### 6.2. Veri Temizleme

  Bazen pipeline’ı yeniden denemek, farklı BBOX’la çalışmak veya veritabanını tamamen sıfırlamak
  isteyebilirsiniz. Bu bölüm, şema ve indeksleri bozmadan sadece veriyi temizlemek için kısa yollar
  içerir.

  **Dikkat:** Aşağıdaki temizleme komutları veriyi geri döndürülemez biçimde siler. Gerçek silme
  işleminden önce gerekliyse yedek almanız önerilir.
  tools/database/clean_all.py kodunu çalıştırın. Ardından terminalde silme işlemi için kullanıcı
  tarafından bir onay beklenecektir. Gerekli onay verildikten sonra tüm database’lerde temizlik işlemi
  başlayacaktır.


  ![](docs/images/image-23.png)
  Görsel 3.22
  ## 7. GÖRSELLEŞTİRME

  Bu bölümde, pipeline ile veritabanlarına yüklediğiniz verileri web tabanlı haritalar üzerinden nasıl
  görüntüleyeceğinizi anlatıyoruz.
  Haritalar, yol segmentlerini ve zaman serisi ölçümlerini renkli çizgiler/ikonlar olarak gösterir; böylece
  trafik yoğunluğunu, hızları ve topolojiyi görsel olarak inceleyebilirsiniz.

  **Not:** Viewer’ların düzgün çalışması için en az bir kere pipeline çalıştırmış olmanız ve ilgili
  veritabanlarında veri bulunması gerekir.

  ### 7.1. Web Viewer Kullanımı

  Projede her veritabanı için ayrı bir viewer script’i vardır:
  - neo4j_viewer.py → Neo4j için
  - arangodb_viewer.py → ArangoDB için
  - tigergraph_viewer.py → TigerGraph için
  - multi_db_viewer.py → Tüm databaseler için toplu
  Hepsi src/visualization klasörü altında bulunur ve küçük bir Flask sunucusu çalıştırarak, tarayıcıdan
  ulaşabileceğiniz bir web haritası üretir.

  #### 7.1.1. multi_db_viewer.py

  1. Viewer klasörüne geçin:
          cd src\visualization
  2. multi_db_viewer.py dosyasını çalıştırın.
          python neo4j_viewer.py


  ![](docs/images/image-24.png)
  Görsel 3.23
  ### 7.2. Harita Anlamlandırma

  Viewer’lar benzer bir görsel mantık kullanır. Haritayı yorumlarken şu noktaları bilmek önemli:

  **Yol segmentleri (Segment):**
  Yol kesimlerini temsil eden çizgiler. Genellikle:
  - Düşük jamFactor → **daha “serin” renkler** (yeşil / sarı tonlar)
  - Yüksek jamFactor → **daha “sıcak” renkler** (turuncu / kırmızı tonlar)
  
  **Yoğunluk (jamFactor):**
  HERE trafik verisinde **0–10** arası bir değerdir:
  - 0–3 → Akıcı trafik
  - 4–7 → Orta yoğunluk
  - 8–10 → Ciddi tıkanıklık / kuyruk

  **Popup / bilgi pencereleri:**
  Bir segmentin üzerine tıkladığınızda genellikle şu bilgiler gösterilir:
  - segmentId
  - Anlık hız (speed)
  - jamFactor
  - Ölçüm zamanı (timestamp)
  - İsteğe bağlı diğer alanlar (confidence, freeFlowSpeed vb.)


  ## 8. BENCHMARK & PERFORMANS

  Bu bölümde, üç veritabanı (Neo4j, ArangoDB, TigerGraph) üzerinde otomatik benchmark testlerini
  nasıl çalıştıracağınızı, üretilen sonuç dosyalarını nasıl okuyacağınızı ve bu sonuçlardan nasıl yorum
  çıkartabileceğinizi anlatıyoruz.
  Benchmark araçları, proje içinde şu klasörde yer alır:
  tools\benchmark\runner.py
  Bu script; okuma, yazma, traversal, toplulaştırma, uzamsal ve zamansal sorgular gibi farklı
  kategorilerde testler çalıştırır ve sonuçları hem okunabilir metin dosyası hem de tablo/grafik olarak
  raporlar.

  ### 8.1. Benchmark Çalıştırma

  #### 8.1.1. Önkoşullar

  Benchmark çalıştırmadan önce:
  - Pipeline en az bir kere çalışmış olmalı (veritabanlarında yeterli veri bulunmalı),
  - Üç veritabanı da çalışır durumda olmalı:
  Neo4j traffic-db → Neo4j Desktop’ta Start
    - ArangoDB → Docker container’ı Up ve traffic_db mevcut
    - TigerGraph → Docker container’ı Up, gadmin status servisler Online
  - .env dosyanızda bağlantı bilgileri doğru olmalı (NEO4J_*, ARANGO_*, TIGERGRAPH_*).

  #### 8.1.2. Profil Seçimi (quick / standard / ultimate)

  Benchmark script’i, süre ve detay seviyesi açısından üç farklı profil sunar:
  - quick
    - Kısa sürede (dakikalar içinde) kaba bir fikir edinmek için.
    - Daha az tekrar, daha az sorgu çeşidi.
  - standard
    - Günlük kullanım için önerilen profil.
    - Çeşitli okuma/yazma/traversal testleri, makul süre.
  - ultimate
    - En detaylı profil; yüksek tekrar sayıları, daha uzun çalışma süresi
    - Akademik çalışma veya rapor hazırlarken derin analiz için kullanılabilir.

  #### 8.1.3. Benchmark Komutlarının Çalıştırılması

  1. Benchmark klasörüne geçin.
          cd tools\benchmark


  2. İstediğiniz profille benchmark çalıştırın.

          a. Hızlı deneme (quick):
               python runner.py --profile quick
          b. Standart test:
               python runner.py --profile standard
          c. Derin test (ultimate):
               python runner.py --profile ultimate
          d. Eğer sadece belirli veritabanları üzerinde test yapmak isterseniz (örneğin sadece
               Neo4j + ArangoDB):
                      python runner.py --profile standard --databases neo4j,arangodb
  3. Terminalde, her test kategorisi için ilerleme mesajları görürsünüz:

          a. Running read tests for Neo4j...
          b. Running write tests for ArangoDB...
          c. Running traversal tests for TigerGraph...
          d. Saving results to outputs/benchmarks/...
  Tüm testler bittiğinde script, özet bir mesaj verir:
  Benchmark completed. Results saved under outputs/benchmarks/

  ### 8.2. Sonuçları Okuma

  Benchmark script’i sonuçları birden fazla formatta üretir. Varsayılan olarak hepsi şu klasörde toplanır:
  - outputs\benchmarks\
  Bu klasör içinde tipik olarak şu dosyaları görürsünüz:
  - benchmark_results_readable.txt
  - comprehensive_benchmark_results.json
  - benchmark_dashboard.html
  - paper_table_performance.csv
  - paper_table_performance.md
  - paper_table_performance.tex


  #### 8.2.1. Metin Raporu (benchmark_results_readable.txt)

  Bu dosya, “insan okunabilir” özet rapor niteliğindedir.
  İçerikte genelde:
  - Her veritabanı için ayrı başlıklar (Neo4j / ArangoDB / TigerGraph),
  - Okuma testleri (örneğin: “Random node read – ortalama süre (ms) / p95 (ms) / başarı oranı
  (%)”),
  - Yazma testleri (insert, batch insert),
  - Traversal testleri (örneğin belirli derinlikte graf gezintisi),
  - Uzamsal/zamansal sorgular (BBOX veya zaman aralığına göre filtreleme)
  yer alır.

  #### 8.2.3. HTML Dashboard (benchmark_dashboard.html)

  Bu dosya, sonuçları görsel grafikler halinde sunan bir mini dashboard’tur.
  Tarayıcıda açarak (çift tıklayarak) şu tür grafikleri görebilirsiniz:
  - Her test kategorisi için bar grafikleri (ör. ortalama sorgu süresi karşılaştırması),
  - Veritabanı bazında opsiyonel “heatmap” veya karşılaştırma tabloları,
  - Profil bazlı özetler.
  Bu dashboard, bir bakışta:
  - Hangi veritabanının hangi tür sorguda öne çıktığını,
  Ortalama süreler ile p95 (tail latency) arasında ne kadar fark olduğunu
  görmenizi sağlar.

  ### 8.3. Karşılaştırma Analizi

  Benchmark sonuçlarını okurken, sadece “kimin ortalaması daha düşük?” sorusuna bakmak çoğu
  zaman yeterli olmaz. Aşağıdaki prensipler daha sağlıklı bir yorum yapmanıza yardımcı olur.

  #### 8.3.1. Ortalama Süre vs. P95 (Tail Latency)

  - Ortalama süre (avg_ms)
    - Çoğu sorgu için tipik performansı gösterir.
    - Kullanıcı deneyimi açısından “genelde ne kadar hızlı?” sorusuna cevap verir.
  - P95 / P99
    - En yavaş %5 veya %1’lik kısmı temsil eder.
    - Sistem yük altındayken veya karmaşık sorgularda “en kötü durumlarda ne kadar
  yavaşlıyor?” sorusu için kritiktir.

  #### 8.3.2. Test Kategorileri Arasında Denge

  Her veritabanı her kategoride aynı derecede başarılı olmak zorunda değildir:

  **- Okuma (read) testleri:**
    - Endeks yapıları, cache ve sorgu optimizasyonundan çok etkilenir.
    - Neo4j gibi graph veritabanları, ID veya index üzerinden node/relationship okumada
  genelde güçlüdür.

  **- Yazma (write) testleri:**
    - Transaction yapısı, loglama ve disk I/O performansından etkilenir.
    - Büyük batch insert’lerde bazı sistemler öne çıkabilir.

  **- Traversal (komşuluk gezintisi):**
    - Asıl graph veritabanlarının fark yarattığı alan.
    - CONNECTS_TO gibi kenarlar üzerinden 1–3 hop’luk sorgularda hangi sistemin daha
  iyi olduğu özellikle GNN/GCN öncesi önemli.

  **- Uzamsal / Zamansal sorgular:**
    - BBOX, belirli zaman aralığı veya belli jamFactor filtreleri.
    - Index stratejiniz (lat/lon, timestamp index’leri) bu testlerde sonucu ciddi etkiler.


