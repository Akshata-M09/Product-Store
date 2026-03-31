FROM node:18-alpine

WORKDIR /app

# Install dependencies first (better caching)
COPY package*.json ./
RUN npm install

# Copy rest of the code
COPY . .

# Set environment
ENV NODE_ENV=production

# Expose port
EXPOSE 5000

# Start app
CMD ["node", "server.js"]