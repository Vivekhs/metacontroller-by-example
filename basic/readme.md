### Overview

In this section, we will discuss on how we can run these controllers in the local environment. One prerequisite is your local machine’s IP must be reachable from the Kubernetes cluster in which the meta-controller is running. You can use some tools like local-tunnel to get a public IP. I am using [k3s](https://k3s.io) in my local setup and my local machine’s IP is reachable from any pod. If meta-controller is not installed then you need to [install](https://github.com/shovanmaity/metacontroller-by-example/tree/master/metacontroller) it. In these example we will use 2 crd `Ping` and `Pong`. For custom resource `Ping` we will create a controller. In `Ping` cr we will provide name and other details. Controller will create a `Pong` resource for each `Ping` in which we can find a greeting message with the details.

### Example Controller
- [Go](https://github.com/shovanmaity/metacontroller-by-example/tree/master/basic/go)
- [Python](https://github.com/shovanmaity/metacontroller-by-example/tree/master/basic/python)
- [JavaScript](https://github.com/shovanmaity/metacontroller-by-example/tree/master/basic/js)