# MD2WeChat 部署指南

## 部署到 Vercel（免费）

### 准备工作

只需要一个 **GitHub 账号**（用于存储代码）

### 部署步骤

#### 1. 创建 GitHub 仓库

1. 打开 [GitHub](https://github.com)
2. 点击右上角 **+** → **New repository**
3. 仓库名称填写 `md2wechat`
4. 选择 **Private**（私有）
5. 点击 **Create repository**

#### 2. 上传代码到 GitHub

**方式 A：使用 GitHub 网页**
1. 在新建的仓库页面，点击 **uploading an existing file**
2. 将 `C:\Users\goorock\projects\MD2WeChat` 文件夹下的所有文件拖拽上传
3. 点击 **Commit changes**

**方式 B：使用 Git 命令**
```bash
cd C:\Users\goorock\projects\MD2WeChat
git init
git add .
git commit -m "Initial commit"
git branch -M main
git remote add origin https://github.com/你的用户名/md2wechat.git
git push -u origin main
```

#### 3. 连接 Vercel

1. 访问 [vercel.com](https://vercel.com)
2. 点击 **Sign Up** 注册账号（可用 GitHub 登录）
3. 登录后点击 **Add New...** → **Project**
4. 在 **Import Git Repository** 中找到你的 `md2wechat` 仓库
5. 点击 **Import**

#### 4. 部署

1. 直接点击 **Deploy**（无需配置环境变量）
2. 等待部署完成（通常 1-2 分钟）
3. 部署成功后，你会获得一个 `.vercel.app` 的域名

### 后续更新

当你修改代码后，只需：
```bash
git add .
git commit -m "更新内容"
git push
```
Vercel 会自动重新部署。

---

## 图片图床（路过图床）

本项目使用 **路过图床** (imgurl.org) 作为默认图床：

- ✅ 无需注册即可使用
- ✅ 国内访问速度快
- ✅ 单张图片最大 10MB
- ✅ 完全免费

### 图片上传限制

- 单张图片大小：≤ 10MB（微信公众号限制）
- 格式支持：JPG, PNG, GIF, WebP 等

---

## 项目文件说明

```
md2wechat/
├── index.html          # 主页面（完整的单页应用）
├── vercel.json         # Vercel 部署配置
├── api/
│   └── upload.js      # 图片上传 API（路过图床）
├── DEPLOY.md           # 本部署指南
└── .claude/
    └── launch.json    # 本地开发配置
```

---

## 本地开发

如果你想在本地运行：

```bash
cd C:\Users\goorock\projects\MD2WeChat

# 使用 npx serve 启动本地服务器
npx serve -l 3000
```

然后访问 http://localhost:3000

---

## 常见问题

### Q: 图片上传失败？

路过图床可能有临时维护的情况。可以：
1. 稍后再试
2. 使用外部图片链接（直接粘贴 URL）

### Q: 如何自定义域名？

1. Vercel 项目 → **Settings** → **Domains**
2. 输入你的域名
3. 按照提示配置 DNS

### Q: 如何查看部署日志？

Vercel 项目 → **Deployments** → 点击最新部署 → **Logs**

---

## 功能概览

| 功能 | 说明 |
|-----|------|
| Markdown 编辑器 | 左侧实时编辑 |
| 实时预览 | 右侧即时渲染 |
| 代码高亮 | 支持 100+ 编程语言 |
| 图片幻灯片 | 使用 `:::gallery` 语法 |
| 5 种预设模板 | 简约白/杂志黑/商务蓝/复古/编辑风 |
| 自定义 CSS | 上传或粘贴 CSS 代码 |
| 可视化编辑 | 调整颜色/字体/行高 |
| 图床上传 | 路过图床直传 |
| 一键导出 | 复制微信兼容 HTML |