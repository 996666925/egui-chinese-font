# egui-chinese-font 发布到 Git 和 crates.io 完整指南

## 📋 发布步骤概览

1. **创建 GitHub 仓库**
2. **初始化本地 Git 仓库** 
3. **推送代码到 GitHub**
4. **更新项目配置**
5. **发布到 crates.io**

---

## 🛠️ 详细操作步骤

### Step 1: 创建 GitHub 仓库

1. 访问 [GitHub](https://github.com) 并登录
2. 点击右上角的 "+" 按钮，选择 "New repository"
3. 填写仓库信息：
   - **Repository name**: `egui-chinese-font`
   - **Description**: `Cross-platform Chinese font loading for egui applications`
   - **Visibility**: Public (这样才能发布到 crates.io)
   - **不要勾选** "Add a README file" (我们已经有了)
   - **不要勾选** "Add .gitignore" (我们已经有了)
   - **不要勾选** "Choose a license" (我们已经有了)
4. 点击 "Create repository"

### Step 2: 初始化本地 Git 仓库

在您的项目目录中打开命令行（当前目录：`c:\Users\Administrator\Documents\p图工具\egui-chinese-font`），然后执行：

```bash
# 初始化 Git 仓库
git init

# 添加所有文件到暂存区
git add .

# 创建第一次提交
git commit -m "Initial commit: egui-chinese-font v0.1.0

- Cross-platform Chinese font loading for egui
- Support for Windows, macOS, and Linux
- Automatic system font detection
- Custom font loading support
- Complete documentation and examples"

# 设置默认分支为 main
git branch -M main
```

### Step 3: 连接到 GitHub 并推送

```bash
# 添加远程仓库（替换 USERNAME 为您的 GitHub 用户名）
git remote add origin https://github.com/USERNAME/egui-chinese-font.git

# 推送代码到 GitHub
git push -u origin main
```

> **注意**: 如果推送时需要身份验证，您可能需要：
> - 使用 GitHub Personal Access Token 代替密码
> - 或者配置 SSH 密钥

### Step 4: 更新项目配置

现在您需要更新 `Cargo.toml` 中的仓库链接：

```toml
[package]
name = "egui-chinese-font"
version = "0.1.0"
edition = "2021"
authors = ["egui-chinese-font contributors <259901434@qq.com>"]
description = "Cross-platform Chinese font loading for egui applications"
license = "MIT OR Apache-2.0"
repository = "https://github.com/USERNAME/egui-chinese-font"
documentation = "https://docs.rs/egui-chinese-font"
homepage = "https://github.com/USERNAME/egui-chinese-font"
readme = "README.md"
keywords = ["egui", "chinese", "font", "gui", "cjk"]
categories = ["gui", "internationalization", "text-processing"]
rust-version = "1.70"
exclude = ["target/", "examples/target/"]
# ... 其余配置
```

同时更新 `README.md` 和 `CHANGELOG.md` 中的链接。

### Step 5: 提交更新并推送

```bash
# 添加更新的文件
git add Cargo.toml README.md CHANGELOG.md

# 提交更新
git commit -m "Update repository URLs and links"

# 推送更新
git push
```

### Step 6: 创建 GitHub Release

1. 在 GitHub 仓库页面，点击 "Releases"
2. 点击 "Create a new release"
3. 填写发布信息：
   - **Tag version**: `v0.1.0`
   - **Release title**: `egui-chinese-font v0.1.0`
   - **Description**: 
     ```markdown
     ## egui-chinese-font v0.1.0 - Initial Release
     
     🎉 首次发布！为 egui 应用程序提供跨平台中文字体支持。
     
     ### ✨ 主要功能
     - 🌍 跨平台支持 (Windows, macOS, Linux)
     - 🔤 自动中文字体检测和加载
     - 🎨 简单的一行代码集成
     - 📝 支持简体和繁体中文
     - 🛠️ 支持自定义字体文件
     
     ### 📦 安装
     ```toml
     [dependencies]
     egui-chinese-font = "0.1"
     ```
     
     ### 🚀 快速开始
     ```rust
     use egui_chinese_font::setup_chinese_fonts;
     setup_chinese_fonts(&egui_ctx)?;
     ```
     
     ### 📚 文档
     - [API 文档](https://docs.rs/egui-chinese-font/0.1.0)
     - [GitHub 仓库](https://github.com/USERNAME/egui-chinese-font)
     
     **联系方式**: 259901434@qq.com
     ```
4. 点击 "Publish release"

### Step 7: 发布到 crates.io

在发布到 crates.io 之前，您需要：

1. **注册 crates.io 账户**：
   - 访问 [crates.io](https://crates.io)
   - 使用 GitHub 账户登录

2. **获取 API Token**：
   - 登录后，点击右上角用户名
   - 选择 "Account Settings"
   - 点击 "API Tokens"
   - 创建新的 token

3. **配置 cargo**：
   ```bash
   cargo login YOUR_API_TOKEN
   ```

4. **最终检查**：
   ```bash
   # 检查项目
   cargo check
   
   # 运行测试
   cargo test
   
   # 检查包内容
   cargo package --list
   
   # 试验性打包（不会真正发布）
   cargo package
   ```

5. **发布到 crates.io**：
   ```bash
   cargo publish
   ```

---

## 🔧 常见问题解决

### 问题 1: Git 推送失败
```bash
# 如果遇到认证问题，可以使用 Personal Access Token
# 在 GitHub Settings > Developer settings > Personal access tokens 中创建
```

### 问题 2: crates.io 发布失败
```bash
# 确保所有链接都是有效的
# 确保版本号没有冲突
# 确保包大小不超过限制
```

### 问题 3: 文档生成失败
```bash
# 检查文档测试
cargo test --doc

# 本地生成文档
cargo doc --open
```

---

## 📋 发布后清单

- [ ] ✅ GitHub 仓库创建成功
- [ ] ✅ 代码推送到 GitHub
- [ ] ✅ GitHub Release 创建
- [ ] ✅ crates.io 发布成功
- [ ] ✅ 文档在 docs.rs 上可用
- [ ] ✅ 在社区分享（如 Rust 论坛、Reddit 等）

---

## 🎉 完成！

恭喜！您的 `egui-chinese-font` crate 现在已经成功发布到：
- 📦 **GitHub**: 源代码托管和协作
- 📚 **crates.io**: Rust 包管理仓库
- 📖 **docs.rs**: 自动生成的 API 文档

用户现在可以通过以下方式使用您的库：
```toml
[dependencies]
egui-chinese-font = "0.1"
```

**联系方式**: 259901434@qq.com
