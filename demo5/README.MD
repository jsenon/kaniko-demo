# Demo5 Knative

This is a Repository of sample in order to show traffic spliting

## Func

Deploy application and demonstrate manual traffic spliting

## Prerequisite

## Demo

### Part1

Deploy first version of application:
```
kubectl apply -f service1.yaml
```

Test Application:
```
curl -H "Host: route-demo.default.example.com" http://af4af4<REDACTED>.amazonaws.com
```

Deploy second version:
```
kubectl apply -f service2.yaml
```

Refresh v1 Application:
```
curl -H "Host: route-demo.default.example.com" http://af4af4<REDACTED>.amazonaws.com

```

Test v2 Application:
```
curl -H "Host: v2.route-demo.default.example.com" http://af4af4<REDACTED>.amazonaws.com
```

All traffics is redirected to the v1, expect if you specified dedicated route to the v2

### Part2

Now we will split traffic to v1 and v2:
```
kubectl apply -f service3.yaml
```

Refresh url:

```
curl -H "Host: route-demo.default.example.com" http://af4af4<REDACTED>.amazonaws.com
```

### Part3

Now we will redirect all traffic to v2:
```
kubectl apply -f service4.yaml
```

Refresh url:
```
curl -H "Host: route-demo.default.example.com" http://af4af4<REDACTED>.amazonaws.com
```

You can acces to the old v1:
```
curl -H "Host: v1.route-demo.default.example.com" http://af4af4<REDACTED>.amazonaws.com
```

## Remarks

Based on https://github.com/mchmarny/knative-route-demo