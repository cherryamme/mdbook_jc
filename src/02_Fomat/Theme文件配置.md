# Theme文件配置

默认渲染器使用一个[handlebars](http://handlebarsjs.com/)模板，用于渲染markdown文件,并mdBook二进制文件包含默认主题.

主题是完全可定制的,您可以通过在根目录`src`旁边，新建一个`theme`文件夹，在其中选择性地添加文件名称，覆盖主题的任意文件。

| 以下是您可以覆盖的文件: | 描述                                                         |
| ----------------------- | ------------------------------------------------------------ |
| **index.hbs**           | hbs模板.                                                     |
| **head.hbs**            | 附加到HTML `<Head>`部分。                                    |
| **header.hbs**          | 内容附加在每本书页面的顶部。                                 |
| **css/**                | 包含用于造型书的 CSS 文件。<br />**/chrome.css**是用于UI元素的。<br />是基本风格。<br />**/general.css**是打印机输出的风格。<br />**/print.css**包含其他CSS文件中使用的变量。 |
| **book.js**             | 主要用于添加客户端功能,如隐藏/取消隐藏侧边栏,更改主题,...    |
| **highlight.js**        | 是用于突出显示代码片段的JavaScript,您不需要修改它.           |
| **highlight.css**       | 是用于代码突出显示的主题                                     |
| **favicon.png**         | 将使用的favicon                                              |



通常，当您想要调整主题时，您不需要覆盖所有文件。如果您只需要更改样式表，则无法覆盖所有其他文件。由于自定义文件优先于内置文件，因此不会使用新的修复/功能进行更新。

**注：**当您覆盖文件时，可能会中断某些功能。因此，我建议使用默认主题中的文件作为模板，并且仅添加/修改您需要的内容。只需删除您不想覆盖的文件，即可自动将默认主题复制到源目录中。`mdbook init --theme`

如果您完全替换所有内置主题，请务必在配置中设置[` output.html.preferred-dark-theme `](https://rust-lang.github.io/mdBook/format/configuration/renderers.html#html-renderer-options)，该主题默认为内置主题。`navy`

