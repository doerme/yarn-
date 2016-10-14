日前，Facebook 发布了全新的 JS 套件管理工具 Yarn，如果你常发生以下几个问题，我想 Yarn 会是你的解决方案
「同事电脑 npm install OK，我却 npm install 挂掉」，通常就是因为套件内部相依关系与你之前的档案冲突，所以只好常常得先 sudo rm -rf node_modules/ 再重新安装。
没网路，npm install 直接挂给你看。
不同专案或不同资料夹下，都要更新某个套件。
npm install 非常久，久到可以泡杯咖啡聊个天，回来都还没好。
Yarn 提供一个更快更稳定的套件管理方案
透过 yarn.lock ，锁住套件版本，因此可以确保安装之套件在每台机器上都能保持一致。
安装过的套件，都会加入到 global cache 中，下次有砍掉要重装，或是不同资料夹要装，都可以在无网路情况底下安装。
非常快，平行化处理每个 operation，全新的 resolving 演算法。
如何使用
// 以前装过 npm 再安装 yarn
npm install -g yarn
// 直接安装 (mac为例，其余官网有介绍)
curl -o- -L https://yarnpkg.com/install.sh | bash
// 一般安装 (等同 npm install)
yarn
// 安装特定套件 (等同 npm install --save)
yarn add react         
yarn add react@15.3.2
// 更新特定套件 (等同 npm upgrade)
yarn upgrade react
// 移除特定套件 (等同 npm uninstall)
yarn remove react
// 新增 package.json
yarn init
// 新增全域套件
yarn global add
// 跑 script
yarn run 
// 其他常用选项
--offline   (离线模式，只拉 cache)
--flat      (将套件扁平化，一个资料夹只会有一个套件)
--dev       (加入到 devDependencies)
--peer      (加入到 peerDependencies)
--optional  (加入到 optionalDependencies)
作者实测结果，非常快且没有迁移问题，可直接舍弃 npm。
虽然说原本的 npm cache-min 设定时间 999999，以及 npm shrinkwrap 锁版本，都可以达到 Yarn 所说的一些优化，不过 Yarn 本身在平行化处理部分有特别加强，也重写了解析演算法，是一个完整的套件解决方案。
附注: push 到 repo 时请记得要上 yarn.lock 档案，才会确保其他机器都能安装一样的套件代码。
Yarn https://yarnpkg.com/