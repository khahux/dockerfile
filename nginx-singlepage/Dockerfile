FROM nginx:1.22.0-alpine

LABEL maintainer="khahux <khahux@gmail.com>"

ARG TZ='Asia/Shanghai'
ENV TZ ${TZ}

RUN apk upgrade --update \
    && apk add bash tzdata curl wget ca-certificates \
    && ln -sf /usr/share/zoneinfo/${TZ} /etc/localtime \
    && echo ${TZ} > /etc/timezone \
    && rm -rf /usr/share/nginx/html /var/cache/apk/*

COPY nginx.conf /etc/nginx/conf.d/default.conf

EXPOSE 80 443

STOPSIGNAL SIGTERM

CMD ["nginx", "-g", "daemon off;"]
