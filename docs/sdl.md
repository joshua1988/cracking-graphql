---
sidebar_position: 2
---

# SDL(Schema Definition Language)

그래프큐엘은 API 스키마를 정의하기 위해 자체적인 타입 시스템을 갖고 있습니다. 이 스키마를 정의하는 문법을 SDL이라고 합니다.

<!-- API 요청으로 받는 응답 구조를 정의하는 문법이 SDL입니다. 이 응답 구조를 스키마(Schema)라고 하며 프런트엔드 개발자와 백엔드 개발자 간의 합의 대상입니다. -->

SDL의 간단한 예시 코드를 보겠습니다.

```graphql
type Person {
  name: String!
  age: Int!
}
```

위 `Person` 타입의 `name` 속성은 문자열이고 `age`는 숫자입니다. `!`는 필수 값을 의미합니다.

## 타입 간 관계 설정

SDL로 정의한 타입 간에 관계를 설정할 수도 있습니다.

```graphql
type Post {
  title: String!
  author: Person!
}
```

위 `Post` 타입에 `author: Person!`을 지정하여 `Person` 타입과의 관계를 정의하였습니다. `Post` 1개는 꼭 1개의 `Person` 타입과 매칭되어야 합니다. 반대로, 아래에 정의된 `Person` 타입은 여러 개의 `Post` 타입과 연결되는 걸 나타냅니다.

```graphql
type Person {
  name: String!
  age: Int!
  posts: [Post!]!
}
```

`posts: [Post!]!` 는 `Post` 타입으로 이뤄진 배열을 의미합니다. `!`는 앞에서 안내한 대로 필수 값을 의미합니다.