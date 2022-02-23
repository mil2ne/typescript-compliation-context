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



