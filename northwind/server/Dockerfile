FROM node:latest

# configure db user & pw
ENV APP_DIR=/app APP_PORT=3000
ENV DB_USER=root DB_PASSWORD=checkit

WORKDIR ${APP_DIR}

ADD package.json .
ADD package-lock.json .
ADD main.js .

ADD config config
ADD public public
ADD views views

# Run App
RUN npm i

HEALTHCHECK --interval=30s --timeout=30s --start-period=5s --retries=3 \
    CMD curl -f -s http://localhost:${APP_PORT}/health || exit 1

EXPOSE ${APP_PORT}

ENTRYPOINT [ "node", "main.js" ]