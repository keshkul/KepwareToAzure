<h1 align="center">Kepware - Azure Bağlantısı</h1>

Not: Aşağıdaki konfigürasyonlar Windows üzerinde çalıştırmak içindir. 

https://javadl.oracle.com/webapps/download/AutoDL?BundleId=246806_424b9da4b48848379167015dcc250d8d




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
