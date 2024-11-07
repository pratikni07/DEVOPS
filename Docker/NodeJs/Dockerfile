# Stage 1: Build stage
FROM node:18-alpine AS builder

# Working directory
WORKDIR /app

# Copy package files
COPY package*.json ./

# Install dependencies
RUN npm install

# Copy source code
COPY . .

# Build the application
RUN npm run build

# ----------------------------------------------------------------------------------------------
# Stage 2: Production stage
FROM node:18-alpine

# Set working directory
WORKDIR /app

# Set node environment to production
ENV NODE_ENV production

# Copy built assets from builder stage
COPY --from=builder /app/dist ./dist
COPY --from=builder /app/package.json ./package.json

# Install only production dependencies
RUN npm ci --only=production

# Expose application port
EXPOSE 3000

# Start the application
CMD ["node", "dist/index.js"]
