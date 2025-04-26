FROM node:18

WORKDIR /app

# Only copy package files first (better cache for docker builds)
COPY package.json package-lock.json ./

# Set npm fetch retry options and install dependencies
RUN npm config set fetch-retries 5 && \
    npm config set fetch-retry-mintimeout 10000 && \
    npm config set fetch-retry-maxtimeout 60000 && \
    npm config set registry https://registry.npmmirror.com && \
    npm install --legacy-peer-deps

# Copy all project files
COPY . .

# Expose app port
EXPOSE 3000

# Set Node.js options for OpenSSL (needed for Node 17/18 sometimes)
ENV NODE_OPTIONS=--openssl-legacy-provider

# Start the application
CMD ["npm", "start"]
