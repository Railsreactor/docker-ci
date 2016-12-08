FROM ubuntu

MAINTAINER rilian <rilian@railsreactor.com>

RUN apt-get update && \
    apt-get install -y --no-install-recommends \
      wget \
      locales

RUN locale-gen en_US.UTF-8
ENV LANG en_US.UTF-8
ENV LANGUAGE en_US:en
ENV LC_ALL en_US.UTF-8

RUN wget --no-check-certificate https://packages.erlang-solutions.com/erlang-solutions_1.0_all.deb && dpkg -i erlang-solutions_1.0_all.deb
RUN apt-get update && \
    apt-get install -y --no-install-recommends \
      esl-erlang \
      elixir
