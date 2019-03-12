# chaosEngineeringTalk
Chaos Engineering Talk


## Prerequisitos

Instancia de K8s con 1 nodo master y al menos 2 workers
Sacar tu cuenta de Gremlins

Tener helm instalado

## Instalar Gremlin en k8s

### Crear secret en k8s
Descargar tu certificado de Gremlins .priv_key.pem   y   pub_cert_pem

Renombra los archivos a gremlin.cert y gremlin.key

Crea el secret en tu cluster de k8s

kubectl create secret generic gremlin-team-cert --from-file=./gremlin.cert --from-file=./gremlin.key

kubectl get secrets

### Instalar gremlin con helm

helm repo add gremlin https://helm.gremlin.com

helm install --set gremlin.teamID=YOUR-TEAM-ID gremlin/gremlin

helm install --set gremlin.teamID=a92c66cf-8c2e-505c-bf59-0adcef8680de gremlin/gremlin



## Referencias

https://www.gremlin.com/community/tutorials/how-to-install-and-use-gremlin-with-kubernetes/

