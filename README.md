# Developer Games - 3scale challenge

### User 10 GUID
    cluster-kc2df.kc2df.sandbox790

## URLs
### Openshift Console:
https://console-openshift-console.apps.cluster-kc2df.kc2df.sandbox790.opentlc.com

### 3scale 
https://user10-admin.apps.cluster-kc2df.kc2df.sandbox790.opentlc.com/

### APICurio
http://apicurio-studio.apps.cluster-kc2df.kc2df.sandbox790.opentlc.com/

### SSO
http://sso-rh-sso.apps.cluster-kc2df.kc2df.sandbox790.opentlc.com/auth/admin/user10/console/

3scale-admin user10 secret 
```
22c1738b-c84b-47dd-8b49-113a4599fd93
```

toolbox_token (scope account management api, read & write)
```
d196db0cb8ba10747060eff9e86875f11998d139798af21e983bb101a2ffe4dd
```

### GIT GOGS

http://gogs.apps.cluster-kc2df.kc2df.sandbox790.opentlc.com/user/login

ESTO NO ME FUNCIONA!!! No puedo entrar al GIT para importar mi repositorio. Supongo que podría decirle a jenkns que escanee el repositorio directamente desde github.


#### Ejecuto en consola:

```
oc login https://api.cluster-kc2df.kc2df.sandbox790.opentlc.com:6443 -p openshift -u user10

 3scale remote add 3scale-onprem "https://d196db0cb8ba10747060eff9e86875f11998d139798af21e983bb101a2ffe4dd@user10-admin.apps.cluster-kc2df.kc2df.sandbox790.opentlc.com/" -k

oc create secret generic 3scale-toolbox -n user10 --from-file="/home/user/.3scalerc.yaml"
```
| NAME | TYPE | DATA | AGE |
|------|-----|--|--|
|3scale-toolbox| Opaque|1|6h44m|

```
oc login https://api.cluster-kc2df.kc2df.sandbox790.opentlc.com:6443 -p openshift -u user10
```

## Esto es lo que me falla

Con mi proyecto GIT:
```
oc new-build https://github.com/ndobler/3scale-challenge.git#main --name=library-core-pipeline -n user10
```

Con el proyecto Git de Fabrizio:
```
oc new-build https://github.com/artudf/library_Core#main --name=library-core-pipeline -n user10
```


### URL SSO

http://3scale-admin:22c1738b-c84b-47dd-8b49-113a4599fd93@sso-rh-sso.apps.cluster-kc2df.kc2df.sandbox790.opentlc.com/auth/realms/user10

secureapp 
    id 9d5963d5
    secret  5b4e44a0d3fc2c93dabd714341c88b29

 http://sso-rh-sso.apps.cluster-kc2df.kc2df.sandbox790.opentlc.com/auth/realms/user10/protocol/openid-connect/auth

 http://sso-rh-sso.apps.cluster-kc2df.kc2df.sandbox790.opentlc.com/auth/realms/user10/protocol/openid-connect/token

 ## Fabrinstructions :)

 - [x] seguir los pasos lab3 lab 4
- [ ] Despues saltar al lab204 y 205
- [ ] Pon un fichero Jenkins file en el proyecto
    - https://github.com/rh-integration/3scale-toolbox-jenkins-samples/blob/master/multi-environment-usecase/Jenkinsfile
    - Del ejemplo pienso que solo necesitamos la parte de prod

De mi cosecha he agregado el setup.yaml

En el jenkinsfile he modificado algunas variables, pero otras no estoy seguro