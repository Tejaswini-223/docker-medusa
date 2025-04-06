FROM node:20.17.0

WORKDIR /app/medusa

COPY package.json ./

RUN apt-get update && \
    apt-get install -y python && \
    npm install -g npm@latest && \
    npm install -g @medusajs/medusa-cli@latest && \
    npm install --loglevel=error

COPY . .

ENTRYPOINT ["./develop.sh", "develop"]
