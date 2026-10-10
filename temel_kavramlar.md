print("Arac Kiralama Sistemi")

# 1. Veri Yapıları
arac_fiyatlari = {
    "ekonomi": 1200,
    "suv": 2000,
    "premium": 3500
}

gecerliAraclar = ["ekonomi", "suv", "premium"]
promosyon_kodlari = {"YAZ2026", "YENI MUSTERI"}

# 2.kullanıcı bilgileri
ad_soyad = input("Ad Soyad: ")
yas = int(input("Yaşınız: "))
ehliyet_yili = int(input("Mevcut ehliyet süresi: "))
arac_tipi = input("Araç tipi (ekonomi/suv/premium): ").lower()
promosyon_kodu = input("Promosyon kodunuz varsa girin yoksa boş bırakın: ").upper()
kiralama_gunu = int(input("Kaç gün kiralanacak?: "))
sigorta_secimi = input("Ek sigorta ister misiniz? (evet/hayır): ").lower()

# 3. Başlangıç Değerleri
kiralama_uygun = True
ret_nedeni = ""
arac_ucreti = 0
sure_indirimi = 0
genc_surucu_ucreti = 0
sigorta_ucreti = 0
promosyon_indirimi = 0
toplam = 0

# 4. Kontroller (İç İçe if - else Mantığı)
if arac_tipi not in gecerliAraclar:
    kiralama_uygun = False
    ret_nedeni = "Geçersiz araç tipi."
else:
    if yas < 21:
        kiralama_uygun = False
        ret_nedeni = "Araç kiralamak için en az 21 yaşında olmalısınız."
    else:
        if ehliyet_yili < 2:
            kiralama_uygun = False
            ret_nedeni = "En az 2 yıllık ehliyete sahip olmalısınız."
        else:
            if arac_tipi == "premium":
                if yas < 25 or ehliyet_yili < 3:
                    kiralama_uygun = False
                    ret_nedeni = (
                        "Premium araç için en az 25 yaşında "
                        "ve 3 yıllık ehliyete sahip olmalısınız."
                    )

# 5. Hesaplama ve Sonuçlar
if kiralama_uygun:
    gunluk_fiyat = arac_fiyatlari[arac_tipi]
    arac_ucreti = gunluk_fiyat * kiralama_gunu

    # Süre indirimi
    if kiralama_gunu >= 14:
        indirim_orani = 0.15
    elif kiralama_gunu >= 7:
        indirim_orani = 0.10
    elif kiralama_gunu >= 3:
        indirim_orani = 0.05
    else:
        indirim_orani = 0

    sure_indirimi = arac_ucreti * indirim_orani
    indirimli_arac_ucreti = arac_ucreti - sure_indirimi

    # Genç sürücü ek ücreti
    if 21 <= yas <= 24:
        genc_surucu_ucreti = kiralama_gunu * 250
    else:
        genc_surucu_ucreti = 0

    # Sigorta ücreti
    if sigorta_secimi == "evet":
        sigorta_ucreti = kiralama_gunu * 150
    else:
        sigorta_ucreti = 0

    # Ara toplam (Her iki sigorta durumunda da hesaplanması için dışarıda)
    ara_toplam = indirimli_arac_ucreti + genc_surucu_ucreti + sigorta_ucreti

    # Promosyon kontrolü
    if promosyon_kodu in promosyon_kodlari:
        promosyon_indirimi = ara_toplam * 0.05
    else:
        promosyon_indirimi = 0

    toplam = ara_toplam - promosyon_indirimi

