# Demo3 Knative

This is a Repository of sample in order to use AWS Lambda function with knative

## Func

Build and deploy application from source code hosted in Github and push artifact to docker registry

## Prerequisite

- Have set credential for your remote registry

## Demo

Deploy buildtemplate for kanico:

```
kubectl apply -f ../buildtemplate/kaniko.yaml
```

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
curl -H "Host: lambda.default.example.com" http://af4<REDACTED>.amazonaws.com --data '{"Name": "Miam"}'

