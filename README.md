# Microservices

## Setup

    $ npm init -y
    $ npm install typescript ts-node-dev express @types/express

    $ tsc --init

    $ docker build -t evaou/auth .

    // infra/k8s/ingress-srv.yaml
    $ vim /etc/hosts

    $ npm install express-validator

    $ npm install express-async-errors

    $ npm install mongoose

## Run

    // infra/k8s/auth-depl.yaml
    // skaffold.yaml
    $ skaffold dev

## GCP

- create k8s cluster
- install [SDK](https://cloud.google.com/sdk/docs/quickstart)
- `$ gcloud container clusters get-credentials ticketing-dev`
- step

  1. enable google cloud build
  2. update skaffold.yaml and auth-depl.yaml
  3. set up [ingress-nginx](https://kubernetes.github.io/ingress-nginx/deploy/)

     ```
     $ kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/controller-v0.44.0/deploy/static/provider/cloud/deploy.yaml
     $ kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/controller-v0.44.0/deploy/static/provider/cloud/deploy.yaml
     ```

  4. update /etc/hosts

     - outside > load balancer on GCP > ingress controller on k8s cluster > pod
     - GCP > Network services > Load balancing > name > ip

  5. `$ skaffold dev`

## Tip

- Skip HTTPS warning in chrome
  - type `thisisunsafe` anywhere in page
- leverage [npm libraries](https://www.npmjs.com/)
