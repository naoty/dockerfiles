FROM debian:wheezy
MAINTAINER Naoto Kaneko <naoty.k@gmail.com>

# Requirements
RUN apt-get update && \
    apt-get install -y \
        build-essential \
        curl \
        git \
        zlib1g-dev \
        libssl-dev \
        libreadline-dev \
        libyaml-dev \
        libxml2-dev \
        libxslt-dev \
        libffi-dev && \
    apt-get clean

# rbenv & ruby-build
ENV RBENV_ROOT /root/.rbenv
RUN git clone https://github.com/sstephenson/rbenv.git $RBENV_ROOT && \
    git clone https://github.com/sstephenson/ruby-build.git $RBENV_ROOT/plugins/ruby-build && \
    $RBENV_ROOT/plugins/ruby-build/install.sh
ENV PATH $RBENV_ROOT/bin:$PATH
# RUN echo 'eval "$(rbenv init -)"' >> /etc/profile.d/rbenv.sh
ADD rbenv.sh /etc/profile.d/rbenv.sh

# Ruby
ENV CONFIGURE_OPTS --disable-install-doc
ADD ./ruby_versions.txt /root/ruby_versions.txt
RUN xargs -L 1 rbenv install < /root/ruby_versions.txt

# Bundler
RUN echo 'gem: --no-rdoc --no-ri' >> /.gemrc && \
    bash -l -c 'for v in $(cat /root/ruby_versions.txt); do rbenv global $v; gem install bundler; done'
