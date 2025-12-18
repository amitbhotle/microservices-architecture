# ---------- BUILD STAGE ----------
FROM node:20-alpine AS builder

WORKDIR /app

# package files copy
COPY package*.json ./

# dependencies install
RUN npm install

# source code copy
COPY . .

# typescript / app build
RUN npm run build


# ---------- RUNTIME STAGE ----------
FROM node:20-alpine

WORKDIR /app

# sirf required files copy karo
COPY --from=builder /app/dist ./dist
COPY --from=builder /app/node_modules ./node_modules
COPY --from=builder /app/package*.json ./

# backend port
EXPOSE 8080

# app start
CMD ["node", "dist/main.js"]

