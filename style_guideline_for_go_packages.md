# Style guideline for Go packages

## Organize by responsibility
A common practise from other languages is to organize types together in a package called models or types. In Go, we organize code by their functional responsibilities.

```go
package models // DON'T DO IT!!!

// User represents a user in the system.
type User struct {...}
```

Rather than creating a models package and declare all entity types there, a User type should live in a service-layer package.

```go
package mngtservice

// User represents a user in the system.
type User struct {...}

func UsersByQuery(ctx context.Context, q *Query) ([]*User, *Iterator, error)
func UserIDByEmail(ctx context.Context, email string) (int64, error)
```