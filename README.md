# Docker images

![Docker](https://docs.docker.com/docker-cloud/images/Docker-Cloud-Blue.svg)

:us: :gb:

In this repository are stored Dockerfile files to build some useful Docker images.

To build an image, go to the directory containing the Dockerfile and type:

    docker build --pull -t _name_ .

:fr:

Dans cet environnement sont stockés des fichiers Dockerfile pour construire quelques images Docker utiles.

Pour construire une image, aller dans le répertoire contenant le Dockerfile et taper :

    docker build --pull -t _nom_ .

# Images

## gentoo/amd64-armv6j-hardfloat-linux-gnueabi

:us: :gb: A gentoo based image containing a compilation toolchain for armv6j-hardfloat-linux-gnueabi (using crossdev).

:fr: Une image basée sur gentoo qui contient une chaîne de compilation pour amd64-armv6j-hardfloat-linux-gnueabi (utilisant crossdev).

## gentoo/amd64-armv7a-hardfloat-linux-gnueabi

:us: :gb: A gentoo based image containing a compilation toolchain for armv7a-hardfloat-linux-gnueabi (using crossdev).

:fr: Une image basée sur gentoo qui contient une chaîne de compilation pour armv7a-hardfloat-linux-gnueabi (utilisant crossdev).

## misybag/amd64-armv6j-hardfloat-linux-gnueabi

:us: :gb: An image used to control a MisybaG armv6j-hardfloat-linux-gnueabi device.

:fr: Une image pour contrôler un appareil amd64-armv6j-hardfloat-linux-gnueabi sous MisybaG.

## misybag/amd64-armv7a-hardfloat-linux-gnueabi

:us: :gb: An image used to control a MisybaG armv7a-hardfloat-linux-gnueabi device.

:fr: Une image pour contrôler un appareil armv7a-hardfloat-linux-gnueabi sous MisybaG.
