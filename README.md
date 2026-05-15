# 声音水系 · Sound Water System

> 一枚爱听歌的听客,给自己画了张音乐水系。

第一支被画完的支流是 **Jazz · 1899—1969**——一段不肯重复自己的音乐。

## 在线访问

GitHub Pages:[chen-house.github.io/sound-water-system](https://chen-house.github.io/sound-water-system/)

(根目录的 `index.html` 会自动跳到主页 `design/prototypes/snare_dial_v5.html`)

## 你看到了什么

- **左边**:一面军鼓的鼓面,9 根张力杆 = 8 个爵士流派的时间表盘(1899 Ragtime → 1969 Fusion)
- **中间**:一根 LP 唱片的侧脊,封面态时唱片在套内,选了某段就被"抽出来"
- **右边**:DJ 面板,显示当前段的引子 + Spotify 嵌入位 + 「读全文」按钮
- **段落页**:每段独立设计形式呼应内容(纸条 / 两手打架 / 五声部 / 三栏密集 / 冷暖切换 / 调线 / 平行宇宙 / 电流网格)

## 怎么用

落地是封面态:鼓棒平放在 ragtime 标签旁边,右边段落面板没展开。点鼓棒 → 鼓棒贴上 ragtime,段落面板从右侧展开。之后可以拖鼓棒 / 点其他张力杆切换章节,或点段落里的「下一段 →」按页翻。

主页:**design/prototypes/snare_dial_v5.html**

## 目录

```
.
├── index.html              GH Pages 入口(重定向到主页)
├── article/                文章正文
│   └── music_map_article_v3.md
├── design/
│   ├── prototypes/         视觉原型(HTML)
│   │   ├── snare_dial_v5.html       主页 · 鼓盘 + DJ 面板
│   │   ├── section_02_ragtime_v2.html ~ section_09_fusion_v2.html
│   │   └── section_*_v1.html        历史版本(留作对照)
│   └── design_judgment_framework_v1.md
├── references/             参考素材(真鼓照片 / 灵感图)
├── PROJECT_MASTER.md       主文档
├── CHANGELOG.md            版本记录
└── STATUS_*.md             每次窗口的快照盘点
```

## 怎么开始读

1. `PROJECT_MASTER.md` —— 项目当前在哪
2. `article/music_map_article_v3.md` —— 文章正文(Jazz 章)
3. 打开主页 HTML,自己上手玩

## 版本

详见 `CHANGELOG.md`。当前 **v0.7.1**(2026-05-14):9 段 v2 文章版 + 鼓盘起手 1899 + LP 唱片侧脊分隔 + 鼓棒磁头感落槽。
