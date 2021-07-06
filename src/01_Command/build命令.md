# build 命令

`build`构建命令,用于渲染您的md,并输出静态 html:

```bash
mdbook build (path/to/book) # 选择path
```

它会尝试解析你的`SUMMARY.md`文件，以了解您的图书的结构并获取相应的文件.

---

为方便起见,渲染的输出将保持与源目录结构相同。因此,大型书籍在渲染时能保持结构化.

`--open (-o)`参数可以在构建后在浏览器中打开

`--dest-dir (-d)` 选项允许您更改书籍的输出目录。为相对路径，（相对于书籍的根目录）。如果未指定,则默认为`book.toml`配置的`build.build-dir`字段, 或者`./book`目录.







------

## Tips

确保在根目录中运行 build 命令,而不是在源`src`目录中运行

