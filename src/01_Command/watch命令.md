# watch 命令

当您希望在每次更改文件，都生成图书时, watch命令会很有用。你当然可以在每次更改文件反复发出`mdbook build`。但，聪明的是使用mdbook watch，这样就能观察您的文件,并会在您修改文件时，自动触发构建.

```shell
mdbook watch (path/to/book)
```

---

`--open (-o)`当你使用该选项，mdbook 将在您的默认 Web 浏览器中打开网页书.


`--dest-dir (-d)`选项允许您更改书籍的输出目录。为相对路径，（相对于书籍的根目录）。如果未指定,则默认为`book.toml`配置的`build.build-dir`字段, 或者`./book`目录.

