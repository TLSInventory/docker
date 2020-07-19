FROM golang:alpine

# maybe use --no-cache to update apk

# git needed for go get and git clone
# openssl is used to download cert
# make is needed to compile zcertificate
RUN apk add git openssl make

# python 3 is used for json beautifing
RUN apk add python3 

RUN go get github.com/zmap/zlint/v2/cmd/zlint

RUN git clone --depth=50 --branch=master https://github.com/zmap/zcertificate.git zmap/zcertificate
WORKDIR /go/zmap/zcertificate
RUN apk add make
RUN make

WORKDIR /go

# The following is just an example
RUN echo -n | openssl s_client -connect example.com:443 | sed -ne '/-BEGIN CERTIFICATE-/,/-END CERTIFICATE-/p' > test1.cert
# RUN zlint test1.cert | python3 -m json.tool

RUN zlint -pretty test1.cert

RUN ./zmap/zcertificate/zcertificate test1.cert | python3 -m json.tool

