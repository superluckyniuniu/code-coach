# 规范层级与选用

校验与出题时按语言选用，**不整本抄手册**。

| 优先级 | 来源 | 何时用 |
|--------|------|--------|
| 1 | 个人 Skill `python-mysql-format` | Python 且含 SQL / f-string SQL：只查缩进与 SQL 排版 |
| 1 | 个人 Skill `f2e-spec` | 前端 JS/TS/CSS |
| 2 | [alibaba-transferable.md](alibaba-transferable.md) | 任意语言脚本/接口：命名、异常、安全、注释等可迁移项 |
| 3 | [python-script-checklist.md](python-script-checklist.md) | Python 脚本/接口练习 |
| 4 | PEP 8 | Python 风格补充；与 `python-mysql-format` 冲突时以后者为准 |

公开参考（需要原文时再查，不必每次全读）：

- 《阿里巴巴 Java 开发手册》嵩山版 / [Alibaba Java Coding Guidelines](https://alibaba.github.io/Alibaba-Java-Coding-Guidelines/) / [alibaba/p3c](https://github.com/alibaba/p3c)
- [PEP 8](https://peps.python.org/pep-0008/)
- [云效 Python 检测规则说明](https://help.aliyun.com/zh/yunxiao/user-guide/supported-detection-rules)

出题时从上述清单抽 **3–8 条** 写进 WORKSHEET「本练习相关规范点」，校验时只严查这些 + 全局必查安全项。
