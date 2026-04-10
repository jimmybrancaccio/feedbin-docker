FROM ruby:2.7.8-alpine

WORKDIR /app

RUN apk add --no-cache \
    linux-headers \
    tzdata \
    git \
    build-base \
    curl

RUN git clone https://github.com/feedbin/privacy-please.git /app \
    && sed -i 's/nio4r (2.5.7)/nio4r (2.7.1)/' Gemfile.lock \
    && sed -i '/group :development/i gem "base64"\ngem "ostruct"\n' Gemfile \
    && gem install ffi -v 1.15.0 --platform ruby \
    && gem install ffi-compiler -v 1.0.1 \
    && bundle install --jobs=1

ENV RACK_ENV=production

EXPOSE 8081

CMD ["bundle", "exec", "foreman", "start"]
