# React 规范

## 命名规范

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

  ```tsx
  // bad
  <Component custom_prop="some value" CustomProp2="some value" />

  // good
  <Component customProp="some value" customProp2="some value" />
  ```

## JSX 规范

- JSX 的引号使用双引号

  ```tsx
  // good
  <Component >

  // bad
  <Component >
  ```

- [强制] JSX 缩进与对齐遵守 eslint: [react/jsx-closing-bracket-location](https://github.com/yannickcr/eslint-plugin-react/blob/master/docs/rules/jsx-closing-bracket-location.md) 及 [react/jsx-closing-tag-location](https://github.com/yannickcr/eslint-plugin-react/blob/master/docs/rules/jsx-closing-tag-location.md)。

  参考自 [Airbnb/React规范/JSX缩进](https://github.com/airbnb/javascript/tree/master/react#spacing)

  ```tsx
  // bad
  <Component
    propA="bar"
    propB="baz" />
  
  // good
  <Component propA="bar" propB="baz" />
  <Component
    propA="bar"
    propB="baz"
  />
  ```

- [强制] JSX 空格遵守 eslint：[no-multi-spaces](https://eslint.org/docs/rules/no-multi-spaces) 及 [react/jsx-tag-spacing](https://github.com/yannickcr/eslint-plugin-react/blob/master/docs/rules/jsx-tag-spacing.md)。

  参考自 [Airbnb/React规范/JSX空格](https://github.com/airbnb/javascript/tree/master/react#spacing)

  ```tsx
  // bad
  <Component/>
  <Component     />
  <Component
    />

  // good
  <Component />
  ```

- [强制] 没有子元素的标签应该要自封闭；当有多个属性且换行时，应该在新一行关闭标签

  ```tsx
  // bad
  <Foo></Foo>
  <Foo
    propA="foor"
    propB="baz" />

  // good
  <Foo />
  <Foo
    propA="foor"
    propB="baz"
  />
  ```

## React 接口使用规范

  - [强制] 类组件禁止使用 React.createClass，应继承 React.Component

  - [强制] 禁止使用 Mixin

  - [强制] 禁止使用字符串 ref，应该使用 `createRef` 或者 回调 ref

    ```tsx
    // bad
    class CustomComponent extends React.Component {
      public render() {
        return (<div ref="containerRef"></div>)
      }
    }

    // good
    class CustomComponent extends React.Component {
      private contentRef = React.createRef<HTMLDivElement>()
    
      public render() {
        return (
          <div ref={ref => { this.containerRef = ref }}>
            <div ref={this.contentRef}></div>
          </div>
        )
      }
    }
    ```