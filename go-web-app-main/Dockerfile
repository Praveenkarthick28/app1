FROM golang:1.22.5 AS base
# using golang image as base images

WORKDIR /apps

COPY go.mod .
#copying go.mod file to install dependencies

RUN go mod download
#installing all the depnedencies

COPY . .
#copying all the source code

RUN go run main.go

#using distroless image for the final stage
FROM golang:1.22.6-alpine3.20 AS final

COPY --from=base /apps/main .

COPY --from=base /apps/static .

EXPOSE 8080
#exposing the port 

cmd ["go", "run", "main"]
