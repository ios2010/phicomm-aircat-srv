# MISC

* buildpack-deps.dockerfile gcc env for build phicomm-k2p programme

* influxdb docker  
  docker run --name=influxdb -d -p 8086:8086 -e INFLUXDB_DB=aricat influxdb

* grafana docker  
  docker run -d --name=grafana -p 3000:3000 grafana/grafanaexp

* change brightness  
  curl -i -XPUT http://localhost:8080/v1/aircat  --data  "{\"brightness\":\"100\",\"type\":2}"