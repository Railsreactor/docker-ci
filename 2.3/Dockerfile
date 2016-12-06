FROM ruby:2.3
MAINTAINER Carlos Lopes <carlos.lopes@codeminer42.com>

# Install dependencies
RUN apt-get update && \
    apt-get install -y --no-install-recommends \
      git \
      libfreetype6 \
      libfontconfig \
      bzip2 \
      qt5-default \
      libqt5webkit5-dev \
      gstreamer1.0-plugins-base \
      gstreamer1.0-tools \
      gstreamer1.0-x \
      xvfb \
      xauth \
      unzip \
      libnss3 \
      libgconf-2-4 \
      openssh-client

# Install Phantom.js
ENV PHANTOMJS_VERSION 2.1.1
RUN mkdir -p /srv/var
RUN curl -sSLO "https://bitbucket.org/ariya/phantomjs/downloads/phantomjs-$PHANTOMJS_VERSION-linux-x86_64.tar.bz2" && \
    tar -xjf "phantomjs-$PHANTOMJS_VERSION-linux-x86_64.tar.bz2" -C "/tmp" && \
    rm -f "phantomjs-$PHANTOMJS_VERSION-linux-x86_64.tar.bz2" && \
    mv "/tmp/phantomjs-$PHANTOMJS_VERSION-linux-x86_64/" /srv/var/phantomjs && \
    ln -s /srv/var/phantomjs/bin/phantomjs /usr/bin/phantomjs

# Install node / npm
ENV NPM_CONFIG_LOGLEVEL info
ENV NODE_VERSION 4.4.7

RUN curl -sSLO "https://nodejs.org/dist/v$NODE_VERSION/node-v$NODE_VERSION-linux-x64.tar.xz" && \
    tar -xJf "node-v$NODE_VERSION-linux-x64.tar.xz" -C /usr/local --strip-components=1 && \
    rm -f "node-v$NODE_VERSION-linux-x64.tar.xz" && \
    npm install npm -g

# ChromeDriver - WebDriver for Chrome
ENV CHROMEDRIVER_VERSION 2.24
RUN mkdir -p /srv/var
RUN curl -sSLO "http://chromedriver.storage.googleapis.com/$CHROMEDRIVER_VERSION/chromedriver_linux64.zip" && \
    unzip "chromedriver_linux64.zip" && \
    rm -f "chromedriver_linux64.zip" && \
    mv "chromedriver" "/srv/var/chromedriver-$CHROMEDRIVER_VERSION" && \
    ln -s "/srv/var/chromedriver-$CHROMEDRIVER_VERSION" /usr/bin/chromedriver

# Google Chrome
ARG CHROME_VERSION="google-chrome-stable"
RUN wget -q -O - https://dl-ssl.google.com/linux/linux_signing_key.pub | apt-key add - \
  && echo "deb http://dl.google.com/linux/chrome/deb/ stable main" >> /etc/apt/sources.list.d/google-chrome.list \
  && apt-get update -qqy \
  && apt-get -qqy install \
    ${CHROME_VERSION:-google-chrome-stable} \
  && rm /etc/apt/sources.list.d/google-chrome.list \
  && rm -rf /var/lib/apt/lists/* /var/cache/apt/*
