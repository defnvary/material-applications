FROM node:16-alpine

EXPOSE 5000

WORKDIR /usr/src/app

COPY . .

RUN adduser -D frontend-user && chown frontend-user -R .

USER frontend-user

RUN npm install && REACT_APP_BACKEND_URL=http://localhost/api npm run build && npm install serve && npm cache clean

CMD ["npx", "serve", "-s", "-l", "5000", "build"]
