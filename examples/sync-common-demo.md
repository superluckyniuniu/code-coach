# 示例：飞书 tenant_access_token（演示用）

本文件演示「出题长什么样」。真实出题应写入工作区 `practice/<topic>/`，不要把本 example 当唯一课程。

题材来自多维表格同步公共能力（`sync_common.get_tenant_access_token`），可替换成任意接口需求。

---

## 1. 需求复述

写一个函数：用飞书应用的 `app_id`、`app_secret`，调用开放平台接口，拿到 `tenant_access_token`。成功返回 token 字符串；失败时既能让调用方知道出错，又不要把 secret 打印出来。

假设：可用 `requests`；网络可达 `open.feishu.cn`。

## 2. 整体思路

1. 准备 POST URL 与 JSON body（`app_id` / `app_secret`）
2. 设置 `Content-Type: application/json`
3. 发请求，设置超时；检查 HTTP 状态
4. 解析 JSON：业务 `code == 0` 时取 `tenant_access_token`
5. 失败时返回空 token + 错误信息（或抛错，二选一，本题用「返回元组」）

## 3. 会用到的函数 / API / 库

### `requests.post(url, json=..., headers=..., timeout=...)`

- **干什么**：发 HTTP POST，`json=` 会序列化并带上 JSON Content-Type（仍建议显式 headers）
- **关键参数**：`url`；`json` 字典；`timeout` 秒
- **返回**：`Response`；用 `.raise_for_status()` 检查 HTTP；`.json()` 得字典
- **怎么用**：

```python
import requests

resp = requests.post(
    "https://httpbin.org/post",
    json={"a": 1},
    headers={"Content-Type": "application/json; charset=utf-8"},
    timeout=10,
)
resp.raise_for_status()
data = resp.json()
```

- **易错点**：忘了 timeout；只检查 HTTP 不检查业务 `code`；把 secret 打进日志

### 返回约定（本题设计）

```python
Tuple[str, Optional[Exception]]  # (token, err)；成功 err 为 None
```

## 4. 本练习相关规范点

- `安全-密钥环境变量`：练习调用处从环境变量读 secret，函数参数传入即可，勿写死在源码
- `异常-信息可查`：失败信息说明是「获取 token 失败」，可含 HTTP/业务码，禁含 secret
- `异常-禁裸except`：可捕获 `Exception`，但要返回/记录，禁止空 `pass`
- `脚本-失败可观测`：失败路径要有明确返回，不能静默空字符串且无 err
- `命名-函数蛇形`：例如 `get_tenant_access_token`

## 5. 建议文件结构

```text
practice/feishu-token/
  WORKSHEET.md
  solution.py
```

## 6. 待你填充的槽位

在 `solution.py`：

```python
from typing import Optional, Tuple

import requests


def get_tenant_access_token(
    app_id: str,
    app_secret: str,
) -> Tuple[str, Optional[Exception]]:
    """请求飞书 tenant_access_token。

    成功: (token, None)
    失败: ("", Exception(...))  # 信息中不得包含 app_secret
    """
    # TODO: 实现
    pass
```

## 7. 功能自测清单

- [ ] 成功时第一个返回值非空，第二个为 `None`
- [ ] HTTP 非 2xx 时进入失败返回
- [ ] 业务 `code != 0` 时进入失败返回
- [ ] 失败信息中不含 `app_secret` 原文

## 8. 规范自检清单

- [ ] 无裸 `except:`
- [ ] 请求带 `timeout`
- [ ] 无密钥写死在文件中

## 9. 能力标签预告

HTTP POST、业务码与 HTTP 码区分、错误返回设计、密钥安全意识

## 10. 下一步

填充后「校验」。对照现有实现可参考仓库 `项目/多维表格/小蓝书/sync_common.py` 中同名函数（仅在说「看答案」后展开讲解）。
