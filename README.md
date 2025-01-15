Explicación del Workflow:
on.push.paths: Este bloque asegura que el pipeline solo se ejecute cuando haya un cambio en index.html, Dockerfile, o docker-compose.yml.
actions/checkout@v2: Obtiene el código del repositorio.
docker/setup-buildx-action@v2: Configura Docker Buildx, que es necesario para crear y subir imágenes Docker.
docker/login-action@v2: Inicia sesión en Docker Hub (aquí deberías agregar tus credenciales en los secretos de GitHub).
docker build: Construye la imagen Docker utilizando el Dockerfile en el directorio actual.
docker push: Subir la imagen construida al Docker Hub.
Deploy (Docker Compose): En este caso, el servidor de destino usa Docker Compose. Asegúrate de que tu servidor tenga configurado Docker y Docker Compose. La instrucción docker-compose down detiene los contenedores actuales, y docker-compose up -d los vuelve a levantar con la nueva imagen.