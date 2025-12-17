FROM alpine:3

WORKDIR /app

RUN apk update && apk add --no-cache \
    linux-headers \
    tzdata \
    git \
    ruby-dev \
    ruby-bigdecimal \
    build-base \
    wget \
    && git clone https://github.com/feedbin/privacy-please.git /app \
    && sed -i 's/nio4r (2.5.7)/nio4r (2.7.1)/' Gemfile.lock \
    && gem install bundler \
    && bundle update --bundler \
    && bundle install

ENV RACK_ENV=production

EXPOSE 8081
