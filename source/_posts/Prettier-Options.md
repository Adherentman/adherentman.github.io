---
title: Prettier Option
date: 2018-02-09 17:50
comments: true
layout: post
tags: [前端工具]
categories: 前端工具
---

# Prettier Option

.Prettierrc

Cli是在终端使用，

Api是在`.Prettierrc`中设置使用
<!--more-->
## printWidth

打印宽度指定打印将换行的行长。

| Default |    Cli Override     |   Api Override    |
| ------- | :-----------------: | :---------------: |
| 80      | --print-width <int> | printWidth: <int> |

## Tab Width

指定每个缩进的空格数。

| Default |   Cli Override    |  Api Override   |
| :-----: | :---------------: | :-------------: |
|    2    | --tab-width <int> | tabWidth: <int> |

## Tabs

用`Tab`缩进而不是空格

| Default |   Cli Override   |  Api Override   |
| :-----: | :--------------: | :-------------: |
|  false  | --use-tabs <int> | useTabs: <bool> |

## Semicolons

在语句的末尾打印分号。

有效的选项：

* true  - 在每个语句的末尾添加一个分号。
* false - 只在可能引入ASI故障的行的开头添加分号。

| Default |  Cli Override   | Api Override |
| :-----: | :-------------: | :----------: |
|  true   | --no-semi <int> | semi: <bool> |

## Quotes

使用单引号而不是双引号。

| Default |  Cli Override  |    Api Override     |
| :-----: | :------------: | :-----------------: |
|  false  | --single-quote | singleQuote: <bool> |

## Trailing Commas

多行时，尽可能打印尾随逗号。 （例如，一个单行数组永远不会得到尾随的逗号。）

有效选项：

* none - 没有尾随逗号。
* es5 - 在ES5中有效的尾随逗号（object，arrays等）
* all - 尽可能尾随逗号（包括函数参数）。

| Default |           Cli Override            |           Api Override            |
| :-----: | :-------------------------------: | :-------------------------------: |
|  None   | --trailing-comma <none\|es5\|all> | trailingComma: "<none\|es5\|all>" |

## Bracket Spacing

在对象文字中的括号之间打印空格。

选项：

* true - Example { foo: bar }
* flase - Example {foo: bar}

| Default | Cli Override         | Api Override           |
| :-----: | -------------------- | ---------------------- |
|  true   | --no-bracket-spacing | bracketSpacing: <bool> |

## JSX Brackets

将多行JSX元素的 `>` 放在最后一行的末尾，而不是单独放在下一行（不适用于自闭元素）。

| Default |      Cli Override       |        Api Override        |
| :-----: | :---------------------: | :------------------------: |
|  false  | --jsx-bracket-same-line | jsxBracketSameLine: <bool> |

## Arrow Function Parentheses

围绕一个唯一的箭头函数参数包括括号。

选项：

* avoid - 尽可能省略括号 Example： x => x
* always - 总是包括括号 Example： (x) => x

| Default |          Cli Override          |          Api Override          |
| :-----: | :----------------------------: | :----------------------------: |
|  avoid  | --arrow-parens <avoid\|always> | arrowParens: "<avoid\|always>" |

## Range

只格式化文件的一部分。

这两个选项可用于格式化以给定字符偏移（分别包含和排除）开始和结束的代码。范围将延伸:

* 返回到包含选定语句的第一行的开头。 
* 转到选定语句的末尾。

这些选项不能与cursorOffset一起使用。

| Default  |    Cli Override     |   Api Override    |
| :------: | :-----------------: | :---------------: |
|    0     | --range-start <int> | rangeStart: <int> |
| Infinity |  --range-end <int>  |  rangeEnd: <int>  |

## Parser

指定使用哪个分析器。

Babylon和流解析器都支持相同的JavaScript特性（包括Flow）。Prettier会自动从输入文件路径中推断解析器，所以你不需要改变这个设置。

Built-in parsers:

- [`babylon`](https://github.com/babel/babel/tree/master/packages/babylon)
- [`flow`](https://github.com/facebook/flow/tree/master/src/parser)
- [`typescript`](https://github.com/eslint/typescript-eslint-parser) *Since v1.4.0*
- [`postcss`](https://github.com/postcss/postcss) *Since v1.4.0*
- [`json`](https://github.com/babel/babylon/tree/f09eb3200f57ea94d51c2a5b1facf2149fb406bf#babylonparseexpressioncode-options) *Since v1.5.0*
- [`graphql`](https://github.com/graphql/graphql-js/tree/master/src/language) *Since v1.5.0*
- [`markdown`](https://github.com/wooorm/remark/tree/master/packages/remark-parse) *Since v1.8.0*

| Default | Cli Override                                | Api Override                                           |
| :-----: | :------------------------------------------ | :----------------------------------------------------- |
| babylon | --parser <string><br />--parser ./my-parser | parser: "<string>"<br />parser: require("./my-parser") |

## FilePath

指定输入文件路径。这将被用来做解析器推理。

例如，以下将使用postcss解析器：

> cat foo | prettier --stdin-filepath foo.css

| Default | Cli Override              | Api Override         |
| ------- | ------------------------- | -------------------- |
| None    | --stdin-filepath <string> | filepath: "<string>" |

## Require pragma

Prettier可以限制自己只能格式化文件顶部包含特殊注释的文件，称为杂注。逐渐将大型，无格式的代码库转换为漂亮的代码库时，这非常有用。

例如，当提供--require-pragma时，将会格式化具有以下第一个注释的文件：

```
/**
 * @prettier
 */
```

or

```
/**
 * @format
 */
```

| Default |   Cli Override   |     Api Override      |
| :-----: | :--------------: | :-------------------: |
|  false  | --require-pragma | requirePragma: <bool> |

## Insert Pragma

Prettier的可以在文件的顶部插入一个特殊的@format标记，指定文件已被格式化为Prettier。

| Default |  Cli Override   |     Api Override     |
| :-----: | :-------------: | :------------------: |
|  false  | --insert-pragma | insertPragma: <bool> |

## Prose Wrap

默认情况下，由于某些服务使用了对换行符敏感的呈现器，因此Prettier会按原样包装降价文本。

选项：

- `"always"` - 如果超出了打印宽度，请将散的包好。
- `"never"` - 不包散的。
- `"preserve"` - 按原样包散的。

|  Default   |              Cli Override              |              Api Override              |
| :--------: | :------------------------------------: | :------------------------------------: |
| "preserve" | --prose-wrap <always\|never\|preserve> | proseWrap: "<always\|never\|preserve>" |

