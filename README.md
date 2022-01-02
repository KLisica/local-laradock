<p align="center">
    <img src="/.github/home-page-images/laradock-logo.jpg?raw=true" alt="Laradock Logo"/>
</p>

# Local Laradock Environment.

## ⚙️ Dev stack

**`PHP`**  (v7.4.23)<br />
**`Composer`**  (v2.1.8)<br />
**`NodeJS`**  (v16.1.0)<br />
**`NPM`**  (v7.11.2)<br />
**`PostgreSQL`**  (v10.15)<br />
**`MongoDB`**  (v4.4.5)<br />
**`NGINX`**

<br />

## 🚀 Quick start

``` shell
docker-compose up -d postgres mongo nginx redis php-worker
docker-compose exec --user=laradock workspace bash
```

## ⭐ Starting the laravel-echo-server

``` shell
# Run the NGROK tunnel from local app (i.e. Mestar.hr):
ngrok http --host-header=rewrite api.mestar.test:80
# Update the laravel-echo-server.json file with public URL in authHost field and re-create the container.
docker-compose up -d --build laravel-echo-server
```
