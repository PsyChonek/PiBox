https://nginxproxymanager.com/

Use docker compose to install

```bash
docker compose up -d
```

- Url: http://127.0.0.1:81/
- Login: admin@example.com
- Password: changeme


## Dark mode

https://docs.theme-park.dev/themes/nginx-proxy-manager/

### Docker compose 
add the following to the `docker-compose.yml` file

```yaml
services:
  app:
    environment:
      - THEME=dark
``` 

```yaml
services:
  app:
    volumes:
        - ./98-themepark:/etc/cont-init.d/99-themepark
```

### Download
Download the file from the link above and place it in the root of the project. **98-themepark**