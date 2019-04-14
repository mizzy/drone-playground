# Drone playground

## References

- [Drone CI – Automate Software Testing and Delivery](https://drone.io/)
- [Kubernetes](https://docs.drone.io/installation/github/kubernetes/)
- [Expose Kubernetes services over HTTPS with Ngrok](https://stefanprodan.com/2018/expose-kubernetes-services-over-http-with-ngrok/)

## Prerequisite


To use `envsubst`, you must install `gettext`.

```
$ brew install gettext
$ brew link --force gettext
```

Create an oAuth App on GitHub according to [Kubernetes](https://docs.drone.io/installation/github/kubernetes/).


Set environment variables.

```
export DRONE_GITHUB_CLIENT_ID=xxxxx
export DRONE_GITHUB_CLIENT_SECRET=xxxxx
export DRONE_RPC_SECRET=xxxxx
export DRONE_SERVER_HOST=xxxxx
```


## Setup the Drone on Kubernetes

```
$ kubectl create ns drone
$ kubens drone
$ envsubst < drone.yaml | kubectl apply -f -
$ kubectl port-forward deployment/drone 8080:80
```

