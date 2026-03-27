# 邮件发送配置

> 更新时间: 2026-03-20

---

## send-email 技能配置

| 配置项 | 值 |
|:---|:---|
| SMTP服务器 | smtp.163.com |
| SMTP端口 | 465 |
| 发件人 | wgyx2000@163.com |
| 授权码 | YAuDEcXVPDGkGNkR |

---

## 使用方式

```bash
# 设置环境变量
export EMAIL_SMTP_SERVER="smtp.163.com"
export EMAIL_SMTP_PORT="465"
export EMAIL_SENDER="wgyx2000@163.com"
export EMAIL_SMTP_PASSWORD="YAuDEcXVPDGkGNkR"

# 发送邮件
python3 ~/.openclaw/skills/send-email/send_email.py "收件人邮箱" "主题" "内容文件路径"
```

---

## 注意事项

1. 授权码不是邮箱登录密码
2. 163邮箱需要在设置中开启 SMTP 服务
3. 技能位置: `~/.openclaw/skills/send-email/`

---

## 配置状态

- ✅ 已配置到 `~/.openclaw/openclaw.json`
- ✅ 已写入公共记忆
