FROM python:3.8.13-buster

LABEL maintainer="khahux <khahux@gmail.com>"

ARG TZ="Asia/Shanghai"

ENV TZ ${TZ}

RUN set -ex \
    && sed -i s@/deb.debian.org/@/mirrors.tuna.tsinghua.edu.cn/@g /etc/apt/sources.list \
    && sed -i s@/security.debian.org/@/mirrors.tuna.tsinghua.edu.cn/@g /etc/apt/sources.list \
    && apt update \
    && apt upgrade -y \
    && apt install curl wget vim htop git rsync screen iftop iotop tree lsof net-tools unzip tzdata locales nload procps dnsutils iputils-ping build-essential -y \
    && locale-gen --purge en_US.UTF-8 zh_CN.UTF-8 \
    && localedef -i en_US -c -f UTF-8 -A /usr/share/locale/locale.alias en_US.UTF-8 \
    && echo 'LANG="en_US.UTF-8"' > /etc/default/locale \
    && echo 'LANGUAGE="en_US:en"' >> /etc/default/locale \
    && ln -sf /usr/share/zoneinfo/${TZ} /etc/localtime \
    && echo ${TZ} > /etc/timezone \
    && apt autoremove -y \
    && apt autoclean -y \
    && rm -rf /var/lib/apt/lists/* \
    && pip config set global.index-url http://pypi.doubanio.com/simple/ \
    && pip config set install.trusted-host pypi.doubanio.com \
    && pip install pip --upgrade \
    && pip install ipdb \
    && rm -rf ~/.cache/pip

CMD ["python3"]
