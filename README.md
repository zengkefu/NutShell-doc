# NutShell 文档

目前该 repo 已经和 github.io 绑定，域名为 https://oscpu.github.io/NutShell-doc/

文档改写完成后，请运行 `gitbook build ./ ./building` 生成网页

### 文档正在撰写中.... 敬请期待！



## 文档编写规范

1. 文档格式是 Markdown，使用中文编写，可夹杂英文；在使用英文的缩写前，保证本页面或相近页面出现过对应的全称解释，比如：

   ```
   我们的分支预测器使用了分支目标缓冲器(Branch Target Buffer，BTB)这一结构, ......
   ......
   目前 BTB 中包含了 ......
   ```

2. 说明结构的时候尽量配图，如果嫌麻烦的话可以手画一张草图传上去然后 后续使用软件画出来做润色

3. 写的时候要记住文档给面向大众，所以多写一些总览框架，不必拘泥于类似信号的含义这样的细节



## TODO List

`流水线：`

总览

IFU

IDU

ISU

EXU

WBU

`功能部件：`

LSU

CSR

Cache ---- 待补充

TLB

BPU

`外围部件`

访存系统 ---- 待补充

外设系统 ---- 待补充

总线 ---- 待补充

`其他`

配套生态 ---- 待补充

参数化配置 ---- 初稿

调试指南 ---- 初稿

上手教程 ---- 初稿



