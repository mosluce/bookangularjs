# 研究筆記
> package.json 中 dependencies 及 devDependencies 套件用途

## 概況
#### Angular2 版本
> 2.0.1

#### package.json
```json
{
  "name": "angular-quickstart",
  "version": "1.0.0",
  "scripts": {
    "start": "tsc && concurrently \"tsc -w\" \"lite-server\" ",
    "lite": "lite-server",
    "postinstall": "typings install",
    "tsc": "tsc",
    "tsc:w": "tsc -w",
    "typings": "typings"
  },
  "license": "ISC",
  "dependencies": {
    "@angular/common": "~2.0.1",
    "@angular/compiler": "~2.0.1",
    "@angular/core": "~2.0.1",
    "@angular/forms": "~2.0.1",
    "@angular/http": "~2.0.1",
    "@angular/platform-browser": "~2.0.1",
    "@angular/platform-browser-dynamic": "~2.0.1",
    "@angular/router": "~3.0.1",
    "@angular/upgrade": "~2.0.1",
    "angular-in-memory-web-api": "~0.1.1",
    "bootstrap": "^3.3.7",
    "core-js": "^2.4.1",
    "reflect-metadata": "^0.1.8",
    "rxjs": "5.0.0-beta.12",
    "systemjs": "0.19.39",
    "zone.js": "^0.6.25"
  },
  "devDependencies": {
    "concurrently": "^3.0.0",
    "lite-server": "^2.2.2",
    "typescript": "^2.0.3",
    "typings":"^1.4.0"
  }
}
```

## Dependencies 不包含於 @angular 的部分

> angular-in-memory-web-api : Demo 用的簡易記憶體資料庫可以移除

1. core-js : 眾多常用的 polyfile (包含了ES6, ES7+, ...)
2. reflect-metadata : (讀文件理解中)
3. rxjs : (讀文件理解中)
4. systemjs : 動態加載 npm 的程式庫 (不打包只有在被使用時才載入)解說
5. zone.js : 被引用到網頁上時，強制對非同步方法進行 Monkey-patched 使所有非同步方法可被監控，主要讓雙向綁定也可以支援非同步方法(如setTimeout, XMLHttpRequest...等) >> [詳細解說](https://github.com/kittencup/angular2-ama-cn/issues/60)

## DevDependencies 部分

> 主要是工具

1. concurrently : 可以同時運行兩個以上 npm 指令 (lite-server + tsc)
2. lite-server : 簡易的開發用伺服器，會自動重新載入程式 (非 Hot)
3. typescript : Typescript 編譯器
4. typings : Typescript 定義檔管理器，可以取得一些本來不是用Typescript撰寫的程式庫 API 定義，最直接的影響就是程式碼自動提示，再來就是IDE及編譯器語法檢查的依據
