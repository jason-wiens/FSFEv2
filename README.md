# Full Stack - Server Setup

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
listen [::]:443 https2 ssl ipv6only=on;
listen 443 http2 ssl;
```
