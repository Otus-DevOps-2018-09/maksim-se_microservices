FROM ruby:2.4.5-alpine3.8

ENV APP_HOME /app
RUN mkdir $APP_HOME
WORKDIR $APP_HOME

COPY . $APP_HOME
# устанавливаем пакеты
RUN apk --no-cache add --virtual build-tools ruby-dev g++ make ruby-bundler \
&& bundle install \
&& apk del build-tools \
&& rm -rf /usr/local/bundle/cache/* \
# чистим кэши и темпы
/root/.bundle/cache/compact_index/rubygems.org*/* \
/var/cache/apk/* \
/var/cache/misc/* \
/var/cache/* \
/tmp/* \
/var/tmp/*

ENV POST_SERVICE_HOST post
ENV POST_SERVICE_PORT 5000
ENV COMMENT_SERVICE_HOST comment
ENV COMMENT_SERVICE_PORT 9292
CMD ["puma"]

