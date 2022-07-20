---
sidebar_position: 3
---

# Mutations

서버 데이터를 변경(생성, 수정, 삭제)하기 위한 타입입니다. REST API로 서버의 데이터를 변경하는 경우 종종 사이드 이펙트가 있었어서 GET 성격의 조회 API와 조작 API를 분리하였습니다.

```graphql
mutation {
  createPerson(name: "Bob", age: 36) {
    name
    age
  }
}
```

## 뮤테이션 장점

뮤테이션의 장점은 한번의 요청으로 생성과 조회(새로 생성된 데이터)를 할 수 있다는 점입니다. 위 `createPerson` 뮤테이션의 서버 응답 형태는 아마 다음과 같을 겁니다.

```graphql
"createPerson": {
  "name": "Bob",
  "age": 36,
}
```

생성된 사람의 `name`과 `age` 속성을 응답으로 받을 수 있기 때문에 REST API를 사용할 때처럼 생성 후 별도의 조회 API를 날리지 않아도 됩니다.



