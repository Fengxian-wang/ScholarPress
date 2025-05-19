```markdown
# 🚀 Hexo + Netlify CMS + Vercel 极速部署指南

[![Vercel Deploy](https://img.shields.io/badge/Deployed_on-Vercel-black?logo=vercel&style=flat-square)](https://vercel.com) 
[![GitHub Release](https://img.shields.io/github/last-commit/Fengxian-wang/hexo-netlify-cms-vercel?color=blue&label=Last%20Update&style=flat-square)](https://github.com/Fengxian-wang/hexo-netlify-cms-vercel)

<div align="center">
  <img src="https://via.placeholder.com/800x200.png?text=Deployment+Workflow+Diagram" alt="部署流程图" width="80%">
</div>

---

## 🔧 部署步骤

### 第一步：Fork项目模板
[![Use Template](https://img.shields.io/badge/-Fork%20Now!-blue?logo=github&style=for-the-badge)](https://github.com/Fengxian-wang/hexo-netlify-cms-vercel/generate)
```plaintext
创建时可以设为私有仓库（建议公开以方便后续维护）
```

### 第二步：部署到 Vercel
[![Deploy with Vercel](https://img.shields.io/badge/-Deploy%20Now-black?logo=vercel&style=for-the-badge)](https://vercel.com/new/clone)
```bash
点击部署，等待完成（约2-5分钟）
获得临时访问地址 "https://your-vercel-domain.vercel.app"
```

### 第三步：域名配置（可选）
```markdown
1. 部署完成后，在Vercel控制台：
   • 前往项目设置 > Domains
   • 可绑定自定义域名（需验证DNS）
   • SSL证书会自动生成
```

---

## ⚙ 核心配置

### 第四步：配置 Netlify-CMS
```yaml
修改 /source/admin/config.yml
backend:
  repo: your-github-username/your-repo-name  # 替换为你的仓库路径
  base_url: https://your-vercel-domain.vercel.app  # 临时访问地址
```

### 第五步：创建 GitHub OAuth 应用
```markdown
1. 访问 https://github.com/settings/developers
2. 点击 "New OAuth App"
3. 填写：
   • Application name: 任意名称（如 MyBlogCMS）
   • Homepage URL: https://your-vercel-domain.vercel.app
   • Authorization callback URL: https://your-vercel-domain.vercel.app/callback
```

---

## 🔑 授权设置

### 第六步：获取客户端凭证
```diff
• Client ID: xxxxxxxx

• Client Secret: gho_xxxxxxxxxxxxxxxxx

```

### 第七步：更新Vercel变量
```env
OAUTH_GITHUB_CLIENT_ID = your_client_id
OAUTH_GITHUB_CLIENT_SECRET = your_client_secret
```
```bash
重新部署，等待完成（约2-5分钟）
```

---

## 🧪 功能验证
```markdown
第八步：测试 CMS 系统
1. 访问 `https://your-domain/admin/`
2. 使用GitHub账号登录
3. 测试功能：
   • 创建新文章
   • 修改配置
   • 查看提交记录是否同步到GitHub仓库
```

---

## 🌈 高级功能
<details>
<summary><b>Netlify 预览功能</b></summary>

```markdown
1. 登录 https://app.netlify.com
2. 新建站点并关联同一个GitHub仓库
3. 无需额外配置，保持默认即可
4. 在Netlify-CMS编辑时即可使用预览功能
```
</details>

---

## 🚨 常见问题
| 问题现象 | 解决方案 |
|---------|----------|
| 403错误 | 检查OAuth回调URL的HTTPS协议 |
| 内容不同步 | 验证config.yml的仓库路径 |
| 样式丢失 | 清除浏览器缓存 |
| 预览失败 | 检查Netlify构建状态 |

---

## 🔄 后续维护
```markdown
1. 所有变更通过Git提交保存
2. 直接编辑/source/_posts内容文件
3. 通过Git同步原仓库主题更新
```

> 💡 建议首次部署后创建测试文章验证流程，遇到授权问题可重新生成Client Secret
```
