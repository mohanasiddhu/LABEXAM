# Frontend multi-stage build for Vite + React
FROM node:18-alpine AS build
WORKDIR /app

# Install dependencies
COPY package.json package-lock.json* ./
RUN npm ci --silent || npm install --silent

# Copy source and build
COPY . .
RUN npm run build

# Production image using a lightweight static server
FROM node:18-alpine AS runner
WORKDIR /app
RUN npm install -g serve@14 --silent

COPY --from=build /app/dist ./dist

EXPOSE 5173
CMD ["serve", "-s", "dist", "-l", "5173"]
