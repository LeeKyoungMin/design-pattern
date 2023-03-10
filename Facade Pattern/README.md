# Facade Pattern

## 1. Facade Pattern 이란?

- 간단한 창구

- 서브시스템이 여러개인 경우 이를 통합한 하나의 인터페이스를 제공

- 서브시스템을 좀 더 편하게 이용하기 위한 높은 수준의 인터페이스를 정의 

- 각 서브시스템의 역할이나 의존관계를 내부에서 올바를 순서로 사용할 수 있도록 외부에는 간단한 인터페이스만을 오픈

![facade](https://user-images.githubusercontent.com/22589581/221869956-3f2b6285-d196-41bc-a05d-75c1a510d6a9.png)

## 2. 의도 (Intent)와 동기(Motivation)

- 서브시스템을 합성하여 사용하는 다수 객체의 집합에 대한 하나의 일관된 인터페이스를 제공함으로써 사용하기 쉽게 함

- 사용의 오류를 방지

![facade4](https://user-images.githubusercontent.com/22589581/221869979-62dda3fd-e4a8-4c46-82ae-301d6bf603b0.png)


- 컴파일러 시스템의 경우 컴파일 명령어만 사용할 뿐 내부의 각 서브시스템의 구조는 알 필요가 없음

![facade2](https://user-images.githubusercontent.com/22589581/221869972-c70ffc3c-9196-45d9-b73e-1c484f8df034.png)

## 3. Class diagram

![facade3](https://user-images.githubusercontent.com/22589581/221869975-4f7cbd99-8a02-4c0c-a694-9a3fd36864e6.png)


## 4. 객체 협력 (collaborations)

- **Facade** : 하나의 일관된 인터페이스 제공


## 5. 중요한 결론 (consequence)

- 복잡한 서브시스템들에 대한 단순하고 기본적인 인터페이스를 앞에서 제공

- 클라이언트와 서브시스템간의 결합도를 줄임

