# ---------- BUILD STAGE ----------
FROM node:20-alpine AS builder

WORKDIR /app

# package files copy karo
COPY package*.json ./

# dependencies install
RUN npm install

# baaki code copy
COPY . .

# frontend build
RUN npm run build


# ---------- RUNTIME STAGE ----------
FROM node:20-alpine

WORKDIR /app

# build stage se output copy
COPY --from=builder /app ./

# frontend port
EXPOSE 3000

# app start
CMD ["npm", "start"]

