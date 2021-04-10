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

    $ npm install mongoose @types/mongoose

    $ npm install cookie-session @types/cookie-session
    $ npm install jsonwebtoken @types/jsonwebtoken

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

## Test

    $ npm install --save-dev @types/jest @types/supertest jest ts-jest supertest mongodb-memory-server
    $ npm run test

## Client Setup

    $ cd client
    $ npm init -y
    $ npm install react react-dom next

    $ docker build -t evaou/client .
    $ docker push evaou/client

    $ skaffold dev

    $ npm install bootstrap

## Tip

- Skip HTTPS warning in chrome
  - type `thisisunsafe` anywhere in page
- leverage [npm libraries](https://www.npmjs.com/)
- [base64 decode and encode](https://www.base64decode.org/)
- [jwt.io](https://jwt.io/ to )
  - decode and generate JWT
  - use JWT signing key to verify JWT
- create secret

  $ kubectl create secret generic jwt-secret --from-literal=JWT_KEY=\<JWT-signing-key\>\
  $ kubectl get secret

- have next pod apply config

  $ kubectl get pods
  $ kubectl delete pod <next-service-pod-name>

## Term

### Cookie vs JWT

|                Cookie                |                  JWT                   |
| :----------------------------------: | :------------------------------------: |
|         Transport mechanism          | Authentication/Authorization mechanism |
| Move data between browser and server |               Store data               |
|   Automatically managed by browser   |            Manage manually             |

### Cookie

- not encrypt Cookie data for cross-language handling

### JWT

- Json Web Token
- in Headers Authorization or Cookie
- in Body token

### SSR

- Server Side Rendering
- return a rendered HTML file
- good for SEO
- need to know auth info with the first reqeust
