docker owncloud for Raspberry Pi
================================

Builds a docker container with owncloud installed.

**N.B**: this project uses raspbian for base images.

## Usage

Build the image:

```bash
docker build -t kphoen/owncloud-data owncloud-data
docker build -t kphoen/owncloud owncloud
```

Run it:

```bash
docker run --name owncloud-data owncloud-data # will create the data container
docker run -p 80:80 --volumes-from owncloud-data kphoen/owncloud
```

## Todo

  * Create a data container for MySQL
  * Provide fig integration
  * Configure HTTPS access

## License

This project is released under the MIT License. See the bundled LICENSE file for
details.
