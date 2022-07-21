---
sidebar_position: 2
---

# 인자(Arguments)

쿼리할 때 필드에 인자를 넘길 수 있다.

```graphql
# 요청
{
  human(id: "1000") {
    name
    height
  }
}
```

```graphql
# 응답
{
  "data": {
    "human": {
      "name": "Luke Skywalker",
      "height": 1.72
    }
  }
}
```

혹은 GraphQL에 정의된 옵션 값을 인자로 넘길 수 있다.

```graphql
# 요청
{
  human(id: "1000") {
    name
    # METER or FOOT
    height(unit: FOOT)
  }
}
```

```graphql
# 응답
{
  "data": {
    "human": {
      "name": "Luke Skywalker",
      "height": 5.6430448
    }
  }
}
```