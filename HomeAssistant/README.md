https://www.home-assistant.io/

Use docker compose to install
```bash
docker compose up -d
```

Dont forget to edit the `docker-compose.yml` file
```yaml
services:
  app:
    volumes:
      - /PATH_TO_YOUR_CONFIG:/config
```

- Url: http://127.0.0.1:8123/
