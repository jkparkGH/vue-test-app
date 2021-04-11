# vue-test-app

#### Project setup

```
yarn install
```

#### Compiles and hot-reloads for development

```
yarn serve
```

#### Compiles and minifies for production

```
yarn build
```

#### Route Info

- Home: `/`
- Event: `/events/preview/smtm`
- Signup: `/signup`

#### ETC

- `vue`, `vue-route`, `vue-property-decorator` 사용, 그 외 라이브러리 또는 플러그인 사용X
- 이벤트 페이지의 애니메이션 로직은 `scss`로 작성 `(opacity, transform, keyframes 사용)`
- `webp` 확장자 이미지 조건부 사용
- 이벤트 페이지의 경우, 해상도 `375px x 667px` 해상도에 최적화
- 회원가입 페이지의 경우 `UI & Component Data Binding` 까지 구현
