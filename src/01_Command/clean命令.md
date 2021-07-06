# clean 命令

`clean` 命令用于删除生成的书籍，和任何其他构建工件.

```shell
mdbook clean (path/to/book) #path可选
```

---

`--dest-dir (-d)`选项允许您覆盖书籍的输出目录,该目录会删除。 为相对路径，（相对于书籍的根目录）。如果未指定,则默认为book.toml配置的build.build-dir字段, 或者./book目录.

