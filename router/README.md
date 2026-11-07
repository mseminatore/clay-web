# web/router

URL pattern matching with `:param` capture for Clay HTTP servers.

## Usage

```clay
import("web/router")

router = Router new()
router add("GET", "/users/:id", myHandler)
router add("GET", "/posts/:pid/comments/:cid", commentHandler)

result = router match("GET", "/users/42")
result get("params") get("id")   // "42"

result = router match("GET", "/posts/5/comments/12")
result get("params") get("pid")  // "5"
result get("params") get("cid")  // "12"
```

## API

| Method | Description |
|--------|-------------|
| `new()` | Create a new router |
| `add(method, pattern, handler)` | Register a route pattern |
| `match(method, path)` | Match a request, returns Dict with `handler` and `params`, or nil |

### Pattern Syntax

- `/users` — exact match
- `/users/:id` — captures `id` param
- `/posts/:pid/comments/:cid` — multiple params
