FROM golang:1.22.5 AS base
# using golang image as base images

WORKDIR /app

COPY go.mod .
#copying go.mod file to install dependencies

RUN go mod download
#installing all the depnedencies

COPY . .
#copying all the source code

RUN go build -o main .

#using distroless image for the final stage
FROM golang:1.22.6-alpine3.20 AS final

COPY --from=base /app/main .

COPY --from=base /app/static ./static

EXPOSE 8080
#exposing the port 

cmd ["./main"]
