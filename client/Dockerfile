FROM node:alpine3.15 as step-1

WORKDIR /app

COPY package*.json ./
RUN npm install

COPY . .
RUN npm run build


FROM nginx:1.23
COPY --from=step-1 /app/build/ /usr/share/nginx/html
COPY ./deployment/nginx.conf /etc/nginx/conf.d/default.conf
