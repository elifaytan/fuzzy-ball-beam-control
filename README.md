# Fuzzy Ball-and-Beam Control

Bu proje, Ball-and-Beam sisteminin konum kontrolünü gerçekleştirmek amacıyla geliştirilen bulanık mantık tabanlı bir kontrol uygulamasıdır.

Projede 0. derece Sugeno bulanık çıkarım yöntemi kullanılmış, konum ve hız bilgilerine göre kontrol sinyali üretilmiş ve sistemin farklı bozucu etkiler altındaki davranışı simüle edilmiştir.

Ayrıca kontrolör parametrelerinin performansını artırmak amacıyla otomatik parametre ayarlama yaklaşımı uygulanmıştır.

## Projenin Amacı

Ball-and-Beam sistemi, bir topun hareketli bir kiriş üzerinde belirlenen hedef konuma getirilmesini amaçlayan klasik bir kontrol problemidir.

Bu projede topun konumu ve hızı giriş olarak alınarak kiriş açısının bulanık mantık ile belirlenmesi hedeflenmiştir.

Sistem üzerinde:

- Konum hatası
- Topun hızı
- Kiriş açısı
- Dış bozucu etkiler
- Ölçüm gürültüsü

gibi değişkenler dikkate alınmıştır.

## Kullanılan Yöntem

Projede 0. derece Sugeno tipi bulanık çıkarım sistemi kullanılmıştır.

Bulanık kontrolör iki temel giriş kullanmaktadır:

- Konum hatası
- Topun hızı

Kontrolör çıktısı ise kirişe uygulanacak kontrol sinyalidir.

## Üyelik Fonksiyonları

Konum hatası ve hız değişkenleri için üçgensel üyelik fonksiyonları kullanılmıştır.

Her giriş değişkeni farklı dilsel bölgelere ayrılmıştır.

Örneğin:

- Negatif
- Sıfır
- Pozitif

Bu üyelik fonksiyonları sayesinde sayısal giriş değerleri bulanık kümelere dönüştürülmektedir.

## Kural Tabanı

Projede 3x3 bulanık kural tabanı kullanılmıştır.

Konum hatası ve hız bilgisinin farklı kombinasyonlarına göre kontrol çıktısı belirlenmektedir.

Örnek olarak:

- Hata negatif ve hız negatif ise belirli bir kontrol değeri
- Hata sıfıra yakın ve hız sıfıra yakın ise düşük kontrol değeri
- Hata pozitif ve hız pozitif ise karşı yönde kontrol değeri

üretilmektedir.

Bu yapı toplam dokuz temel kontrol kuralından oluşmaktadır.

## Sugeno Bulanık Çıkarım

Projede 0. derece Sugeno yaklaşımı kullanılmaktadır.

Her bulanık kural sabit bir çıktı değerine sahiptir.

Aktif kuralların üyelik dereceleri hesaplandıktan sonra kontrol sinyali ağırlıklı ortalama yöntemiyle elde edilmektedir.

Genel çıktı:

    u = Sum(w_i * z_i) / Sum(w_i)

şeklinde hesaplanmaktadır.

Burada:

- `w_i` ilgili kuralın ateşleme derecesini
- `z_i` ilgili kuralın sabit çıktı değerini
- `u` ise kontrol sinyalini ifade etmektedir.

## Ball-and-Beam Simülasyonu

Kontrolörün performansı Ball-and-Beam sisteminin dinamik modeli üzerinde test edilmiştir.

Topun konumu ve hızı zaman içerisinde hesaplanarak sistem davranışı simüle edilmektedir.

Kontrolör topu hedef konuma yaklaştırmak için kiriş açısını sürekli olarak güncellemektedir.

## Sayısal Çözüm

Sistemin hareket denklemlerinin zaman içerisinde çözülmesi için sayısal integrasyon yöntemi kullanılmıştır.

Simülasyonda ikinci dereceden Runge-Kutta yaklaşımı olarak değerlendirilebilecek Heun yöntemi kullanılmaktadır.

Bu yöntem ile sistemin konum ve hız değerleri her zaman adımında güncellenmektedir.

## Bozucu Etkiler

Kontrol sisteminin yalnızca ideal ortamda değil, daha gerçekçi koşullarda da test edilmesi amacıyla farklı bozucu etkiler simüle edilmiştir.

### Ölçüm Gürültüsü

