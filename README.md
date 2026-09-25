# 托管这两个页面（GitHub Pages，约 10 分钟）

ASC 提审时**必须**填一个「隐私政策 URL」，Apple 会去访问它，**打不开就卡在提审前**。
这个 URL 还必须是 **https**，纯 http 不接受。

你没有域名，所以走 GitHub Pages 的免费子域名：

```
https://<你的用户名>.github.io/swipeshine/privacy.html
https://<你的用户名>.github.io/swipeshine/support.html
```

> **为什么不用别的免费方案**：Google Sites / Notion 公开页也能出 https 链接，但
> Notion 的公开页 URL 里带一长串随机 id，看着不像一家能收信的实体；而且随时可能改规则。
> GitHub Pages 无限期、URL 干净、还能顺手当官网。这是最省事且不会返工的一条。

---

## 一次性设置（约 10 分钟）

### 1. 建仓库

需要 GitHub 账号。没有就先注册（免费）。

建一个 **public** 仓库，名字就叫 `swipeshine`。

> **必须 public。** 私有仓库的 GitHub Pages 需要付费计划，而且即使能用，
> Apple 的审核爬虫也访问不到。

### 2. 上传文件

把本目录里的**四个**文件传到仓库根目录：

```
swipeshine/
├── index.html       ← 落地页（也是 ASC 的「营销 URL」）
├── privacy.html     ← 隐私政策（ASC 必填）
├── support.html     ← 支持页（ASC 必填）
└── icon.png         ← index.html 顶部那个 App 图标
```

浏览器里直接拖拽上传即可，不用装 git。

> **文件名别改。** 页面之间互相链接用的就是这些名字，而 `icon.png` 的路径
> 写在 `index.html` 里——改名会让图标裂成一个小方块。

> `icon.png` 是 512×512（85 KB），从 `AppIcon1024.png` 缩来的。
> 别直接把 1024 的原图传上去，465 KB 在网页上显示 96px 是浪费。
> 重新生成：`sips -z 512 512 <AppIcon1024.png> --out icon.png`

### 3. 打开 Pages

仓库 → **Settings** → 左侧 **Pages** → Source 选 **Deploy from a branch** →
Branch 选 **main** / 目录选 **/ (root)** → **Save**。

等 1–2 分钟（第一次要构建）。刷新这个页面，顶部会出现绿色的一行：

```
Your site is live at https://<你的用户名>.github.io/swipeshine/
```

### 4. 验证

浏览器里打开这两个地址，**确认能打开**：

- `https://<你的用户名>.github.io/swipeshine/privacy.html`
- `https://<你的用户名>.github.io/swipeshine/support.html`

页面应该是白底、带样式的，标题是 "Swipeshine Privacy Policy" /
"Swipeshine Support"。用手机也打开看一眼——审核员大概率用手机看。

> **务必自己先打开一遍。** 拼错用户名、仓库名大小写不对、Pages 还没构建完，
> 这三种情况都会让 Apple 那边看到 404，而你在 ASC 里是看不出区别的。

### 5. 填回 ASC

把这三个 URL 填进 App Store Connect：

| ASC 字段 | 值 |
|---|---|
| 隐私政策 URL | `https://<你的用户名>.github.io/swipeshine/privacy.html` |
| 支持 URL | `https://<你的用户名>.github.io/swipeshine/support.html` |
| 营销 URL | `https://<你的用户名>.github.io/swipeshine/` |

> **营销 URL 是唯一一条「填了更好、但不填也能过」的。** 它显示在商品页上，
> 是用户点进来看到的第一印象。有 `index.html` 之后就不该再留空了——
> 之前留空是因为根目录打开是 README，那个不能给用户看。

同时把 `../01-元数据/metadata.md` 里那三行占位符改成实际地址。

---

## 域名以后想加也行

买了域名之后，GitHub Pages 支持绑自定义域（Settings → Pages → Custom domain）。
届时 URL 变成 `https://swipeshine.app/privacy.html`，**改完记得回 ASC 同步更新**——
但已上架的 App 改这些 URL 不需要重新提审。

> 所以**不要**为了域名把提审往后推。先用 github.io 上架，域名是后续的事。

---

## 常见问题

**打开是 404**
仓库要是 public；Pages 的 branch 要选 `main` 和 `/ (root)`；刚 Save 完要等 1–2 分钟。

**打开是纯文本、没有样式**
文件被当成源码显示了，说明扩展名不是 `.html`，或者上传时被改名了。
GitHub 上点进文件看一眼文件名。

**打开显示的是 README 而不是页面**
说明访问的是 `.../swipeshine/` 而不是 `.../swipeshine/privacy.html`。
根目录没有 `index.html` 时会显示 README——这不影响 ASC，因为 ASC 填的是完整路径。

**想改内容怎么办**
在 GitHub 网页上点开文件 → 铅笔图标 → 改 → Commit。大约 1 分钟后生效。

---

## 支持邮箱：✅ 已定稿

邮箱定为 **`phoenixchao2002@foxmail.com`**——用现成邮箱，不买域名。
代码、两个网页、隐私政策里已经全部换成这个地址。

**提审前唯一要做的：确认它真的能收信。** 从别的邮箱发一封过去，确认收得到。
审核员真的会发信，**发信没人回是独立的拒审理由**。

> **为什么不用 `support@swipeshine.app`**：`support@` 前缀看着专业，但
> **能收信**比前缀好看重要得多。以后真有量了再迁到自有域名也不迟——代价是
> 那时候要重新提审一次，因为邮箱进了二进制。

### `swipeshine.app` 还买不买？

**跟提审无关了，纯看你想不想要个官网。**

- **不买** → 两个页面托管在 GitHub Pages（上面那一整节），完全够用。
- **买**（RDAP 实测 404，约 $10/年）→ 页面可托管在
  `https://swipeshine.app/privacy.html`，比 `<用户名>.github.io` 好看，
  也更像一家能收信的实体。`.app` 是 Google 的 TLD，**强制 HTTPS**，
  Cloudflare 免费给证书。

> ⚠️ **买了域名也别再开 `support@swipeshine.app`。** 邮箱已经定死了，
> 两个地址并存只会让审核员和用户不知道该发哪个。真要换就得重新 build +
> 重新提审，这个代价等真有量了再付。
