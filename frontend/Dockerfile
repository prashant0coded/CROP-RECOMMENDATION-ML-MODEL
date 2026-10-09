# Stage 1: build the React app
FROM node:22-alpine AS build
WORKDIR /app
COPY package*.json ./
RUN npm install --legacy-peer-deps
COPY . .
RUN npm run build

# Stage 2: serve the built files
FROM node:22-alpine
WORKDIR /app
RUN npm install -g serve
COPY --from=build /app/build ./build
CMD serve -s build -l ${PORT:-3000}
