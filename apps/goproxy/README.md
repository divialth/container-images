# goproxy container

Container image for [snail007/goproxy](https://github.com/snail007/goproxy), based on `ghcr.io/linuxserver/baseimage-alpine`.

## What this image does

- Downloads the prebuilt `goproxy` release binary during image build.
- Starts `proxy` under s6 supervision.
- On first start, initializes `/config` with:
  - `blocked`
  - `direct`
  - `proxy.crt` and `proxy.key` (generated with `proxy keygen`)
  - `${GOPROXY_INSTANCES_DIR}` (default `/config/instances.d`)

## Runtime modes

`GOPROXY_MODE` controls process startup:

- `auto` (default)
  - If valid `*.args` files exist in `${GOPROXY_INSTANCES_DIR}`, runs multi mode.
  - Otherwise runs plain mode.
- `plain`
  - Runs one `proxy` process from `GOPROXY_ARGS`.
- `multi`
  - Runs one process per `${GOPROXY_INSTANCES_DIR}/*.args` file.
  - Fails if no valid instance files are found.

## Environment variables

- `GOPROXY_MODE` (default: `auto`)
- `GOPROXY_ARGS` (default: `http -p :8080`)
- `GOPROXY_INSTANCES_DIR` (default: `/config/instances.d`)
- `GOPROXY_STRICT_ARGS` (default: `true`)
  - `true`: malformed or empty instance files fail startup in multi mode.
    In `auto` mode, parse failures with `true` also fail startup.
  - `false`: malformed or empty instance files are skipped.

## Instance file format (multi mode)

- Location: `${GOPROXY_INSTANCES_DIR}` (default `/config/instances.d`)
- Pattern: `*.args`
- One argument per line.
- `#` comment lines and blank lines are ignored.

Example `http-8080.args`:

```text
http
-p
:8080
--nolog
```

Example `socks-1080.args`:

```text
socks
-p
:1080
--intelligent
direct
```

Sample files are provided in `apps/goproxy/examples/instances.d`.

## Example: plain mode (env only)

```yaml
services:
  goproxy:
    image: ghcr.io/divialth/goproxy:main
    container_name: goproxy
    restart: unless-stopped
    ports:
      - "18080:18080"
    volumes:
      - ./config:/config
    environment:
      - PUID=1000
      - PGID=1000
      - TZ=UTC
      - GOPROXY_MODE=plain
      - GOPROXY_ARGS=http -p :18080 --nolog
```

## Example: auto mode with multi instances

```yaml
services:
  goproxy:
    image: ghcr.io/divialth/goproxy:main
    container_name: goproxy
    restart: unless-stopped
    ports:
      - "8080:8080"
      - "1080:1080"
    volumes:
      - ./config:/config
    environment:
      - PUID=1000
      - PGID=1000
      - TZ=UTC
      - GOPROXY_MODE=auto
```

`./config/instances.d/http-8080.args`:

```text
http
-p
:8080
```

`./config/instances.d/socks-1080.args`:

```text
socks
-p
:1080
--intelligent
direct
```

In `auto` mode, valid instance files take precedence over `GOPROXY_ARGS`.
If no valid instance files are present, it falls back to plain mode (`GOPROXY_ARGS`).

## Example: multi mode (same files, stricter behavior)

```yaml
services:
  goproxy:
    image: ghcr.io/divialth/goproxy:main
    restart: unless-stopped
    ports:
      - "8080:8080"
      - "1080:1080"
    volumes:
      - ./config:/config
    environment:
      - GOPROXY_MODE=multi
      - GOPROXY_STRICT_ARGS=true
```

`./config/instances.d/http-8080.args`:

```text
http
-p
:8080
```

`./config/instances.d/socks-1080.args`:

```text
socks
-p
:1080
--intelligent
direct
```

This uses the same instance files as the auto example above.
Difference vs auto mode:
- `auto`: uses multi when valid instance files exist, otherwise falls back to plain mode.
- `multi`: requires valid instance files and does not fall back.

## Volumes

- `/config` for runtime files, generated certs, and `instances.d`.

## Upstream references

- Project: https://github.com/snail007/goproxy
- Manual: https://snail007.github.io/goproxy/manual/
