# Mi imagen en Docker Hub

Llena este archivo en **tu copia**, dentro de
`estudiantes/<tu-login>/08_contenedores/`.

## Quién soy, en los dos lados

- Usuario de GitHub:LuisRyes
- Usuario de Docker Hub:luisryes

No tienen por qué ser el mismo, y los nombres de imagen **van en minúsculas
siempre**.

## La URL pública

La que sirve es `https://hub.docker.com/r/<tu-usuario>/<tu-imagen>`. La que te
da el navegador cuando estás con tu sesión abierta empieza con
`hub.docker.com/repository/docker/` y **da 404 a todos los demás, incluido yo**.
Ábrela en una ventana privada antes de entregar.

URL:https://hub.docker.com/r/luisryes/mi-imagen

## El digest

```text
docker inspect --format '{{index .RepoDigests 0}}' <tu-usuario>/<tu-imagen>
luisfernandoreyesaltamirano@MacBook-Air-de-Luis-4 fdd_o26_LuisRyes % docker inspect --format '{{index .RepoDigests 0}}' luisryes/mi-imagen:v1
luisryes/mi-imagen@sha256:6c445695389bad5b9a7936fdd2b7116366cb961d8d2a44a8b5f398447b06fd94
```

## Cómo la corro yo

Comando exacto:

```text
docker run --rm luisryes/mi-imagen:v1
```

Salida que debo esperar:

```text
Corriendo como: root
requests 2.32.3
```

## La prueba de que se baja del registro

Pega la salida **completa**, con sus líneas `Unable to find image locally` y
`Pulling from`:

```text
docker logout
docker rmi -f <tu-usuario>/<tu-imagen>
docker run --rm <tu-usuario>/<tu-imagen>

luisfernandoreyesaltamirano@MacBook-Air-de-Luis-4 fdd_o26_LuisRyes % docker logout
Removing login credentials for https://index.docker.io/v1/
luisfernandoreyesaltamirano@MacBook-Air-de-Luis-4 fdd_o26_LuisRyes % docker rmi -f luisryes/mi-imagen:v1
Untagged: luisryes/mi-imagen:v1
Deleted: sha256:6c445695389bad5b9a7936fdd2b7116366cb961d8d2a44a8b5f398447b06fd94
luisfernandoreyesaltamirano@MacBook-Air-de-Luis-4 fdd_o26_LuisRyes % docker run --rm luisryes/mi-imagen:v1
Unable to find image 'luisryes/mi-imagen:v1' locally

What's next:
    Debug this container error with Gordon → docker ai "help me fix this container error"
docker: Error response from daemon: no matching manifest for linux/arm64/v8 in the manifest list entries: no match for platform in manifest: not found

Run 'docker run --help' for more information
luisfernandoreyesaltamirano@MacBook-Air-de-Luis-4 fdd_o26_LuisRyes % docker run --platform linux/amd64 --rm luisryes/mi-imagen:v1
Unable to find image 'luisryes/mi-imagen:v1' locally
v1: Pulling from luisryes/mi-imagen
a6ec7710ba76: Pull complete 
29ca634d3e9b: Pull complete 
0380fc010d91: Pull complete 
61fd4a0539f5: Pull complete 
44136fa355b3: Already exists 
e88021c77ba5: Download complete 
Digest: sha256:6c445695389bad5b9a7936fdd2b7116366cb961d8d2a44a8b5f398447b06fd94
Status: Downloaded newer image for luisryes/mi-imagen:v1
Corriendo como: root
requests 2.32.3
```

## El tamaño

Menos de 300 MB. Pega la salida con el tamaño visible:

```text
docker images <tu-usuario>/<tu-imagen>

luisfernandoreyesaltamirano@MacBook-Air-de-Luis-4 fdd_o26_LuisRyes % docker images luisryes/mi-imagen:v1
                                                                                                                                                                                      i Info →   U  In Use
IMAGE                   ID             DISK USAGE   CONTENT SIZE   EXTRA
luisryes/mi-imagen:v1   6c445695389b        195MB         47.7MB     
```
