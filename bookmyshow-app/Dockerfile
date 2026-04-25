# ---------- STAGE 1: BUILD ----------
FROM node:18 AS builder

WORKDIR /app

COPY package*.json ./

RUN npm install

COPY . .

# 🔥 FIX OPENSSL ERROR HERE
ENV NODE_OPTIONS=--openssl-legacy-provider

# Build React app
RUN npm run build


# ---------- STAGE 2: RUN ----------
FROM nginx:alpine

COPY --from=builder /app/build /usr/share/nginx/html

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]
