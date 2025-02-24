# 4-Pick

제네릭이 익숙하지 않아 쉽게 풀리지 않았다.

제네릭은 타입을 마치 함수의 파라미터처럼 사용하는 것을 의미한다.

extends keyof 는 T를 가져와서 key들을 가리키는 것이고 T 안에 있는 키값을 통해 타입을 설정한다.

noah에서 실제로 사용을 해보았고 pick과는 반대인 omit이라는 키워드가 있음.

omit은 특정 속성만 제거한 타입을 정의한다.

## 질문


`T`에서 `K` 프로퍼티만 선택해 새로운 오브젝트 타입을 만드는 내장 제네릭 `Pick<T, K>`을 이를 사용하지 않고 구현하세요.

```ts
type MyPick<T, K extends keyof T> = {
	[P in K]: T[P];
};
	
/* _____________ 테스트 케이스 _____________ */
import type { Equal, Expect } from '@type-challenges/utils'

type cases = [
	Expect<Equal<Expected1, MyPick<Todo, 'title'>>>,
	Expect<Equal<Expected2, MyPick<Todo, 'title' | 'completed'>>>,
	// @ts-expect-error
	MyPick<Todo, 'title' | 'completed' | 'invalid'>,
]

interface Todo {
	title: string
	description: string
	completed: boolean
}

interface Expected1 {
	title: string
}

interface Expected2 {
	title: string
	completed: boolean
}
```


## 참고문헌

- https://joshua1988.github.io/ts/guide/generics.html#%EC%A0%9C%EB%84%A4%EB%A6%AD-%ED%83%80%EC%9E%85-%EB%B3%80%EC%88%98
- https://kyounghwan01.github.io/blog/TS/fundamentals/utility-types/#partial