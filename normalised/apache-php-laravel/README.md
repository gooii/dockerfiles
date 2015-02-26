apache2 - php5 with mcrypt extension.

Can be used for running laravel apps.

Currently web root is /app, will move to /data soon to match our other containers
otherwise you cant use volumes_from in docker-compose.yml, you have to explicitly define the mount point under volumes.

