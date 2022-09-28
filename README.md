<h1 align="center">KEPServerEX - Azure Bağlantısı</h1>

Aşağıdaki konfigürasyonlara başlamadan önce bazı ön gerekliliklerin tamamlanmış olması beklenmektedir. Bunlar;

* Kurulmuş ve verisi aktarılmak istenen cihazların tanımlandığı KEPServerEX yazılımı. Örnek proje olarak bu repository'nin içerisindeki .opf dosyası indirilip KEPServerEX'te açılarak içerisindeki hazır veriler kullanılabilir. 
* KEPServerEX - IoT Gateway eklentisi için Java'nın 32-bitlik versiyonunun kurulu olması gerekmektedir. [Buradan](https://javadl.oracle.com/webapps/download/AutoDL?BundleId=246806_424b9da4b48848379167015dcc250d8d) doğrudan indirilebilir.
* Azure Portal hesabı. [Buradan](https://azure.microsoft.com/tr-tr/get-started/azure-portal/) yeni hesap açabilirsiniz. Yeni açılan hesaplarda 200USD bakiye tanımlanıyor.
* Azure IoT Hub kurulumu. (Madde 1'den 16'ya)

# Azure IoT Hub Kurulumu

1) Azure Portal hesabınıza giriş yapın.
2) Giriş yaptıktan sonra karşınıza gelen + işaretine tıklayıp arama kısmında IoT Hub yazarak arama yapın.
![ss1](https://user-images.githubusercontent.com/76865995/192784263-e8e4205b-6c87-4d1b-8b33-ef3bc13d837f.png)
3) IoT Hub sayfasına geldikten sonra "Create" diyerek kuruluma başlayın.
![ss2](https://user-images.githubusercontent.com/76865995/192785275-f9441974-a55f-4264-93b1-9baa53354072.png)
4) Karşınıza gelen sayfada eğer bir Resource Group oluşturmadıysanız "Create New" seçeneği ile hızlıca bir isim vererek oluşturun.
5) IoT Hub Name kısmına belirlediğiniz bir ismi yazıp diğer kısımları olduğu gibi bırakarak bir sonraki sayfaya geçin.
![ss3](https://user-images.githubusercontent.com/76865995/192785616-01f88fed-144b-4c22-9c5b-99020accf7c8.png)
6) Network kısmında ise demo ortamında çalışacağımız için Public Access seçeneğini seçerek bir sonraki sayfaya geçin. 

7)  


```
docker pull influxdb:latest
```

```
docker pull telegraf:latest
```

```
docker pull grafana:latest
```

```
docker run -d --name=influxdb -p 8086:8086 influxdb
```

```
docker run -d --name=grafana -p 3000:3000 grafana
```
