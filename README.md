# ⭐ Star 星星走起 动动发财手点点⭐Star


![设备验证](./3.png)


## ⚠️ 注意
- 支持 Mobile验证 和 2FA验证
- 首次运行：需要设备验证，收到 TG 通知后 30 秒内批准
- REPO_TOKEN：需要有 Secrets 写入权限才能自动更新
- Cookie 有效期：每次运行都会更新，保持最新
### Mobile验证
![设备验证](./1.png)
### 2FA验证
![设备验证](./4.png)

### 验证设置
![设置Mobile优先验证](./2.png)

---

## Secrets 配置
| Secret 名称 | 说明 |
| --- | --- |
| `GH_USERNAME` | GitHub 用户名 |
| `GH_PASSWORD` | GitHub 密码 |
| `GH_SESSION` | Cookie 不用添加自动生成 |
| `TG_BOT_TOKEN` | Telegram Bot Token |
| `TG_CHAT_ID` | Telegram Chat ID |
| `REPO_TOKEN` | GitHub Token（用于自动更新 Secret） |

---

## 快速开始

### 1. Fork 仓库

点击右上角 **Fork** 按钮

### 2. 配置 Secrets

进入 **Settings** → **Secrets and variables** → **Actions**，添加：

**必需：**
- `GH_USERNAME`: GitHub 用户名
- `GH_PASSWORD`: GitHub 密码

**推荐：**
- `TG_BOT_TOKEN`: Telegram Bot Token
- `TG_CHAT_ID`: Telegram Chat ID
- `REPO_TOKEN`: GitHub Personal Access Token (自动更新 Cookie)

### 3. 启用 Actions

进入 **Actions** → 点击 **I understand my workflows**

### 4. 手动测试

选择 **Auto Login** workflow → **Run workflow**

---
## 流程图
```
开始
  ↓
加载已保存的 Cookie（如果有）
  ↓
访问 ClawCloud
  ↓
已登录？ ─是→ 保活 → 提取新 Cookie → 保存 → 完成
  ↓否
点击 GitHub 登录
  ↓
Cookie 有效？ ─是→ 直接 OAuth 授权
  ↓否
输入用户名密码
  ↓
需要设备验证？ ─是→ 发送 TG 通知 → 等待 30 秒
  ↓
登录成功
  ↓
OAuth 授权
  ↓
重定向到 ClawCloud
  ↓
保活（访问控制台、应用页面）
  ↓
提取新的 Session Cookie
  ↓
自动更新 GH_SESSION Secret
  ↓
发送 Telegram 通知
  ↓
完成 ✅

```
