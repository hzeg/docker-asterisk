FROM alpine:3.9

MAINTAINER Hubert Zegota <hubert.zegota@gmail.com>

RUN apk add --update \
      asterisk \
      asterisk-sample-config \
      asterisk-cdr-mysql \
      asterisk-odbc \
      asterisk-sounds-en \
      asterisk-sounds-moh \
      asterisk-speex \
      asterisk-srtp \
&& asterisk -U asterisk \
&& sleep 5 \
&& pkill -9 asterisk \
&& pkill -9 astcanary \
&& sleep 2 \
&& rm -rf /var/run/asterisk/* \
&& mkdir -p /var/spool/asterisk/fax \
&& chown -R asterisk: /var/spool/asterisk/fax \
&& truncate -s 0 /var/log/asterisk/messages \
                 /var/log/asterisk/queue_log \
&&  rm -rf /var/cache/apk/* \
           /tmp/* \
           /var/tmp/*

EXPOSE 5060/udp 5060/tcp
CMD /usr/sbin/asterisk -T -W -p -vvvdddf

