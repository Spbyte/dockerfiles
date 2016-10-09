FROM resin/rpi-raspbian:jessie
MAINTAINER Spybyte <spybyte@online.de>

ENV BASE_URL=False IMAGE_PROXY=False \
    UID=991 GID=991

RUN apt-get update \  
    && apt-get -qy install curl \
		apt-utils \
		build-essential \
		zlib1g-dev \
      	ca-certificates \
		libxml2 \
		libxslt-dev \
	    libffi-dev \
	    libxslt-dev \
	    libxml2-dev \
	    openssl \
		libssl-dev \
	    tar \
		wget \
        python \
        python-dev \
		python-pip \
	&& pip install -r https://raw.githubusercontent.com/asciimoo/searx/master/requirements.txt \
	&& mkdir /usr/local/searx && cd /usr/local/searx \
    && wget -qO- https://github.com/asciimoo/searx/archive/master.tar.gz | tar xz --strip 1 \
    && sed -i "s/127.0.0.1/0.0.0.0/g" searx/settings.yml 

COPY run.sh /usr/local/bin/run.sh

RUN chmod +x /usr/local/bin/run.sh

EXPOSE 8888

CMD ["run.sh"]