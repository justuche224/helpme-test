# Use an official Node.js slim image
FROM node:20-slim AS base

# Set working directory
WORKDIR /app

# Install pnpm globally
RUN corepack enable && corepack prepare pnpm@latest --activate

# Copy only package.json and lockfile first for better layer caching
COPY package.json pnpm-lock.yaml ./

# Install dependencies
RUN pnpm install

# Copy the rest of the application code
COPY . .

# Build the app
RUN pnpm run build
# RUN pnpm run db:migrate  # Uncomment if needed

# Default command
CMD ["pnpm", "run", "start"]