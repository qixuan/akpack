# Packager

基于 https://github.com/react-component/rn-packager rn0.19.0分支创建
![react-native](https://img.shields.io/badge/react--native-%3D_0.19.0-green.svg)

## Install

```
$ npm install akpack -g
```

## Dependences

```
"devDependencies": {
  "rn-core": "~0.2.0"
}
```
"rn-core" 是 `0.19.0` 的全量sdk工程，从官方的 "react-native" 依赖中抽取了必要的代码，做了精简。

## akpack bundle
> 在项目工程根目录下执行打包命令，默认不打包框架代码及polyfills

```
$ akpack bundle --entry-file  entry/file/path.js --bundle-output out/file/path.jsbundle --platform ios
```

Options, 参数参考react-native命令，增加了参数：

*  --include-framework  Whether to bundle include module `react-native` and polyfills   [default: false]
*  --runBeforeMainModule  Modules required before main module                           [default: ["InitializeJavaScriptAppEngine"]]
    

## Bundle sdk

```
$ akpack bundle --entry-file node_modules/rn-core/react-native/Libraries/react-native/react-native.js --bundle-output ~/Desktop/react-native-debug.js --platform ios --include-framework
```

## Server

```
$ akpack start
```
url请求参数新增 `framework=true` `runBeforeMainModule=[]`

## Programmatic API
```
var RNPackager = require('akpack');

gulp.task('task', function(){
  return RNPackager.bundle({
    "--entry-file": "tests/index.ios.js",
    "--bundle-output": "tests/index.ios.bundle",
    "--platform": "ios"
  });
});
```

## Project Sample

```
$ cd tests
$ npm i
$ akpack start
```
Visit:

* [http://localhost:8081/index.ios.bundle?platform=ios](http://localhost:8081/index.ios.bundle?platform=ios)
* [http://localhost:8081/index.android.bundle?platform=android](http://localhost:8081/index.android.bundle?platform=android)