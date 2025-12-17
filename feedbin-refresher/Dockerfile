FROM alpine:3

WORKDIR /app

RUN apk update && apk add --no-cache \
    build-base \
    git \
    ruby-dev \
    libidn-dev \
    libxml2-dev \
    && git clone https://github.com/feedbin/refresher.git /app \
    && gem install bundler \
    && bundle update --bundler \
    && bundle install

CMD ["bundle", "exec", "foreman", "start"]
