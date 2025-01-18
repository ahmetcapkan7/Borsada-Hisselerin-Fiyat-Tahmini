Derin Öğrenme İle Hisselerin Fiyat Tahmini 

Öz 

Bu proje , hisselerin kapanış fiyatlarını tahmin etmek amacıyla bir derin öğrenme modeli geliştirmeyi hedeflemektedir. Model olarak zaman serisi analizi için  uygun olan LSTM(Long Short-Term Memory) mimarisi kullanılmıştır. Proje kapsamında , 2005-2023 yılları arasında Apple Şirketine ait finansal veriler üzerine çalışılmış ve modelin performansı çeşitli  metriklerle değerlendirilmiştir. Çıkan sonuçları ile umut verici bir sonuç elde edilmiştir. Böylelikle insanların kendini sosyal medya üzerinden “trader” olarak tanıtan ve teknik analiz adı altında onlara güvenmesine gerek kalmamıştır. Böylelikle insanların dolandırılmama konusunda önemli bir yol katedilmiştir.  

Giriş 

Borsa finansal piyasaların en hareketli alanlarından biridir. İnsanlar büyük umutlar ile girdikleri bu sisteme aniden iflas ile sonuçlanabilmektedir. Bunun en önemli sebebi kendini “trader” olarak tanıtan teknik analizi iyi biliyorum diyerek insanların güvenini kazanan dolandırıcılardır. Bu projemizde geçmiş zamanlara göre hareketlere dayanarak gelecek zamandaki hareketleri tahmin edebilen bir derin öğrenme projesi geliştirdik. 

Yöntem  

LSTM(Long Short-Term Memory) modeli kullanarak zaman serisi analizi yaparak gelecekteki fiyatları tahmin etmek. LSTM modelini kullanmamızın sebebi zaman serisi analizi için en uygun model olmasıdır. RNN mimarilerinin bir alt türüdür RNN’lerin uzun süreli zorluklarını(azalan gradyan problemi) sorununun üstesinden gelebildiği için bunu kullanmam bir nedenidir. Veri setim çok büyük olmamasından dolayı eğitim sürecinde bir dezavataj yaşamadım. 

Veri Seti 

Veri seti olarak Yahoo Finance Kütüphanesini kullandım.  

Özellikleri: 

-İstediğimiz veriyi çekmek istediğimizde çekebilmemiz. 

-Verilerin kapanış özelliklerini alabilmemizdeki kolaylık sağlaması. 

- Eksik veriler kontrol edildi gerekirse kaldırılmıştır. 

Örnek veri seti olarak Apple hissesi alınmıştır.  

Sebebi: 

-Bilindik bir hisse olması sebebiyle borsa manipülasyonunun az olması. 

-Veri çokluğu.(Borsaya açılan ilk hisselerden biri olması.) 

 

 

Şekil1.Veri Seti(Apple Kapanış Fiyatları) 

	 

Veri Önişleme: 

1.Veri Temizleme: Eksik veriler kontrol edilmiş ve temizlenmiştir. 

2.Normalize Etme: Veriler minmaxScaler kullanılarak 0 ile 1 arasında ölçeklendirilmiştir. 

3.Eğitim ve Test Verilerini Ayırma: Verilerin %80’i eğitim , %20’si test veri seti olarak kullanılmıştır. Test veri setine son 60 gün eklenmiştir. 

4.Zaman Penceresi Oluşturma: 60 günlük kapanış fiyatları kullanarak bir sonraki gün tahmini hedeflenmiştir. 

 

Model Mimarisinin Detayları: 

Model Türü:LSTM tabanlı Sequental. 

Optimizasyon Algoritması:Adam Optimizasyon Algoritması kullanıldı. 

Kayıp Fonksiyonu: Ortalama Kare Hatası(MSE) regresyon için seçildi. 

Eğitim: 

Batch Size:32  

Epoch:15  verildi. 

 

 

 

Sonuçlar  

				 

Şekil.2 Model Tahmin Sonuçları 

 

Şekil-3 Model Performans Sonuçları 

 

-Model , son 60 verilerini kullanarak 1 ay sonraki fiyatı tahmin edebiliyor. 

-Tahmin etmek istenilen her Yahoo Finance’deki hisseleri tahmin edebiliyor. 

-Tahmin edilen fiyat (1 ay sonraki): 116.57 

 -Performans ve Metrikler: 

Ortalama Kare Hatası(MSE).:153.70 	 

Kök Ortalama Kare Hatası(RMSE):12.40 

Ortalama Mutlak Hata(MAE):10.92 

R² Skoru:0.90 

 

Araştırma genel bulguları itibari ile umut verici bir sonuç elde edildi. Buradan çıkarılan sonuç ile borsada işlem yapan yatırımcılar dolandırıcılara inanmadan kendi başlarına işlem yapabilir. 

Kaynakça: 

[1]Şişmanoğlu, G., Koçer, F., Önde, M. A., & Sahingoz, O. K. (2020). Derin öğrenme yöntemleri ile borsada fiyat tahmini. Bitlis Eren Üniversitesi Fen Bilimleri Dergisi, 9(1), 434-445. 

[2] Dalkıran, İ., & Ozan, M. (2022). Derin Öğrenme Teknikleri Kullanılarak Borsadaki Hisse Değerlerinin Tahmin Edilmesi. Avrupa Bilim ve Teknoloji Dergisi, (39), 143-148. 

[3] Öztürk, C., & Karacı, A. (2024). Derin Öğrenme Yöntemleri Kullanılarak Hisse Senedi Fiyat Tahmini Üzerine Ampirik Bir Analiz: LSTM, GRU, GAN ve WGAN-GP. Gazi Journal of Engineering Sciences, 10(3), 472-495. 

[4] Tokmak, M. (2022). Uzun-Kısa süreli bellek ağı kullanarak hisse senedi fiyatı tahmini. Mehmet Akif Ersoy Üniversitesi Uygulamalı Bilimler Dergisi, 6(2), 309-322. 

[5] Alpay, Ö. (2020). LSTM mimarisi kullanarak USD/TRY fiyat tahmini. Avrupa Bilim ve Teknoloji Dergisi, 452- 456. 

 

CV 

İsmim Ahmet Çapkan,İstanbul Topkapı Üniversitesinde Yazılım Mühendisliği 3.Sınıf öğrencisiyim. Web geliştirme ve yapay zekaya ilgim var.Şu ana kadar Udemy üzerinden ve btk akademi üzerinden bir çok web back-end ve asp.net geliştirme kursu aldım.Ayrıca B1 seviye ingilizceye sahibim.İleride back-end geliştirici olmayı hedefliyorum.Birçok web geliştirme projesi yaptım.Yapay zeka alanında deepfake video tespiti projesinde görev aldım.Derin öğrenme yöntemleri ile borsada hisselerin fiyat analizi projesi yaptım. Her alanda bilgim var ama back-end alanında uzmanım ,  kendini geliştiren öğrenmeye aç genç bir mühendislik öğrencisiyim. 

 
