# 04-Archive - 归档库

> **这是什么**：**已完成**的项目、历史记录、不再活跃的内容
> **什么时候用**：项目完成、日志过期、清理旧文件时
> **存放内容**：已完成项目、历史日志、旧备份、遗留文件
> **管理方式**：按时间归档、保留索引、定期清理

**与其他目录的区别**：Archive 是终点，其他目录是进行中

## 📁 归档结构

```
04-Archive/
├── README.md                    # 本文件
├── 2026-02-Legacy/              # 2026年2月遗留
├── 2026-03-Early/               # 2026年3月早期
├── legacy-clash-backup/         # clash旧备份（41M）
├── legacy-workspace-2026-02/    # 旧workspace归档（38M）
├── Scripts/                     # 归档的脚本
└── Weibo-Data/                  # 微博数据归档
```

## 🗃️ 已归档项目

| 项目 | 完成日期 | 原位置 | 归档位置 |
|:---|:---:|:---|:---|
| **旧workspace数据** | 2026-02 | ~/.openclaw/workspace/ | [[04-Archive/legacy-workspace-2026-02/]] |
| **clash配置备份** | 2026-03-13 | ~/.openclaw/archives/ | [[04-Archive/legacy-clash-backup/]] |

## 📅 历史日志归档

按年月归档：
- [[memory/archive/|memory/archive/]] - 自动归档的旧日志
- [[04-Archive/2026-02-Legacy/|2026年2月遗留]]
- [[04-Archive/2026-03-Early/|2026年3月早期]]

## 归档规则

1. **项目归档**：完成后移动到 `memory/projects/`，然后标记完成
2. **日志归档**：超过7天的日期日志自动按月归档到 `memory/archive/`
3. **配置备份**：旧配置备份到 `openclaw-full-config/`
4. **遗留文件**：定期清理到 `04-Archive/legacy-*/`

## 快速链接

- [[../memory/projects/|活跃项目]]
- [[../memory/archive/|历史日志]]
- [[../01-Projects/|返回项目]]
- [[../openclaw-full-config/|配置备份]]