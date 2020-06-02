FROM alpine:3.12

ENV UID=991 GID=991

RUN \
apk add --no-cache npm python2 ffmpeg tini su-exec && \
apk add --no-cache --repository http://dl-cdn.alpinelinux.org/alpine/edge/testing/ \
    atomicparsley

WORKDIR /app

COPY run.sh /usr/local/bin/run.sh

COPY package.json /app/

RUN npm install

COPY ./ /app/

EXPOSE 17442

RUN chmod +x /usr/local/bin/run.sh

ENTRYPOINT [ "run.sh" ]
CMD [ "node", "app.js" ]
