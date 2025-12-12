---
title: Markdown 语法示例
published: 2024-05-01
updated: 2024-11-29
description: 'Read more about Markdown features in Fuwari'
image: ''
tags: [Demo, Example, Markdown, Fuwari]
category: 'Examples'
draft: false 
---

根据你提供的 Markdown 扩展功能示例，以下是这些扩展语法的总结：

## GitHub 仓库卡片

用于展示 GitHub 仓库信息的动态卡片。

```markdown
::github{repo="用户名/仓库名"}
```


示例：
```markdown
::github{repo="Anfioo/AnfiooBlog"}
```
::github{repo="Anfioo/AnfiooBlog"}

## 提示框（Admonitions）

支持多种类型的提示框：`note`、`tip`、`important`、`warning`、`caution`。

### 基本语法

```markdown
:::note
这是一个 note 类型的提示框。
:::

:::tip
这是一个 tip 类型的提示框。
:::
```
:::note
这是一个 note 类型的提示框。
:::

:::tip
这是一个 tip 类型的提示框。
:::

### 自定义标题

可以在类型后添加自定义标题。

```markdown
:::note[我的自定义标题]
这是带有自定义标题的 note 提示框。
:::
```
:::note[我的自定义标题]
这是带有自定义标题的 note 提示框。
:::

### GitHub 风格语法

也支持 GitHub 风格的提示框语法。

```markdown
> [!NOTE]
> 这是 GitHub 风格的 note 提示框。

> [!TIP]
> 这是 GitHub 风格的 tip 提示框。
```
> [!NOTE]
> 这是 GitHub 风格的 note 提示框。

> [!TIP]
> 这是 GitHub 风格的 tip 提示框。

## 剧透文本（Spoiler）

隐藏部分文本内容，鼠标悬停或点击时显示。

```markdown
内容 :spoiler[被隐藏的文字 **粗体也可以**]!
```
内容 :spoiler[被隐藏的文字 **粗体也可以**]!

示例：
```markdown
The content :spoiler[is hidden **ayyy**]!
```
The content :spoiler[is hidden **ayyy**]!




### 草稿状态控制
- 通过 `draft` 字段控制文章是否为草稿状态
- `draft: true` 表示文章处于草稿状态，不会对公众可见
- `draft: false` 表示文章已发布，对公众可见

### Frontmatter 配置示例

```markdown
---
title: Draft Example
published: 2022-07-01
tags: [Markdown, Blogging, Demo]
category: Examples
draft: true
---
```


### 发布草稿
当文章准备就绪时，将 `draft` 字段从 `true` 改为 `false` 即可发布：

```markdown
---
title: Draft Example
published: 2024-01-11T04:40:26.381Z
tags: [Markdown, Blogging, Demo]
category: Examples
draft: false
---
```



## 美化 Markdown 中的代码块。提供的示例基于官方文档，你可以参考官方文档获取更多详细信息。

### 语法高亮

