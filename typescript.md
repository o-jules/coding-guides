# Typescript 代码规范

## 基础

- [强制] 文件编码使用 UTF-8 (无 BOM)

- [强制] 换行使用 LF

- [强制] 缩进使用 2 个空格，不使用 Tab

  ```ts
  if (true) {
    // good
  }

  if (false) {
      // bad
  }
  ```

- [强制] 普通字符串使用单引号

  ```ts
  // good
  const mood = 'happy'

  // bad
  const mood = "sad"
  ```

- [强制] 不使用分号

  ```ts
  // good
  const count = 0

  // bad
  const count = 1;
  ```

## 命名规范

- [推荐] 名字尽量使用英文，且不应使用缩写；常见的惯例除外
  ```ts
  // good
  let i = 0, j = 0, k = 0 // 临时变量惯例

  class Animal {}
  class Cat {}
  class Dog {}

  // bad
  class Mao {}
  class Neko {}
  class Goyangi {}
  ```

- [强制] 全局常量使用全大写字母加下划线分隔

  ```ts
  /* some global scope */

  // good
  const BASE_URL = ''

  // bad
  const baseUrl = ''
  ```

- [强制] 变量名、函数名、属性名、方法名使用小驼峰命名法

  ```ts
  // good
  let userName = 'julia'
  // bad
  let user_name = 'john'

  // good
  function doSomething()｛}
  // bad
  function do_Something() {}

  // good
  class Dog {
    name: string
    bark() {}
  }

  class Cat {
    Name: string // bad
    Bark() {} //bad
  }
  ```

- [强制] 类名、Type名、接口名、枚举名使用 Pascal 命名法（大驼峰命名法）

  ```ts
  // good
  class Dog {}

  // bad
  class cat {}

  // good
  interface LanguageServer {}
  // bad
  interface languageServer {}

  // good
  type DisplayProp = 'none' | 'block' | 'flex'
  // bad
  type displayProp = 'none' | 'block' | 'flex'

  enum YesNo {
    yes = 1,
    no = 0
  }
  ```


- [强制] 路径（文件夹），文件名采用 kebab-case

  ```bash
  # good
  article-edit

  # bad
  article_edit
  ```

## 语句规范

- [强制] `if` / `else` / `for` / `do` / `while` 等控制语句主体需换行且不能省略 `{}`
  ```ts
  if (good) {
    doSomething()
  }

  if (bad) doSomething()
  if (bad)
    doSomething()
  ```

## 语义规范

- [推荐] `null` 与 `undefined`

  TODO: 具体细节需要进一步讨论

- [推荐] 同一区块内的不同逻辑的代码，使用空行进行分隔

- [推荐] 函数、方法等代码不要宜太长，功能尽量简单

- [强制] 模块使用 ES 模块

- [强制] 模块导出的函数独立定义，方便打包工具进行 Tree-Shaking 优化
  ```ts
  // good
  export function format() {}
  export function validate() {}

  // bad
  export default {
    format() {},
    validate() {}
  }
  ```

- [强制] 外部依赖的导入顺序，遵循从外到内，从远到近的原则

  0. 静态资源
  1. 第三方依赖包
  2. 团队内部自建的依赖包
  3. 项目全局的依赖
  4. 项目外部模块的依赖
  5. 项目当前模块的依赖

  ```ts
  // good
  import 'antd/styles/index.css'

  import React from 'react'
  import { throttle } from 'lodash'
  import { cacheManager } from 'xmiot-function'

  import { DeleteDialog } from '@/components/dialog'
  import { isDeletable } from './utils'
  ```

## 功能规范

- 禁止改写宿主内置对象

```ts
// bad
Array.prototype.someCoolMethod = function() {}
```