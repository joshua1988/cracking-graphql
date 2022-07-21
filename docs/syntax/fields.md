---
sidebar_position: 1
---

# 필드(Fields)

쿼리할 속성을 필드라고 한다.

```graphql
# 요청
{
  hero {
    name
  }
}
```

```graphql
# 응답
{
  "data": {
    "hero": {
      "name": "R2-D2"
    }
  }
}
```