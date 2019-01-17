# Demo1 Knative

This is a Repository of sample in order to build form source with kanico and knative

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