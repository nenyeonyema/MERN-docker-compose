# Stage 1
FROM node:18.9.1 AS deps

WORKDIR /app

COPY package.json package-lock.json ./

RUN --mount=type=cache,target=/root/.npm \
	npm ci

# Stage 2
FROM node:18.9.1

WORKDIR /app

COPY --from=deps /app/node_modules ./node_modules

EXPOSE 5050

COPY . .

CMD ["npm", "start"]  
