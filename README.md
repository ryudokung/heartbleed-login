# heartbleed-login

`heartbleed-login` is a small demonstration of the Heartbleed
(CVE-2014-0160) vulnerability. It serves a simple login form over
HTTPS using an intentionally outdated version of OpenSSL so the
container is vulnerable. The project is intended for educational and
testing purposes only.

## Prerequisites

- Docker installed and running.
- Permission to build and run containers (e.g. via `sudo` or membership in
the `docker` group).

## Building the image

```bash
docker build -t heartbleed-login .
```

The Dockerfile installs an old snapshot of OpenSSL (1.0.1e) on purpose to
expose the Heartbleed bug. Do **not** use this image in production.

## Running the container

```bash
docker run -p 443:443 heartbleed-login
```

After the container starts, browse to `https://localhost` (or the host
IP) and you will see the login page served by Apache.

## Project structure

The `app` directory contains the static web assets (HTML, CSS, and
JavaScript) that are copied into `/var/www/html/` inside the image.

## Purpose

This repository provides a convenient way to experiment with
Heartbleed in a controlled environment. The vulnerable OpenSSL version
is installed deliberately to demonstrate the attack and should not be
used elsewhere.
