# toml配置

您可以在 `book.toml `文件中配置图书的参数。

这是一个 `book.toml`文件示例，如下所示：

```toml
[book]
title = "Example book"
author = "John Doe"
description = "The example book covers examples."

[build]
build-dir = "my-example-book"
create-missing = false

[preprocessor.index]

[preprocessor.links]

[output.html]
additional-css = ["custom.css"]

[output.html.search]
limit-results = 15
```

## 支持的配置选项

重要的是要注意到，配置中指定的**任何**相对路径，都是相对于配置文件所在的书籍的根目录.

### 通用元数据——[Book]

这是有关您图书的一般

| 信息            | 描述                                                         |
| --------------- | ------------------------------------------------------------ |
| **title**       | 这本书的标题                                                 |
| **author**      | 本书的作者                                                   |
| **description** | 该书的描述,作为元信息,添加在每页 html 的`<head>`             |
| **src**         | 默认情况下,源目录位于名为`src`的目录中(在根文件夹)。但这`src`是可配置的，就在`book.toml`。 |
| **language:**   | 国家语言, 例如用在网页的 `<html lang="en">` 属性。           |

**book.toml**

```toml
[book]
title = "Example book"
authors = ["John Doe", "Jane Doe"]
description = "The example book covers examples."
src = "my-src"  # 源文件夹，用 `root/my-src` 替代 `root/src`
language = "zh-CN"
```

### Build 选项——[Build]

这可以控制您图书的构建过程.

- **build-dir** | 放置渲染图书的目录。默认情况下在根目录的`book/`:

- **create-missing** | 默认情况(`create-missing = true`)下，在书籍建成时，会创建`SUMMARY.md`中缺失的文件。如果是`false`，则有文件不存在,那么构建过程将以错误退出。

- **use-default-preprocessors** | 设为 `false`，会禁用(`links`&`index`)的默认预处理器。

  - 如果您通过配置文件声明了，相同的和/或其他预处理器,由它们主导.

  - 为清楚起见,没有预处理器配置,默认`links`和`index`运行.设置`use-default-preprocessors = false`，将禁用这些默认预处理器运行.

  - 若添加`[preprocessor.links]`，那无论如何,都能确保`use-default-preprocessors`运行`links`。

默认情况下,以下预处理器运行，并包含:

- `links`:扩展章节中`{{ #playpen }}`和`{{ #include }}`控制条，能帮助引入文件的内容.
- `index`:将所有名为`README.md`的章节文件转换`index.md`。也就是说,所有`README.md`将被渲染成`index.html`，在渲染的书中.

**book.toml**

```toml
[build]
build-dir = "build"
create-missing = false

[preprocessor.links]

[preprocessor.index]
```

### HTML 渲染器

HTML 渲染器也有几个选项。渲染器的所有选项都需要在 TOML 表下指定。`[output.html]`

提供以下配置选项：

