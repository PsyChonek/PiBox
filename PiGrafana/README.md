https://github.com/oijkn/Docker-Raspberry-PI-Monitoring

```
git clone https://github.com/oijkn/Docker-Raspberry-PI-Monitoring.git
```

```
cd Docker-Raspberry-PI-Monitoring
```

```
mkdir -p prometheus/data grafana/data && \
sudo chown -R 472:472 grafana/ && \
sudo chown -R 65534:65534 prometheus/
```

Moved to different file
```
sudo nano /boot/firmware/cmdline.txt
```

Add to the end of the line:
```
cgroup_enable=cpuset cgroup_enable=memory cgroup_memory=1
```

```
docker compose up -d
```