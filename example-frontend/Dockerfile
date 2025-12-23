FROM node:16-alpine

EXPOSE 5000

WORKDIR /usr/src/app

COPY . .

RUN adduser -D frontend-user

RUN chown frontend-user -R .

USER frontend-user

RUN npm install

ENV REACT_APP_BACKEND_URL=http://localhost/api

RUN npm run build

RUN npm install serve

CMD ["npx", "serve", "-s", "-l", "5000", "build"]
