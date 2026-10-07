# Compose apps

Container images and Foundries composeapps, built independently of the Yocto
images in the sibling `../meta-foundries` repository.

- `matrix/`: Matrix web application for AMD64 and ARM64.
- [`led-matrix-anim/`](led-matrix-anim/README.md): UNO Q LED matrix firmware and controller
  for ARM64, with build, test, installation, and recovery instructions.

The GitHub Actions workflow builds and pushes images to GHCR, publishes
composeapps with pinned image digests, and uploads their URIs as workflow
artifacts. It runs on self-hosted Linux X64 runners and uses the configured
`COMPOSECTL` path. Archive and update-server assembly are not configured.

Validate locally:

```sh
python3 -B -m unittest discover -s led-matrix-anim/tests -v
docker compose -f matrix/docker-compose.yml config --quiet
docker compose -f led-matrix-anim/docker-compose.yml config --quiet
```
