---
sidebar_position: 6
---

# 스키마(Schema)

스키마란 그래프큐엘 API 요청을 받았을 때 백엔드에서 제공될 데이터의 형상을 의미합니다. SDL(Schema Definition Language)로 스키마를 정의할 수 있고 타입과 필드로 구성됩니다. 스키마는 또 다른 의미로 클라이언트에서 어떻게 서버의 데이터를 접근할 지 클라이언트와 서버 간에 합의한 문서입니다.

## 스키마 작성 방법

스키마는 SDL을 이용해서 아래와 같이 작성합니다.

```graphql
# schema.graphql 파일
type Book {
  title: String
  author: Author
}

type Author {
  name: String
  age: Int
}
```

위 코드는 `Book`과 `Author` 타입을 SDL로 정의한 코드입니다. `Book` 타입에는 `title` 필드와 `author` 필드가 있습니다. `title` 필드는 문자열 타입이고 `author` 필드는 `Author` 타입입니다. `Book` 타입의 `author` 필드가 `Author` 타입으로 연결되어 있다는 의미죠.

`Author` 타입을 보면 `name` 필드가 문자열이고 `age` 필드가 인티저 숫자입니다. 이렇게 `String`, `Int` 등의 원시 타입을 [스칼라 타입](./docs/scalar-types) 이라고 합니다.

## 스키마 필드 타입

스키마 필드에 연결될 수 있는 타입은 다음 5가지 입니다.

- 스칼라 타입
- 객체 타입
- 이넘 타입
- 유니언 타입
- 인터페이스 타입

