# Smokeping on Docker using Trafik for TLS and Let's Encrypt

This repository contains the necessary tools to run a [Smokeping] on [Docker] using
[Docker Compose] and [Traefik].

## Quick start

In order to quickly run Smokeping on a machine running Docker and Docker Compose,
follow these steps:

* Clone this repository to your computer.
  * `git clone https://github.com/prunux/smokeping-traefik-docker-compose && cd smokeping-traefik-docker-compose`
* Create a ``.env`` file by copying and adjusting ``env.example``
  * `cp env.example .env`
* Create required `CONFIG` directories
  * `mkdir -p ~/.smokeping-cfg`
  * `mkdir -p ~/.traefik-cfg`
* Run ``docker-compose up -d``.
* Access the web UI at [``http://myhost.mydomain:44080``](http://myhost.mydomain:44080) (or a different port, in case you set another port in the env or compose file).
* Access the web UI at [``https://myhost.mydomain:44443``](https://myhost.mydomain:44443) (or a different port, in case you set another port in the env or compose file).


## Configuration

The configuration is performed via environment variables contained in a ``.env`` file. You
can copy the provided ``env.example`` file as a reference.

**IMPORTANT**: At the moment, the configuration is not regenerated on every container boot, so
if you make any unwished changes to your ``.env`` file, make sure you remove the configuration
directory before starting your containers again (``CONFIG_TRAEFIK``,``CONFIG_SMOKEPING`` )

Variable | Description | Example
--- | --- | ---
`CONFIG_SMOKEPING` | Directory where all configuration of smokeping will be stored | ~/.smokeping-cfg
`CONFIG_TRAEFIK` | Directory where all configuration of smokeping will be stored | ~/.traefik-cfg
`TZ` | System Time Zone | Europe/Amsterdam
`HTTP_PORT` | Exposed port for HTTP traffic | 44080
`HTTPS_PORT` | Exposed port for HTTPS traffic | 44443
`RESTART_POLICY` | Container restart policy | defaults to `unless-stopped`

[Smokeping]: https://oss.oetiker.ch/smokeping/
[Docker]: https://www.docker.com/
[Docker Compose]: https://docs.docker.com/compose/
[Traefik]: https://containo.us/traefik/