# 01-Projects - 项目目录

> **这是什么**：有**明确截止日期**的任务和事项
> **什么时候用**：启动新任务、跟踪项目进展、项目完成后归档
> **存放内容**：项目文档、计划、进展记录、交付物
> **完成标准**：达成目标后标记完成，移动到 Archive/

**与 Areas 的区别**：Projects 有 deadline，Areas 是长期维护

## 🔥 当前活跃项目

| 项目名称 | 截止日期 | 位置 | 状态 |
|:---|:---:|:---|:---|
| **配置优化专项** | 2026-03-20 | [[memory/projects/optimization.md]] | 🟡 进行中 |
| **8-Agent团队建设** | - | [[01-Projects/8-Agent-Team-Setup/]] | ✅ 已完成 |
| **飞书集成** | - | [[01-Projects/Feishu-Integration/]] | 🟢 运行中 |
| **微博数据采集** | - | [[01-Projects/Weibo-Data-Collection/]] | 🟢 运行中 |

## 项目文件夹结构

```
01-Projects/
├── 8-Agent-Team-Setup/          # 8-Agent 团队建设
│   └── handoff_planner_to_boss.md
├── Feishu-Integration/          # 飞书集成项目
└── Weibo-Data-Collection/       # 微博数据采集
    ├── weibo_alternative_solution.md
    ├── WEIBO_AUTOMATION_GUIDE.md
    └── WEIBO_SCRAPER_README.md
```

实际项目档案存储位置：
```
memory/projects/
├── agent-team-setup.md          ✅ 已完成
├── feishu-integration.md        🟡 进行中
├── optimization.md              🟡 进行中
├── word-formatting-skills-research.md
├── vpn-optimization-analysis.md
└── ...（共11个项目档案）
```

## ✅ 完成标准

项目完成后：
1. 在此标记状态为 ✅
2. 将项目档案移动到 `memory/projects/`
3. 更新本索引指向归档位置
4. 记录经验教训到 `memory/lessons/`

## 快速链接

- [[../memory/projects/|查看所有项目档案]]
- [[../04-Archive/Projects/|查看已归档项目]]
- [[../memory/appointments.md|查看项目待办]]
- [[00-Inbox/|处理新任务]]