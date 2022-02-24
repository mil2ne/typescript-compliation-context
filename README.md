## Typescript Compliation Context 정리

## 프로젝트 구성
- `npm init -y`
- `npm i typescript -D`
- `npx tsc --init`

## compileOnSave
- Enable Compile-on-Save for this project.
- true / false (default false)
- Visual Studio 2015 with TypeScript 1.8.4 이상
- atom-typescript 플러그인
  - https://github.com/TypeStrong/atom-typescript#compile-on-save

## extends
- Path to base configuration file to inherit from. Requires TypeScript version 2.1 or later.
- 파일 (상대) 경로명: string
- TypeScript 2.1 New Spec
- (참고) https://github.com/tsconfig/bases

```
npm install --save-dev @tsconfig/deno

{
 "extends": "@tsconfig/deno/tsconfig.json",
 ...
}
```

## files, include, exclude
- 셋다 설정이 없으면, 전부다 컴파일
- files
  - 상대 혹은 절대 경로의 리스트 배열입니다.
  - exclude 보다 쎕니다.
- include, exclude
  - glob 패턴 (마치 .gitignore)
  - include
    - exclude 보다 약합니다.
    - \* 같은걸 사용하면, .ts / .tsx / .d.ts 만 include (.js 등은 allowJS 켜야함)
  - exclude
    - 설정 안하면 4가지(node_modules, bower_components, jspm_packages, \<outDir>)를 default 로 제외합니다.
    - \<outDir> 은 항상 제외합니다. (include 에 있어도)

## compileOptions : type
### @types
- TypeScript 2.0 부터 사용 가능해진 내장 type definition 시스템
- 아무 설정을 안하면 ?
  - `node_modules/@types` 라는 모든 경로를 찾아서 사용
- typeRoots 를 사용하면 ?
  - typeRoots 를 사용하면 ?
- types 를 사용하면 ?
  - 배열 안의 모듈 혹은 `./node_modules/@types/` 안의 모듈 이름에서 찾아옵니다.
  - [] 빈 배열을 넣는다는건 이 시스템을 이용하지 않겠다는 것입니다.
- typeRoots 와 types 를 같이 사용하지 않습니다

### target
- 빌드의 결과물을 어떤 버전으로 할 것이냐
- 지정을 안하면 es3 입니다.

### lib
- 기본 type definition 라이브러리를 어떤 것을 사용할 것이냐
- lib 를 지정하지 않을 때
  - target 이 'es3' 이고, 디폴트로 lib.d.ts 를 사용합니다.
  - target 이 'es5' 이면, 디폴트로 dom, es5, scripthost 를 사용합니다.
  - target 이 'es6' 이면, 디폴트로 dom, es6, dom.iterable, scripthost 를 사용합니다.
- lib 를 지정하면 그 lib 배열로만 라이브러리를 사용하니다.
  - 빈 [] => 'no definition found 어쩌구

### compileOptions : strict
- `--noImplicitAny`
- `--noImplicitThis`
- `--strictNullChecks`
- `--strictFunctionTypes`
- `--strictPropertyInitialization`
- `--strictBindCallApply`
- `--alwaysStrict`