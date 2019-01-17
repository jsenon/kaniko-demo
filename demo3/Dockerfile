FROM golang:alpine
RUN apk --no-cache add git \
&& go get github.com/triggermesh/aws-custom-runtime \
&& go get github.com/triggermesh/knative-lambda-runtime/go-1.x \
&& go get github.com/golang/dep/...

WORKDIR /go/src/handler
COPY . .
RUN if [ -f "Gopkg.toml" ]; then dep ensure; fi
RUN go get -v && go install

FROM alpine
WORKDIR /opt

ENV LAMBDA_TASK_ROOT "/opt"
ENV _HANDLER "handler"

COPY --from=0 /go/bin/go-1.x /opt/bootstrap
COPY --from=0 /go/bin/ /opt

ENTRYPOINT ["/opt/aws-custom-runtime"]