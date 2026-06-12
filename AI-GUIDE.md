# AI 开发指南 — 李昊冉个人网站

## 项目身份

- **所有者**：李昊冉，22岁女生，河南人，海口。海南大学生态学本科在读。
- **用途**：应聘章鱼陶陶艺术馆手工兼职店员的个人展示页。
- **在线地址**：https://synowiecsixsl5063-spec.github.io/resume/
- **GitHub 仓库**：https://github.com/synowiecsixsl5063-spec/resume
- **GitHub 账号**：synowiecsixsl5063-spec

## 技术架构

```
resume-project/
├── index.html    ← 唯一入口，单文件，CSS/JS 全部内联
├── images/       ← 所有图片资源
│   ├── avatar.png           ← 用户头像
│   ├── 微信图片_...276...jpg ← 手工作品1
│   ├── 微信图片_...277...jpg ← 手工作品2
│   ├── zueimon-hero.png     ← 肥嘟嘟左卫门 武士款
│   ├── zueimon-jump.png     ← 肥嘟嘟左卫门 飞跃款
│   ├── zueimon-peek.png     ← 肥嘟嘟左卫门 探头款
│   └── zueimon-sketch.png   ← 肥嘟嘟左卫门 线稿款
├── AI-GUIDE.md  ← 本文件
├── README.md
└── resume.md
```

- **部署方式**：GitHub Pages，main 分支根目录
- **技术栈**：纯 HTML + 内联 CSS + 原生 JS，零依赖构建工具
- **外部 CDN**：仅 Font Awesome 6.5.1（jsdelivr，国内可访问）

## 如何本地编辑与预览

用户使用 Cursor（或 VS Code）编辑器。

1. 打开文件夹：`C:\Users\20672\Downloads\resume-project`
2. 安装 Live Server 插件
3. 右键 `index.html` → "Open with Live Server"
4. 浏览器打开 `http://127.0.0.1:5500`，改代码 Ctrl+S 保存后自动刷新

**本地预览不需要登录任何账号。**

## 如何部署到线上

### 方式A：由 Claude Code 部署（推荐，用户无需操作）

用户把修改后的代码发给 Claude Code，Claude Code 执行：
```bash
cd "C:\Users\20672\Downloads\resume-project"
git add . && git commit -m "更新描述" && git push
```
等约 20 秒，GitHub Pages 自动更新。

### 方式B：用户自行部署

用户的 Git 已配置好（用户名 synowiecsixsl5063-spec，remote 指向 GitHub）。
用户只需在终端运行上面三条命令即可。如果提示输入密码，需要 GitHub Personal Access Token。

### 如何验证部署成功
等 20 秒后访问 https://synowiecsixsl5063-spec.github.io/resume/ ，Ctrl+Shift+R 强制刷新。

## 设计系统

### 配色
```css
--bg: #FDFBF7 → #FFF5FA（粉色渐变背景）
--text-main: #3D2C35（深褐）
--text-muted: #7A6068（浅褐）
--accent: #E892A8（粉色强调）
```

### 布局
- 最大宽度 1280px，桌面端多列展开
- Hero 双栏（左侧头像+姓名+标签，右侧肥嘟嘟展示）
- 经历三列、手作三列、联系三列
- 手机端 ≤960px 全部收为单列

### 动效
- 飘落花瓣（28 个 emoji 花瓣，CSS @keyframes）
- 滚动淡入（IntersectionObserver）
- 肥嘟嘟边缘装饰（漂浮、摇摆、探头）

## 设计偏好与历史教训

### ✅ 用户喜欢的
- 通透粉色系（不要闷粉）
- 花瓣装饰、花朵元素
- 玻璃拟态（backdrop-filter blur）
- 桌面端利用全屏宽度
- 肥嘟嘟左卫门作为边缘装饰（不要卡片区）

### ❌ 用户不喜欢的
- 搓衣板式窄单列布局
- AI 味的翻译腔文字
- 肥嘟嘟左卫门的 SVG 自绘或 emoji 代替（必须用真实图片）
- 肥嘟嘟左卫门的文字卡片区（已删除）
- 白色圆角卡片堆叠

### ❌ 不要做的事
- 不要引入被中国屏蔽的 CDN（Google Fonts、CDNJS 部分资源等）
- 不要用需要登录/API Key 的第三方服务
- 不要拆分 index.html 成多文件（除非明确要求）
- 不要删除肥嘟嘟左卫门的四张边缘装饰图
- 不要把头像放回右侧

## 肥嘟嘟左卫门说明

肥嘟嘟左卫门是蜡笔小新中的角色——一只胖橘猫，春日部防卫队成员。页面中有 4 张已抠好背景的透明 PNG：
- `zueimon-hero.png`：武士拔刀款，放在 hero 右侧展示区
- `zueimon-jump.png`：飞跃款，桌面端右侧固定漂浮
- `zueimon-peek.png`：探头款，hero 右下角探头
- `zueimon-sketch.png`：线稿款，桌面端左侧固定摇摆

所有图片已完成 AI 去背景处理（rembg/U2-Net），无需再次抠图。

## 与用户协作的规则

1. 用户可能通过其他 AI（ChatGPT、Gemini 等）生成前端代码，然后交给 Claude Code 部署
2. 给其他 AI 的提示词：不要限制创意，只提供事实和技术边界
3. 用户没有视觉能力判断图片内容——需要视觉判断时，让用户把图片发给能看图的 AI
4. 所有产出文件放 `C:\Users\20672\Downloads`
5. 用户偏好先搜后写，能用现成方案不重复造轮子
