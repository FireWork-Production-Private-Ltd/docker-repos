# Docker-Repos

- this will have `config` and `express` package under its docker image.

## workflow
```yml
name: Build and Push Docker Image to Docker Hub

on: push
jobs:
  push_to_registry:
    name: push docker image to hub
    runs-on: ubuntu-latest
    steps:
      - name: check repository
        uses: actions/checkout@v4

      - name: login to docker registry
        uses: docker/login-action@v3
        with:
          username: ${{secrets.DOCKERHUB_USERNAME}}
          password: ${{secrets.DOCKERHUB_TOKEN}}

      - name: build and push docker image to registry
        uses: docker/build-push-action@v5
        with:
          context: DockerFileFolder/
          push: true
          tags: black1512/demo1:latest

```

- you need to specify your `DOCKERHUB_USERNAME` and `DOCKERHUB_TOKEN` inside your repos secrets.

# Docker Registry
- This will update `https://hub.docker.com/r/black1512/demo1` docker registry.
```zsh
# pull this image by
docker pull black1512/demo1:latest
```
