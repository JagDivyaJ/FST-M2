#build phase
FROM node:18-alpine as builder
WORKDIR /usr/app
COPY package.json .
RUN npm install
COPY . .
RUN npm run build
#run phase
FROM node:18-alpine
WORKDIR /usr/app
COPY package.json .
RUN npm install
COPY --from=builder /usr/app/dist ./
CMD ["node","server.js"]