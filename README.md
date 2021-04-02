# Microservices

## Setup

    $ npm init -y
    $ npm install typescript ts-node-dev express @types/express

    $ tsc --init

    $ docker build -t evaou/auth .

    // infra/k8s/ingress-srv.yaml
    $ vim /etc/hosts

## Run

    // infra/k8s/auth-depl.yaml
    // skaffold.yaml
    $ skaffold dev

## Tip

- Skip HTTPS warning in chrome
    - type ```thisisunsafe``` anywhere in page
