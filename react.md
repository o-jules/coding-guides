## React 规范

- [强制] React 组件文件名使用 Pacal 命名法：

  ```bash
  # good
  ArticleDetail.tsx

  # bad
  articleDetail.tsx
  article-detail.tsx
  ```

- [强制] 类组件名应和文件名保持一致

  ```ts
  // good
  /// ArticleDetail.tsx
  class ArticleDetail extends React.Component {}

  // bad
  /// ArticleDetail.tsx
  class ArticleContent extends React.Component {}
  ```

- [强制] 组件引用名应使用 Pacal 命名法

  ```ts
  // good
  import ArticleDetail from 'views/article/ArticleDetail'

  // bad
  import articleDetail from 'views/article/ArticleDetail'
  ```

- [建议] 组件属性名应遵守：
  * 应避开 sytle、className 等保留名
  * 使用 camelCase 命令

  ```ts
  // bad
  <Component custom_prop="some value" CustomProp2="some value" />

  // good
  <Component customProp="some value" customProp2="some value" />
  ```

- [强制] JSX 缩进遵守 eslint: [react/jsx-closing-bracket-location](https://github.com/yannickcr/eslint-plugin-react/blob/master/docs/rules/jsx-closing-bracket-location.md) 及 [react/jsx-closing-tag-location](https://github.com/yannickcr/eslint-plugin-react/blob/master/docs/rules/jsx-closing-tag-location.md)。

  参考自 [Airbnb/React规范/JSX缩进](https://github.com/airbnb/javascript/tree/master/react#spacing)

  ```ts
  ```

- [强制] JSX 空格遵守 eslint：[no-multi-spaces](https://eslint.org/docs/rules/no-multi-spaces) 及 [react/jsx-tag-spacing](https://github.com/yannickcr/eslint-plugin-react/blob/master/docs/rules/jsx-tag-spacing.md)。

  参考自 [Airbnb/React规范/JSX空格](https://github.com/airbnb/javascript/tree/master/react#spacing)

  ```ts
  ```