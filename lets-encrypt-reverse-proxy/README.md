# lets-encrypt-reverse-proxy
Docker image for a https-safe reverse proxy, powered by nginx and lets encrypt.

## Build

To create the image `lerenn/lets-encrypt-reverse-proxy`, execute the following command on the reverse-proxy project folder:

    docker build -t lerenn/lets-encrypt-reverse-proxy .

## Run

If you want to use a reverse-proxy on HTTP and/or HTTPS websites, here is the basic command :

    docker run -d -p 80:80 -p 443:443 -v /path/in/host:/etc/nginx/sites-enabled lerenn/nginx-reverse-proxy

## Arguments

### Volumes

* **/etc/nginx/sites-enabled** : [Mandatory] Should contains nginx configurations for redirections to websites/web apps.
* **/etc/letsencrypt** : [Optional] Should contains lets encrypt. Mount it should avoid regeneration of certifcates.

### Ports

* **80**: [Optional] HTTP port.
* **443**: [Mandatory] HTTPS port.

### Environment variables

* **LETSENCRYPT_EMAIL**: [Mandatory] E-mail that will be given to lets encrypt in order to generate certificates. Defaults to `none`.
* **RSA_KEY_SIZE**: [Optional] Size of RSA keys that will be generated or renewed. Defaults to `4096`.
* **STARTUP_WAIT**: [Optional] Seconds to wait before launching LetsEncrypt and then Nginx. Defaults to `0`.

### Links

[Mandatory] Add links to other container with `--link source-container-name:alias-container-name` as an argument.
Then, you'll have to add `http://alias-container-name` into your nginx website/webapp configuration to redirect flux.

## Lets Encrypt

### Warnings

TODO

### Support

TODO