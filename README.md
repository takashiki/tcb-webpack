Tencent CloudBase Webpack Plugin
====================

> 上传 Webpack Assets 至 腾讯云 CloudBase

## 安装

```sh
npm i -D tcb-webpack
```

## 使用方法

支持的配置项:

+ `env` CloudBase 环境ID
+ `path` 存储路径， 默认为 `[hash]`，也可以指定 hash 长度，如: `[hash:8]`
+ `exclude` 可选，排除特定文件，正则表达式，如: `/index\.html$/`
+ `include` 可选，指定要上传的文件，正则表达式，如: `/app\.js$/`

***注: Webpack 的 `output.publicPath` 要指向 TCB（或自定义的）域名地址***

```js
// 引入
const TcbPlugin = require('tcb-webpack');

// 配置 Plugin
const tcbPlugin = new TcbPlugin({
  env: 'my-env-id',
  path: '[hash]/'
});

// Webpack 的配置
module.exports = {
 output: {
    // 此处为 TCB 访问域名(env-xxx-1250000000.tcloudbaseapp.com) 加上 path([hash]/)
    publicPath: "https://env-xxx-1250000000.tcloudbaseapp.com/[hash]/"
    // ...
 },
 plugins: [
   tcbPlugin
   // ...
 ]
 // ...
}
```
