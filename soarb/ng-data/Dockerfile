# a generic 'data' container which can be shared with other docker
# containers to expose local filesystem directories, or folders we
# create within the container itself
#
# see Data-only container pattern:-
#
# 	http://www.tech-d.net/2013/12/16/persistent-volumes-with-docker-container-as-volume-pattern/
#

# base image to use - only want a really tiny base linux distro
# here as all we need, is to create an internal folder which we
# can expose as a volume to other Docker containers
#
FROM progrium/busybox

# guess?
#
MAINTAINER "Benji Soar" <benji@gooii.com>

# Now create a non root user to run all our dev tools:-
#   -H (don't auto create a home directory)
#   -D (don't assign a password)
#   -s (set login shell)
#
RUN adduser -HDs /bin/bash gooii
# Copy the nice dotfiles that dockerfile/centos gives us:-
#
RUN mkdir /home/gooii
# Set ownership of new home directory
#
RUN chown -R gooii:gooii /home/gooii

# Switch to this user
#
USER gooii
ENV HOME /home/gooii

# tell Docker to create a directory on the host (boot2docker VM), within the 
# docker root path (by default /var/lib/docker) and mount it to the path you
# have specified (in this case /data)
# 
# volumes decouple the life of the data stored within them, from the life of 
# the container that created them
#
VOLUME ["/data"]

# provide a prompt when this image is spun up - busybox uses 'ash'
#
CMD ["ash"]