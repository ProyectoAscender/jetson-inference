
# Imagen

La imagen que se está utilizando es:

`dustynv/jetson-inference:r35.3.1`

Corresponde a una imagen pública de nvidia en dockerhub.


Primero hay que preparar el repositorio, así que dentro de la carpeta jetson-inference`
`git submodule update --init`

El comando para ejecutarlo es:

`bash docker/run.sh --run "video-viewer data/b2drop/smartCity/barcelona/urgell/videos/0003_01.mp4  rtp://239.255.12.40:5000 --input-loop=1000`

Esta línea ejecuta dentro del contenedor un loop de 10000 iteraciones de un vídeo de 2 min. Pero cambiando la ruta del mp4 se cambia fácilmente le vídeo que quieres emitir. Esa ruta corresponde a los vídeos en b2drop que se montan dentro del contendor. Si el contenedor se para, se detendrá y borrará automaticamente.

La ruta rtp es la ruta en la que se emitirá el streaming. (Nota ,el streaming es multicast, así que mas de un proceso puede leerlo). Puedes elegir la ip , pero no el puerto, que siempre tiene que ser 5000.

Camera-edge leerá el streaming de vídeo en esta ip, siempre y cuando esté configurado en data/all_cameras.yaml (`input: !<!> "239.255.12.40"`) del proyecto camera-edge.

