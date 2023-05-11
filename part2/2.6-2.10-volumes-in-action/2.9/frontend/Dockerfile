FROM node:16-alpine

EXPOSE 5000

WORKDIR /usr/src/app

COPY . .

ENV REACT_APP_BACKEND_URL=http://localhost/api

RUN npm install

RUN npm install -g serve

RUN npm run build

CMD ["serve", "-s", "-l", "5000", "build"]