# web/http-server

Simple HTTP server with routing for Clay.

## Usage

```clay
import("web/http-server")

server = HttpServer new(8080)

server get("/", { |req|
    server html(200, "<h1>Hello Clay!</h1>")
})

server get("/api/greet", { |req|
    server json(200, "{\"message\": \"hello\"}")
})

server post("/api/data", { |req|
    body = req body()
    server text(201, "Received: " + body)
})

server start()
```

## API

### HttpServer

| Method | Description |
|--------|-------------|
| `new(port)` | Create server on given port |
| `get(path, handler)` | Register GET route |
| `post(path, handler)` | Register POST route |
| `put(path, handler)` | Register PUT route |
| `delete(path, handler)` | Register DELETE route |
| `start()` | Start listening (blocking) |

### Response Helpers

| Method | Description |
|--------|-------------|
| `text(status, body)` | Plain text response |
| `html(status, body)` | HTML response |
| `json(status, body)` | JSON response |
| `redirect(url)` | 302 redirect response |
| `formData(req)` | Parse URL-encoded POST body into Dict |

### Request Object

The handler receives a request object with:

| Method | Description |
|--------|-------------|
| `method()` | HTTP method (GET, POST, etc.) |
| `path()` | Request path |
| `query()` | Query string (after `?`) |
| `body()` | Request body |

### Low-level API

The server brick builds on the built-in `Http` prototype:

```clay
// Direct usage without routing
Http serve(8080, { |req|
    Http response(200, "Hello!")
})
```
