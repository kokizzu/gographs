# GoGraphs

[GoGraphs](https://gographs.io) renders dependency graphs for Go packages:

![GoGraphs dependency example](https://gographs.io/repo/github.com/siggy/gographs.svg?cluster=false "GoGraphs Dependencies")

## Local dev

### First-time setup

```bash
go get github.com/loov/goda
brew install dot # or equivalent
brew install redis # or equivalent
redis-server /usr/local/etc/redis.conf
```

### Boot server

```bash
go run main.go
```

Browse to http://localhost:8888

## HTTP Endpoints

### GET /

Defaults to rendering this Go package.

- Content-Type: `text/html; charset=utf-8`
- Example: http://localhost:8888
- Example: https://gographs.io

### GET /?repo=[GO_REPO]?cluster=[false|true]

Permalink to view a Go repo SVG.

- Content-Type: `text/html; charset=utf-8`
- Example: http://localhost:8888/?repo=github.com/linkerd/linkerd2?cluster=false
- Example: https://gographs.io/?repo=github.com/siggy/gographs?cluster=false

### GET /?url=[SVG_URL]

Permalink to view an arbitrary SVG URL.

- Content-Type: `text/html; charset=utf-8`
- Example: http://localhost:8888/?url=https://upload.wikimedia.org/wikipedia/commons/0/05/Go_Logo_Blue.svg
- Example: https://gographs.io/?url=https://upload.wikimedia.org/wikipedia/commons/0/05/Go_Logo_Blue.svg

### GET /repo/[GITHUB_REPO].svg?cluster=[false|true]

Go repo SVG direct link.

- Content-Type: `image/svg+xml; charset=utf-8`
- Example: http://localhost:8888/repo/github.com/linkerd/linkerd2.svg?cluster=false
- Example: https://gographs.io/repo/github.com/siggy/gographs.svg?cluster=false

### GET /repo/[GITHUB_REPO].dot?cluster=[false|true]

Go repo GraphViz DOT direct link.

- Content-Type: `text/plain; charset=utf-8`
- Example:  http://localhost:8888/repo/github.com/linkerd/linkerd2.dot?cluster=false
- Example:  https://gographs.io/repo/github.com/siggy/gographs.dot?cluster=false

## Credits

This tool is built using many open source packages, but two in particular
deserve calling out:

- [goda](https://github.com/loov/goda)
- [SVGPan](https://github.com/ariutta/svg-pan-zoom)

## TODO

- default to this repo
- "refresh now", show cache age
- better fonts on svg
- size control-panel
- runtime flags
  - log-level
  - redis-server
- firefox support
- prevent normal dragging on mobile
- remove or repurpose localhost URLs in readme
- refresh button
- fix thumbnail resize/refresh jitter
- fix irc logo thumbnail border aspect ratio
- show progress during repo compile
- generic svg and dot support, paste and url
- consider capturing all mouse scrolling over every element
- on drag mouseup, don't open godoc link
