# Microservices

## Setup

    $ npm init -y
    $ npm install typescript ts-node-dev express @types/express

    $ tsc --init

    $ docker build -t evaou/auth .

## Run

    // infra/k8s/auth-depl.yaml
    // skaffold.yaml
    $ skaffold dev
