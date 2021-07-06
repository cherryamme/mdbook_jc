# Summary.md 格式

MDbook使用摘要文件来了解要包含的章节，以它们所显示的顺序为单位，它们的层次结构是什么以及源文件所在的顺序。 没有这个文件，没有书。



此标记文件必须命名为summary.md。 它的格式非常严格，必须遵循下面概述的结构，以便容易解析。 任何未指定的元素都在下面指定，无论是格式化还是文本，都可能最多忽略，或者在尝试构建本书时可能会导致错误。

## 允许的 elements

1. Title一般来说,通常以# Summary.标题开头是常见的做法，但它不是强制性的,解析器只是忽略它.如果你也是这样想,也忽略它。

2. 开头章节位于主编号章节前,您可以添加一些不编号的元素。这对前言,介绍等很有用.但是有一些限制。你不能嵌套开头章节,它们都应该在根级别.一旦添加了编号章节,就无法添加开头章节

   ```markdown
   [开头章节的标题](relative/path/to/markdown.md)
   ```

3. 编号章节是本书的主要内容,它们将被编号，并可以嵌套,从而产生一个很好的层次结构(章节,子章节等)

   ```markdown
   # Title of Part
   
   - [First Chapter](relative/path/to/markdown.md)
   - [Second Chapter](relative/path/to/markdown2.md)
      - [Sub Chapter](relative/path/to/markdown3.md)
   
   # Title of Another Part
   
   - [Another Chapter](relative/path/to/markdown4.md)
   ```

   你可以使用-或*表示编号的章节.

4. 空白章节是没有文件的章节

   ```markdown
   - [Draft Chapter]()
   ```

5. 分隔符能分隔内容表

   ```markdown
   # My Part Title
   
   [A Prefix Chapter](relative/path/to/markdown.md)
   
   ---
   
   - [First Chapter](relative/path/to/markdown2.md)
   ```

   



---

## Tips

 `SUMMARY.MD`中，也支持层级的嵌套，或者是分章节的目录形式，其格式如下：

```markdown
# Summary

- [mdBook](README.md)
- [Command Line Tool](cli/README.md)
    - [init](cli/init.md)
    - [build](cli/build.md)
    - [watch](cli/watch.md)
    - [serve](cli/serve.md)
    - [test](cli/test.md)
    - [clean](cli/clean.md)
- [Format](format/README.md)
    - [SUMMARY.md](format/summary.md)
        - [Draft chapter]()
    - [Configuration](format/configuration/README.md)
        - [General](format/configuration/general.md)
        - [Preprocessors](format/configuration/preprocessors.md)
        - [Renderers](format/configuration/renderers.md)
        - [Environment Variables](format/configuration/environment-variables.md)
    - [Theme](format/theme/README.md)
        - [index.hbs](format/theme/index-hbs.md)
        - [Syntax highlighting](format/theme/syntax-highlighting.md)
        - [Editor](format/theme/editor.md)
    - [MathJax Support](format/mathjax.md)
    - [mdBook-specific features](format/mdbook.md)
- [Continuous Integration](continuous-integration.md)
- [For Developers](for_developers/README.md)
    - [Preprocessors](for_developers/preprocessors.md)
    - [Alternative Backends](for_developers/backends.md)

-----------

[Contributors](misc/contributors.md)
```

使用两个空格可分为下级

其他格式的内容将被忽略或导致错误.

