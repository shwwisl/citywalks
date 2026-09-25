# Citywalks · 全国半日漫游攻略合集 🏮🌳🐼

> 一份攻略走透一座城 · 纯静态 HTML · GitHub Pages 部署

一个持续收录的「全国城市漫游攻略」合集站。每座城市一个子目录，独立完整；汇总首页展示已收录城市清单与全国示意图。

**在线访问**：https://<your-github-username>.github.io/citywalks/ （部署后填入）

---

## 📁 项目结构

```
citywalks/
├── index.html              # 汇总首页（全国 3 城卡片 + SVG 地图）
├── README.md               # 本文件
│
├── shanghai/
│   ├── tianzifang/         # 田子坊 · 6 文件完整攻略（含二级页面 + 5 轮迭代记录）
│   │   ├── index.html
│   │   ├── food.html
│   │   ├── history.html
│   │   ├── architecture.html
│   │   ├── style.css
│   │   ├── README.md
│   │   └── 制作一份城市 Citywalk 半日路线攻略.md   # 原始 5 轮迭代记录
│   └── wukang/             # 武康路 · 单页 7 站攻略
│       └── index.html
│
└── chengdu/
    └── kuanzhai/           # 宽窄巷子 · 单页 5 站攻略
        └── index.html
```

**总大小**：约 130 KB · 纯静态、无构建工具、无第三方依赖

---

## 🗺️ 已收录城市

| 城市 | 片区 | 主题 | 文件数 | 状态 |
|---|---|---|---|---|
| 上海 | 田子坊 | 石库门 + 弄堂 + 艺术 | 6（+二级页） | ✅ |
| 上海 | 武康路 | 梧桐 + 法租界老洋房 | 1（单页） | ✅ |
| 成都 | 宽窄巷子 | 川西民居 + 茶馆 + 小吃 | 1（单页） | ✅ |

---

## 🚀 GitHub Pages 部署指南

### 一次性部署（5 分钟）

1. **创建 GitHub 仓库**
   - 仓库名推荐：`<username>.github.io`（个人主页）或 `citywalks`（项目页）
   - 类型：Public
   - 勾选 "Add a README"

2. **上传文件**
   - 仓库页 → `Add file` → `Upload files`
   - 把整个 `citywalks/` 文件夹内容拖进去（保持目录结构）
   - Commit message 写 "Initial citywalk collection"
   - ⚠️ 注意 GitHub 网页端上传不支持自动建文件夹，建议用 Git 客户端或 VS Code

3. **开启 Pages**
   - 仓库 → `Settings` → `Pages`
   - Source 选 `Deploy from a branch`
   - Branch 选 `main`、目录 `/ (root)`
   - 点 Save

4. **等待部署**
   - 1-3 分钟后刷新 Settings → Pages
   - 顶部出现绿色横幅："Your site is live at https://<username>.github.io/citywalks/"
   - 这个 URL 就是分享链接 ✅

### 后续更新流程

**方式 A：网页端直接改**
- 仓库 → 点开文件 → 右上角铅笔 ✏️ → 编辑 → Commit changes
- 适合偶尔改一两处

**方式 B：Git 推送（推荐）**
```bash
# 首次克隆
git clone https://github.com/<username>/citywalks.git
cd citywalks

# 修改文件后
git add .
git commit -m "添加 XX 城市攻略"
git push
# 1-3 分钟自动部署
```

**方式 C：GitHub Desktop / VS Code 图形界面**
- 适合不熟悉命令行的用户
- 提交 + 推送都可视化

### 部署后必做

- [ ] 浏览器强刷（`Ctrl + F5` / `Cmd + Shift + R`）测试访问
- [ ] 手机扫码测试（GitHub Pages 国内访问偶有延迟，2-3 次重试通常 OK）
- [ ] 检查每个城市链接是否可点

---

## ➕ 如何新增一个城市

### 步骤 1：创建城市目录

```bash
# 在 citywalks/ 下建新城市目录
mkdir beijing/oldcity/
# 或者在已有城市目录下建新片区
mkdir shanghai/xintiandi/
```

### 步骤 2：生成攻略文件

使用本项目的「Citywalk Guide Generator」Skill：

1. 加载 skill：`skill({ name: "citywalk-guide-generator" })`
2. 提供参数：城市 + 主题 + 日期 + 人数 + 出发地 + 预算
3. 复制生成的 6 文件到对应目录
4. 在每个现有页面的顶部导航添加链接

### 步骤 3：更新汇总首页

打开 `citywalks/index.html`，在「已收录城市」section 加一张城市卡片：

