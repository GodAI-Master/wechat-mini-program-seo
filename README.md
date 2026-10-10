# 微信小程序 SEO 页面设计与 Codex 技能

把微信小程序的长尾搜索页面从“想到一个词就加一页”，整理成一套可复用的设计、实现和验收方法。仓库同时提供 Codex 技能，让后续小程序开发任务能自动参考这套方法。

## 这套方法解决什么

- 按用户的搜索意图组织页面，减少重复、空洞的关键词页。
- 为公开内容提供稳定链接，让页面在没有首页状态、登录状态或上一个页面的情况下也能打开。
- 用清晰标题、真实正文、页面间链接和 sitemap 共同描述可搜索内容。
- 公开内容先展示；收藏、同步等需要身份的操作再要求登录。
- 将“技术上允许被抓取”与“微信实际收录、展示或排名”区分开。任何实现都不能保证官方收录或排名。

## 仓库内容

- [Codex 技能](skills/wechat-miniprogram-seo/SKILL.md)：小程序开发时使用的精简工作指引。
- [完整设计与实现规范](skills/wechat-miniprogram-seo/references/seo-page-standard.md)：页面模型、搜索意图、URL、内容、内链、sitemap、发布和验收方法。

## 安装给 Codex

Windows PowerShell：

```powershell
git clone https://github.com/GodAI-Master/wechat-mini-program-seo.git
Set-Location .\wechat-mini-program-seo
$skillPath = Join-Path $env:USERPROFILE ".codex\skills\wechat-miniprogram-seo"
New-Item -ItemType Directory -Path $skillPath -Force | Out-Null
Copy-Item .\skills\wechat-miniprogram-seo\* $skillPath -Recurse -Force
```

这会把技能装到当前 Windows 用户的 Codex 技能目录，供不同小程序项目复用。若本机设置了自定义 `CODEX_HOME`，请把目标目录改为该目录下的 `skills\wechat-miniprogram-seo`。安装后重新打开 Codex；也可以在任务中明确写 `$wechat-miniprogram-seo`。

只想在单个项目内使用时，把 `skills/wechat-miniprogram-seo` 复制到项目的 `.agents/skills/wechat-miniprogram-seo` 目录。

## 使用示例

新建小程序时：

> 使用 `$wechat-miniprogram-seo`。先检查项目类型、页面结构和公开内容，规划哪些用户需求值得形成独立的搜索落地页，再实现需要的页面。搜索词按意图聚类，不编造营业、价格或地点信息；说明哪些页面具备被收录的技术条件，以及还需要在微信公众平台完成什么设置。

修改已有小程序时：

> 使用 `$wechat-miniprogram-seo`，先检查当前 sitemap、公开页面、直达链接和内容来源，再按本项目现有结构改进搜索落地页。保留业务功能，验证冷启动、未登录访问、标题、内链和 sitemap，并明确哪些结论还需要开发者工具、微信公众平台或真机确认。

这项技能会在新小程序开发任务中提醒 Codex 检查 SEO 机会；普通功能与搜索无关时，不会要求为了 SEO 强行新增页面。

## 使用边界

页面具备稳定 URL、公开内容、正确标题、内链和 sitemap 配置，只表示它达到了“可索引候选页”的技术条件。微信是否抓取、收录、展示以及排序，由平台决定；小程序后台的页面收录设置、内容质量、审核状态和真实用户体验也会影响结果。发布前请查阅下方官方文档的现行要求。

## 官方参考

- [微信小程序搜索优化指南](https://developers.weixin.qq.com/miniprogram/dev/framework/search/seo.html)
- [微信小程序 sitemap 配置](https://developers.weixin.qq.com/miniprogram/dev/reference/configuration/sitemap.html)
- [微信小程序 navigator 组件](https://developers.weixin.qq.com/miniprogram/dev/component/navigator.html)
- [微信官方小程序示例中的 sitemap.json](https://github.com/wechat-miniprogram/miniprogram-demo/blob/master/sitemap.json)