[语法高亮](https://expressive-code.com/key-features/syntax-highlighting/)

#### 常规语法高亮

```js
console.log('This code is syntax highlighted!')
```

#### 渲染 ANSI 转义序列

```ansi
ANSI colors:
- Regular: [31mRed[0m [32mGreen[0m [33mYellow[0m [34mBlue[0m [35mMagenta[0m [36mCyan[0m
- Bold:    [1;31mRed[0m [1;32mGreen[0m [1;33mYellow[0m [1;34mBlue[0m [1;35mMagenta[0m [1;36mCyan[0m
- Dimmed:  [2;31mRed[0m [2;32mGreen[0m [2;33mYellow[0m [2;34mBlue[0m [2;35mMagenta[0m [2;36mCyan[0m

256 colors (showing colors 160-177):
[38;5;160m160 [38;5;161m161 [38;5;162m162 [38;5;163m163 [38;5;164m164 [38;5;165m165[0m
[38;5;166m166 [38;5;167m167 [38;5;168m168 [38;5;169m169 [38;5;170m170 [38;5;171m171[0m
[38;5;172m172 [38;5;173m173 [38;5;174m174 [38;5;175m175 [38;5;176m176 [38;5;177m177[0m

Full RGB colors:
[38;2;34;139;34mForestGreen - RGB(34, 139, 34)[0m

Text formatting: [1mBold[0m [2mDimmed[0m [3mItalic[0m [4mUnderline[0m
```

### 编辑器与终端框架

[编辑器与终端框架](https://expressive-code.com/key-features/frames/)

#### 代码编辑器框架

```js title="my-test-file.js"
console.log('Title attribute example')
```

---

```html
<!-- src/content/index.html -->
<div>File name comment example</div>
```

#### 终端框架

```bash
echo "This terminal frame has no title"
```

---

```powershell title="PowerShell terminal example"
Write-Output "This one has a title!"
```

#### 覆盖框架类型

```sh frame="none"
echo "Look ma, no frame!"
```

---

```ps frame="code" title="PowerShell Profile.ps1"
# Without overriding, this would be a terminal frame
function Watch-Tail { Get-Content -Tail 20 -Wait $args }
New-Alias tail Watch-Tail
```

### 文本和行标记

[文本和行标记](https://expressive-code.com/key-features/text-markers/)

#### 标记整行和行范围

```js {1, 4, 7-8}
// Line 1 - targeted by line number
// Line 2
// Line 3
// Line 4 - targeted by line number
// Line 5
// Line 6
// Line 7 - targeted by range "7-8"
// Line 8 - targeted by range "7-8"
```

#### 选择行标记类型 (mark, ins, del)

```js title="line-markers.js" del={2} ins={3-4} {6}
function demo() {
  console.log('this line is marked as deleted')
  // This line and the next one are marked as inserted
  console.log('this is the second inserted line')

  return 'this line uses the neutral default marker type'
}
```

#### 为行标记添加标签

```jsx {"1":5} del={"2":7-8} ins={"3":10-12}
// labeled-line-markers.jsx
<button
  role="button"
  {...props}
  value={value}
  className={buttonClassName}
  disabled={disabled}
  active={active}
>
  {children &&
    !active &&
    (typeof children === 'string' ? <span>{children}</span> : children)}
</button>
```

#### 在单独的行上添加长标签

```jsx {"1. Provide the value prop here:":5-6} del={"2. Remove the disabled and active states:":8-10} ins={"3. Add this to render the children inside the button:":12-15}
// labeled-line-markers.jsx
<button
  role="button"
  {...props}

  value={value}
  className={buttonClassName}

  disabled={disabled}
  active={active}
>

  {children &&
    !active &&
    (typeof children === 'string' ? <span>{children}</span> : children)}
</button>
```

#### 使用类似 diff 的语法

```diff
+this line will be marked as inserted
-this line will be marked as deleted
this is a regular line
```

---

```diff
--- a/README.md
+++ b/README.md
@@ -1,3 +1,4 @@
+this is an actual diff file
-all contents will remain unmodified
 no whitespace will be removed either
```

#### 结合语法高亮和类似 diff 的语法

```diff lang="js"
  function thisIsJavaScript() {
    // This entire block gets highlighted as JavaScript,
    // and we can still add diff markers to it!
-   console.log('Old code to be removed')
+   console.log('New and shiny code!')
  }
```

#### 标记行内的单个文本

```js "given text"
function demo() {
  // Mark any given text inside lines
  return 'Multiple matches of the given text are supported';
}
```

#### 正则表达式

```ts /ye[sp]/
console.log('The words yes and yep will be marked.')
```

#### 转义正斜杠

```sh /\/ho.*\//
echo "Test" > /home/test.txt
```

#### 选择行内标记类型 (mark, ins, del)

```js "return true;" ins="inserted" del="deleted"
function demo() {
  console.log('These are inserted and deleted marker types');
  // The return statement uses the default marker type
  return true;
}
```

### 自动换行

[自动换行](https://expressive-code.com/key-features/word-wrap/)

#### 为每个代码块配置自动换行

```js wrap
// Example with wrap
function getLongString() {
  return 'This is a very long string that will most probably not fit into the available space unless the container is extremely wide'
}
```

---

```js wrap=false
// Example with wrap=false
function getLongString() {
  return 'This is a very long string that will most probably not fit into the available space unless the container is extremely wide'
}
```

#### 配置换行的缩进

```js wrap preserveIndent
// Example with preserveIndent (enabled by default)
function getLongString() {
  return 'This is a very long string that will most probably not fit into the available space unless the container is extremely wide'
}
```

---

```js wrap preserveIndent=false
// Example with preserveIndent=false
function getLongString() {
  return 'This is a very long string that will most probably not fit into the available space unless the container is extremely wide'
}
```

## 可折叠部分

[可折叠部分](https://expressive-code.com/plugins/collapsible-sections/)

```js collapse={1-5, 12-14, 21-24}
// All this boilerplate setup code will be collapsed
import { someBoilerplateEngine } from '@example/some-boilerplate'
import { evenMoreBoilerplate } from '@example/even-more-boilerplate'

const engine = someBoilerplateEngine(evenMoreBoilerplate())

// This part of the code will be visible by default
engine.doSomething(1, 2, 3, calcFn)

function calcFn() {
  // You can have multiple collapsed sections
  const a = 1
  const b = 2
  const c = a + b

  // This will remain visible
  console.log(`Calculation result: ${a} + ${b} = ${c}`)
  return c
}

// All this code until the end of the block will be collapsed again
engine.closeConnection()
engine.freeMemory()
engine.shutdown({ reason: 'End of example boilerplate code' })
```

## 行号

[行号](https://expressive-code.com/plugins/line-numbers/)

### 为每个代码块显示行号

```js showLineNumbers
// This code block will show line numbers
console.log('Greetings from line 2!')
console.log('I am on line 3')
```

---

```js showLineNumbers=false
// Line numbers are disabled for this block
console.log('Hello?')
console.log('Sorry, do you know what line I am on?')
```

### 更改起始行号

```js showLineNumbers startLineNumber=5
console.log('Greetings from line 5!')
console.log('I am on line 6')
```


## 放入视频

```yaml
---
title: 视频
published: 2023-10-19
// ...
---
<iframe width="100%" height="468" src="//player.bilibili.com/player.html?bvid=BV1fK4y1s7Qf&p=1" scrolling="no" border="0" frameborder="no" framespacing="0" allowfullscreen="true"> </iframe>
```

## Bilibili

<iframe width="100%" height="468" src="//player.bilibili.com/player.html?bvid=BV1fK4y1s7Qf&p=1" scrolling="no" border="0" frameborder="no" framespacing="0" allowfullscreen="true"> </iframe>


## 公式

$$I = \int \rho R^{2} dV$$

$$
\begin{equation*}
\pi
=3.1415926535
\;8979323846\;2643383279\;5028841971\;6939937510\;5820974944
\;5923078164\;0628620899\;8628034825\;3421170679\;\ldots
\end{equation*}
$$


## 脚注和其他


段落之间用空行分隔。

第二段内容。_斜体_、**粗体**和`等宽字体`。无序列表如下：

- 第一项
- 第二项
- 第三项

> 块引用的写法如下。
>
> 块引用可以跨多个段落，
> 按需添加即可。

用三个连字符表示破折号（——），两个连字符表示范围（例如“章节12--14”），三个点会被转换为省略号（……）。支持Unicode字符 ☺

## 二级标题示例

这是一个有序列表：

1. 第一项
2. 第二项
3. 第三项

这里有一个链接指向[外部网站](https://github.com/Anfioo/AnfiooBlog)，以及指向[当前文档的章节](#二级标题示例)。这里有一个脚注[^1]。

这里有一个链接指向[外部网站](https://github.com/Anfioo/AnfiooBlog)，以及指向[当前文档的章节](#二级标题示例)。这里有一个脚注[^2]。


[^1]: 这是第一个脚注的内容，比如解释某个概念、标注引用文献，或补充正文未展开的细节。
[^2]: 这是第一个脚注的内容，比如解释某个概念、标注引用文献，或补充正文未展开的细节。


