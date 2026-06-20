# GitHub Pages 外网 Demo 发布教程

本文从零开始说明如何把本项目发布成一个外网可访问的 Demo 页面。

## 1. 准备 GitHub 账号

1. 打开 https://github.com/
2. 点击右上角 `Sign up`。
3. 输入邮箱、密码、用户名。
4. 按 GitHub 邮件提示完成邮箱验证。
5. 登录后，进入 GitHub 首页。

建议用户名使用英文和数字，例如：

```text
yourname-stageai
```

最终外网 Demo 地址会包含你的用户名。

## 2. 创建远程仓库

1. 登录 GitHub 后，点击右上角 `+`。
2. 选择 `New repository`。
3. Repository name 填写：

```text
StageRehearsal
```

4. Visibility 建议选择 `Public`。GitHub Pages 免费公开访问最简单。
5. 不要勾选 `Add a README file`，因为本地项目已经有 README。
6. 点击 `Create repository`。

## 3. 上传当前项目

在本项目根目录打开 PowerShell：

```powershell
cd H:\Ugit\StageRehearsal
```

如果还没有绑定 GitHub 远程仓库：

```powershell
git remote add origin https://github.com/EndToFx/StageRehearsal.git
git branch -M main
git add .
git commit -m "Prepare public demo"
git push -u origin main
```

把 `EndToFx` 替换成你的 GitHub 用户名。

如果已经绑定过远程仓库，只需要：

```powershell
git add .
git commit -m "Update demo"
git push
```

## 4. 开启 GitHub Pages

1. 打开你的仓库页面。
2. 点击顶部 `Settings`。
3. 左侧找到 `Pages`。
4. 在 `Build and deployment` 中：
   - Source 选择 `Deploy from a branch`
   - Branch 选择 `main`
   - Folder 选择 `/ (root)`
5. 点击 `Save`。

等待 1 到 3 分钟，GitHub 会生成外网地址。

## 5. 访问 Demo

你的项目主页地址通常是：

```text
https://endtofx.github.io/StageRehearsal/
```

交互 Demo 地址是：

```text
https://endtofx.github.io/StageRehearsal/demo/
```

## 6. 常见问题

如果页面打开但模型或字体没有加载，确认仓库根目录保留了：

```text
.nojekyll
```

如果页面 404，确认 Pages 的 Branch 是 `main`，Folder 是 `/ (root)`。

如果 Unreal 实时联动不可用，这是正常的：GitHub Pages 只能托管网页，不能直接访问你的本地 Unreal Editor。实时联动仍需要在本机运行 Python bridge。
