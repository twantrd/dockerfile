#
# Toan's CentOS 6.6 for bare dev environment with network tools, vim, macros, and bash_it
#
FROM centos:6.6
MAINTAINER Toan Nguyen
RUN yum update -y
RUN yum install -y vim-enhanced vim-minimal vim-common jwhois mlocate strace bind-utils telnet wget curl git

# Install epel repo
RUN rpm --import http://download.fedoraproject.org/pub/epel/RPM-GPG-KEY-EPEL-6
RUN rpm -Uvh http://dl.fedoraproject.org/pub/epel/6/x86_64/epel-release-6-8.noarch.rpm

# Install bash_it
RUN \
        git clone --depth=1 https://github.com/Bash-it/bash-it.git ~/.bash_it && \
        cd ~/.bash_it && \
        bash ./install.sh --none

# Change to powerline theme
RUN sed -i 's/bobby/powerline/' ~/.bashrc

# Install git, base, history plugins for bash-it
RUN /bin/bash -i -c 'bash-it enable plugin base'
RUN /bin/bash -i -c 'bash-it enable plugin history'
RUN /bin/bash -i -c 'bash-it enable plugin git'

# Grab my .vimrc
ADD https://github.com/twantrd/dotfiles/raw/master/.vimrc /root/.vimrc
