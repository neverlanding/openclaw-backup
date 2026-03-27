# 05-Attachments - 附件箱

> **这是什么**：从**外部接收**的文件、下载的内容、临时附件
> **什么时候用**：接收外部文件、下载资料、临时存放
> **存放内容**：文档、图片、PPT、下载的文件
> **处理流程**：接收 → 处理 → 决定去向（Resources/Archive/删除）

**与 Resources 的区别**：Attachments 是输入口，Resources 是已整理的资源

## 📂 子目录说明

| 目录 | 用途 | 当前内容 |
|:---|:---|:---|
| `documents/` | 文档附件 | PDF, Word, Excel文件 |
| `images/` | 图片附件 | github_proxy.png, moores_law.png |
| `presentations/` | 演示文稿 | PPT文件 |

## 📂 当前内容

```
05-Attachments/
├── documents/
│   ├── 今日OpenClaw探索之旅.html
│   └── ...
├── images/
│   ├── github_proxy.png
│   └── moores_law.png
└── presentations/
    ├── CYBERPUNK-AI未来.pptx
    ├── OpenClaw-Linux安装部署指南.pptx
    ├── 今日探索-Gamma风格.pptx
    ├── 今日探索-Prezentit风格.pptx
    └── 今日OpenClaw探索之旅.pptx
```

## 🔄 与其他目录的关系

| 目录 | 用途 | 区别 |
|:---|:---|:---|
| `05-Attachments/` | **输入**（外部接收）| 从外部获取的文件 |
| `output/` | **输出**（系统生成）| 系统生成的结果（如白板图片）|
| `tmp/` | **临时**（中转）| 用完即删的临时文件 |

## 处理流程

1. 外部文件放入 `05-Attachments/`
2. 处理后决定去向：
   - 重要资料 → `03-Resources/Documents/`
   - 临时使用 → `tmp/`
   - 输出结果 → `output/`
   - 无需保留 → 删除

## 快速链接

- [[../output/|查看输出]]
- [[../tmp/|查看临时文件]]
- [[../03-Resources/Documents/|查看资源]]