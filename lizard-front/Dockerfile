FROM node:12

# Documents
# http://docs.docker.jp/engine/articles/dockerfile_best-practice.html

# Working Directory
WORKDIR /usr/src/app

# Install dependency package
RUN apt-get update \
 && apt-get clean \
 && rm -rf /var/lib/apt/lists/*

# Install app dependencies
# https://mimirswell.ggnet.co.jp/blog-221
COPY lizard-front/package.json /usr/src/app/package.json
COPY lizard-front/package-lock.json /usr/src/app/package-lock.json
RUN cd /usr/src/app; npm install --only=production --no-optional

# Copy files
COPY lizard-front/.eslintrc.js   /usr/src/app/.eslintrc.js
COPY lizard-front/.prettierrc    /usr/src/app/.prettierrc
COPY lizard-front/nuxt.config.js /usr/src/app/nuxt.config.js
COPY lizard-front/jsconfig.json  /usr/src/app/jsconfig.json
COPY lizard-front/tsconfig.json  /usr/src/app/tsconfig.json
COPY lizard-front/assets         /usr/src/app/assets
COPY lizard-front/components     /usr/src/app/components
COPY lizard-front/layouts        /usr/src/app/layouts
COPY lizard-front/middleware     /usr/src/app/middleware
COPY lizard-front/pages          /usr/src/app/pages
COPY lizard-front/plugins        /usr/src/app/plugins
COPY lizard-front/static         /usr/src/app/static
COPY lizard-front/store          /usr/src/app/store

# Listen Port
EXPOSE 5000

# Environment Variables
# APP_NAME lizard-front

CMD ["/bin/sh", "-c", "npm run build:docker && npm run start"]
