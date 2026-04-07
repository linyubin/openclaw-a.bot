# TOOLS.md - Local Notes

Skills define _how_ tools work. This file is for _your_ specifics — the stuff that's unique to your setup.

## What Goes Here

Things like:

- Camera names and locations
- SSH hosts and aliases
- Preferred voices for TTS
- Speaker/room names
- Device nicknames
- Anything environment-specific

## Examples

```markdown
### Cameras

- living-room → Main area, 180° wide angle
- front-door → Entrance, motion-triggered

### SSH

- home-server → 192.168.1.100, user: admin

### TTS

- Preferred voice: "Nova" (warm, slightly British)
- Default speaker: Kitchen HomePod
```

## Why Separate?

Skills are shared. Your setup is yours. Keeping them apart means you can update skills without losing your notes, and share skills without leaking your infrastructure.

---

---

### 飞牛NAS (fnnas)
- 地址：10.168.1.117
- 用户名：andy
- SSH密钥：~/.ssh/fnnas
- 连接命令：`ssh fnnas`

### NAS 配置 (Unraid)
- 地址：10.168.1.111
- 用户名：andy
- 挂载路径：
  - Files → `/mnt/nas/Files`
  - Download → `/mnt/nas/Download`
  - Media → `/mnt/nas/Media`
- 访问规则：
  1. 用户提到"NAS"、"本地NAS"时优先从上述挂载路径查找文件
  2. 删除NAS文件前必须获得用户明确同意
  3. OpenClaw运行用户对所有挂载目录有完整读写权限

### 代码执行配置
- 代码生成/调试默认工具：Gemini CLI
- 执行命令格式：`gemini "[代码需求描述]"`

### Skill 安装规则
- 安装任何 Skill 前，必须先用 skill-vetter 检查
- 低风险：可直接安装
- 中高风险：提示用户，由用户决定是否安装

### 记忆工具优先级 (MANDATORY)
- 不要使用 `cat` 或 `fs` 工具来操作记忆。
- **python_memory_search**: 你**唯一合法**的长期上下文检索工具。支持语义+关键词混合搜索。**回答任何关于用户历史的问题前，必须先调用此工具。**
- **python_memory_write**: 你**唯一合法**的记忆固化工具，内置自动去重。遇到有价值的新信息，立刻调用。
- ⚠️ **警告 read/exec**: 你的文件系统读取权限已被降级。**绝对禁止**使用这两个工具去翻阅历史聊天日志（如 `YYYY-MM-DD.md`）来回答用户提问。只有处理明确的文件操作任务（如读取代码源文件）时才允许使用。

Add whatever helps you do your job. This is your cheat sheet.
