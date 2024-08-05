# 分页

Intel在Ice Lake处理器支持了[5级分页](https://en.wikipedia.org/wiki/Intel_5-level_paging)，但是绝大部分还是只支持4级分页。

Linux内核为了兼容各种硬件，在数据结构上是设计了5个级别：
1. PGD(Page Global Direcotry)，页全局目录
2. P4D(Page 4th Directory)，页四级目录
3. PUD(Page Upper Directory)，页上级目录
4. PMD(Page Middle Directory)，页中级目录
5. PT(Page Table)，页表