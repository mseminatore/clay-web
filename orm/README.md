# web/orm

ActiveRecord-style ORM over Clay's `Db` prototype.

## Usage

```clay
import("web/orm")

db = Db open("app.db")
db exec("CREATE TABLE IF NOT EXISTS todos (id INTEGER PRIMARY KEY AUTOINCREMENT, title TEXT, done INTEGER DEFAULT 0)")

Todo = Model define(db, "todos", ["title", "done"])

// Create
d = Dict clone
d set("title", "Buy milk")
todo = Todo create(d)

// Read
todos = Todo all()                  // Array of model instances
todo = Todo find(1)                 // Single instance or nil
done = Todo where("done", 1)        // Array matching condition

// Access fields
todo _data get("title")             // "Buy milk"
todo _id                            // 1

// Count
Todo count()                        // number of records
```

## API

### Model (class methods)

| Method | Description |
|--------|-------------|
| `define(db, table, columns)` | Create a model for a table |
| `create(dict)` | INSERT a new record, returns instance with id |
| `find(id)` | SELECT by id, returns instance or nil |
| `all()` | SELECT all records, returns Array |
| `where(col, val)` | SELECT with WHERE, returns Array |
| `count()` | COUNT all records |

### Model Instance

Each instance has:
- `_id` — the record's primary key
- `_data` — Dict with column values
- `_model` — reference to the Model for save/destroy
