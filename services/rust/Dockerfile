ARG ALPINE_VERSION
FROM alpine:${ALPINE_VERSION}

ARG ALPINE_MIRROR_URL
RUN if [ "${ALPINE_MIRROR_URL}" != "" ]; then \
        sed -i "s/dl-cdn.alpinelinux.org/${ALPINE_MIRROR_URL}/g" /etc/apk/repositories; \
    fi

ARG DATABASE_TYPE
RUN if [ "${DATABASE_TYPE}" == "postgresql" ]; then \
        apk add libpq; \
    fi
RUN if [ "${DATABASE_TYPE}" == "mysql" ]; then \
        apk add mariadb-dev; \
    fi


ARG RUST_APP_PORT
EXPOSE ${RUST_APP_PORT}

ARG RUST_APP_NAME
ENV RUST_APP_NAME ${RUST_APP_NAME}
WORKDIR /app
CMD ./$RUST_APP_NAME




