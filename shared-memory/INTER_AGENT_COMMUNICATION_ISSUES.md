# 跨Agent通信机制问题追踪

> 创建时间：2026-03-21
> 优先级：高
> 状态：已确认是已知问题

---

## 问题1：sessions_send 超时

### 现象
- 通过 `sessions_send` 进行跨Agent通信时，经常出现**超时问题**
- 超时时间设置：默认 60秒（announceTimeoutMs）

### GitHub Issues

| Issue | 标题 | 状态 | 说明 |
|:---:|:---|:---:|:---|
| **#42233** | sessions_send frequently times out | Open | 最直接相关 |
| **#40863** | Default announceTimeoutMs (60s) too short | Open | 有PR |
| **#40864** | Add persistent message queue | Open | 功能请求 |

### 解决方案
```json
{
  "agents": {
    "defaults": {
      "announceTimeoutMs": 180000
    }
  }
}
```

---

## 问题2：skills.entries.*.env 不注入

### 现象
- exec 工具运行 skill 脚本时，环境变量不被注入
- 影响：send-email、tavily-search 等技能

### GitHub Issues

| Issue | 标题 | 状态 | 说明 |
|:---:|:---|:---:|:---|
| **#31583** | exec tool does not inherit skills.entries.*.env | Open | 🔴 bug + regression，有11个PR |
| **#43078** | Skill env vars not injected into exec child processes | Open | 同样问题 |

### 临时解决方案
```javascript
exec({
  command: "python3 script.py",
  env: { EMAIL_SMTP_SERVER: "xxx", ... }
})
```

---

## 监控清单

- [ ] #31583 PR合并状态（skills.entries.*.env 注入）
- [ ] #40863 PR合并状态（announceTimeoutMs 增加）
- [ ] #40864 消息队列功能

---

*最后更新：2026-03-21 00:35*