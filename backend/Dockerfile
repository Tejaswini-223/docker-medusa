FROM node:20.17.0

WORKDIR /app/medusa

# Copy only package files first to leverage Docker cache
COPY package.json ./
COPY package-lock.json ./

# Install system & npm dependencies
RUN apt-get update && \
    apt-get install -y python3 && \
    npm install -g npm@latest && \
    npm install -g @medusajs/medusa-cli@latest

# Install app dependencies
RUN npm install --legacy-peer-deps --loglevel=error

# Copy rest of the code
COPY . .

# Make the script executable
RUN chmod +x develop.sh

# Start the container
ENTRYPOINT ["./develop.sh", "develop"]
