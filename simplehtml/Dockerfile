# docker
# docker -p -v HOST:CONTAINER
#
# docker build --no-cache -t simplehtml .
# docker run -d --rm -p 8080:80 simplehtml
#
FROM node:22-slim AS build
WORKDIR /src
COPY . .
RUN npm install
#RUN npm run format
RUN npm run lint
#RUN npm run test:unit
#RUN npm run test:e2e
RUN npm run build-only

FROM nginx:stable-alpine
COPY --from=build /src/dist /usr/share/nginx/html
