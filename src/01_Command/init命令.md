# init命令

---

`init`命令可以生成一个最小的Demo样板

在终端中输入以下命令：

```bash
mdbook init [path/to/book] #path可定义输出路径
```

该命令会生成如下结构：

```shell
./
├── book # html页面输出的位置；即网页结果
└── src # markdown书。它包含所有源文件,配置文件等.
    ├── chapter_1.md # 文章内容
    ├── chapter_2.md # ...
    └── SUMMARY.md # md书的骨架，即侧边导航
```

当一个`SUMMARY.md`文件已存在,`init`命令将首先解析它，并根据`SUMMARY.md`中，帮其补全丢失的文件路径。这允许您创建书的整个结构,然后让mdBook为您生成它.





---

## Tips

`--theme`命令可以指定一个主题

当你使用`--theme`,默认主题将被复制到一个名为`theme`的目录.

