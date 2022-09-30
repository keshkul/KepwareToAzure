<h1 align="center">KEPServerEX - Azure Bağlantısı</h1>

Aşağıdaki konfigürasyonlara başlamadan önce bazı ön gerekliliklerin tamamlanmış olması beklenmektedir. Bunlar;

* Kurulmuş ve verisi aktarılmak istenen cihazların tanımlandığı KEPServerEX yazılımı. Örnek proje olarak bu repository'nin içerisindeki .opf dosyası indirilip KEPServerEX'te açılarak içerisindeki hazır veriler kullanılabilir. 
* KEPServerEX - IoT Gateway eklentisi için Java'nın 32-bitlik versiyonunun kurulu olması gerekmektedir. [Buradan](https://javadl.oracle.com/webapps/download/AutoDL?BundleId=246806_424b9da4b48848379167015dcc250d8d) doğrudan indirilebilir.
* Azure Portal hesabı. [Buradan](https://azure.microsoft.com/tr-tr/get-started/azure-portal/) yeni hesap açabilirsiniz. Yeni açılan hesaplarda 200USD bakiye tanımlanıyor.
* Azure IoT Hub kurulumu. (Madde 1'den 16'ya)

# Azure IoT Hub Kurulumu

1) Azure Portal hesabınıza giriş yapın.
2) Giriş yaptıktan sonra karşınıza gelen + işaretine tıklayıp arama kısmında IoT Hub yazarak arama yapın.
<img src="https://user-images.githubusercontent.com/76865995/192784263-e8e4205b-6c87-4d1b-8b33-ef3bc13d837f.png" width=65% height=65%>

3) IoT Hub sayfasına geldikten sonra "Create" diyerek kuruluma başlayın.
<img src="https://user-images.githubusercontent.com/76865995/192785275-f9441974-a55f-4264-93b1-9baa53354072.png" width=65% height=65%>

4) Karşınıza gelen sayfada eğer bir Resource Group oluşturmadıysanız "Create New" seçeneği ile hızlıca bir isim vererek oluşturun.
5) IoT Hub Name kısmına belirlediğiniz bir ismi yazıp diğer kısımları olduğu gibi bırakarak bir sonraki sayfaya geçin.
<img src="https://user-images.githubusercontent.com/76865995/192785616-01f88fed-144b-4c22-9c5b-99020accf7c8.png" width=65% height=65%>

6) Network kısmında ise demo ortamında çalışacağımız için Public Access seçeneğini seçerek bir sonraki sayfaya geçin. 
<img src="https://user-images.githubusercontent.com/76865995/192786528-e881277b-c1b1-4d44-8111-203a5e53a4cd.png" width=65% height=65%>

7) Management kısmında ise Defender for IoT özelliğine ihtiyacımız olmadığı için bu seçeneği kapatın. Role-based access control kısmında ise "Shared access policy + RBAC" seçeneğini seçin. Ek olarak "Assign me to the IoT Hub Data Contributor role" seçeneğini aktif ederek bir sonraki sayfaya geçin.

<img src="https://user-images.githubusercontent.com/76865995/192799282-ed3a4fda-fc8a-463f-9ae5-9fa349194e5b.png" width=49% /> <img src="https://user-images.githubusercontent.com/76865995/192786475-c6acefad-2d80-4928-bcc8-03aec99e96a1.png" width=50% />

8) En son karşınıza bir özet sayfası geliyor. Ayarları kontrol ettikten sonra sayfanın altındaki Create seçeneğine tıklayarak IoT Hub'ınızın kurulumunu tamamlayın.
<img src="https://user-images.githubusercontent.com/76865995/192789742-2316aa01-943a-4b28-a4be-52912decb2f9.png" width=45% height=45%>

9) IoT Hub kurulumu tamamlandıktan sonra sayfanın altında bulunan "Go to resource" butonuna tıklayarak detay sayfasına gidin.
<img src="https://user-images.githubusercontent.com/76865995/192790505-3f417043-4c99-43d1-b2a1-95b88f18fb2e.png" width=65% height=65%>

10) Detay sayfasında yazan Hostname bilgisini not alın. Benim örneğimde hostname:
```
KepwareDemoHub.azure-devices.net
```
<img src="https://user-images.githubusercontent.com/76865995/192791272-4708a3e4-ac90-4f94-ae4c-f43548096fee.png" width=75% height=75%>

