# Chaos Engineering Talk

Platica de Ingenieria de Chaos con Gremlin

Este es el material de la platica sobre ingenieria del chaos para la comunidad de [Cloud Native MX](https://cloudnative.mx/)


## Prerequisitos

Para la demo vamos a usar un ambiente de Kubernetes levantado en GCP.

Las especificaciones de Gremlin indican al menos 1 nodo master y 2 workers.

Tener cuenta de Gremlin, hay una versión gratuita.

## Instalación de Gremlin en k8s

### Crear secret en k8s

Primero tienes que descargar tus certificados de Gremlin .priv_key.pem   y   pub_cert_pem

Renombra los archivos a gremlin.cert y gremlin.key

Crea el secret en tu cluster de k8s

```
kubectl create secret generic gremlin-team-cert --from-file=./gremlin.cert --from-file=./gremlin.key
```

Así de simple :)   

Puedes consultar el secret con el siguiente comando:

```sh
kubectl get secrets
```

### Instalar gremlin con helm

Para la instalación de los componentes de Gremlin en el ambiente, necesitas instalar previamente Helm, esta [guía](https://helm.sh/docs/using_helm/) puede ayudarte.

Una vez instalado Helm es tan sencillo como agregar el repositorio de Gremlin 

```
helm repo add gremlin https://helm.gremlin.com
```

Despues lo único que debes de hacer es instalar el componente de Gremlin indicandole el ID de tu equipo de trabajo definido en la aplicación de Gremlin.

```
helm install --set gremlin.teamID=YOUR-TEAM-ID gremlin/gremlin
```

Y listo puedes iniciar el chaos en tu ambiente :P

## Referencias

[Gremlin](https://www.gremlin.com/)

[Como instalar Gremlin en k8s](https://www.gremlin.com/community/tutorials/how-to-install-and-use-gremlin-with-kubernetes/)
