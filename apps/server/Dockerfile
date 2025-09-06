FROM node:20-slim AS base

# Enable pnpm
RUN corepack enable && corepack prepare pnpm@latest --activate

# Set working directory
WORKDIR /app

# Copy only the app's package.json
COPY package.json ./

# Install dependencies (without lockfile)
RUN pnpm install

# Copy the rest of the app
COPY . .

# Build the app
RUN pnpm run build
# RUN pnpm run db:migrate  # Optional

# Run the app
CMD ["pnpm", "run", "start"]