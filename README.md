# 声音水系 · Sound Water System

> 一枚爱听歌的听客,给自己画的音乐谱系。

两条已经画完的支流:一条往回追到 1899,一条只看最近二十年。两个页面都能听,都是单个自包含的 HTML,不依赖任何服务端。

## 在线访问

**入口:[chen-house.github.io/sound-water-system](https://chen-house.github.io/sound-water-system/)**

| 作品 | 打开 | 是什么 |
|---|---|---|
| **星轨播放器** · DownBeat 2006—2025 | [`mixer_v36_open.html`](https://chen-house.github.io/sound-water-system/mixer_v36_open.html) | 二十张年度专辑排成一张星图,能听 |
| **军鼓表盘** · Jazz 1899—1969 | [`design/prototypes/snare_dial_v5.html`](https://chen-house.github.io/sound-water-system/design/prototypes/snare_dial_v5.html) | 鼓面即时间表盘,八个流派 |

英文版:军鼓表盘走 `snare_dial_v5_en.html`;星轨播放器的中英切换在页面右下角的 `EN` 开关里。

---

## 一、星轨播放器

DownBeat 国际乐评人票选(第 54–73 届 / 2006–2025)的二十张年度专辑,做成一张可以听的星图。

**三个视角,同一批星:**

- **星轨** —— 全部二十张,按届次排在各自的轨道上
- **北斗** —— 用耳朵挑出来的七首,对应北斗七星
- **天鹅** —— 按鼓挑出来的八首,对应天鹅座

切换视图不是换图表,是**观察者换了位置**(视差)。

**几条自己给自己定的规矩:**

1. **坐标是真的。** 星位来自真实星表的赤经赤纬投影。天鹅座头臂是尾臂的 2.5 倍、两翼一高一低,这些不对称是天上本来就有的。
2. **大小是真的。** 骨架星的半径按**真实视星等**给(维基各恒星条目信息框的 V 波段值),不按"我觉得这张重要"。
3. **界面上每一行都在讲音乐。** 榜单名次、发行渠道这类信息属于研究文档,不进卡片。
4. **借来的乐评一律用原话。** 英文版显示发表时的原句,查不到出处的不显示。8 条里找回 6 条,过程记在 `research/playlist_v1.md` 第 20 条。
5. **听过的星变金,连线自己接上。** 星座是被听出来的,不是画好摆在那儿的。

**音源**:iTunes 30 秒预览(有 CORS,所以星的脉动是真实频谱驱动的);Maria Schneider《Data Lords》不在 Apple Music 上,走网易云整轨。Sonny Rollins《Road Shows, Vol. 1》还没定代表曲,是唯一一颗哑星。

---

## 二、军鼓表盘

一面军鼓的鼓面,九根张力杆就是八个爵士流派的时间表盘(1899 Ragtime → 1969 Fusion)。

- **左边**:鼓面与张力杆
- **中间**:一根 LP 唱片的侧脊,封面态时唱片在套内,选了某段就被"抽出来"
- **右边**:DJ 面板,当前段的引子 + Spotify 嵌入位 + 「读全文」
- **段落页**:每段的版式按它自己的音乐设计——纸条 / 两手打架 / 五声部 / 三栏密集 / 冷暖切换 / 调线 / 平行宇宙 / 电流网格

落地是封面态,鼓棒平放在 ragtime 标签旁。点鼓棒 → 段落面板从右侧展开。

---

## 三、目录

```
.
├── index.html                  入口页(两件作品)
├── mixer_v36_open.html         星轨播放器 · 当前版
│
├── design/
│   ├── covers/                 入口页用的封面图
│   ├── prototypes/
│   │   ├── snare_dial_v5.html      军鼓表盘 · 当前版
│   │   ├── snare_dial_v5_en.html   英文版
│   │   ├── mixer/                  星轨播放器 v0–v35 全部历史版本
│   │   ├── sections/               九个爵士段落页(v1 / v2)
│   │   ├── snare/                  军鼓表盘的早期迭代
│   │   └── misc/                   其它原型
│   ├── bird_iter/              星座形状的迭代过程图
│   ├── palette/                配色
│   └── design_judgment_framework_v1.md
│
├── research/                   研究记录 —— 这个项目的地基
│   ├── playlist_v1.md              三个视图的内容清单 + 每个决定的依据 + 作废理由
│   ├── jazz_critics_poll_2006_2025.md
│   ├── why_it_won_2006_2025.md
│   ├── landscape_1976-2026_final.md
│   ├── star_spec_v1.md
│   ├── trusted_ears.md
│   ├── 复盘_星轨播放器.md
│   └── ...
│
├── article/                    文章正文与 DJ 引子
├── references/                 参考素材(真鼓照片 / 灵感图)
├── music-corpus-viz.skill      从这个项目里提出来的方法(Agent Skill)
│
├── PROJECT_MASTER.md           项目主文档
├── CHANGELOG.md                版本记录
└── STATUS_LOG.md               每次窗口的快照
```

**`research/` 是这个项目真正的地基。** 二十三张唱片的鼓手署名逐条核实、乐评原话逐条溯源、星等逐颗查证,过程和作废的判断都记在里面。`playlist_v1.md` 的开头是变更日志,记着每一次改动的理由——包括做错了又推翻的那些。

---

## 四、方法

`music-corpus-viz.skill` 是从这个项目里提取出来的方法,可以直接装进 Claude 使用:

- 动手前的三个问题(单位是什么 / 有没有可查证的排序 / 能听到多少)
- 六条约束,每条带这个项目里的正反例
- **什么时候不该用星图**——判据和四种替代形状
- 音源决策树,带实测数字
- 工程与验证:四种"测量工具骗了我"的具体案例

---

## 怎么开始读

1. `PROJECT_MASTER.md` —— 项目当前在哪
2. `research/playlist_v1.md` —— 星轨播放器的全部内容与依据
3. `research/复盘_星轨播放器.md` —— 做完之后的复盘、评价与后续方向
4. 打开两个 HTML,自己上手玩

## 版本

详见 `CHANGELOG.md`。

- **军鼓表盘** v0.7.1(2026-05-14):9 段 v2 文章版 + 鼓盘起手 1899 + LP 唱片侧脊分隔 + 鼓棒磁头感落槽
- **星轨播放器** v36(2026-08-12):中英切换 + 开场曲换成 2012 届 Accelerando(前 3 秒比原来轻 16 dB)

## 授权

CC BY-NC-ND 4.0,见 `LICENSE`。
