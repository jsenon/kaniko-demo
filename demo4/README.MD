# Demo4 Knative

This is a Repository of sample in order to show autoscalling functionalities

## Func

Deploy application and demonstrate autoscalling

## Prerequisite

- Knative metrics
- The `hey` load generator installed (`go get -u github.com/rakyll/hey`)

## Demo

Install service:
```
kubectl apply -f service.yaml
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
curl -H "Host: autoscale-go.default.example.com" "http://af4<REDACTED>.amazonaws.com?sleep=100&prime=10000&bloat=5"
```

Send traffic:
```
hey -z 30s -c 50 \
  -host "autoscale-go.default.example.com" \
  "http://af4<REDACTED>?sleep=100&prime=10000&bloat=5" \
  && kubectl get pods
```

And check new pod created:
```
kubectl get pods -n default --watch
```

## Remarks

Observe that your deployment will scale down to zero if your function is never used