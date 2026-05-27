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

## Supported Platforms

The images are available for the following architectures:
- `amd64` (x86_64)
- `arm64` (AArch64)

These are the platforms supported by the upstream `mise` apt repository.

## Supported Tags

The images are built using Debian as the base OS. The following Debian versions are supported:

- `bookworm` (Stable)
- `trixie` (Testing)
- `forky` (Experimental)
- `sid` (Unstable)

Each version is available in several variants:
- **Default:** Standard Debian base.
- **-slim:** A smaller image based on Debian's slim variant.
- **-buildpack:** Based on [`buildpack-deps`](https://hub.docker.com/_/buildpack-deps), which includes many development headers and libraries.
- **-buildpack-curl:** Based on `buildpack-deps:<codename>-curl`, includes `curl` and `ca-certificates`.
- **-buildpack-scm:** Based on `buildpack-deps:<codename>-scm`, includes `curl`, `ca-certificates`, and SCM tools like `git` and `mercurial`.

### Tag Formats

- `<debian-codename>[-slim]` (e.g., `bookworm`, `bookworm-slim`) - Points to the latest `mise` version.
- `<mise-version>-<debian-codename>[-slim]` (e.g., `2024.5.1-bookworm`) - Points to a specific `mise` version.
- `<debian-codename>-<date>[-slim]` (e.g., `bookworm-20240525`) - Points to a specific Debian image snapshot.
- `<mise-version>-<debian-codename>-<date>[-slim]`
