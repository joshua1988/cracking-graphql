---
sidebar_position: 2
---

# 기본 문법

### 필드(Fields)

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

### 인자(Argument)

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

### 프래그먼트(Fragments)

반복되는 쿼리 스키마를 저장해 놓고 재사용할 수 있다. `fragment` 라고 선언

```graphql
# 요청
{
  leftComparison: hero(episode: EMPIRE) {
    ...comparisonFields
  }
  rightComparison: hero(episode: JEDI) {
    ...comparisonFields
  }
}

fragment comparisonFields on Character {
  name
  appearsIn
  friends {
    name
  }
}
```

```graphql
# 응답
{
  "data": {
    "leftComparison": {
      "name": "Luke Skywalker",
      "appearsIn": [
        "NEWHOPE",
        "EMPIRE",
        "JEDI"
      ],
      "friends": [
        {
          "name": "Han Solo"
        },
        {
          "name": "Leia Organa"
        },
        {
          "name": "C-3PO"
        },
        {
          "name": "R2-D2"
        }
      ]
    },
    "rightComparison": {
      "name": "R2-D2",
      "appearsIn": [
        "NEWHOPE",
        "EMPIRE",
        "JEDI"
      ],
      "friends": [
        {
          "name": "Luke Skywalker"
        },
        {
          "name": "Han Solo"
        },
        {
          "name": "Leia Organa"
        }
      ]
    }
  }
}
```