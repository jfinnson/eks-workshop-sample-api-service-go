# build stage
FROM golang:alpine AS build-env
ADD src /src
RUN cd /src && go build -o hello_k8s main.go

# final stage
FROM alpine
WORKDIR /app
COPY --from=build-env /src/hello_k8s /app/
EXPOSE 8080
RUN ["chmod", "+x", "./hello_k8s"]
ENTRYPOINT ./hello_k8s