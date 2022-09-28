<h1 align="center">KEPServerEX - Azure Bağlantısı</h1>

Aşağıdaki konfigürasyonlara başlamadan önce bazı ön gerekliliklerin tamamlanmış olması beklenmektedir. Bunlar;

* Kurulmuş ve verisi aktarılmak istenen cihazların tanımlandığı KEPServerEX yazılımı. Örnek proje olarak bu repository'nin içerisindeki .opf dosyası indirilip KEPServerEX'te açılarak içerisindeki hazır veriler kullanılabilir. 
* KEPServerEX - IoT Gateway eklentisi için Java'nın 32-bitlik versiyonunun kurulu olması gerekmektedir. [Buradan](https://javadl.oracle.com/webapps/download/AutoDL?BundleId=246806_424b9da4b48848379167015dcc250d8d) doğrudan indirilebilir.
* Azure Portal hesabı. [Buradan](https://azure.microsoft.com/tr-tr/get-started/azure-portal/) yeni hesap açabilirsiniz. Yeni açılan hesaplarda 200USD bakiye tanımlanıyor.
* Azure IoT Hub kurulumu. (Madde 1'den 16'ya)

# Azure IoT Hub Kurulumu

1) Azure Portal hesabınıza giriş yapın.
2) Giriş yaptıktan sonra karşınıza gelen + işaretine tıklayıp arama kısmında IoT Hub yazarak arama yapın.
<img src="https://user-images.githubusercontent.com/76865995/192784263-e8e4205b-6c87-4d1b-8b33-ef3bc13d837f.png" width=50% height=50%>
![ss1](https://user-images.githubusercontent.com/76865995/192784263-e8e4205b-6c87-4d1b-8b33-ef3bc13d837f.png)
3) IoT Hub sayfasına geldikten sonra "Create" diyerek kuruluma başlayın.
![ss2](https://user-images.githubusercontent.com/76865995/192785275-f9441974-a55f-4264-93b1-9baa53354072.png)
4) Karşınıza gelen sayfada eğer bir Resource Group oluşturmadıysanız "Create New" seçeneği ile hızlıca bir isim vererek oluşturun.
5) IoT Hub Name kısmına belirlediğiniz bir ismi yazıp diğer kısımları olduğu gibi bırakarak bir sonraki sayfaya geçin.
![ss3](https://user-images.githubusercontent.com/76865995/192785616-01f88fed-144b-4c22-9c5b-99020accf7c8.png)
6) Network kısmında ise demo ortamında çalışacağımız için Public Access seçeneğini seçerek bir sonraki sayfaya geçin. 
![ss4](https://user-images.githubusercontent.com/76865995/192786528-e881277b-c1b1-4d44-8111-203a5e53a4cd.png)
7) Management kısmında ise Defender for IoT özelliğine ihtiyacımız olmadığı için bu seçeneği kapatın. Role-based access control kısmında ise "Shared access policy + RBAC" seçeneğini seçin. Ek olarak "Assign me to the IoT Hub Data Contributor role" seçenğeni aktif ederek bir sonraki sayfaya geçin.

![ss5](https://user-images.githubusercontent.com/76865995/192786466-b7477186-41e8-4afb-9ae9-47b9c8414ae9.png) 
![ss6](https://user-images.githubusercontent.com/76865995/192786475-c6acefad-2d80-4928-bcc8-03aec99e96a1.png)

8) En son karşınıza bir özet sayfası geliyor. Ayarları kontrol ettikten sonra sayfanın altındaki Create seçeneğine tıklayarak IoT Hub'ınızın kurulumunu tamamlayın.

![ss7](https://user-images.githubusercontent.com/76865995/192789742-2316aa01-943a-4b28-a4be-52912decb2f9.png)

9) IoT Hub kurulumu tamamlandıktan sonra sayfanın altında bulunan "Go to resource" butonuna tıklayarak detay sayfasına gidin.
![ss8](https://user-images.githubusercontent.com/76865995/192790505-3f417043-4c99-43d1-b2a1-95b88f18fb2e.png)

10) Detay sayfasında yazan Hostname bilgisini not alın. Benim örneğimde hostname:
```
KepwareDemoHub.azure-devices.net
```
![ss9](https://user-images.githubusercontent.com/76865995/192791272-4708a3e4-ac90-4f94-ae4c-f43548096fee.png)






```
docker run -d --name=grafana -p 3000:3000 grafana
```