Sensörlerden gelen konum ve hız bilgilerinde oluşabilecek ölçüm hatalarını temsil etmek amacıyla sisteme gürültü eklenmiştir.

### Fiziksel Gürültü

Sistemin dinamiğini etkileyebilecek küçük rastgele fiziksel değişimler modellenmiştir.

### Darbe Bozucusu

Belirli bir anda topa dışarıdan kuvvet uygulanmış gibi sistemin hızında ani bir değişiklik oluşturulmuştur.

Bu senaryo kontrolörün bozucu etkiye karşı toparlanma davranışını incelemek için kullanılmıştır.

## Otomatik Parametre Ayarlama

Projede yalnızca elle belirlenen kontrol parametreleri kullanılmamış, kontrolör performansını artırmak amacıyla otomatik parametre arama yaklaşımı da uygulanmıştır.

Random Search yöntemi kullanılarak farklı kontrol parametreleri denenmiştir.

Her parametre seti simülasyon üzerinde test edilmiş ve performansı bir maliyet fonksiyonu ile değerlendirilmiştir.

Amaç, daha düşük hata ve daha kararlı sistem davranışı sağlayan parametrelerin bulunmasıdır.

## Performans Değerlendirmesi

Kontrolör performansı aşağıdaki kriterler kullanılarak değerlendirilebilir:

- Hedef konuma ulaşma
- Toplam konum hatası
- Yerleşme süresi
- Aşım miktarı
- Kontrol sinyalinin büyüklüğü
- Bozucu etkilerden sonra toparlanma
- Sistem kararlılığı

Manuel olarak ayarlanan kontrolör ile otomatik olarak ayarlanan kontrolörün sonuçları karşılaştırılabilir.

## Görselleştirme

Simülasyon sonuçlarının incelenmesi için Matplotlib kullanılmıştır.

Grafikler üzerinde:

- Topun konumu
- Hedef konum
- Topun hızı
- Kontrol sinyali
- Kiriş açısı

gibi değerler zaman içerisinde görüntülenebilmektedir.

Ayrıca sistem davranışını daha anlaşılır hale getirmek için Ball-and-Beam sisteminin interaktif animasyonu oluşturulmuştur.

## Kullanılan Teknolojiler

- Python
- Jupyter Notebook
- NumPy
- Matplotlib
- Fuzzy Logic
- Sugeno Fuzzy Inference
- Control Systems
- Numerical Simulation
- Random Search
- Heun Method

## Proje Dosyaları

- `Bulanık_Mantık_Kod.ipynb` — Bulanık kontrolör, Ball-and-Beam simülasyonu, parametre ayarlama ve görselleştirme kodlarının bulunduğu Jupyter Notebook
- `README.md` — Proje açıklamaları

## Çalıştırma

Projeyi çalıştırmak için Jupyter Notebook kullanılabilir.

`Bulanık_Mantık_Kod.ipynb` dosyasını açın ve hücreleri sırasıyla çalıştırın.

Gerekli Python kütüphaneleri:

    pip install numpy matplotlib

Notebook çalıştırıldığında Ball-and-Beam sisteminin simülasyonu gerçekleştirilir ve kontrol sonuçları grafikler üzerinde görüntülenir.

## Öğrenilen Kavramlar

Bu proje kapsamında aşağıdaki konular uygulamalı olarak kullanılmıştır:

- Bulanık Mantık
- Sugeno Bulanık Çıkarım
- Üyelik Fonksiyonları
- Bulanık Kural Tabanı
- Kontrol Sistemleri
- Ball-and-Beam Sistemi
- Sayısal Simülasyon
- Heun Yöntemi
- Gürültü Modelleme
- Bozucu Etki Analizi
- Random Search
- Parametre Optimizasyonu
- Veri Görselleştirme

## Projenin Amacı

Bu çalışma ile bulanık mantık tabanlı bir kontrolörün doğrusal olmayan bir kontrol problemi üzerinde uygulanması amaçlanmıştır.

Ball-and-Beam sisteminin konum kontrolü gerçekleştirilmiş, sistem farklı bozucu etkiler altında test edilmiş ve kontrol parametrelerinin otomatik olarak iyileştirilmesi için Random Search yaklaşımı kullanılmıştır.

## Proje Notu

Bu proje Bulanık Mantık dersi kapsamında geliştirilmiş akademik bir çalışmadır.
