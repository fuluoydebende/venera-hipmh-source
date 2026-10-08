# Venera 漫画源 · 嬉皮漫畫 (hipmh) v1.0.2

适用于 [Venera / VeneraX](https://github.com/venera-app) 漫画阅读器的 `hipmh`（m.hipmh.com）漫画源。

## 导入方式（在 Venera App 内）
主页 → **漫画源** → 添加漫画源 → 选 **使用配置文件** → 粘贴下方地址 → 确认：

```
https://ghproxy.net/https://raw.githubusercontent.com/fuluoydebende/venera-hipmh-source/main/index.json
```

> 如果你的网络能直连 GitHub，也可以直接用：
> `https://raw.githubusercontent.com/fuluoydebende/venera-hipmh-source/main/index.json`

key 为 `hipmh`，会覆盖社区大源里那份已失效（站点改前端渲染后列表空白）的旧版本。

## 本版本修复了什么
- 站点近期把首页 / 详情页改为前端渲染，旧源靠抓 SSR HTML 取卡片导致**列表空白**。
- v1.0.2 改为全部走接口：
  - 首页 `explore` → `/v1/mangas?sort=latest|updated|popular`
  - 详情 `loadInfo` → `/manga/{slug}` 路由 + 章节接口取数字 mid
  - 章节 / 图片 → 数字 mid 反推 + `toApiHid` 转换，图片解码器沿用原实现
- 已用真实接口数据通过 Node 模拟测试（首页出卡 / 反推 mid / 50 章节 / 解码真实图片 URL 均正常）。

## 文件
- `hipmh.js` — 源本体（Venera `ComicSource` 实现）
- `index.json` — 导入配置文件

## ⚠️ 须知
`m.hipmh.com` 为第三方漫画聚合站，含国漫 / 日漫 / 韩漫及成人分区。请自行确认所在地区合规与内容过滤。
