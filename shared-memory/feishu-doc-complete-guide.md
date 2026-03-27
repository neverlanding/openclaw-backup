# 飞书文档完整操作指南

**关键词**: 飞书、文档、创建、feishu_doc、accountId

---

## 一、工具简介

`feishu_doc` 是 OpenClaw 官方飞书文档操作工具，支持：
- 创建文档 (`create`)
- 读取文档 (`read`)
- 追加内容 (`append`)
- 插入内容 (`insert`)
- 更新内容 (`update`)
- 删除内容 (`delete`)
- 上传图片 (`upload_image`)

---

## 二、各助手账号 ID 对照表

| 助手 | Agent ID | 账号 ID | App ID | 说明 |
|:---|:---|:---:|:---|:---|
| 方案搭子 | planner | 1 | cli_a92bd5e6d339dcd2 | 负责 PPT/Word 方案 |
| 办公搭子 | office | 2 | cli_a92ce59b76fb9cc2 | 负责会议纪要/日报 |
| **写作搭子** | writer | **3** | cli_a92cc78ef8b89ccd | 负责内容创作 |
| 信息搭子 | info | 4 | cli_a92ce03f79b85cee | 负责新闻监控 |
| 读书搭子 | reader | 5 | cli_a92ce21baa3a9cb5 | 负责阅读笔记 |
| 生活搭子 | life | 6 | cli_a92ce269bd789cc6 | 负责生活管理 |
| 技术搭子 | tech | 7 | cli_a92ce2c190769cb3 | 负责开发调试 |

**重要**: 每个助手必须使用自己的账号 ID，否则会报 `Feishu credentials not configured for account "default"` 错误。

---

## 三、正确调用格式

### 3.1 创建文档（必须两步骤）

**步骤 1：创建空文档**
```json
{
  "action": "create",
  "title": "文档标题",
  "folder_token": "可选，目标文件夹 token"
}
```

**步骤 2：追加正文内容（必须！）**
```json
{
  "action": "append",
  "doc_token": "上一步返回的文档 token",
  "content": "Markdown 格式的正文内容"
}
```

**步骤 3：验证内容**
```json
{
  "action": "read",
  "doc_token": "文档 token"
}
```

### 3.2 参数说明

| 参数 | 类型 | 必填 | 说明 |
|:---|:---|:---:|:---|
| action | string | ✅ | 操作类型：create/read/append/insert |
| title | string | ✅ (create) | 文档标题 |
| content | string | ✅ (append/insert) | Markdown 内容 |
| doc_token | string | ✅ (read/append) | 文档 token |
| folder_token | string | ❌ | 目标文件夹 token |
| block_id | string | ❌ | 插入位置 block ID |
| index | number | ❌ | 插入位置索引 |

### 3.3 常见错误

| 错误 | 原因 | 解决方案 |
|:---|:---|:---|
| `Feishu credentials not configured for account "default"` | 未指定 accountId 或账号不存在 | 添加正确的 accountId 参数 |
| `value?.trim is not a function` | OpenClaw 版本 bug，参数类型验证问题 | 等待版本修复，或用其他方式 |
| `Request failed with status code 400` | 参数格式错误 | 检查 JSON 格式和必填参数 |

---

## 四、Markdown 内容格式

飞书支持 Lark-flavored Markdown，常用语法：

| 格式 | 语法 | 示例 |
|:---|:---|:---|
| 一级标题 | `# 标题` | `# 我是标题` |
| 二级标题 | `## 标题` | `## 二级标题` |
| 粗体 | `**文字**` | **粗体** |
| 斜体 | `*文字*` | *斜体* |
| 链接 | `[文字](URL)` | [飞书](https://feishu.cn) |
| 无序列表 | `- 项目` | - 项目1 |
| 有序列表 | `1. 项目` | 1. 第一项 |
| 代码块 | ` ```语言\n代码\n``` ` | ```js\nconsole.log()\n``` |
| 表格 | `| 列1 | 列2 |` | \| name \| age \| |
| 分割线 | `---` | --- |
| 引用 | `> 文字` | > 引用内容 |

---

## 五、最佳实践

### 5.1 创建完整文档流程

```markdown
# 第一步：创建标题
feishu_doc(action="create", title="2026年度总结")

# 第二步：获取 doc_token 后，追加正文
feishu_doc(
  action="append",
  doc_token="xxxxxx",
  content="# 2026年度总结\n\n## 一、年度目标\n\n...内容..."
)

# 第三步：验证
feishu_doc(action="read", doc_token="xxxxxx")

# 第四步：发送链接给用户
message(action="send", target="user_id", message="文档已创建：https://xxxxx")
```

### 5.2 注意事项

1. **必须两步骤**：create 创建空文档 → append 追加内容
2. **验证后再发送**：创建后立即 read 验证内容完整
3. **本地备份**：重要文档本地保留一份
4. **账号匹配**：确认使用的账号有权限

---

## 六、实测验证（2026-03-24）

**测试时间**: 2026-03-24 22:59
**测试结果**: ✅ 成功！

**验证步骤**：
1. `feishu_doc create` → 返回 document_id
2. `feishu_doc append` → 成功追加 11 个 blocks
3. `feishu_doc read` → 内容完整，12 blocks

**文档链接**: https://feishu.cn/docx/WlfRd7aRLoMIhBx1uVXcPD5nnhg

---

## 七、临时解决方案

由于当前版本 (2026.3.23-2) 存在 accountId 参数 bug：

**方案 A**：手动在飞书中创建文档 → 让助手编辑内容
**方案 B**：等待 OpenClaw 版本更新修复
**方案 C**：使用其他工具（如 web 浏览器）创建后分享链接

---

## ⚠️ 重要提示

**所有助手请注意**：
- 飞书文档操作指南保存在 `shared-memory/feishu-doc-complete-guide.md`
- 遇到问题先查这份指南
- 不要重复问相同问题

---

## 七、相关文件

| 文件 | 说明 |
|:---|:---|
| `shared-memory/feishu-ids.md` | 飞书机器人 ID 对照表 |
| `shared-memory/feishu-image-send-guide.md` | 飞书图片发送指南 |
| `shared-memory/failure-lessons-quickref.md` | 失败教训速查 |

---

*更新时间：2026-03-24 22:57*
*维护者：搭子总价*