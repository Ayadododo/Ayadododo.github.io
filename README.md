# 个人主页 — 科幻化改造规划

> 目标：在现有 `index.html` 单文件架构内，将页面从「清新玻璃拟态」升级为「科幻未来感」，不新增任何文件。

---

## 🎨 视觉风格迁移

### 色彩体系
| 当前 | 改为 |
|------|------|
| `bg-slate-50` 暖白底 | `bg-[#0a0a0f]` 深空黑底 |
| `#0ea5e9` / `#22c55e` 蓝绿渐变 | `#00f0ff` 霓虹青 + `#7b61ff` 电紫 双色渐变 |
| `text-slate-800` 深灰文字 | `text-gray-100` 亮白文字，辅助用 `text-gray-400` |
| 白色半透明 glass-effect | 深色半透明 + 辉光边框 `rgba(0,240,255,0.1)` |

### 背景效果
- **替换** 模糊色块 `.blob` → **网格扫描线** + **星空粒子**（纯 CSS `radial-gradient` 叠加，无新文件）
- 添加缓慢移动的 **扫描光线**（`::after` 伪元素 + `@keyframes scanline`）
- `.grid-pattern` 从白点网格改为 `#00f0ff` 暗色荧光网格

### 字体
- 保留 Outfit + Noto Sans SC，`h1`/`h2` 追加 `tracking-wider` + `uppercase` 营造科技感
- `.gradient-text` 渐变改为 `#00f0ff → #7b61ff`

---

## 🧩 组件改造

### 导航栏
- `glass-effect` 改为 `bg-[#0a0a0f]/80 border-cyan-500/20`
- Logo 的渐变方块加 **旋转光晕**（`box-shadow` 脉冲动画）
- 「联系我」按钮加 **辉光悬停** `hover:shadow-[0_0_20px_rgba(0,240,255,0.5)]`

### Hero Section
- 移除 `.animate-float` 的 Bento 网格（浮在黑底上太轻浮）
- 替换为 **终端风格信息卡**：`border border-cyan-500/30 bg-[#0a0a0f]/60` + 左上角闪烁光标
- 欢迎标签 `.inline-flex` 改为 **状态指示灯风格**：左侧绿色脉冲点 + `border-cyan-500/20`
- 主标题字间距拉大，`letter-spacing: 0.05em`

### 卡片组件（About / Skills / Projects）
- 统一改为 **暗色终端卡**：
  ```css
  bg-[#111118] border border-cyan-500/10
  hover:border-cyan-500/40 hover:shadow-[0_0_30px_rgba(0,240,255,0.08)]
  ```
- 移除 `backdrop-blur`（深底不需要）
- `.card-hover` 悬停效果：从上浮改为 **边框辉光扩散**

### 技能条
- 背景改为 `bg-gray-800`，填充色改为 `from-cyan-400 to-purple-500`
- 尾端加 **光点拖尾**（`box-shadow` 发光）

### 项目卡片（Bento Grid）
- 保留 Bento 布局，但所有渐变背景改为 **深色 + 微弱霓虹边缘**
- emoji 图标替换为 **SVG 线框图标** 或保留但加 `filter: drop-shadow` 发光
- 「查看详情」箭头加 **水平扫描动画**

### 联系表单
- 输入框：`bg-[#111118] border-gray-700 focus:border-cyan-400 focus:shadow-[0_0_10px_rgba(0,240,255,0.2)]`
- 提交按钮：渐变改为 `from-cyan-500 to-purple-500`，加 **按钮边框扫光** 动画

---

## ✨ 动效升级

| 动效 | 实现 |
|------|------|
| 背景扫描线 | `::after` + `@keyframes scan` Y轴缓慢下移，2px 青色线 |
| 卡片边框辉光 | `hover` 时 `border-color` + `box-shadow` 渐入 |
| 文字打字机 | Hero 副标题加 `typewriter` 动画（`overflow` + `border-right` 光标） |
| 技能条光尾 | 填充条末尾 `box-shadow: 0 0 8px currentColor` |
| 鼠标跟随 | 保留当前 blob 跟随，但改为单个青色光点 `box-shadow: 0 0 60px rgba(0,240,255,0.3)` |
| 滚动渐入 | 保留 `scroll-reveal`，阈值可调 |
| Navbar 吸顶 | 滚动后加底部辉光线 `border-bottom: 1px solid rgba(0,240,255,0.2)` |

---

## 📝 内容微调

- 「1.6 年全栈/AI应用开发经验」→ 如果数据需更新顺手改
- Projects 区域的项目描述目前是占位文案，可替换为真实项目简介
- Footer 版权年份 `2024` → `2026`
- 社交图标保留 GitHub / LinkedIn，移除 Twitter（除非长官有）

---

## 🚫 不动项

- 不新增文件（CSS/JS/图片全部内联在 index.html）
- 不改 HTML 结构骨架（section / nav / footer 位置不变）
- 不改 Tailwind CDN 引用方式
- 不改移动端响应式断点

---

## 🔧 执行顺序

1. **色彩变量替换** — 全局搜索替换核心色值
2. **背景系统重写** — 删除 blob，写扫描线+星空 CSS
3. **导航栏改造** — 暗色玻璃+辉光边框
4. **Hero 区域** — 深色终端卡+打字机效果
5. **卡片组件统一** — About / Skills / Projects 全部切暗色终端风
6. **表单改造** — 暗色输入框+霓虹按钮
7. **动效注入** — 扫描线、边框辉光、技能条光尾
8. **内容微调** — 年份、文案、项目描述
9. **终检** — GitHub Pages 部署预览

> 所有改动在 `index.html` 单文件内完成，CSS 写在 `<style>` 标签，JS 写在底部 `<script>`。
