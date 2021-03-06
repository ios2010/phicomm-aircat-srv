# Phicomm-aircat-srv

A Server serv at port 9000 for phicomm wukong m1 aircat, after you hijack DNS aircat.phicomm.com for your phicomm m1.

## Configuration

```json
{
    "ServerAddr": ":9000",
    "RESTServerAddr": "localhost:8080",
    "InfluxdbServer": "localhost:8086"
}
```

* *RESTServerAddr* serv at this address for changing brightness
* *InfluxdbServer* write data into influxdb(db=aircat),  
  phicomm-aircat-srv write data in console ,as if deleting this line if you dont use influxdb

## Usage

### Basic Usage

* Change brightness  
you can change brightness for (0,25,50,100)

```shell
curl -XPUT http://localhost:8080/v1/aircat  --data  "{\"brightness\":\"100\",\"type\":2}"
```

* Query latest air measurement

```shell
curl http://localhost:8080/v1/aircat
```

* Control device to report current air measurement

```shell
curl -XPUT http://localhost:8080/v1/aircat  --data  "{\"type\":5,\"status\":1}"
```

### Run in docker

```shell
cd docker
docker-compose up -d
```

login in your grafana web at <http://localhost:3000> with (admin/admin), enjoy it.  

![screen](docs/picture/screen-1.jpg)

## Compile&Run on router

You can run *phicomm-aircat-srv* in router(ex. Phicomm k2p),too.

```shell
GOOS=linux GOARCH=mipsle go build github.com/corbamico/phicomm-aircat-srv/aircat-srv
```

## Reference

![arch](docs/picture/programme.png)

## Todo

* [x] Serv at 9000
* [x] REST Serv for changing brightness
* [x] Output to influxDB
* [x] docker-compose.yaml for influxDB/grafana
* [x] default dashboard for grafana docker
* [ ] support more than one device
* [x] version aircat-srv-rs: rust-lang version
* [x] version aircat-srv-cs: dotnet core 3.1 version
* [x] version aircat-srv-client: simulate aircat device, sending packet
