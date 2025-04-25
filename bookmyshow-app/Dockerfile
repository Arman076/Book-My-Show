FROM node:18
WORKDIR /app

COPY package.json package-lock.json ./

# Set npm retry policies & use reliable registry
RUN npm config set retry 5 && \
    npm config set fetch-retries 5 && \
    npm config set fetch-retry-mintimeout 10000 && \
    npm config set fetch-retry-maxtimeout 60000 && \
    npm config set registry https://registry.npmmirror.com && \
    npm install --legacy-peer-deps

COPY . .

EXPOSE 3000
ENV NODE_OPTIONS=--openssl-legacy-provider
CMD ["npm", "start"]
