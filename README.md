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


