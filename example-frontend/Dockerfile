FROM node:16-alpine AS build-stage

EXPOSE 5000

WORKDIR /usr/src/app

COPY . .

RUN adduser -D frontend-user && chown frontend-user -R .

USER frontend-user

RUN npm install && REACT_APP_BACKEND_URL=http://localhost/api npm run build

FROM node:16-alpine

WORKDIR /usr/src/app

COPY --from=build-stage /usr/src/app/build .

RUN npm install -g serve && adduser -D frontend-user && chown frontend-user -R .

USER frontend-user

CMD ["serve", "-s", "-l", "5000", "build"]


