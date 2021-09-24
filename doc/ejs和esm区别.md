在 `nodejs.cn` 中学习 assert 严格断言模式，发现CJS(CommonJs)和ESM(ES Modules)模式。
```
// CJS
const assert = require('assert').strict;
const assert = require('assert/strict');

// ESM
import { strict as assert } from 'assert';
import assert from 'assert/strict';
```

所以其实也是`require`和`import`的区别。
| require      | import |
| ----------- | ----------- |
| 动态评估     | 静态评估       |
| 运行时报错   | 解析时报错    |
| 同步   | 异步    |
| 不是关键词	 | 是关键词    |

```
// @cjs-esm.js
module.exports = {
  github1: 'gocpplua1'
}

// cjs-@esm.js
export const github2 = 'gocpplua2'

// test.js
// commonjs 和 module 不兼容

// package.json -- "type": "commonjs"
var git1 = require('./@cjs-esm')
console.log(git1.github1)

// package.json -- "type": "module"
//import { github2 as git2} from "./cjs-@esm.js";
//console.log(git2)
```

我们使用 npm init 创建 package.json。 此文件中"type" 默认是 commonjs。

由于esm和cjs不兼容。如果我们需要使用esm，那么需要将"type"设置为"module",否则会保存。 同理我们使用cjs，那么需要设置为commonjs，否则保存。

参考文章:
1. [require和import的区别是什么？看这个你就懂了](https://blog.csdn.net/weixin_33795093/article/details/88840974)