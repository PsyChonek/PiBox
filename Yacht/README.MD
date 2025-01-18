https://yacht.sh/

Use docker compose to install

```bash
docker compose up -d
```

Moved to different file
```
sudo nano /boot/firmware/cmdline.txt
```

Add to the end of the line:
```
cgroup_enable=cpuset cgroup_enable=memory cgroup_memory=1
```

- Url: http://127.0.0.1:8000/
- Login: admin@yacht.local 
- Password: pass