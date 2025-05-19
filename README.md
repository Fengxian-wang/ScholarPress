# 🚀 Hexo + Netlify CMS + Vercel 极速部署指南

第一步：Fork项目模板

[![GitHub Template](https://img.shields.io/badge/Template-Ready%20to%20Use-blueviolet?logo=github&style=for-the-badge)](https://github.com/Fengxian-wang/hexo-netlify-cms-vercel/generate)
创建时可以设为私有仓库（建议公开以方便后续维护）

第二步：部署到 Vercel
[![Deploy with Vercel](https://img.shields.io/badge/deploy%20with-vercel-%23000000.svg?style=for-the-badge&logo=vercel)](https://vercel.com/new/clone)

点击部署，等待完成（约2-5分钟）
获得临时访问地址“https://your-vercel-domain.vercel.app”

第三步：域名配置（可选）
1. 部署完成后，在Vercel控制台：
   • 前往项目设置 > Domains

   • 可绑定自定义域名（需验证DNS）

   • SSL证书会自动生成

第四步：配置 Netlify-CMS
1. 在仓库中找到文件: `/source/admin/config.yml`
2. 修改以下字段：
   ```yaml
   backend:
     repo: your-github-username/your-repo-name  # 替换为你的仓库路径
     base_url: https://your-vercel-domain.vercel.app  # 临时访问地址
   ```

第五步：创建 GitHub OAuth 应用
1. 访问 https://github.com/settings/developers
2. 点击 "New OAuth App"
3. 填写：
   • Application name: 任意名称（如 MyBlogCMS）

   • Homepage URL: https://your-vercel-domain.vercel.app  # 临时访问地址

   • Authorization callback URL: https://your-vercel-domain.vercel.app/callback

   (暂时用临时域名，部署后可以修改)

第六步：获取客户端凭证
1. 创建完OAuth应用后，记录：
   • Client ID

   • 点击 "Generate a new client secret" 获取密钥


第七步：更新Vercel变量
 在环境变量设置中添加：
   • `OAUTH_GITHUB_CLIENT_ID` ➔ 你的Client ID

   • `OAUTH_GITHUB_CLIENT_SECRET` ➔ 你的Client Secret

重新部署，等待完成（约2-5分钟）

第八步：测试 CMS 系统
1. 访问 `https://your-domain/admin/`  # 临时访问地址/admin/ 或者 绑定的自定义域名/admin/
2. 使用GitHub账号登录
3. 测试功能：
   • 创建新文章

   • 修改配置

   • 查看提交记录是否同步到GitHub仓库


高级配置（预览功能）
1. 登录 https://app.netlify.com
2. 新建站点并关联同一个GitHub仓库
3. 无需额外配置，保持默认即可
4. 在Netlify-CMS编辑时即可使用预览功能

常见问题排查
1. 403错误：检查OAuth应用的回调URL是否包含HTTPS协议
2. 内容不同步：确保仓库名称在config.yml正确
3. 样式丢失：等待Vercel完成部署后强制刷新浏览器缓存
4. 预览失败：确认Netlify站点是否正常构建

后续维护
1. 所有内容变更都会通过Git提交记录保存
2. 可通过GitHub网页直接修改内容文件（位于/source/_posts）
3. 主题更新建议通过Git同步原仓库的更新

建议首次部署后先创建测试文章，验证整个工作流程是否正常。如果遇到授权问题，可重新生成Client Secret并更新Vercel的环境变量。
