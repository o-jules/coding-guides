# 前端代码规范

## JavaScript / Typescript 代码规范

### 基础

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

### 命名规范

- [强制] 全局常量使用全大写字母加下划线分隔

```ts
/* some global scope */

// good
const BASE_URL = ''

// bad
const baseUrl = ''
```

- [强制] 变量名、函数名、方法名使用小驼峰命名法

```ts
let userIndex = 0

function doSomething()｛}

class Dog {
  bark() {}
}
```

- [强制] 类名使用 Pascal 命名法（大驼峰命名法）

```ts
// good
let userName = 'julia'

// bad
let user_name = 'john'
```

- React 组件名使用 Pacal 命名法

```bash
# good
ArticleDetail.tsx

# bad
articleDetail.tsx
```

### 语句规范

- [强制] `if` / `else` / `for` / `while` 等语句主体需换行且不能省略 `{}`
  ```ts
  if (good) {
    doSomething()
  }

  if (bad) doSomething()
  if (bad)
    doSomething()
  ```

### 语义规范

- [推荐] 不同逻辑的代码，使用空行进行分隔

- [推荐] 函数、方法等代码不要宜太长，功能尽量简单

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

## Typescript 规范

## 代码格式化工具

推荐团队成员都使用同样的格式化工具及配置，以保证相同的代码格式化的结果是一致的。

- Visual Studio Code + [Prettier](https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode)
