# code-coach

Cursor Agent Skill：小白友好的代码教练。

你提需求 → 生成教学文件（思路、函数用法、空槽、阿里风格规范点）→ 你动手填充 → 说「校验」做功能 + 规范双点评。

## 安装

复制到个人 Skills 目录：

```text
%USERPROFILE%\.cursor\skills\code-coach\
```

或在本机已有路径：`C:\Users\user\.cursor\skills\code-coach\`

## 触发词

`练手` / `代码教练` / `生成教学文件` / `校验作业` / `code coach`

## 结构

- `SKILL.md` — 出题 / 校验协议
- `worksheet-template.md` — 教学文件模板
- `review-protocol.md` — 校验输出协议
- `standards/` — 阿里可迁移规约 + Python 脚本清单
- `examples/sync-common-demo.md` — 示例（非固定课程）

## 规范

- 可迁移项参考《阿里巴巴 Java 开发手册》/ P3C
- Python 排版可与个人 Skill `python-mysql-format` 配合
- 前端可与 `f2e-spec` 配合
