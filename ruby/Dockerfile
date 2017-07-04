FROM ruby:2.3

MAINTAINER rilian <rilian@railsreactor.com>

ENV PHANTOMJS_VERSION 2.1.1
ENV NPM_CONFIG_LOGLEVEL info
ENV NODE_VERSION 4.4.7
ARG CHROME_VERSION="google-chrome-stable"

RUN CHROMEDRIVER_VERSION=$(wget -qO- http://chromedriver.storage.googleapis.com/LATEST_RELEASE) && \
    wget -q -O - https://dl-ssl.google.com/linux/linux_signing_key.pub | apt-key add - \
    && echo "deb http://dl.google.com/linux/chrome/deb/ stable main" >> /etc/apt/sources.list.d/google-chrome.list \
    && apt-get update && \
    apt-get install -y --no-install-recommends \
      git \
      google-chrome-stable \
      gstreamer1.0-plugins-base \
      gstreamer1.0-tools \
      gstreamer1.0-x \
      libgconf-2-4 \
      libfontconfig \
      libfreetype6 \
      libnss3 \
      libqt5webkit5-dev \
      openssh-client \
      qt5-default \
      unzip \
      xauth \
      xvfb \

    # phantomjs
    && mkdir -p /srv/var \
    && curl -sSLO "https://bitbucket.org/ariya/phantomjs/downloads/phantomjs-$PHANTOMJS_VERSION-linux-x86_64.tar.bz2" && \
    tar -xjf "phantomjs-$PHANTOMJS_VERSION-linux-x86_64.tar.bz2" -C "/tmp" && \
    rm -f "phantomjs-$PHANTOMJS_VERSION-linux-x86_64.tar.bz2" && \
    mv "/tmp/phantomjs-$PHANTOMJS_VERSION-linux-x86_64/" /srv/var/phantomjs && \
    ln -s /srv/var/phantomjs/bin/phantomjs /usr/bin/phantomjs \

    # node / npm
    && curl -sSLO "https://nodejs.org/dist/v$NODE_VERSION/node-v$NODE_VERSION-linux-x64.tar.xz" && \
    tar -xJf "node-v$NODE_VERSION-linux-x64.tar.xz" -C /usr/local --strip-components=1 && \
    rm -f "node-v$NODE_VERSION-linux-x64.tar.xz" && \
    npm install npm -g \

    # ChromeDriver - WebDriver for Chrome
    && mkdir -p /srv/var \
    && curl -sSLO "http://chromedriver.storage.googleapis.com/$CHROMEDRIVER_VERSION/chromedriver_linux64.zip" && \
    unzip "chromedriver_linux64.zip" && \
    rm -f "chromedriver_linux64.zip" && \
    mv "chromedriver" "/srv/var/chromedriver-$CHROMEDRIVER_VERSION" && \
    ln -s "/srv/var/chromedriver-$CHROMEDRIVER_VERSION" /usr/bin/chromedriver \

    # Google Chrome
    && rm /etc/apt/sources.list.d/google-chrome.list \

    # Cleanup
    && rm -rf /var/lib/apt/lists/* /var/cache/apt/*
