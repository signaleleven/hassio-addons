ARG BUILD_FROM
FROM $BUILD_FROM

ARG BUILD_ARCH

ENV LANG C.UTF-8
ENV SNAPCAST_VERSION 0.14
#Install snapcast-server
RUN DEBIAN_FRONTEND=noninteractive apt-get install -y curl 
RUN curl -L https://github.com/badaix/snapcast/releases/download/v0.14.0/snapserver_0.14.0_armhf.deb -o /tmp/snapcastserver.deb 
RUN dpkg -i /tmp/snapcastserver.deb

RUN pip install Mopidy-Scrobbler

COPY mopidy_cast.conf /var/lib/mopidy/.config/mopidy/mopidy_cast.conf



# Copy data for add-on
COPY run.sh /
RUN chmod a+x /run.sh

EXPOSE 6600 6680 1704 1705


CMD [ "/run.sh" ]
