FROM node:16 as builder
ENV NODE_ENV=production
WORKDIR /app
COPY ["package.json", "package-lock.json*", "./"]
RUN npm install --production
COPY . .
RUN npm run build

FROM nginx:stable
COPY --from=builder /app/build /usr/share/nginx/html
COPY nginx-default.conf /etc/nginx/conf.d/default.conf
EXPOSE 3000
