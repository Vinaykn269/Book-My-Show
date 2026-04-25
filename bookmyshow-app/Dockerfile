# ---------- STAGE 1: BUILD ----------
FROM node:18 AS builder

WORKDIR /app

COPY package*.json ./

# Install dependencies
RUN npm install

COPY . .

# Build React app (THIS IS KEY)
RUN npm run build


# ---------- STAGE 2: RUN ----------
FROM nginx:alpine

# Copy build files to nginx
COPY --from=builder /app/build /usr/share/nginx/html

# Expose nginx port
EXPOSE 80

# Start nginx
CMD ["nginx", "-g", "daemon off;"]