- **theme:** **mdBook**附带了默认主题和它所需的所有资源文件。但是，如果设置此选项，mdBook 将选择性地用指定文件夹中找到的主题文件覆盖主题文件。
- **default-theme:** 主题配色方案。默认为 ：`light`
- **preferred-dark-theme:** 默认的黑暗主题。默认为 ：  `navy`
- **curly-quotes:** 将直引号转换为反引号,代码块中的除外。默认为 ：`false`
- **mathjax-support:** 添加对 [MathJax](https://rust-lang.github.io/mdBook/format/mathjax.html)的支持。 默认为 ：`false`
- **copy-fonts:** 将字体.css和各自的字体文件复制到输出目录中，并在默认主题中使用它们. 默认为 ：`true`
- **google-analytics:** 如果您使用 Google 分析，此选项只需在配置文件中指定 ID 即可启用它。
- **additional-css:** 这些样式表将在默认样板之后加载，以便通过后续改变样式。
- **additional-js:** 如果您需要在不删除当前行为的情况下在书中添加一些行为，则可以指定一组 JavaScript 文件，这些文件将与默认文件一起加载。
- **print:** 配置打印设置的子表。默认情况下，mdBook增加了将该书打印为单页的支持。使用书右上角的打印图标访问此问题。
- **no-section-label:** 默认情况下，mdBook在内容表列中添加节标签。例如，"1"，"2.1"。将此选项设置为"禁用这些标签"。默认为 ：`false`
- **fold:** 用于配置侧边栏部分折叠行为的子表。
- **playground:** 用于配置各种playground设置的子表。
- **search:** 用于配置浏览器内搜索功能的子表。mdBook必须在启用该功能时进行编译（默认情况下为）：`search`
- **git-repository-url:** 给这本书的git存储库的网址。如果提供图标链接，将在本书的菜单栏中输出。
- **git-repository-icon:** 用于 git 存储库链接的字体操作图标类。默认为 ：`fa-github`
- **edit-url-template:** 编辑网址模板时，显示"建议编辑"按钮，以便直接跳转到当前查看的页面编辑。对于 gitHub 项目将其设置为或用于 Bitbucket 项目将其设置为 {路径" 将被存储库中文件的完整路径替换的位置。.`https://github.com/<owner>/<repo>/edit/master/{path}``https://bitbucket.org/<owner>/<repo>/src/master/{path}?mode=edit`
- **redirect:** 用于在移动页面时生成重定向的子表。该表包含关键值对，其中密钥是需要创建重定向文件的位置，作为生成目录的绝对路径（例如）。值可以是浏览器应导航到的任何有效 URI（例如，或）。`/appendices/bibliography.html``https://rust-lang.org/``/overview.html``../bibliography.html`
- **input-404:** 用于丢失文件的减价文件的名称。相应的输出文件将相同，扩展将替换为。 默认为 ：`html``404.md`
- **site-url:** 将托管该书的网址。这需要确保 404 文件中的导航链接和脚本/css 导入工作正常，即使在以子标题访问网址时也是如此。默认为 ：`/`
- **cname:** 将托管您的书的 DNS 子域或顶点域。根据 GitHub 页面的要求，此字符串将写入网站根部中名为 CNAME 的文件 (see [*Managing a custom domain for your GitHub Pages site*](https://docs.github.com/en/github/working-with-github-pages/managing-a-custom-domain-for-your-github-pages-site)).

#### [output.html.print]

- **enable:** 启用打印支持。默认为 ：`false``true`

#### [output.html.fold]

- **enable:** 启用部分折叠。关闭时，所有折叠均为打开。 默认为 ：`false`
- **level:** 折叠区域越高，开放区域就越多。当级别为 0 时，所有折叠均关闭。默认为 ：`0`

#### [output.html.playground]

- **editable:** 允许编辑源代码。默认为 ：`false`
- **copyable:** 在代码片段上显示副本按钮。默认为 ：`true`
- **copy-js:** 将编辑器的 JavaScript 文件复制到输出目录。 默认为 ：`true`
- **line-numbers** 在代码的可编辑部分显示行号。 默认为 ：`editable``copy-js``true``false`

#### [output.html.search]

- **enable:** 启用搜索功能。 默认为 ：`true`
- **limit-results:** 搜索结果的最大数量。默认为 ：`30`
- **teaser-word-count:** 用于搜索结果显示的单词数。默认为 ：`30`
- **use-boolean-and:** 定义多个搜索词之间的逻辑链接。如果是真的，所有搜索词都必须出现在每个结果中。 默认为 ：`false`
- **boost-title:** 如果标题中出现搜索字，则搜索结果分数的提升因子。默认为 ：`2`
- **boost-hierarchy:** 如果搜索字出现在等级中，则搜索结果分数的提升因子。等级包含父文档的所有标题和所有父标题。默认为 ：`1`
- **boost-paragraph:** 如果文本中出现搜索字，则搜索结果分数的提升因子。 默认为 ：`1`
- **expand:** 如果搜索应匹配较长的结果，则确实如此，例如搜索应匹配。默认为 ：`micro``microwave``true`
- **heading-split-level:** S搜索结果将链接到包含结果的文档的一部分。文档按此级别或更少的标题分成几个部分。 默认为 ： (`3``### This is a level 3 heading`)
- **copy-js:** 将JavaScript文件复制到输出目录中以进行搜索实现。默认为 ：`true`



---

## Tips

这显示了**book.toml**所有可用的 HTML 输出选项:

```toml
[book]
title = "Example book"
authors = ["John Doe", "Jane Doe"]
description = "The example book covers examples."

[output.html]
theme = "my-theme"
default-theme = "light"
preferred-dark-theme = "navy"
curly-quotes = true
mathjax-support = false
copy-fonts = true
google-analytics = "UA-123456-7"
additional-css = ["custom.css", "custom2.css"]
additional-js = ["custom.js"]
no-section-label = false
git-repository-url = "https://github.com/rust-lang/mdBook"
git-repository-icon = "fa-github"
edit-url-template = "https://github.com/rust-lang/mdBook/edit/master/guide/{path}"
site-url = "/example-book/"
cname = "myproject.rs"
input-404 = "not-found.md"

[output.html.print]
enable = true

[output.html.fold]
enable = false
level = 0

[output.html.playground]
editable = false
copy-js = true
line-numbers = false

[output.html.search]
enable = true
limit-results = 30
teaser-word-count = 30
use-boolean-and = true
boost-title = 2
boost-hierarchy = 1
boost-paragraph = 1
expand = true
heading-split-level = 3
copy-js = true

[output.html.redirect]
"/appendices/bibliography.html" = "https://rustc-dev-guide.rust-lang.org/appendix/bibliography.html"
"/other-installation-methods.html" = "../infra/other-installation-methods.html"[book]
title = "Example book"
authors = ["John Doe", "Jane Doe"]
description = "The example book covers examples."

[output.html]
theme = "my-theme"
default-theme = "light"
curly-quotes = true
mathjax-support = false
google-analytics = "123456"
additional-css = ["custom.css", "custom2.css"]
additional-js = ["custom.js"]
no-section-label = false
git-repository-url = "https://github.com/rust-lang-nursery/mdBook"
git-repository-icon = "fa-github"

[output.html.playpen]
editable = false # true使代码块可编辑
copy-js = true

[output.html.search]
enable = true
limit-results = 30
teaser-word-count = 30
use-boolean-and = true
boost-title = 2
boost-hierarchy = 1
boost-paragraph = 1
expand = true
heading-split-level = 3
copy-js = true
```