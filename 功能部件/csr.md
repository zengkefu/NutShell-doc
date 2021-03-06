# CSR 单元

CSR 单元主要负责特权级指令的执行以及例外/中断的处理. 

RISC-V 特权级是比较复杂的，涉及到很多寄存器的读写与控制，为了简化设计难度、提高代码的可读性，我们构造了一个特殊的 MaskedRegMap 结构来优化特权级寄存器的读写，并围绕这一设计给出相应的特权级控制逻辑. 针对每一个 CSR 寄存器构造 MaskedRegMap，包括了

* CSR 寄存器索引
* CSR 寄存器存储位置
* 读、写掩码
* 写副作用（side effect）函数

这几个经过凝练的通用读写控制域，每当接受到读写请求时均会按照设定做出相应的修饰再最终读写物理寄存器.

在 CSR 单元中，我们大量地使用了 BoringUtils 这一 Chisel 内置类来进行飞线，这是因为很多其他的功能部件需要从 CSR 中获取到当前系统状态来实现相应功能（比如 LSU，TLB 等）.

NutShell 默认支持以下的 CSR 寄存器. 要调整可使用的 CSR 以及设置 CSR 的 初始值, 参见源码中的 CSR.scala:

```
# U 模式
1. Ustatus    2. Uie        3. Utvec     4. Uscratch
5. Uepc       6. Ucause     7. Utval     8. Uip
# S 模式
1. Sstatus    2. Sedeleg    3. Sideleg   4. Sie
5. Stvec      6. Scounteren 7. Sscratch  8. Sepc
9. Scause     10. Stval     11. Sip      12. Satp
# M 模式
1. Mvendorid  2. Marchid    3. Mimpid    4. Mhartid
5. Mstatus    6. Mstatus    7. Misa      8. Medeleg 
9. Mideleg    10. Mie       11. Mtvec    12. Mcounteren
13. Mscratch  14. Mepc      15. Mcause   16. Mtval 
29. Mip
```

