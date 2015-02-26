# a generic 'toolkit' container for use with any JS/Angular
# based project - installs nodejs, grunt, bower and compass
#
FROM centos:centos6

# guess?
#
MAINTAINER "Benji Soar" <benji@gooii.com>

###############################################################################
# At this point we're running as the Root user                                #
###############################################################################

# Enable EPEL (Extra Packages for Enterprise Linux) for Node.js
#
RUN rpm -Uvh http://download.fedoraproject.org/pub/epel/6/i386/epel-release-6-8.noarch.rpm

# Ensure yum Repos are up to date
#
RUN yum update -y

# Install Node.js and npm (-y applies yes to 'Is this ok [y/N] prompt')
#
RUN yum install -y npm

# Lots of node modules appear to require 'inherits' which doesn't appear to be
# installed by default?
#
RUN npm install -g inherits

# Update Node
#
RUN npm install -g node

# Update Node Package Manager
#
RUN npm install -g npm

# Install Git
#
RUN yum install -y git

# Install Grunt CLI (plus Grunt) globally
#
RUN npm install -g grunt-cli

# Install Bower
#
RUN npm install -g bower

# Install Ruby (required for GEMs and installation of Compass GEM)
#
RUN yum install -y ruby-devel
RUN yum install -y rubygems
RUN gem install compass
# Install a better JSON library: https://groups.google.com/forum/#!topic/selenium-users/6Y7wJOdBG7o
#
RUN gem install json

# Now create a non root user to run all our dev tools:-
# 	-m (auto create a /home/gooii directory if it doesn't already exist)
# 	-u (set user id - vital to enable user to make filesystem/container volume changes)
#
RUN useradd -m -u 1000 gooii

# Copy the nice dotfiles that dockerfile/centos gives us:-
#
RUN cd && cp -R .bash_profile .bashrc /home/gooii
# Create .ssh directory
#
RUN mkdir /home/gooii/.ssh
# Disable StrictHostKeyChecking
#
RUN echo -e "Host github.com\n\tStrictHostKeyChecking no\n" >> /home/gooii/.ssh/config
# Set ownership of new home directory
#
RUN chown -R gooii:gooii /home/gooii

# Switch to this user
#
USER gooii
ENV HOME /home/gooii

# provide a prompt when this image is spun up
#
CMD ["bash"]
