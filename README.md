# Unofficial Docker Images for mise-en-place

This repository provides unofficial Docker images for [mise-en-place](https://mise.jdx.dev/), a polyglot tool manager.

## Registries

The images are available on both GitHub Container Registry (GHCR) and Docker Hub:

- **GHCR:** `ghcr.io/amartani/mise-images`
- **Docker Hub:** `amartani/mise`

## Usage

You can use these images as a base for your own Dockerfiles or run them directly:

```bash
docker run amartani/mise:bookworm mise exec python@3.12 -- python -c 'print("hello world")'
```

Or in a Dockerfile:

```dockerfile
FROM amartani/mise:bookworm-slim
RUN mise use -g node@20
```

## Supported Tags

The images are built using Debian as the base OS. The following Debian versions are supported:

- `sid` (Unstable)
- `bookworm` (Stable)
- `trixie` (Testing)
- `forky` (Upcoming)

Each version is available in two variants:
- **Default:** Standard Debian base.
- **-slim:** A smaller image based on Debian's slim variant.

### Tag Formats

- `<debian-codename>[-slim]` (e.g., `bookworm`, `bookworm-slim`) - Points to the latest `mise` version.
- `<mise-version>-<debian-codename>[-slim]` (e.g., `2024.5.1-bookworm`) - Points to a specific `mise` version.
- `<debian-codename>-<date>[-slim]` (e.g., `bookworm-20240525`) - Points to a specific Debian image snapshot.
- `<mise-version>-<debian-codename>-<date>[-slim]`
