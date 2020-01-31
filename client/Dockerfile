FROM node:alpine as builder 
WORKDIR /app
COPY package.json ./
RUN npm install
COPY . .
RUN npm run build


FROM nginx
EXPOSE 3000
EXPOSE 5000
COPY ./nginx/default.conf /etc/ngnix/conf.d/default.conf
COPY  --from=builder /app/build /use/share/nginx/html/