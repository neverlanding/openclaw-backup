# 03-Resources - 资源库

> **这是什么**：可**复用**的参考资料、模板、工具脚本
> **什么时候用**：查找工具脚本、参考历史报告、复用模板
> **存放内容**：脚本库、报告文档、会议纪要、经验教训
> **使用方式**：需要时直接取用，不需要时保持原样

**与 Inbox 的区别**：Resources 是已整理的资源，Inbox 是待处理的临时文件

## 📜 脚本库

| 脚本 | 用途 | 位置 |
|:---|:---|:---|
| **openclaw-backup.sh** | 系统备份 | [[../scripts/openclaw-backup.sh]] |
| **openclaw-restore.sh** | 系统恢复 | [[../scripts/openclaw-restore.sh]] |
| **export-openclaw-config.sh** | 配置导出 | [[../scripts/deploy/export-openclaw-config.sh]] |
| **import-openclaw-config.sh** | 配置导入 | [[../scripts/deploy/import-openclaw-config.sh]] |
| **task-send.sh** | 任务发送 | [[../scripts/task/task-send.sh]] |
| **task-update.sh** | 任务更新 | [[../scripts/task/task-update.sh]] |
| **daily-stats.sh** | 每日统计 | [[../scripts/core/daily-stats.sh]] |
| **memory-health.sh** | 健康检查 | [[../scripts/core/memory-health.sh]] |

## 📊 报告资源

| 报告 | 日期 | 位置 |
|:---|:---:|:---|
| **AI Agent论文综述** | 2024 | [[03-Resources/Reports/ai-agent-papers-review.md]] |
| **AI芯片报告2024** | 2024 | [[03-Resources/Reports/ai_chip_report_2024.md]] |
| **A股技能研究报告** | 2024 | [[03-Resources/Reports/a-stock-skills-research-report.md]] |
| **数字员工报告** | 2024 | [[03-Resources/Reports/digital-employee-report.md]] |

## 💡 经验教训

实际位置：`memory/lessons/`（通过软链接访问）

| 教训 | 日期 | 位置 |
|:---|:---:|:---|
| **定时任务进度严禁编造** | 2026-03-11 | [[memory/lessons/cron-progress-reporting.md]] |
| **飞书多机器人配置** | 2026-03-06 | [[memory/lessons/feishu-multi-bot.md]] |
| **飞书多机器人配置指南** | 2026-03-16 | [[memory/lessons/feishu-multi-bot-config.md]] |

## 🗂️ 资源子目录

```
03-Resources/
├── README.md               # 本文件
├── Documents/              # 文档资源
├── Lessons-Learned/        # → 软链接到 ../memory/lessons/
├── Meeting-Notes/          # 会议纪要
├── Reports/                # 报告文件
│   ├── ai-agent-papers-review.md
│   ├── ai_chip_report_2024.md
│   └── ...
└── Scripts/                # 脚本资源
    ├── js/                 # JavaScript脚本
    ├── python/             # Python脚本
    └── shell/              # Shell脚本
```

## 快速链接

- [[../scripts/|浏览所有脚本]]
- [[memory/lessons/|浏览所有教训]]
- [[../output/|浏览输出文件]]
- [[../tmp/|浏览临时文件]]