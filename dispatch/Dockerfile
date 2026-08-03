FROM golang:1.24

WORKDIR /go/src/app

COPY *.go ./

RUN go mod init dispatch
RUN go mod tidy
RUN go build -o dispatch

CMD ["./dispatch"]
