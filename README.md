LOKI setup from docker

loki
```
docker run -d --name loki -v $(pwd):/mnt/config -p 3100:3100 grafana/loki:2.2.1 -config.file=/mnt/config/loki-config.yaml
```

promtail
```
docker run -d --name promtail --link loki -v $(pwd):/mnt/config -v /var/log:/var/log grafana/promtail:2.2.1 -config.file=/mnt/config/promtail-config.yaml
```

grafana
```
docker run -d --name grafana --link loki -p 3000:3000 -v grafana_config:/etc/grafana -v grafana_data:/var/lib/grafana -v grafana_logs:/var/log/grafana grafana/grafana
```
