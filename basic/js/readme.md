### Prerequisite

Make sure metacontroller is [installed](https://github.com/shovanmaity/metacontroller-by-example/tree/master/metacontroller).

Make sure you are inside `basic/js` directory.

### Do it yourself

Edit the `../deploy/controller.yaml` file and update the URL.
```yaml
spec:
  hooks:
    sync:
      webhook:
        url: http://192.168.1.15:8080/sync
```

Apply the crd and controller.
```bash
kubectl apply -f ../deploy/controller.yaml
kubectl apply -f ../deploy/crd.yaml
```

Update dependency and run the js file
```bash
npm install
node sync.js
```

Create a ping cr. Find the sample `Ping` is [here](https://github.com/shovanmaity/metacontroller-by-example/blob/master/basic/deploy/ping.yaml).
```bash
cat <<EOF | kubectl apply -f -
apiVersion: example.com/v1
kind: Ping
metadata:
  name: shovan
spec:
  name: Shovan Maity
EOF
```

Check the `Pong` cr and validate the message. `Pong` cr will be created in the same namespace in which `Ping` cr is present.
```bash
kubectl get pong -A
kubectl get pong -A -o=jsonpath='{range .items[*]}{@.spec.message}{"\n"}{end}'
```

### Cleanup

```bash
kubectl delete ping -A --all
kubectl delete -f ../deploy/controller.yaml
kubectl delete -f ../deploy/crd.yaml
# Stop the javascript file execution.
```
