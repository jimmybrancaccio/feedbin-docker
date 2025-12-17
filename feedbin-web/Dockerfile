FROM alpine:3

ARG FEEDBIN_URL

WORKDIR /app

RUN apk update && apk add --no-cache \
    linux-headers \
    tzdata \
    git \
    ruby-dev \
    ruby-bigdecimal \
    build-base \
    imagemagick-dev \
    imagemagick-libs \
    libxml2-dev \
    libxslt-dev \
    nodejs \
    libldap \
    libidn-dev \
    bind-tools \
    postgresql-client \
    libpq \
    postgresql-dev \
    yaml-dev \
    vips \
    && gem install 'etc:1.4.6' 'idn-ruby:0.1.5' \
    && git clone https://github.com/feedbin/feedbin.git /app \
    && gem install bundler \
    && bundle update --bundler \
    && bundle lock --add-platform x86_64-linux-musl \
    && bundle install \
    && bundle exec rake assets:precompile

ENV RAILS_SERVE_STATIC_FILES=true

EXPOSE 3000