```html
<a class="city-card" href="beijing/oldcity/">
  <div class="cover YOUR-CITY-GRADIENT">
    YOUR-EMOJI
    <span class="badge">BEIJING · 北京</span>
  </div>
  <div class="body">
    <div class="city">BEIJING · 北京</div>
    <h3>老城区 Citywalk</h3>
    <p class="lead">一句话定位...</p>
    <div class="tags">
      <span class="tag">标签 1</span>
      <span class="tag">标签 2</span>
    </div>
    <div class="meta">
      <span>⏱ 时长</span>
      <span>📍 起讫</span>
      <span>👥 人数</span>
    </div>
  </div>
</a>
```

并更新顶部 Hero meta 的「已收录 X 个城市片区」数字。

### 步骤 4：更新每个子页面的顶部导航

每个城市的 `index.html` 都有一段 `.topnav`，需要加入新城市链接：

```html
<nav class="topnav">
  <a href="../../">🌏 Citywalks</a>
  <a href="../../shanghai/tianzifang/">🏮 田子坊</a>
  <a href="../../shanghai/wukang/">🌳 武康路</a>
  <a href="../../chengdu/kuanzhai/">🐼 宽窄巷子</a>
  <!-- 在这里加新城市链接 -->
  <a href="../../beijing/oldcity/">🏯 老城区</a>
</nav>
```

⚠️ **路径必须用相对路径**（`../../city/`），不要用 `/city/`（会指向域名根目录 404）。

---

## 🎨 设计 token

| 城市 | 主色 | 辅助 | 寓意 |
|---|---|---|---|
| 汇总站 | `#c2542e` 暖橘红 | `#d9a441` 金黄 | 旅行通用主题色 |
| 上海田子坊 | `#c2542e` 暖橘红 | `#3d6b5e` 墨绿 | 老上海弄堂 |
| 上海武康路 | `#3d6b5e` 墨绿 | `#7ba05b` 草绿 | 梧桐 + 法租界 |
| 成都宽窄巷子 | `#a4262c` 故宫红 | `#c89b3c` 琉璃黄 | 川西民居 |

每个城市攻略都用自己的主色作为 Hero 渐变色 + 主题高亮色，视觉一致又有辨识度。

---

## 📋 内容来源

| 内容 | 主要参考 |
|---|---|
| 田子坊基本信息 | 黄浦区政府官网、百度百科、上海市地方志 |
| 田子坊时间线 | 上海地方志、黄浦区文化志 |
| 武康大楼/罗密欧阳台/巴金故居 | 百度百科、徐汇区政府官网 |
| 宽窄巷子历史 | 百度百科、成都市文旅局 |
| 三大小吃/茶馆文化 | 携程攻略、四川美食指南 |
| 高铁班次与价格 | 12306（中国铁路客户服务中心） |
| 画家楼 2025 焕新 | 首届上海城市更新发展大会官方通报 |

⚠ **动态信息提示**：店铺营业时间、排队时长、价格区间随季节与节假日变化，文内数字均为 2025-2026 年参考值，**实际出行请以 12306 与实地为准**。

---

## 🛠️ 维护速查

| 症状 | 原因 | 解法 |
|---|---|---|
| 页面全是裸文字无样式 | 相对路径错误 | 检查 `href="style.css"` 是否在同一目录 |
| 点链接 404 | 路径深度不对 | 子目录里的链接用 `../../city/` 不是 `/city/` |
| 改了没变化 | CDN 缓存 | `Ctrl + F5`，等 3 分钟 |
| 国内访问慢 | GitHub Pages 无大陆节点 | 改用 Netlify / Vercel / Cloudflare Pages |
| SVG 在小屏挤成蚂蚁 | CSS 媒体查询缺失 | 检查 `style.css` 末尾的 `@media (max-width:600px)` |

---

## 📜 License & 致谢

- 内容创作：David（舒三石）+ AI 联合创作
- 全部为个人非商业学习使用
- 车次、价格、开放时间等信息请以官方渠道实时数据为准

---

## 🗓️ 项目历程

| 日期 | 事件 |
|---|---|
| 2026.09.25 | 上海田子坊 5 轮迭代完成 |
| 2026.09.25 | 沉淀 `citywalk-guide-generator` Skill |
| 2026.09.25 | 整理为多城市合集站，部署 GitHub Pages |
| 2026.09.25 | 新增上海武康路、成都宽窄巷子 |

> 一句话：**愿这份合集能帮你走透每一座值得半日的城** 🏮🌳🐼