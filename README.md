# Beyin Tümörü Sınıflandırması

  Beyin tümörü, hücrelerin kontrol edilemeyen ve anormal şekilde bölünmesinden kaynaklanan ciddi bir kanser hastalığıdır. Yapılan çalışmada 3 farklı tümör tipi ve tümör bulunmayan sağlıklı bireylerin MRI görüntüleri kullanılmıştır. Derin Öğrenme alanında yapılan çalışmalar sonucunda görüntü işleme ve sağlıkta yapay zeka alanı çok fazla gelişim göstermiştir. Görsel öğrenme ve Görüntü Tanıma için  erişimli sinir ağları (CNN), en yaygın olarak kullanılan makine öğrenme algoritmasıdır. Yapılan çalışmada 2 farklı model kullanılmıştır ve karşılaştırma yapılmıştır. İlk modelde  CNN algoritmalarından VGG16 ile çalışılmıştır ve ikinci modelde CNN algoritması ile katmanlı bi model oluşturulmuştur. Eğitim aşamasında 4 farklı sınıf ve  5700’den fazla görüntü kullanılmıştır. VGG16 algoritmasının sonucunda %92’den fazla bir başarı oranı elde edilmiştir. CNN modelinde ise %95’ten fazla başarı elde edilmiştir. 

Anahtar Kelimeler : CNN, Derin Öğrenme, VGG16, Beyin Tümörü, MRI

<img width="688" alt="Ekran Resmi 2022-01-10 17 00 28" src="https://user-images.githubusercontent.com/48045619/148778245-21c12c7c-0c76-48d0-943b-04fa1e647364.png">

## VGG16 Modeli 

  Basit bir ağ modeli olup öncesindeki modellerden en önemli farkı evrişim katmalarının 2’li ya da 3’li kullanılmasıdır. Tam bağlantı (FC) katmanında 7x7x512=4096 nöronlu bir öznitelik vektörüne dönüştürülür[15]. İki FC katmanı çıkışında 1000 sınıflı softmax başarımı hesaplanır. Yaklaşık 138 milyon parametre hesabı yapılmaktadır. Diğer modellerde olduğu gibi girişten çıkışa doğru matrislerin yükseklik ve genişlik boyutları azalırken derinlik değeri (kanal sayısı) artmaktadır.

<img width="562" alt="Ekran Resmi 2022-01-10 16 58 46" src="https://user-images.githubusercontent.com/48045619/148778313-b0944936-4708-45cf-9646-077d44a3a714.png">

## CNN Modeli

  Çalışmada basit bir CNN modeli önerildi, RGB Renk kanallarına sahip 256 × 256 giriş boyutundaki artırılmış MRI görüntü verilerini CNN modeli aracılığıyla inceledik. İlk olarak, filtre boyutu 3 × 3 olan tek bir 64 filtre evrişim katmanı eklendi. Daha sonra 2 × 2 olarak bir MaxPooling2D katmanı eklendi. Aynı şekilde 32 filtreli bir erişim katmanı ve sonrasında yine 2 × 2 bir MaxPooling2D eklenmiştir. MaxPooling2D katmanlarının eklemesinin sebebi evrişimsel katmanlardan en iyi verimi alabilmektir. Son olarak, her sınıf için olasılık puanını hesaplayan ve giriş MRI görüntüsünün kanser içerdiğini veya kanser içermediğini, içeriyorsa hangi türde olduğunu  sınıflandıran softmax çıkış katmanıyla birlikte tam bağlı yoğun bir 64 Dense katmanı uygulandı. Alınan sonuçlar VGG16 modeli ile karşılaştırılıp ideal model seçimi yapıldı.
  
## Sonuçlar

  Kaggle’den alınan veri setinde, toplamda 7023 görüntü üzerinde imge sınıflandırma yapılarak işlem tamamlanmıştır. Bu imge işlemede iki farklı model oluşturulmuş ve sonuçları karşılaştırılmıştır. İlk modelde  farklı filtreleme sayısı ile 2 katman oluşturulmuştur. Bu katmanlardan alınan verimi arttırmak için oluşturulan katmanlardan sonra birer MaxPooling2D katmanı eklenmiştir. Son olarak sınıflandırma için olasılık hesaplayan tam bağlı bir Dense katmanı oluşturulmuştur. Verileri eğitim ve test olarak ayırdık. Modelimizin doğruluğunu değerlendirmek için eğitim için 5712 görüntü ve test için 1311 görüntü vardır. Modelleri, toplu iş boyutu 32 olan 15 dönem için eğittik. Deney, 16 Gb ram'li 2.3 GHz çekirdek i9 işlemciye sahip bir CPU üzerinde python'daki TensorFlow ve Keras kitaplıkları kullanılarak yapıldı. Önerilen 1.modelde,  10 Epoch’tan sonra eğitim verilerinde %96’ya kadar çıkan doğruluk gösterdi.
  
![image](https://user-images.githubusercontent.com/48045619/148780519-940ac6dc-90df-4563-88e0-70a9ae66adf0.png)
<img width="618" alt="Ekran Resmi 2022-01-10 17 16 22" src="https://user-images.githubusercontent.com/48045619/148780543-65c6e566-4386-4ac7-938e-29cd46112f7d.png">
