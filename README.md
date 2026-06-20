# Qwen-NoHuman — Qwen Code Dev 分支独立维护版

> 基于 [QwenLM/qwen-code](https://github.com/QwenLM/qwen-code) 的 fork 维护分支。
> 独立版本线：**Qwen-NoHuman v0.0.1**

[![License](https://img.shields.io/github/license/QwenLM/qwen-code.svg)](./LICENSE)
[![Node.js Version](https://img.shields.io/badge/node-%3E%3D22.0.0-brightgreen.svg)](https://nodejs.org/)

---

## 什么是 Qwen-NoHuman？

Qwen-NoHuman 是 Qwen Code 的 **自主维护版本**，在上游基础上增加了：

- **下班模式 (NoHuman Mode)** — 自主质量迭代、批量 bug 修复、代码审查，无需人工干预
- **热补丁系统** — 9 个已验证的 fork 热补丁（审批模式绕过、Windows 编码适配、容器路由等）
- **上游 Issue 追踪修复** — 主动监控上游 issue，逐 issue 分析根因并推送修复

## NoHuman 主要特点

| 特点                | 说明                                                  |
| ------------------- | ----------------------------------------------------- |
| **自主质量迭代**    | `/btw 下班了` 激活，自动执行 lint→test→fix 循环       |
| **批量 Issue 修复** | 从上游 issue 列表自动获取、分析根因、建分支修复、推送 |
| **Swarm 并行审查**  | 4 Agent 并行安全/性能/健壮性/可维护性审查             |
| **TDD 硬门禁**      | Red→Green→Refactor 三步法强制执行                     |
| **容器优先工作流**  | 所有代码操作通过 SSH 容器执行，隔离本地环境           |
| **自动提交**        | 修复完成后自动 commit+push，无需手动操作              |

---

## Dev 分支修补记录

### 2026-06-20

| Issue                                                    | 类型     | 说明                                                              | 分支                                  |
| -------------------------------------------------------- | -------- | ----------------------------------------------------------------- | ------------------------------------- |
| [#5199](https://github.com/QwenLM/qwen-code/issues/5199) | bug      | React error #185 — useEffect cleanup 中 setState 导致组件卸载异常 | `fix/aspnmy-agent-cli-issue-5199-...` |
| [#5142](https://github.com/QwenLM/qwen-code/issues/5142) | bug      | VP 模式初始渲染时历史不可见                                       | `fix/aspnmy-agent-cli-issue-5142-...` |
| [#5102](https://github.com/QwenLM/qwen-code/issues/5102) | security | 非交互 yolo 模式下 shell 输出重定向绕过权限合约                   | `fix/aspnmy-agent-cli-issue-5102-...` |
| [#5083](https://github.com/QwenLM/qwen-code/issues/5083) | bug      | 长会话僵尸进程导致 TUI 冻结                                       | `fix/aspnmy-agent-cli-issue-5083-...` |

### 历史修补

| Issue                                                    | 类型 | 说明                                             | 分支                                  |
| -------------------------------------------------------- | ---- | ------------------------------------------------ | ------------------------------------- |
| [#5410](https://github.com/QwenLM/qwen-code/issues/5410) | bug  | QQ Bot 无限重试 — reconnectAttempts 递增防死循环 | `fix/aspnmy-agent-cli-issue-5410-...` |
| [#5422](https://github.com/QwenLM/qwen-code/issues/5422) | bug  | 死字段 `updatedMCPToolOutput` 删除               | `fix/aspnmy-agent-cli-issue-5422-...` |
| [#5019](https://github.com/QwenLM/qwen-code/issues/5019) | bug  | (已合入 dev)                                     | `fix/aspnmy-agent-cli-issue-5019`     |
| [#4177](https://github.com/QwenLM/qwen-code/issues/4177) | bug  | (已合入 dev)                                     | `fix/aspnmy-agent-cli-issue-4177`     |

---

## 安装

### 从 Release 下载 (推荐)

```bash
# Linux x64 standalone
curl -LO https://github.com/aspnmy/qwen-code/releases/latest/download/qwen-nohuman-linux-x64.tar.gz
tar -xzf qwen-nohuman-linux-x64.tar.gz
sudo cp qwen-nohuman /usr/local/bin/
```

### 从源码构建

```bash
git clone https://github.com/aspnmy/qwen-code.git
cd qwen-code
git checkout dev
npm ci
npm run build
npm run bundle
node scripts/prepare-package.js
npm install -g ./dist
```

---

## 使用

```bash
# 进入下班模式（自主质量迭代）
qwen-code
> /btw 下班了

# 恢复正常模式
> /btw 上班了

# 批量修复上游 issue
qwen-code -p "下班模式 恢复对up仓库的issue的fix"
```

---

## 与上游的关系

- **上游**: [QwenLM/qwen-code](https://github.com/QwenLM/qwen-code) — 官方版本，npm 包名 `@qwen-code/qwen-code`
- **Fork**: [aspnmy/qwen-code](https://github.com/aspnmy/qwen-code) — dev 分支为 Qwen-NoHuman 独立版本线
- 定期从上游 main 同步，仅合入业务代码（不含 workflow/docs 差异）
- 热补丁不向上游提交（属于 fork 专属配置）

---

## License

Apache-2.0 — 与上游一致
