# Python 脚本练习检查清单

与 [alibaba-transferable.md](alibaba-transferable.md) 一起用。含 SQL 时另遵 `python-mysql-format`。

## 必查

- [ ] 文件编码声明或 UTF-8 无乱码中文（按需 `# -*- coding: utf-8 -*-`）
- [ ] 4 空格缩进，无 Tab
- [ ] import 分组正确，无未使用的导入（练习阶段可放宽「未使用」）
- [ ] 函数/变量 `snake_case`，类 `CapWords`，常量 `UPPER_SNAKE`
- [ ] 对外函数有简短 docstring
- [ ] 无裸 `except:`
- [ ] 密钥/连接串来自环境变量或调用方传入，不写死
- [ ] 网络请求有超时（如 `timeout=`）
- [ ] DB/文件使用 `with` 或 `finally` 关闭
- [ ] 类型注解：练习鼓励对公开函数参数/返回加注解（推荐）

## 脚本结构建议

```text
imports
常量
小工具函数
核心业务函数
main / handler 入口
if __name__ == "__main__":
    main()
```

## 常见扣分

| 现象 | 对应短名 |
|------|----------|
| `except:` 后 `pass` | 异常-禁裸except / 异常-勿吞掉 |
| 密码写在源码 | 安全-密钥环境变量 |
| f-string 拼用户输入进 SQL | 安全-SQL参数化 |
| 函数 80+ 行且多职责 | 控制-嵌套不过深（建议拆） |
| 只有成功路径无失败分支 | 脚本-失败可观测 |
