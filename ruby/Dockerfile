FROM naoty/base
MAINTAINER Naoto Kaneko <naoty.k@gmail.com>

# Requirements
RUN apt-get install -y \
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

# Ruby
WORKDIR /root
ADD ./version.txt /root/versions/ruby.txt
ADD ./gemrc /root/.gemrc
RUN RUBY_VERSION=$(cat versions/ruby.txt) && \
    RUBY_SHORT_VERSION=$(echo $RUBY_VERSION | sed -E "s/\.[0-9]+$//") && \
    curl -O http://ftp.ruby-lang.org/pub/ruby/$RUBY_SHORT_VERSION/ruby-$RUBY_VERSION.tar.gz && \
    tar -zxvf ruby-$RUBY_VERSION.tar.gz && \
    cd ruby-$RUBY_VERSION && \
    ./configure --disable-install-doc && \
    make && \
    make install && \
    cd && \
    rm -r ruby-$RUBY_VERSION ruby-$RUBY_VERSION.tar.gz

# Bundler
RUN gem install bundler
