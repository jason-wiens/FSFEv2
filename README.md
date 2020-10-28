# Full Stack - Server Setup

todo: add first part of course

## Add HTTPS

Go to [certbot](https://certbot.eff.org/)

select server (nginx) and system (ubuntu) and follow instructions

## Add HTTP/2

note: ensure https is setup as it is a prerequisite for http/2

Edit nginx config

```
$ sudo vi /etc/nginx/sites-available/default
```

navigate to `/443` and insert http2 in between 443 and ssl

```
listen [::]:443 http2 ssl ipv6only=on;
listen 443 http2 ssl;
```

## Add websockets

Edit nginx config

```
$ sudo vi /etc/nginx/sites-available/default
```

to include the following location

```
location / {
    proxy_set_header Upgrade $http_upgrade;
    proxt_set_header Connection "upgrade";

    proxy_pass http://127.0.0.1:3000;
}
```
