FROM alpine:latest AS build
RUN apk add npm --no-cache
WORKDIR /frontend
COPY ./frontend /frontend
RUN npm install && npm run build

FROM alpine:latest
COPY --from=build /frontend/build /build
RUN apk add npm --no-cache && npm install -g serve
ENTRYPOINT [ "serve" ]
EXPOSE 3000
CMD ["-s", "build"]
