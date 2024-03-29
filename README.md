# rex

rex is a data layer for relational model

## Language Support

- [x] go
- [ ] java
- [ ] typescript

## Adapter Support

- [ ] sqlite
- [x] postgresql
- [ ] mysql

```hcl
client "db" {
  generator = "rex-client-go"
  adapter   = "postgresql"

  config "development" {
    database = "blog_development"
    user     = "postgres"
    password = "postgres"
  }
  config "production" {
    url = env("DATABASE_URL")
  }

  model "Post" {
    column "title" {
      type = string
    }
    column "content" {
      type = text
    }
  }
}
```

```sh
REX_ENV=development rex db:create
rex g client
rex g migration init
rex db:migrate
rex db:rollback
rex db:drop
```
