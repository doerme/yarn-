# [译]取代 npm 的新利器 Yarn
日前，Facebook 发布了全新的 JS 包管理工具 Yarn，如果你常发生以下几个问题，我想 Yarn 会是你的解决方案

1. 「同事电脑 npm install OK，我却 npm install 挂掉」，通常就是因为包内部相依关系与你之前的文件冲突，所以只好常常得先 sudo rm -rf node_modules/ 再重新安装。

2. 没网络，npm install 直接挂给你看。

3. 不同项目或不同文件夹下，都要更新某个包。

4. npm install 非常久，久到可以泡杯咖啡聊个天，回来都还没好。

## Yarn 提供一个更快更稳定的包管理方案

1. 通过 yarn.lock ，锁住包版本，因此可以确保安装之包在每台机器上都能保持一致。

2. 安装过的包，都会加入到 global cache 中，下次有砍掉要重装，或是不同文件夹要装，都可以在无网络情况底下安装。

3. 非常快，平行化处理每个 operation，全新的 resolving 演算法。

## 如何使用

  ```javascript
// 以前装过 npm 再安装 yarn
npm install -g yarn
// 直接安装 (mac为例，其余官网有介绍)
curl -o- -L https://yarnpkg.com/install.sh | bash
// 一般安装 (等同 npm install)
yarn
// 安装特定包 (等同 npm install --save)
yarn add react         
yarn add react@15.3.2
// 更新特定包 (等同 npm upgrade)
yarn upgrade react
// 移除特定包 (等同 npm uninstall)
yarn remove react
// 新增 package.json
yarn init
// 新增全域包
yarn global add
// 跑 script
yarn run 
// 其他常用选项
--offline   (离线模式，只拉 cache)
--flat      (将包扁平化，一个文件夹只会有一个包)
--dev       (加入到 devDependencies)
--peer      (加入到 peerDependencies)
--optional  (加入到 optionalDependencies)
```

作者实测结果，非常快且没有迁移问题，可直接舍弃 npm。

虽然说原本的 npm cache-min 设定时间 999999，以及 npm shrinkwrap 锁版本，都可以达到 Yarn 所说的一些优化，不过 Yarn 本身在平行化处理部分有特别加强，也重写了解析演算法，是一个完整的包解决方案。

附注: push 到 repo 时请记得要上 yarn.lock 文件，才会确保其他机器都能安装一样的包代码。

Yarn [https://yarnpkg.com/](http://www.w3cplus.com/javascript/immutable-js.html)
