# 各助手PARA目录变更清单

**整理日期**: 2026-03-23

---

## 读书搭子 (workspace-reader)

### 变更的文件
| 原位置 | 新位置 |
|:---|:---|
| `library/` | `03-Resources/Books/library/` |
| `library_rag/` | `03-Resources/Books/library_rag/` |
| `test_book*` | `03-Resources/Books/` |
| `karamazov*.html` | `05-Attachments/images/` |

### 需要检查的配置
- 任何引用 `~/library_rag/` 的路径 → 改为 `~/workspace-reader/03-Resources/Books/library_rag/`
- 任何引用 `~/library/` 的路径 → 改为 `~/workspace-reader/03-Resources/Books/library/`

---

## 办公搭子 (workspace-office)

### 变更的文件
- 会议纪要移至 `03-Resources/Meeting-Minutes/`
- 转录脚本移至 `03-Resources/Scripts/`
- 16个祖冲之项目文件归档

### 需要检查的配置
- 检查引用会议纪要路径的配置

---

## 写作搭子 (workspace-writer)

### 变更的文件
- 散落文件已整理

### 需要检查的配置
- 基本无需变更

---

## 技术搭子 (workspace-tech)

### 变更的文件
| 原位置 | 新位置 |
|:---|:---|
| `scripts/` | `03-Resources/Scripts/` |
| `research/` | `01-Projects/research/` |
| `fix-new-machine.sh` | `03-Resources/Scripts/` |
| `todo-tracker.*` | `03-Resources/Scripts/` |

### 公网方案变更
- **删除**: ngrok
- **新增**: cloudflared (统一标准)

### 需要检查的配置
- 任何使用 ngrok 的脚本 → 改用 cloudflared
- 任何引用 scripts/ 的路径 → 改为 03-Resources/Scripts/
- 任何引用 research/ 的路径 → 改为 01-Projects/research/

---

## 信息搭子 (workspace-info)

### 变更的文件
- `morning_news_brief_*.md/html/pdf` → `03-Resources/Reports/Daily-Briefs/`
- 测试文件 → `04-Archive/Tests/`

### 需要检查的配置
- 简报生成脚本的输出路径

---

## 生活搭子 (workspace-life)

### 变更的文件
| 原位置 | 新位置 |
|:---|:---|
| `reports/` | `03-Resources/Reports/` |
| 中文文件夹x4 | `03-Resources/Knowledge/` |

### 需要检查的配置
- 检查引用这些目录的脚本

---

## 方案搭子 (workspace-planner)

### 变更的文件
| 原位置 | 新位置 |
|:---|:---|
| `baidu-news.png` | `05-Attachments/images/` |
| `transcribe_audio.py` | `03-Resources/Scripts/` |

### 需要检查的配置
- 检查输出路径配置

---

## 通用PARA规范

所有助手的新文件流向：
```
新文件 → 00-Inbox/ → 每周五整理 → 移到PARA目录
```

PARA目录结构：
- 00-Inbox/ - 收件箱
- 01-Projects/ - 项目
- 02-Areas/ - 领域
- 03-Resources/ - 资源
- 04-Archive/ - 归档
- 05-Attachments/ - 附件

---

**完成后请单独发消息给组长汇报调整内容**