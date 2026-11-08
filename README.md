# web

Web bricks for [Clay](https://github.com/mseminatore/clay): an HTTP server with routing, URL
pattern matching and an ActiveRecord-style ORM. They build on Clay's built-in `Http` and `Db`
prototypes.

## Installation

clay-web ships with Clay (as the `lib/web` submodule of the Clay repository), so there is nothing to
install. To pin a different version for one project, add it as a brick; a project's `bricks/web`
takes precedence over the bundled copy:

```sh
clay bricks add github.com/mseminatore/clay-web@v1.0.0 web
```

Import everything at once:

```clay
import("web")
```

or just the bricks you need:

```clay
import("web/router")
```

## Bricks

| Brick | Description |
|-------|-------------|
| [http-server](http-server/) | `HttpServer`: routes with `:param` patterns, text/html/json/redirect responses |
| [router](router/) | `Router`: URL pattern matching with `:param` capture |
| [orm](orm/) | `Model`: ActiveRecord-style ORM over SQLite (`Db`) |

These were part of [clay-stdlib](https://github.com/mseminatore/clay-stdlib) until they moved here;
`import("stdlib/router")` is now `import("web/router")`.

## License

MIT — see [LICENSE](LICENSE). Applies to every brick in this repository.
