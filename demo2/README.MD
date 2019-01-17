# Demo2 Knative

This is a Repository of sample in order to build form source with kanico and knative

## Func

Deploy application from an existing docker image

## Prerequisite

## Demo

Deploy your application:
```
kubectl apply --filename service.yaml
```

Retrieve your knative istio ingress gateway
```
kubectl get svc knative-ingressgateway --namespace istio-system
```

Check your knative application url
```
kubectl get ksvc
```

Perfom Test:
```
curl -H "Host: helloworld-go.default.example.com" http://af4<REDACTED>.amazonaws.com
