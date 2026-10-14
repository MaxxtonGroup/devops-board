FROM node:9.11.1-alpine@sha256:f8f6c69cce180a9a7c9fa685c86671b1e1f2ea7cc5f9a0dbe99d30cc7a0b6cbe

WORKDIR /app/webscale-core
ADD webscale-core/dist/package.json ./
RUN yarn link

WORKDIR /app/webscale-collection
ADD webscale-collection/dist/package.json ./
RUN yarn link

ARG NAME
WORKDIR /app/$NAME
ADD $NAME/package.json $NAME/yarn.lock ./
RUN yarn link @webscale/collection @webscale/core && yarn --frozen-lockfile

ADD $NAME/tslint.json $NAME/tsconfig.json $NAME/tsconfig.build.json $NAME/README.md ./

CMD yarn run watch