# Unofficial Docker Images for mise-en-place

This repository provides unofficial Docker images for [mise-en-place](https://mise.jdx.dev/), a polyglot tool manager.

## Registries

The images are available on both GitHub Container Registry (GHCR) and Docker Hub:

- **GHCR:** `ghcr.io/amartani/mise-images`
- **Docker Hub:** `amartani/mise`

## Usage

You can use these images as a base for your own Dockerfiles or run them directly:

```bash
docker run amartani/mise:trixie mise exec python@3.12 -- python -c 'print("hello world")'
```

Or in a Dockerfile:

```dockerfile
FROM amartani/mise:trixie-slim
RUN mise use -g node@20
```

## Supported Tags

The images are built using Debian as the base OS. The following Debian versions are supported:

- `bookworm` (Old Stable)
- `trixie` (Stable)
- `forky` (Testing)
- `sid` (Unstable)

Each version is available in several variants:
- **Default:** Standard Debian base.
- **-slim:** A smaller image based on Debian's slim variant.
- **-buildpack:** Based on [`buildpack-deps`](https://hub.docker.com/_/buildpack-deps), which includes many development headers and libraries.
- **-buildpack-curl:** Based on `buildpack-deps:<codename>-curl`, includes `curl` and `ca-certificates`.
- **-buildpack-scm:** Based on `buildpack-deps:<codename>-scm`, includes `curl`, `ca-certificates`, and SCM tools like `git` and `mercurial`.

### Tag Formats

- `<debian-codename>[-variant]` (e.g., `trixie`, `trixie-slim`, `trixie-buildpack`) - Points to the latest `mise` version.
- `<mise-version>-<debian-codename>[-variant]` (e.g., `2024.5.1-trixie`) - Points to a specific `mise` version.
- `<mise-version>-<debian-codename>-<date>[-variant]` (e.g., `2024.5.1-trixie-20240525`) - Points to a specific `mise` version and a specific Debian image snapshot.
