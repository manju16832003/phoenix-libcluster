# PhoenixLibcluster

To start your Phoenix app:

  * Install dependencies with `mix deps.get`
  * Create and migrate your database with `mix ecto.create && mix ecto.migrate`
  * Install Node.js dependencies with `npm install`
  * Start Phoenix endpoint with `mix phoenix.server`

Now you can visit [`localhost:4000`](http://localhost:4000) from your browser.


### Run clustering Locally

To make this work, local dev servers need to be started in "named" mode. For example, to start 2 named nodes on the same machine:

```
PORT=4000 elixir --name n1@127.0.0.1 -S mix phoenix.server &
PORT=4001 elixir --name n2@127.0.0.1 -S mix phoenix.server
```

In development, the topology is fixed and uses the built-in erlang discovery.


### Run on Kubernetes

* Install minikube (https://kubernetes.io/docs/tutorials/stateless-application/hello-minikube/)
* Create a Docker container image
  ```
  eval $(minikube docker-env)
  docker build -t libcluster:v1 .
  ```
* Create Kubernetes deployment file
  `kubectl create -f k8s.yaml`
  
* See Pods
  `kubectl get pods`
  
* Run the Service
  `minikube service phoenix-libcluster`


#### References

http://learnyousomeerlang.com/distribunomicon

https://github.com/bitwalker/libcluster

http://bitwalker.org/posts/2016-08-04-clustering-in-kubernetes/

https://github.com/NetComposer/nkcluster

http://erlangonxen.org/more/clustering

https://dockyard.com/blog/2016/01/28/running-elixir-and-phoenix-projects-on-a-cluster-of-nodes

