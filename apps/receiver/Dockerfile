FROM node:16.2.0-buster-slim

WORKDIR /opt/receiver
COPY . /opt/receiver/

RUN groupadd --gid 9001 receiver \
    && useradd -M --uid 9001 --no-user-group --group receiver receiver \
    && mkdir /tmp/cache \
    && npm install --cache /tmp/cache --production \
    && rm -rf /tmp/cache \
    && chown receiver:receiver -R /opt/receiver \
    && chmod +x /opt/receiver/entrypoint.sh

USER receiver

ENTRYPOINT ["npm", "start"]