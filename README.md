<p align="center">
    <img src="https://laradock.io/images/laradock-full-logo.jpg" alt="Laradock"/>
</p>

`Local development setup for all of my projects.`

## ⚙️ Dev stack

**`PHP`**  (v7.4.23)<br />
**`Composer`**  (v2.1.8)<br />
**`PostgreSQL`**  (v14.1)<br />
**`MongoDB`**  (v5.0.5)<br />
**`NodeJS`**  (v16.1.0)<br />
**`NPM`**  (v7.11.2)<br />
**`Laravel Echo Server`**
**`NGINX`**

<br />

## 🚀 Quick start

``` shell
docker-compose up -d postgres mongo nginx redis php-worker
docker-compose exec --user=laradock workspace bash
```

### ⭐ Starting the laravel-echo-server

``` shell
# Run the NGROK tunnel from local app (i.e. Mestar.hr):
ngrok http --host-header=rewrite api.mestar.test:80
# Update the laravel-echo-server.json file with public URL in authHost field and re-create the container.
docker-compose up -d --build laravel-echo-server
```

Additional configurations for other apps:

**.env**
```
LARAVEL_ECHO_SERVER_URL=http://172.17.0.1
LARAVEL_ECHO_SERVER_PORT=6001
LARAVEL_ECHO_SERVER_APP_ID=testID
LARAVEL_ECHO_SERVER_APP_KEY=0eb6be7bf551351b5e436fba69c88cf2
LARAVEL_ECHO_SERVER_CHANNEL='user-online.'
```

**laravel-echo-server.json**
```
{
	"authHost": "http://d4b6-95-178-176-164.ngrok.io",
	"authEndpoint": "/broadcasting/auth",
	"clients": [
		{
			"appId": "testID",
			"key": "0eb6be7bf551351b5e436fba69c88cf2"
		}
	],
	"database": "redis",
	"databaseConfig": {
		"redis": {
			"port": "6379",
			"host": "redis"
		}
	},
	"devMode": true,
	"host": null,
	"port": "6001",
	"protocol": "http",
	"socketio": {},
	"sslCertPath": "",
	"sslKeyPath": ""
}
```

<br />

### ⭐ Creating a new database table in Postrges

``` shell
docker-compose exec postgres bash
psql -U default
CREATE DATABASE database_name;

# Exit postgres bash.
exit
exit
```