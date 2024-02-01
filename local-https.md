# Enable HTTPS on Your Local Environment

## Install mkcert and Create Certificates

```bash
brew install mkcert
mkcert -install
mkcert local.place-your-domain-here.com localhost 127.0.0.1 ::1
```

Two `.pem` files will be generated. Rename them as `domain.pem` and `domain-key.pem`.

Add the following line to your `/private/etc/hosts` file:

```
127.0.0.1   local.place-your-domain-here.com
```

## Create Nginx Config File

```bash
touch nginx.conf
```

```nginx
events {

}

http {
  server {
    listen 443 ssl;
    listen [::]:443 ssl;
    ssl_certificate ~/domain.pem;
    ssl_certificate_key ~/domain-key.pem;
    server_name local.place-your-domain-here.com;

    location / {
        proxy_pass http://localhost:3000;
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
    }
  }
}
```

## Run Nginx

```bash
nginx -c nginx.conf -p .
```

Now, you can open `https://local.place-your-domain-here.com`.
```

This format retains the clarity and completeness of your instructions. Remember to replace "place-your-domain-here.com" with the actual domain you want to use. Users can follow these steps to easily set up HTTPS on their local development environment using `mkcert` and Nginx.
