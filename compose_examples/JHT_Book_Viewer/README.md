Suitable for local dev of JHT Book Viewer.

nginx runs on port 9000

angular app files are expected to be in /dist

bower_components are in the root, /bower_components

TODO : The ngToolkit needs to be switched for Benji's as this one has a bad entrypoint.

If you do use it, then to run npm/grunt/bower you have to do something like this :

docker-compose run --entrypoint="/usr/local/bin/grunt" ngToolkit local

etc..

Also, ngTestkit hasn't itself been tested at all. Don't know if it works, pretty sure the selenium link will need something doing to it.
