# Build stage
FROM node:20-alpine AS build
WORKDIR /app

ARG VITE_API_BASE_URL=http://api.example.com/api

# Install dependencies
COPY package*.json ./
RUN npm install --frozen-lockfile

# Copy source and build the app
COPY . .
RUN npm run build

# Production stage
FROM nginx:stable-alpine

# Copy built static files and custom nginx config
COPY --from=build /app/dist /usr/share/nginx/html
COPY nginx.conf /etc/nginx/conf.d/default.conf

EXPOSE 80
