# 推送说明

## 当前状态
✅ 所有文件已创建并提交到本地仓库
✅ 仓库位置：`/Users/wangjunpeng/Desktop/junpengwang.github.io`

## 文件清单
- `index.html` - 个人主页（深色主题，移动端自适应）
- `assets/style.css` - 样式文件
- `.gitignore` - Git 忽略文件配置
- `README.md` - 原有的 README 文件

## 推送到 GitHub

由于当前 SSH 密钥关联的是 `czwjp2004` 账户，而不是 `junpengwang` 账户，你需要手动推送。有以下几种方法：

### 方法 1: 使用个人访问令牌 (推荐)

1. 在 GitHub 上创建个人访问令牌：
   - 访问 https://github.com/settings/tokens
   - 点击 "Generate new token" → "Generate new token (classic)"
   - 勾选 `repo` 权限
   - 生成并复制 token

2. 推送代码：
```bash
cd /Users/wangjunpeng/Desktop/junpengwang.github.io
git push https://YOUR_TOKEN@github.com/junpengwang/junpengwang.github.io.git main
```

### 方法 2: 配置 junpengwang 账户的 SSH 密钥

1. 为 junpengwang 账户生成新的 SSH 密钥：
```bash
ssh-keygen -t ed25519 -C "jw901@duke.edu" -f ~/.ssh/id_ed25519_junpengwang
```

2. 将公钥添加到 GitHub：
```bash
cat ~/.ssh/id_ed25519_junpengwang.pub
# 复制输出，添加到 https://github.com/settings/keys
```

3. 配置 SSH config：
```bash
cat >> ~/.ssh/config << 'EOF'

Host github.com-junpengwang
    HostName github.com
    User git
    IdentityFile ~/.ssh/id_ed25519_junpengwang
EOF
```

4. 修改远程 URL 并推送：
```bash
cd /Users/wangjunpeng/Desktop/junpengwang.github.io
git remote set-url origin git@github.com-junpengwang:junpengwang/junpengwang.github.io.git
git push origin main
```

### 方法 3: 使用 GitHub CLI (如果已安装)

```bash
cd /Users/wangjunpeng/Desktop/junpengwang.github.io
gh auth login  # 使用 junpengwang 账户登录
git push origin main
```

## 验证部署

推送成功后，等待 1-2 分钟，访问：
https://junpengwang.github.io

## 后续修改

记得更新 `index.html` 中的占位符链接：
- GitHub: 当前是 `https://github.com/junpengwang`
- LinkedIn: 当前是 `https://linkedin.com/in/junpengwang`

根据你的实际账户名修改这些链接。

