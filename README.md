# Let's Encrypt Node.js (via Nginx)

[![Docker Repository on Quay](https://quay.io/repository/patrickheneise/lets-nginx-node/status "Docker Repository on Quay")](https://quay.io/repository/patrickheneise/lets-nginx-node)

Put browser-valid TLS termination in front of any Dockerized HTTP service with one command.

```bash
docker run
  --net=host \
  --name lets-node \
  --env EMAIL=you@email.com \
  --env DOMAIN=yourdomain.com \
  quay.io/patrickheneise/lets-nginx-node
```

Issues certificates from [letsencrypt](https://letsencrypt.org/), installs them in [nginx](https://www.nginx.com/), and schedules a cron job to reissue them monthly.

:zap: To run unattended, this container accepts the letsencrypt terms of service on your behalf. Make sure that the [subscriber agreement](https://letsencrypt.org/repository/) is acceptable to you before using this container. :zap:

## Prerequisites

Before you begin, you'll need:

 1. A [place to run Docker containers](https://www.digitalocean.com/?refcode=f962f6792618) with a public IP.
 2. A domain name with an *A record* pointing to your cluster (example `events.yourdomain.com A XX.YY.ZZ.AA`)

## Usage

Have your node.js server/app/api running on port 3000 on the same machine. Options are:

 * `-e EMAIL=` your email address, used to register with letsencrypt.
 * `-e DOMAIN=` the domain name.
