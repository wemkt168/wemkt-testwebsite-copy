# 🤖 Agent Protocol (MUST READ)

> **致未来的 Agent**: 请在开始工作前阅读此准则，确保协作顺畅。

## 1. 🚀 部署铁律 (The Golden Rule of Deployment)
**所有代码更改必须同步到 GitHub。**
*   **为什么？**: 本项目依赖 Zeabur 的自动构建。只有 Push 到 GitHub，部署才会触发。
*   **怎么做？**:
    *   ✅ 完成任务后，**必须** 运行 `git push`。
    *   🛠️ **推荐方式**: 使用我为你准备好的 Workflow: `/deploy_changes`。

## 2. 🧠 记忆维持 (Memory Persistence)
不要依赖对话历史，要依赖**文件文档**。
*   Chatwoot 配置? 👉 `docs/CHECKLIST_CHATWOOT.md`
*   环境变数? 👉 `ZEABUR_ENV_VARS.md` (或询问用户)

## 3. 🛠️ 常用指令
*   **自动部署**: `git add . && git commit -m "update" && git push`
*   **查看状态**: `git status`

---
*Created by Antigravity on 2026-01-21*