11) Sayfanın solundaki listeden "Shared access policies" kısmına tıklayıp gelen sayfada Add diyerek devam edin.
<img src="https://user-images.githubusercontent.com/76865995/192812073-a8667b73-f317-4bc0-9aea-5696078db2c0.png" width=65% height=65%>

12) Yeni policy için bir isim girin ve demo yapılacağı için bütün izinleri verip Add butonuna tıklayarak policy ekleyin.
<img src="https://user-images.githubusercontent.com/76865995/192812290-91c9a45f-b7b1-4ac8-9420-ca80ce8e7961.png" width=65% height=65%>

13) Listede yeni eklediğiniz policy'yi görebilirsiniz. Eklediğiniz policy'nin üstüne tıklayarak devam edin ve "Primary connection string" kısmını kopyalayarak not edin. Kopyaladığınız string aşağıdaki gibi olmalıdır:
```
HostName=KepwareDemoHub.azure-devices.net;SharedAccessKeyName=KepwareDemo;SharedAccessKey=1DSozN0+9iIHnNMDswdxdnC3VINbKqlI/OJs8iv5hi8=
```
Artık IoT Hub'a bağlanmaya ve yeni sanal cihazlar oluşturmaya hazırız.

14) Bu sayfanın yukarısında bulunan listeden "SetupDeviceExplorer.msi" adlı dosyayı indirin ve kurun. Bu dosyaya ayrıca [Azure Github](https://azure.microsoft.com/tr-tr/get-started/azure-portal/) sayfasında biraz aşağı kısımlarda da ulaşabilirsiniz.
15) Kurduğunuz "Device Explorer" programını çalıştırın. Daha önce not ettiğiniz bilgileri burada kullanacaksınız. "Primary connection string" bilginizi IoT Hub Connection String kısmına, hostname bilginizi de Protocol Gateway HostName kısmına girip "Update" butonuna basın. Azure IoT Hub'ınıza bağlantı sağlandı. 
<img src="https://user-images.githubusercontent.com/76865995/193204395-d9357f0e-0641-40ca-a779-ecf0d2b11fed.png" width=65% height=65%>

16) Bağlantı sağlandıktan sonra Device Explorer üzerinden IoT Hub'ınızda yeni sanal cihazlar oluşturabilirsiniz. Bundan sonra Azure IoT Hub'a Kepware'den MQTT ve REST protokolleri üzerinden veri gönderimi gerçekleştireceğiz. Demomuzda iki protokol için iki ayrı sanal cihaz oluşturacağız.

# Kepware - MQTT 

17) Device Explorer'da Management sekmesinin altındaki Create butonuna tıklayarak Kepware'den MQTT ile veri aktarabilmek için yeni bir cihaz oluşturun. Gelen ekranda Device ID kısmına bir isim girerek Create diyin.   
<img src="https://user-images.githubusercontent.com/76865995/193208579-32023bc6-049a-40ae-85a8-9df0022ad09d.png" width=49% height=65%> <img src="https://user-images.githubusercontent.com/76865995/193209226-15b829ce-e0d2-4ec6-bb13-90cae1973dac.png" width=50% height=50%>

18) Yeni oluşturduğunuz cihazı seçip "SAS Token..." butonuna tıklayın. Gelen ekranda Device ID kısmından token üretmek istediğiniz cihazı seçin. TTL (Days) kısmına tokenın geçerli olacağı süreyi gün olarak belirtin ve "Generate" diyin. Oluşturulan tokenın aşağıdaki ekran görüntüsündeki gibi seçili olan kısmını kopyalayıp not edin. Generate dedikten sonra gelen bütün stringi kopyalamayın, kopyaladığınız kısım aşağıdaki gibi olmalıdır:
```
SharedAccessSignature sr=KepwareDemoHub.azure-devices.net%2Fdevices%2FAzureMQTT&sig=U%2Bz7ex8OgJvGW3Stp4ZhfwXQShppHoFkcsMZTWyJkKE%3D&se=1696063201
```
<p align="center">
  <img src="https://user-images.githubusercontent.com/76865995/193232202-b02c71f5-b887-4120-a62b-c8eb8ad421ca.png" width=50% height=50% >
</p>
