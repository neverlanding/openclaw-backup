# TOOLS.md - 工具速查表

> 版本: v1.1 | 更新: 2026-03-20

---

## 常用工具

| 工具 | 用途 | 典型场景 |
|:---|:---|:---|
| `write`/`edit` | 文件编辑 | 创建/修改代码、配置文件 |
| `read` | 文件读取 | 查看代码、文档内容 |
| `exec` | 命令执行 | 系统操作、脚本运行 |
| `process` | 进程管理 | 后台任务管理 |
| `browser` | 浏览器自动化 | 网页操作、截图 |
| `sessions_spawn` | 子任务分发 | 复杂任务拆分 |
| `sessions_send` | 跨会话通信 | 与其他助手通信，**timeoutSeconds: 120** |
| `memory_search` | 记忆检索 | 查询历史记录 |
| `feishu_doc` | 飞书文档 | 文档读写操作 |

---

## 关键参数配置

### sessions_send 超时配置

**默认超时**: 120秒（2分钟）

```javascript
sessions_send(
  sessionKey: "agent:boss:main",
  message: "...",
  timeoutSeconds: 120  // 等待2分钟
)
```

**参数说明**:
- `timeoutSeconds: 0` → fire-and-forget 模式（不等待回复）
- `timeoutSeconds: 120` → 等待最多2分钟（推荐默认值）

---

### 全局超时配置

**配置位置**: `agents.defaults.subagents.announceTimeoutMs`

**当前值**: 120000ms（2分钟）

**作用范围**: `sessions_spawn` 创建的子 agent announce 流程

**注意**: `sessions_send` 的 announce 等待会被代码限制在 60 秒以内（`Math.min(announceTimeoutMs, 60_000)`）

---

### 两个配置的关系

| 配置 | 作用场景 | 推荐值 |
|:---|:---|:---|
| `agents.defaults.subagents.announceTimeoutMs` | sessions_spawn 子 agent | 120000 |
| `sessions_send(timeoutSeconds)` | sessions_send 等待回复 | 120 |

**两者独立，互不影响**

---

## 常用路径

| 路径 | 说明 |
|:---|:---|
| `~/.openclaw/` | OpenClaw 根目录 |
| `~/.openclaw/openclaw.json` | 主配置文件 |
| `~/.openclaw/backups/` | 配置备份目录 |
| `~/.openclaw/workspace-tech/` | 我的工作目录 |
| `~/.openclaw/workspace-tech/03-Resources/Scripts/` | 脚本目录（PARA）|
| `~/.openclaw/workspace-tech/01-Projects/research/` | 研究资料（PARA）|
| `~/.openclaw/shared-memory/` | 公共记忆目录 |
| `~/.openclaw/skills/` | 共享技能目录 |

---

## 技能命名规范

### 命名前缀

| 前缀 | 含义 | 示例 |
|:---|:---|:---|
| **0-** | 本地生成技能（团队自建）| `0-agent-config-optimizer` |
| 无前缀 | 外部安装技能（ClawHub/其他）| `self-improving`、`tavily-search` |

### 判断标准

- **有 `_meta.json` 或 `.clawhub/` 目录** → 外部安装（无前缀）
- **无上述文件** → 本地生成（加 0- 前缀）

### 当前技能清单

| 技能 | 类型 | 用途 |
|:---|:---|:---|
| 0-agent-config-optimizer | 本地 | 配置文件优化 |
| 0-doxen-notes | 本地 | 读写客笔记导出到Obsidian |
| email-sender | 外部 | 邮件发送 |
| find-skills | 外部 | 技能发现 |
| freeride | 外部 | 免费模型管理 |
| nano-pdf | 外部 | PDF 编辑 |
| self-improving | 外部 | 自我改进记忆 |
| skill-vetter | 外部 | 技能安全审查 |
| summarize | 外部 | URL/文件摘要 |
| tavily-search | 外部 | AI 搜索 |

**总计**：2个本地 + 8个外部 = 10个技能

---

## 快捷命令

### OpenClaw 管理
```bash
openclaw status          # 查看状态
openclaw gateway status  # Gateway状态
openclaw gateway restart # 重启Gateway
openclaw cron list       # 查看定时任务
```

### 系统操作
```bash
# 备份配置
mkdir -p ~/.openclaw/backups/$(date +%Y-%m-%d)
cp ~/.openclaw/openclaw.json ~/.openclaw/backups/$(date +%Y-%m-%d)/openclaw-$(date +%H%M%S).json

# 查看日志
tail -f ~/.openclaw/logs/gateway.log
```

### 公网访问（cloudflared）
```bash
# 启动隧道（统一方案）
nohup cloudflared tunnel --url http://localhost:PORT > /tmp/cloudflared-PORT.log 2>&1 &

# 查看公网地址
tail -f /tmp/cloudflared-PORT.log | grep "trycloudflare.com"

# 使用快捷脚本
~/.openclaw/workspace-tech/03-Resources/Scripts/start-cloudflared.sh PORT
```

---

## 关键配置

### Gateway重启安全流程
详见：`shared-memory/COMMON_RULES.md` → Gateway重启安全机制

**四步流程**：备份 → 请示组长 → 执行 → 验证汇报

### 定时任务配置
```json
{
  "agentId": "tech",
  "sessionTarget": "isolated",
  "payload": {
    "kind": "agentTurn",
    "message": "任务描述"
  },
  "delivery": {
    "mode": "announce",
    "channel": "feishu"
  }
}
```

---

## 共享记忆路径

| 文件 | 内容 |
|:---|:---|
| `shared-memory/COMMON_RULES.md` | 公共规则手册 |
| `shared-memory/SKILL_SOURCES.md` | 技能查找渠道 |
| `shared-memory/USER_MAPPING.md` | 用户ID映射表 |

---

## 术语偏好

| 当组长说... | 指的是... |
|:---|:---|
| **open code** | **OpenCode** - 开源 AI 编程代理，不是 OpenAI Codex |