# Bilgisayar Bilimleri Temel Kavramları
## 1. Giriş
Bilgisayar bilimleri (Computer Science), bilgisayarların çalışma prensiplerini, verilerin nasıl işlendiğini ve problemlerin bilgisayarlar aracılığıyla nasıl çözüldüğünü inceleyen bilim dalıdır. Bilgisayar sistemleri temel olarak donanım (Hardware) ve yazılım (Software) olmak üzere iki ana bölümde incelenir. Donanım bilgisayarın fiziksel parçalarını, yazılım ise bilgisayara belirli görevleri yaptıran programları ve komutları ifade eder. Bu iki bölüm, bilgisayarın doğru ve verimli çalışabilmesi için birlikte görev yapar.
## 2. Donanım (Hardware)
Donanım, bilgisayarın fiziksel olarak görülebilen ve dokunulabilen parçalarından oluşur. İşlemci, RAM, disk, ekran kartı ve anakart donanım bileşenlerine örnektir.
## CPU – İşlemci (Central Processing Unit):
CPU, bilgisayarın temel işlem birimidir. Programlardan gelen komutları işler ve matematiksel, mantıksal ve kontrol işlemlerini gerçekleştirir. İşlemcinin özellikleri bilgisayarın genel performansını etkiler.
## RAM – Geçici Bellek (Random Access Memory): 
RAM, bilgisayar çalışırken programların ve ihtiyaç duyulan verilerin geçici olarak saklandığı bellektir. İşlemcinin verilere hızlı erişmesini sağlar. RAM geçici bir bellek olduğu için bilgisayar kapatıldığında burada tutulan veriler silinir. RAM kapasitesi genellikle gigabyte (GB) ile ifade edilir.
## Disk ve Depolama (Storage):
Depolama birimleri, işletim sistemi, programlar, belgeler, fotoğraflar ve videolar gibi verilerin uzun süre saklanmasını sağlar. RAM'den farklı olarak bilgisayar kapatıldığında depolama birimindeki dosyalar korunur. SSD ve HDD, yaygın depolama birimleridir.
## SSD (Solid State Drive):
SSD, verileri elektronik bellek yongalarında saklayan bir depolama birimidir. Hareketli mekanik parçalar içermediğinden genellikle HDD'lerden daha hızlıdır. Bilgisayarın açılmasını ve programların yüklenmesini hızlandırabilir.
## HDD (Hard Disk Drive): 
HDD, verileri manyetik diskler üzerinde saklayan bir depolama birimidir. İçerisinde hareketli mekanik parçalar bulunur. Genellikle yüksek depolama kapasitesini daha düşük maliyetle sunabilmesi nedeniyle tercih edilir.
## GPU – Grafik İşlemci (Graphics Processing Unit): 
GPU, grafik işlemlerini ve çok sayıda paralel hesaplamayı gerçekleştirmek için tasarlanmıştır. Bilgisayar oyunları, grafik tasarım, video işleme ve yapay zekâ uygulamalarında önemli bir rol oynar.
## Anakart (Motherboard):
Anakart, bilgisayarın temel donanım bileşenlerini birbirine bağlayan ana devre kartıdır. İşlemci, RAM, depolama birimleri ve diğer bileşenler arasındaki iletişimi sağlar.
Girdi ve Çıktı Birimleri (Input and Output Devices): Girdi birimleri, kullanıcının bilgisayara veri veya komut göndermesini sağlar. Klavye, fare ve mikrofon bu gruba örnektir. Çıktı birimleri ise bilgisayarın ürettiği sonuçları kullanıcıya aktarır. Monitör, hoparlör ve yazıcı çıktı birimlerine örnektir.
## 3. Yazılım (Software)
Yazılım, bilgisayara hangi işlemleri yapacağını bildiren programlar, komutlar ve ilgili verilerden oluşur. Yazılım, bilgisayarın fiziksel bir parçası değildir. İşletim sistemleri, uygulamalar ve programlama ile oluşturulan yazılımlar bu gruba girer.
## İşletim Sistemi (Operating System): 
İşletim sistemi, bilgisayarın donanım ve yazılım kaynaklarını yöneten temel sistem yazılımıdır. Windows, macOS ve Linux işletim sistemlerine örnektir. İşletim sistemi işlemciyi, belleği ve dosyaları yönetir; kullanıcı ile bilgisayar arasındaki etkileşimi sağlar.
## Programlama (Programming):
Programlama, bilgisayara belirli görevleri yaptırmak amacıyla komutlar yazma sürecidir. C, C++, Java ve Python yaygın programlama dillerindendir. Programlama sayesinde problemler bilgisayarın uygulayabileceği adımlara dönüştürülür.
## Algoritma (Algorithm): 
Algoritma, belirli bir problemi çözmek veya görevi gerçekleştirmek için izlenen sıralı ve sonlu adımlar bütünüdür. Örneğin iki sayıyı toplamak için sayıları almak, toplamak ve sonucu göstermek bir algoritmadır.
## Veri (Data): 
Veri, bilgisayar tarafından işlenebilen ham değerlerdir. Sayılar, metinler, resimler, sesler ve videolar veri olarak kabul edilir.
## Bilgi (Information):
Bilgi, işlenmiş ve anlamlı hâle getirilmiş veridir. Örneğin öğrencilerin sınav notları veridir; bu notların ortalamasının hesaplanmasıyla elde edilen sonuç ise bilgidir.
## Değişken (Variable):
Değişken, program içerisinde veri saklamak için kullanılan ve bir isme sahip olan alandır. Örneğin bir öğrencinin notunu saklamak için grade isimli bir değişken kullanılabilir. Değişkenin değeri program çalışırken değişebilir.
## Veri Tipi (Data Type):
Veri tipi, bir verinin türünü belirler. Integer tam sayıları, float ondalıklı sayıları, char tek bir karakteri, string metinleri ve boolean doğru veya yanlış değerlerini ifade etmek için kullanılır.
## Koşul Yapıları (Conditional Statements):
Koşul yapıları, programın belirli şartlara göre farklı işlemler yapmasını sağlar. if-else yapısı buna örnektir. Örneğin bir öğrencinin notunun 50 veya daha yüksek olup olmadığı kontrol edilerek başarılı veya başarısız sonucu üretilebilir.
## Döngüler (Loops):
Döngüler, bir kod bloğunun belirli bir koşula bağlı olarak tekrar tekrar çalıştırılmasını sağlar. for ve while yaygın döngü türleridir. Örneğin 1'den 100'e kadar sayıları ekrana yazdırmak için döngü kullanılabilir.
## Dizi (Array):
Dizi, birden fazla verinin belirli bir düzen içerisinde saklanmasını sağlayan veri yapısıdır. Örneğin bir sınıftaki öğrencilerin sınav notları tek bir dizi içerisinde tutulabilir.
## Fonksiyon (Function):
Fonksiyon, belirli bir görevi gerçekleştirmek için oluşturulan ve gerektiğinde tekrar kullanılabilen kod bloğudur. Fonksiyonlar kod tekrarını azaltır ve programın daha düzenli olmasını sağlar.
## Derleyici (Compiler):
Derleyici, programlama dilinde yazılmış kaynak kodu başka bir forma, genellikle makine koduna, dönüştüren yazılımdır. C ve C++ gibi dillerde derleyiciler programın çalıştırılabilir hâle getirilmesinde önemli rol oynar.
## Hata ve Hata Ayıklama (Bug and Debugging):
Programın yanlış veya beklenmeyen sonuçlar vermesine neden olan hatalara bug denir. Bu hataları bulma ve düzeltme işlemine debugging adı verilir. Hata ayıklama, yazılım geliştirme sürecinin önemli bir parçasıdır.
## Uygulama Yazılımı (Application Software):
Uygulama yazılımları, kullanıcıların belirli görevleri gerçekleştirmesi için geliştirilir. Web tarayıcıları, kelime işlemciler, fotoğraf düzenleme programları ve müzik uygulamaları bu gruba örnektir.
## 4. Donanım ve Yazılım Arasındaki İlişki
Donanım ve yazılım birbirini tamamlayan iki temel bilgisayar bileşenidir. Donanım fiziksel parçaları oluştururken yazılım bu parçaların hangi işlemleri yapacağını belirler. Örneğin bir program çalıştırıldığında programın dosyaları depolama biriminde bulunabilir. Program açıldığında gerekli veriler RAM'e yüklenir ve CPU komutları işler. Grafik işlemleri gerektiğinde GPU da bu işlemlere katkıda bulunur. İşletim sistemi ise donanım kaynaklarının programlar tarafından kullanılmasını yönetir.
Bu örnek, bilgisayarın çalışması için donanım ve yazılımın birlikte çalışması gerektiğini gösterir.
## 5. Sonuç
Bilgisayar bilimleri, donanım ve yazılımın birlikte çalışmasını sağlayan birçok temel kavramı kapsar. CPU, RAM, disk, SSD, HDD, GPU ve anakart gibi donanım bileşenleri bilgisayarın fiziksel yapısını oluşturur. İşletim sistemi, algoritma, programlama, değişken, veri tipi, koşul, döngü ve fonksiyon gibi yazılım kavramları ise bilgisayarların görevleri nasıl yerine getirdiğini açıklar.
Bu kavramların öğrenilmesi, bilgisayar sistemlerinin çalışma mantığını anlamak için önemli bir başlangıçtır. Ayrıca veri tabanları, bilgisayar ağları, yapay zekâ ve siber güvenlik gibi daha ileri bilgisayar bilimi alanlarının öğrenilmesine temel oluşturur.











Bu kişiliği beğeniyor musun?
