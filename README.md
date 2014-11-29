docker owncloud
===============

Builds a docker container with owncloud installed.

## Usage

Build the image:

```bash
run docker build -t 'kphoen/owncloud' .
```

Run it:

```bash
docker run -p 80:80 -v $(pwd)/data:/var/www/owncloud/data kphoen/owncloud
```
