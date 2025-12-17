FROM alpine:3

WORKDIR /app

RUN apk update && apk add --no-cache \
    build-base \
    git \
    ruby-dev \
    libxml2-dev \
    vips-dev \
    && git clone https://github.com/feedbin/image.git /app \
    && gem install bundler \
    && bundle update --bundler \
    && bundle install

CMD ["bundle", "exec", "foreman", "start"]
