FROM golang:alpine as  builder
RUN mkdir /build
ADD . /build/
WORKDIR /build
RUN go build -o main .

#stage2

FROM alpine 
RUN  adduser -s -d  -H -h /app appuser
USER appuser

COPY . /app
COPY   --from=builder /builder/main /app
WORKDIR /app

EXPOSE 1999
CMD [ "./main" ]

