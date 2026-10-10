# 怎么往作品集里加新作品

素材唯一来源：`D:\新建文件夹\作品集\作品集`

## 一、加图片（最省事）

把图片丢进素材根下**任意文件夹**，然后重新构建：

```powershell
cd D:\沙盒\_anim-portfolio
node src/build.mjs
```

就这样。规则：

| 你做的事 | 网站上的效果 |
|---|---|
| 往已有文件夹丢图（如 `平面视觉\海报`） | 自动出现在对应作品的图集里，排在最后 |
| 新建一个文件夹（如 `平面视觉\画册`） | 自动多出一组新作品，标题用文件夹名 |
| 把图放到素材根最外层 | 归到最外层目录那一组 |

## 二、给它一个好标题和说明（推荐）

打开 `works.config.mjs`，在 `WORKS` 里加一条：

```js
{
  id: "album-design",                 // 网址会是 work-album-design.html
  match: { group: "平面视觉", sub: "画册" },
  order: 6,                           // 越小越靠前
  featured: false,                    // true = 首页放大当主案例
  kind: "poster",                     // 决定分类标签
  kindLabel: "视觉",
  type: "画册 · 版式",
  title: "品牌画册",
  subtitle: "一句话说清这是什么",
  accentLine: "卡片上的一句话，要能让人想点进去",
  role: "独立完成",
  tags: ["版式", "画册"],
  metrics: [{ k: "页数", v: "24", u: "页" }],
  overview: { summary: "两三句讲清做了什么、怎么做的。" },
  sections: { heading: "取舍", points: ["要点一", "要点二"] },
  note: "事实边界：课程作业 / 自命题 / 真实商单，如实写。",
}
```

## 三、只看文件夹名也要懂：分类标签

`kind` 可选：`threed`（三维）`poster`（视觉）`packaging`（包装）`ecom`（运营）
`layout`（版式）`illustration`（插画）`product`（产品）`research`（调研）`other`

## 四、几个常用命令

```powershell
node src/build.mjs --watch          # 挂着，素材一改自动重建
node src/build.mjs --no-images      # 只改了文案，跳过图片压缩，秒出
node src/build.mjs --serve 8900     # 建完起本地预览 → http://127.0.0.1:8900/
```

## 五、什么不要往里放

- 别人的作品集、下载的模板、带水印的外部图 —— 一律不要。网站是要公开的。
- 疑似临摹但没标注的稿子 —— 先确认，再放。
