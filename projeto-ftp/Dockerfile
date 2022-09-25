FROM alpine:3.16.2

ARG USER=gleydson
ARG PASS=123

ENV FTP_USER=${USER} \
	FTP_PASS=${PASS} \
	GID=1000 \
	UID=1000

RUN apk add --no-cache --update \
	vsftpd==3.0.5-r1

COPY [ "/src/vsftpd.conf", "/etc" ]
COPY [ "/src/entrypoint.sh", "/" ]

CMD [ "/usr/sbin/vsftpd" ]
ENTRYPOINT [ "/entrypoint.sh" ]
EXPOSE 20/tcp 21/tcp 40000-40009/tcp
HEALTHCHECK CMD netstat -lnt | grep :21 || exit 1