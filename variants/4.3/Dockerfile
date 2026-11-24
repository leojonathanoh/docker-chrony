FROM alpine:3.17

RUN apk add --no-cache ca-certificates

# Install chrony
RUN set -eux; \
    apk add --no-cache chrony~=4.3; \
    chronyd --version; \
    chronyc --version

COPY docker-entrypoint.sh /docker-entrypoint.sh
RUN chmod +x docker-entrypoint.sh

EXPOSE 123/udp

HEALTHCHECK CMD chronyc tracking || exit 1

ENTRYPOINT [ "/docker-entrypoint.sh" ]
CMD [ "-d", "-x" ]