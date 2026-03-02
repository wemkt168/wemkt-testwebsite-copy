# Chatwoot 集成指南 (Best Practices)

> **最后更新**: 2026-01-21
> **状态**: ⭐️ 黄金标准 (Golden Standard)

本文档记录了 `wemkt-testwebsite` 项目中集成 Chatwoot 的标准做法。未来任何修改都应遵循此规范。

## 1. 核心配置 (Configuration)

| 项目 | 值 | 说明 |
|------|-----|------|
| **Website Token** | `jBA7mJRqkZ13jUYAPSSgrrD4` | 请勿随意从后端环境变量覆盖此值，这是前端专用 Token |
| **Base URL** | `https://chatwoot-wemkt.zeabur.app` | 必须包含 `https://` 协议头 |

## 2. 标准代码片段 (Standard Code Snippet)

这是经过验证的、包含**智能语言判断**功能的标准代码。

**功能亮点**:
- ✅ `hideMessageBubble: false`: 确保气泡显示
- ✅ `position: 'right'`: 固定在右下角
- ✅ `locale: navigator.language || 'en'`: **关键逻辑**，自动读取用户浏览器语言，默认回退到英语。
- ✅ `defer` & `async`: 确保脚本异步加载，不阻塞页面渲染。

### `index.html` 插入位置

放在 `<body>` 标签结束前：

```html
    <script>
      window.chatwootSettings = {
        hideMessageBubble: false,
        position: 'right', // 聊天框在右下角
        locale: navigator.language || 'en', // ✨ 关键修改：自动跟随浏览器语言，否则默认英语
        type: 'standard'
      };

      (function(d,t) {
        var BASE_URL = "https://chatwoot-wemkt.zeabur.app";
        var g=d.createElement(t),s=d.getElementsByTagName(t)[0];
        g.src=BASE_URL+"/packs/js/sdk.js";
        g.defer = true;
        g.async = true;
        s.parentNode.insertBefore(g,s);
        g.onload=function(){
          window.chatwootSDK.run({
            websiteToken: 'jBA7mJRqkZ13jUYAPSSgrrD4', // ⚠️ 务必确认 Token 正确
            baseUrl: BASE_URL
          })
        }
      })(document,"script");
    </script>
```

## 3. 常见问题 (Troubleshooting)

- **Widget 不显示**:
  - 检查 Token 是否与 Chatwoot 后台 Inbox 设置一致。
  - 检查 Base URL 是否可访问（使用 `curl -I` 测试）。
  - 检查浏览器 Console 是否有 CORS 错误。

- **语言不切换**:
  - 确保没有硬编码 `locale: 'en'`。
  - 确保使用了 `navigator.language` 逻辑。
