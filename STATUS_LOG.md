# Jazz 1899-1969 · Status Log

> 合并历史 STATUS 快照(之前是按日期分散的多个文件)。最新在上。
> 当前线上:https://chen-house.github.io/sound-water-system/
> 项目目前作为 DrumFeather hub 项目下 Drum enthusiast 分支的一件作品。

---

# 项目状态盘点 · 2026-05-15

> 本窗口主题:封面态 + LP 唱片侧脊分隔 + 鼓棒磁头落槽 + 9 个 Spotify 真音频 + 部署到 GitHub Pages

---

## 一、本窗口的关键决策

### 1. 封面态(cover state)上线

之前一进鼓盘默认指 ragtime + 段落面板已展开。现在改成「先看一眼鼓盘,再选段进入」:

- 落地默认是 **封面态**:body 加 `cover` class
- 鼓盘扩到屏幕大部分(grid 从 `1fr 20px 1fr` → `1fr 20px 0fr`,段落面板宽度降为 0)
- 鼓棒**平放在 ragtime 标签旁**(横躺、棒尖朝右)
- 段落面板透明 + pointer-events: none
- 中间分隔条(LP 唱片侧脊)始终在
- 点鼓棒 / 点任意张力杆 → 退封面 + 段落面板展开

### 2. 鼓棒「磁头感」落槽

封面态点鼓棒,鼓棒不是瞬间跳到 ragtime,是用 CSS `transition: transform 0.55s cubic-bezier(0.2, 0.85, 0.25, 1)` 流畅滑过去:

- 起点:`rotate(180deg) translate(-164px, 220px)` — 平放在左上(棒尖在右)
- 终点:`rotate(230deg) translate(0, 0)` — 自然贴到 ragtime 张力杆
- 过渡:rotate 走 50° CCW,translate 同时缩回原点,**ease-out 曲线让落槽前快后慢,像被磁力吸上去**
- JS 加了 `currentTransformAngle` 追踪累积角度,保证后续 notch 切换都走最短路径(不绕大圈)

### 3. 中间分隔条:LP 唱片套侧脊(放弃 channel strip)

走过一次"DJ 调音台 channel strip"的弯路(84px 宽,带 fader/knob/EQ + 电平表)——cc 一句**"假按钮是大忌"**让我退回到正确方向。重做:

- **20px 宽** LP 唱片套侧脊,卡纸色(`#cdb88a` 偏暖,内含暗线模拟纸板厚度)
- 内含 **52px 唱片本体**(黑胶 + 中央红色 label,比套宽 32px,左右各超出 16px)
- 封面态:唱片藏在套内 + opacity 0,只看见空套子
- 打开态:唱片向上"浮出 30px" + opacity 1,像被抽出半截
- **完全静态**——没有任何"长得像可点但不能点"的元素,不撒谎
- 唱片位置改在 `top: 56px`,正好和右面 h3 章节标题对齐(在标题上方,作为开篇标记)

### 4. 9 段 Spotify 真音频全部填好

之前都是 `audio-todo` 虚线占位框写"Spotify embed 位"。本窗口用 WebSearch 找到 9 个曲目的真实 Spotify track ID,**全部换成可播放的 30 秒预览 iframe**:

| 段 | 曲目 | Spotify track ID |
|---|---|---|
| Modal | Miles Davis · So What (1959) | `7azylXFRsebfrIoAtwfjaB` |
| Ragtime | Scott Joplin · Maple Leaf Rag (Joshua Rifkin) | `5cO1oGqX8S2w96CwISPlLE` |
| 新奥尔良 | Louis Armstrong · West End Blues (Hot Five 1928) | `7dOz8RrPWP9UgJ8X8p1vU7` |
| Swing | Benny Goodman · Sing Sing Sing (Carnegie Hall Live 1938) | `4JHMsQ2zPc5iQPur7dAsXm` |
| Bebop | Charlie Parker · Ko-Ko (1945-11-26) | `51mk0FeNTNnpZoLnbbjI0i` |
| Cool | Miles Davis · Boplicity (Birth of the Cool) | `4ktYXnHdjI1mYN5mM0lpjh` |
| Hard Bop | Art Blakey · Moanin' (with Lee Morgan, Benny Golson, Bobby Timmons) | `2JdjC4PecpphQ9Gw6ez5NN` |
| Free Jazz | Ornette Coleman · Lonely Woman (Cherry/Haden/Higgins) | `6xuN1e5UKLipvF764gW5gr` |
| Fusion | Miles Davis · Pharaoh's Dance (Bitches Brew) | `7eEp1mm5xRfPMpilLFUKwX` |

### 5. Logo 改:JAZZ 大写 + 年份在右下角

放弃了之前"音乐水系右上 + JAZZ 1899-1969 左下"的对角呼应。新版本:

- `JAZZ` — 48px serif 大字,居中
- `1899 — 1969` — 11px mono 小字,放在 JAZZ 的右下角(锚点 anchor=end)
- 没有下划线 rule、没有副品牌名,极简

### 6. Overlay 打开时锁住鼓盘

cc 在做封面之前就发现的 bug:在段落 overlay 里,左面鼓棒还能拖,左右两边脱钩。现在加了 `isLocked()` 守卫:overlay 打开 → 鼓棒、张力杆、键盘箭头全部封死。CSS 也加了 `pointer-events: none` 双层防御。

### 7. 部署到 GitHub Pages

`chen-house/sound-water-system` 仓库初始化 + push,Settings → Pages 启用,根目录 `index.html` 自动跳转到 `design/prototypes/snare_dial_v5.html`。

线上地址:**https://chen-house.github.io/sound-water-system/**

---

## 二、当前文件清单

### 顶级

| 文件 | 状态 |
|---|---|
| `README.md` | 已更新到 v0.7.2,含 GH Pages 地址 + 目录说明 |
| `index.html`(根目录,新增) | GH Pages 入口,自动跳转到主页 |
| `.gitignore`(新增) | 忽略 .DS_Store / .obsidian/ |
| `PROJECT_MASTER.md` | v0.6.0,铁律仍有效 |
| `CHANGELOG.md` | 待加 v0.7.2 条目(本窗口产出) |
| `STATUS_2026-05-15.md` | 本文件 |

### 设计 / 原型(design/prototypes/)

| 文件 | 角色 |
|---|---|
| `snare_dial_v5.html` | **主页** · 封面态 + 鼓棒磁头落槽 + LP 侧脊分隔 + 9 真 Spotify 嵌入 |
| `section_02 — section_09 _v2.html` | 8 段 v2 文章页(按编年顺序) |
| `section_01_kind_of_blue_v2.html` | 冷宫保留(内容已并入 section_07) |
| `section_*_v1.html` / `snare_dial_v1—v4*.html` | 历史版本,留作对照 |

---

## 三、现在能做什么

线上的人现在可以:

1. 落地看到一个鼓面 + 旁边躺着一根鼓棒
2. 点鼓棒(或任意张力杆)→ 鼓棒磁头吸上 ragtime,右面 DJ 面板从右侧展开
3. 看到 1899 Maple Leaf Rag 的简介 + Spotify 30 秒预览(可播放)
4. 点 「读全文」 → iframe 悬浮层装入 ragtime 全文
5. 段尾点 「下一段 →」 一直按编年翻到 1969 Fusion
6. 任何时候按 Esc / 关闭按钮 / 「← 回到鼓面」 回到鼓盘
7. 在鼓盘上拖鼓棒、点其他张力杆切换段落

中间始终有一根 LP 唱片侧脊,封面态时唱片在套内,选了段落唱片就被抽出来——视觉上明确"哪一章正在被播放"。

---

## 四、下一步候选(等定)

- **小红书 9 图卡片**:把 9 段做成 swipe carousel,每段一张,引流到线上版
- **短视频(15-30s trailer)**:屏幕录制 + 简单 voiceover,展示鼓棒磁头落槽 + 唱片浮出 + 段落翻页
- 移动端断点(目前主要是桌面优化)
- 其它 3 章串场词(Blues→Hip-hop / Electronic / 鼓手视角)
- 9 张海报封面方向(原产物 C / 音乐签名)

---

## 五、本窗口踩的坑

1. **DJ channel strip 走偏**——做了一根 84px 宽带 fader/knob/EQ/电平表的"调音台条",cc 一眼看出"假按钮 = 大忌"。回滚到 LP 唱片侧脊。教训:**装饰元素不能长得像可交互的**。
2. **鼓棒方向反了 + 挡 Bebop 标签**——translate(-150, 250) 把鼓棒摆在鼓正下方居中,看着像放大镜把手 + 压在 Bebop 字面上。修到 ragtime 旁边 + 平放 + 棒尖朝右才对。
3. **磁头感不是"瞬间跳"**——第一版做成"贴在 ragtime 旁 30px 外侧 → 拿起 = translate 缩到 0",实际感觉是"瞬间跳上去,太突然"。改成"平放在 ragtime 标签上方 → 拿起 = rotate 50° + translate 200+px",过渡时间 0.55s + ease-out,才有"被磁力拉过去"的物理感。
4. **沙箱不能完成 git push**——virtiofs mount 不支持 unlink,git 没法清理临时锁文件,只能让 cc 在 Mac 终端做 `rm -rf .git && git init && commit && push`。
5. **第一次 push 被远端 reject** — 远端有自动生成的 README,本地没有。`git push --force origin main` 一行解决。


---

# 项目状态盘点 · 2026-05-14

> 本窗口主题:把 9 段 v2 文章版做出来 + 修正 section_01 / section_07 的结构性误读(忠于原文)+ 鼓盘起手位置和 logo 调整。
> 不写复盘文学,只列事实。

---

## 一、本窗口的关键决策

### 1. 9 段段落页全部升级到 v2(文章版)

旧 v1 段落页是「DJ 串场 + 中心金句 + 视觉本体」三件套居中拼凑,接近流媒体歌词风格。cc 反馈"看着乱"。重新定型为 v2:

- 顶部保留每段独有的视觉本体(纸条 / 两手打架 / 波形 / 五声部 / 三栏密集 / 冷暖切换 / 调线 / 平行宇宙 / 电流网格)
- 中段是 max-width 640、left-align、line-height 1.75、font-size 17 的**叙事散文**
- 段尾是金线 blockquote(每段引语来自原文章)
- 不再有居中大字"重锤金句"
- 颜色主题继承 v1(每段独有色板保留)

### 2. **结构性修正**:section_01 / section_07 的关系

回查原文 `music_map_article_v3.md` 后发现:

- **Kind of Blue 在原文是 Jazz 这一章的「序章 / 开场钩子」**,标题叫"一段不能'对'的音乐"
- Kind of Blue **实际属于 Modal Jazz 这一节**(原文 Modal 章里写"1959 年。我们回到开篇那个录音棚")
- 原文 Jazz 章只有 **8 个编年子章节** + 1 段序章 + 1 段尾章总结,**不是 9 个并列章节**

此前我做的 section_01 = Kind of Blue 独立页是个误读。修正:

- section_01 的正文搬到 section_07 开头,**替换掉原文那句"我们回到开篇那个录音棚"过渡**
- 中间用第一个 blockquote(Miles "上一代爵士的规矩太紧了。我得松一松")作为序章 → 章节的桥梁
- section_07 现在含两个视觉(纸条 + 调线)和两个 blockquote(论点 + 技术洞见)
- section_01 文件保留(冷宫),没有任何链接指向它

### 3. 鼓盘默认指针改为 1899 Ragtime

之前默认指 1959 Modal(θ=0)是 demo 阶段随手选的,被我事后误读为"Kind of Blue 是入口"。现按"按编年从头读起"的逻辑:

- 默认指针 → Ragtime(θ=230)
- 默认 DJ 面板 → Ragtime 块
- Modal 槽现在指 section_07_modal_v2.html(合并版),不再指 section_01

### 4. 翻页链路(像翻书)

每段右下角加「下一段 · 〔年份〕〔标题〕 →」链接,对称左下「← 回到鼓面」。在 iframe 内点翻页,直接换页 + 鼓盘鼓棒自动转到对应槽位(走原有 `section-shown` postMessage 协议)。链路:

```
Ragtime 1899 (section_02) ← 起手
  ↓ 新奥尔良 1925 (section_03)
  ↓ Swing 1937 (section_04)
  ↓ Bebop 1945 (section_05)
  ↓ Cool / Hard Bop 1949 (section_06)
  ↓ Modal Jazz 1959 (section_07) ← 含 Kind of Blue 序章
  ↓ Free Jazz 1959 (section_08)
  ↓ Fusion 1969 (section_09) ← 末页
```

### 5. Overlay 打开时锁住鼓盘

cc 发现在段落页时左面鼓棒还能拖,左右两边脱钩。加 `isLocked()` 守卫:overlay 打开 → 鼓棒、张力杆、键盘箭头三种交互全封死。关闭 overlay 自动解封。同步加 CSS `pointer-events: none` 作视觉提示。

### 6. 鼓面 logo 调整

- 名字:`声音水系` → **`音乐水系`**(和文章标题一致)
- 位置:从居中对叠改对角呼应——**音乐水系**右上(x=472, y=298)、**JAZZ · 1899—1969**左下(x=328, y=332)
- 去掉中间的下划线 rule

### 7. Ragtime 左手栏文字压线 bug

`.hands .left` 的 `repeating-linear-gradient` 在每行 35-36px 处画细线,CJK 字符下沿正好压在线上。去掉网格背景,改成只靠 `.beat` 标签 + 右栏向下偏移半拍(`padding-top: 20px`)表达"两手打架",字号略放大到 17px、行高放到 40px。

---

## 二、当前文件清单

### 设计 / 原型(design/prototypes/)

| 文件 | 角色 |
|---|---|
| `snare_dial_v5.html` | **主页定稿**(本窗口) · 左右分屏 · 起手 1899 · 9 槽 · 含 DJ 面板 + Spotify 占位 + overlay 锁 |
| `snare_dial_v4.html` | 上一版主页(无 DJ 面板,无 overlay 锁,默认指 Modal),保留作历史 |
| `snare_dial_v4_side.html` / `_v3` / `_v2` / `_v1` | 历史版本,保留 |
| `section_01_kind_of_blue_v2.html` | **冷宫**——内容已并入 section_07,无链接指向 |
| `section_02_ragtime_v2.html` | 段 2 · 1899 Ragtime · 起手 |
| `section_03_new_orleans_v2.html` | 段 3 · 1925 新奥尔良 |
| `section_04_swing_v2.html` | 段 4 · 1937 Swing |
| `section_05_bebop_v2.html` | 段 5 · 1945 Bebop |
| `section_06_cool_hardbop_v2.html` | 段 6 · 1949/1958 Cool / Hard Bop |
| `section_07_modal_v2.html` | 段 7 · 1959–1965 Modal Jazz · **含 Kind of Blue 序章合并** |
| `section_08_free_jazz_v2.html` | 段 8 · 1959 Free Jazz |
| `section_09_fusion_v2.html` | 段 9 · 1969 Fusion · 末页 |
| `section_*_v1.html` | 上一轮 9 段,保留作历史 |

### 顶级文档

| 文件 | 状态 |
|---|---|
| `PROJECT_MASTER.md` | v0.6.0,铁律仍有效 |
| `CHANGELOG.md` | 待加 v0.7.1 条目(本窗口产出) |
| `STATUS_2026-05-13.md` | 上一窗口快照,视觉方向已定 + 9 段 v1 完成 |
| `STATUS_2026-05-14.md` | 本文件,9 段 v2 完成 + 结构性修正 + 鼓盘起手改 1899 |
| `NEXT_SESSION_KICKOFF.md` | 待更新 |

### 文章

| 文件 | 状态 |
|---|---|
| `article/music_map_article_v3.md` | 文字 v3 定稿,本窗口回查后确认 Jazz 章结构(序章 + 8 编年 + 尾章) |

---

## 三、本窗口尾段又改了两件事

### 8. 合并鼓盘 cool / hard-bop 成一个槽(忠于原文)

原文 Jazz 章里 cool 和 hard bop 是一节("Cool / Hard Bop:从冷到热再回来"),不是两节——因为它们不是两个独立革命,而是 bebop 的"温度调节"周期(cool 降温 → hard bop 把火接回来)。鼓盘上之前用两个槽是按"年份事件"切分的,现在按"原文章节"切分:

- 新槽位置:θ=30°(原 cool 45° 和 hard-bop 15° 的中点)
- 标签:`1949—58 · Cool / Hard Bop`,name 用 `.compound` 类(22px 字号)防溢出
- DJ 面板 hard-bop 块删除,cool 块改为**装两个 Spotify 嵌入位**(Boplicity 代表冷 / Moanin' 代表热)
- 鼓盘从 9 槽变 8 槽,与原文 8 编年章节 1:1

### 9. 升级音乐嵌入(Spotify embed)

所有 9 段(实际 8 个 DJ 块)的 `audio-todo` 占位从泛指 placeholder 升级为「曲目 + 专辑 + 年份」具名占位,并在 DJ 面板顶部加全局 HTML 注释,写清楚换成真实 iframe 的模板和拿 TRACK_ID 的步骤(Share → Copy Song Link)。

每段的推荐曲目:

| 段 | 曲目 | 专辑 / 年份 |
|---|---|---|
| Ragtime | Scott Joplin · Maple Leaf Rag | Joshua Rifkin 1970 录音 |
| 新奥尔良 | Louis Armstrong · West End Blues | Hot Five & Seven · 1928 |
| Swing | Benny Goodman · Sing Sing Sing | Carnegie Hall 1938 版 |
| Bebop | Charlie Parker · Ko-Ko | Savoy 78rpm 原版 · 1945 |
| **Cool / Hard Bop** | **Miles Davis · Boplicity(1949)** + **Art Blakey · Moanin'(1958)** | Birth of the Cool / Moanin' |
| Modal | Miles Davis · So What | Kind of Blue · 1959 |
| Free Jazz | Ornette Coleman · Lonely Woman | The Shape of Jazz to Come · 1959 |
| Fusion | Miles Davis · Pharaoh's Dance | Bitches Brew · 1970 |

填实际 Spotify URI 时,把对应的 `.audio-todo` 整个替换为 iframe(模板在 DJ 面板顶部注释里)。

---

## 四、还没做的事

1. ~~section_10 / 尾章页~~ **决定不做了**(cc 本窗口)
2. **Spotify embed 真实 URI**——结构已就位,等填 TRACK_ID
3. ~~鼓盘 cool / hard-bop 合并~~ **本窗口完成**
4. **section_01 文件**——**冷宫保留**(cc 本窗口决定),不删
5. **移动端断点**还没做
6. **其它 3 章串场词**(Blues→Hip-hop / Electronic / 鼓手视角)还没做

---

## 五、待决

- 9 张海报封面方向(原产物 C / 音乐签名)

---

## 六、本窗口踩的坑

1. **section_01 = 入口** 这个判断是基于我自己制造的痕迹(文件编号 + demo 默认指针)反推的,cc 一问才意识到这是 bug 思维。后来回查原文确认 Kind of Blue 在原文里就是序章,**结论碰巧对、推理过程全错**。
2. **9 段段落页 v1 → v2** 中间花了好几轮:先是"DJ + 重锤 + 散文"三层堆叠被批"歌词模式";再"居中拍照文学"被批"乱";最后才落到现在的"视觉 + 左对齐叙事 + 段尾 blockquote"。
3. **鼓盘默认指针**最初放在 Modal 槽是 demo 阶段随手做的,我事后给它编了一套"Kind of Blue 是入口"的故事。
4. **ragtime 文字压线**——`repeating-linear-gradient` 在 36px 行高上 35-36px 处画线,正好压在 CJK 字符下沿。


---

# 项目状态盘点 · 2026-05-13

> 这一份是单次盘点(一次性快照),不是 PROJECT_MASTER 的替代。
> 用途:cc 一眼看清"现在到底有什么、停在哪一步、下一步要决定什么"。
> 不写检讨,不写复盘文学,只列事实。

---

## 一、文件清单

### 顶级文档
| 文件 | 状态 |
|---|---|
| `PROJECT_MASTER.md` | v0.6.0(2026-05-11),铁律和待办仍有效 |
| `CHANGELOG.md` | 已加 v0.7.0 条目(本窗口产出) |
| `STATUS_2026-05-12.md` | 上一次盘点,文字定稿后视觉方向未定时拍的 |
| `STATUS_2026-05-13.md` | 本文件,视觉方向已定 + 9 段实做完成时拍的 |
| `NEXT_SESSION_KICKOFF.md` | 给下一窗口的硬话 |
| `README.md` | 过时,未更新到 v0.7.0 |

### 文章(article/)
| 文件 | 状态 |
|---|---|
| `music_map_article_v3.md` | 文字 v3 定稿,13,658 字 |
| `dj_intros/jazz_chapter.md` | Jazz 章 9 段串场词定稿 |

### 设计 / 原型(design/prototypes/)—— **本窗口的核心产出**
| 文件 | 角色 |
|---|---|
| `snare_dial_v4.html` | **主页定稿**,螺丝外移到轮箍外 lug 位置 + 鼓皮内阴影 + 轮箍外阴影 + **9 个标签按"离鼓圈最近字符在大圆上 r=235"统一对齐** |
| `snare_dial_v3.html` | 主页定稿前版(螺丝嵌在轮箍中央,无内外阴影),留作历史 |
| `snare_dial_v4_side.html` | 侧面 3/4 视角实验(被否,留作历史) |
| `time_dial_v1.html` | 时间表盘前身,黑胶 metaphor 阶段 |
| `snare_dial_v1.html` | 早期黑胶版本(历史) |
| `snare_dial_v2.html` | 白鼓皮中期版(历史) |
| `section_01_kind_of_blue_v1.html` | 段 1 · KoB 锚点 |
| `section_02_ragtime_v1.html` | 段 2 · 1899 Ragtime |
| `section_03_new_orleans_v1.html` | 段 3 · 1925 新奥尔良 |
| `section_04_swing_v1.html` | 段 4 · 1937 Swing |
| `section_05_bebop_v1.html` | 段 5 · 1945 Bebop |
| `section_06_cool_hardbop_v1.html` | 段 6 · 1949/1958 Cool / Hard Bop |
| `section_07_modal_v1.html` | 段 7 · 1959/65 Modal |
| `section_08_free_jazz_v1.html` | 段 8 · 1959/65 Free Jazz |
| `section_09_fusion_v1.html` | 段 9 · 1969 Fusion |
| `divider_card_jazz_v6.html` / `divider_flow_...` | 早期 divider 探索(历史) |

### 设计文档
| 文件 | 状态 |
|---|---|
| `design_judgment_framework_v1.md` | 视觉决策四层框架,仍有效 |

### 参考素材(references/)
- INDEX.md 索引仍有效
- 用户实拍真鼓照片(对 v3 鼓面定型起决定作用)

---

## 二、当前进度

### 文字层
- v3 定稿,不再迭代

### 视觉层 —— **本窗口完成的事**
- **主页 snare_dial_v3.html 定稿**:
  - 镀铬轮箍(linearGradient 上亮下暗)
  - 9 颗方形螺丝头(7×7 深金属渐变 + 中央 3.5×3.5 方钥匙口)
  - 150px 立体木质鼓棒(锥度木杆 + 棒头球 + 投影 + 高光,常驻可见,默认指向 1959 Modal)
  - 鼓皮中央 12 点钟方向品牌牌子(声音水系 / JAZZ · 1899—1969)
  - 9 段两行排标签:**年份小细在上(14px),流派名大正在下(28px),流派名 LEFT EDGE 对齐到年份第 3 数字位置**
  - 左右分屏悬浮(50vw / -22vw),滚动锁定,Esc / × / 段内按钮三种关闭方式
  - 鼓棒按 SVG rotate 绕 (400,400) 转,z-order 调换让标签永在鼓棒上方
- **9 个段落页全部完成**,每段独立形式呼应内容
- **9 段段内邻居卡已撤掉**(导航全靠主页鼓面)
- **每段底部 design-note 开发笔记已撤掉**
- **每段保留"回到鼓面"链接**(在 iframe 内通过 postMessage 关闭悬浮)

### 9 段视觉本体一览
- 段 1 KoB:6 张纸条 + "我们就这么吹"
- 段 2 Ragtime:左右手打架的两栏错位网格
- 段 3 NOLA:5 声部 clip-path 波形 + Louis 切出
- 段 4 Swing:20 个乐手 roster + 长短交替"咚"
- 段 5 Bebop:3 栏文字墙 + 沉默 + "建议你先坐下来"
- 段 6 Cool/Hard Bop:上半冷色 + 下半暖色,色温做反
- 段 7 Modal:两根横线 + 9 个稀疏音点 = D Dorian / E♭ Dorian
- 段 8 Free Jazz:两个平行宇宙倾斜叠加 + 版面网格被破
- 段 9 Fusion:一道电青色光带 + Miles 43 岁

### 交互机制
- **postMessage 协议**:每段在 iframe 加载时向主页发送 `{type: 'section-shown', sectionId: 'xxx'}`,主页据此把鼓棒滑到对应张力杆
- **suppressNextShown 标志**:避免点击张力杆后段落上报"我是这一段"导致鼓棒"再动一次"
- **iframe 内的"回到鼓面"链接**:通过 postMessage `{type: 'close-overlay'}` 通知主页关闭悬浮,不真正跳转

---

## 三、路线已修正(2026-05-13 复盘开场 intent 后)

**v0.6.0 的"两产物"框架已被 cc 撤掉。**回到原始 intent:**一个产品 + 一条分发链**。

- **产品** = jazz 网页作品(当前 v3 + 9 段)
- **分发** = 9 张海报封面发小红书 / 公众号,把人带去网页

不是两件作品,是网页是本体,海报是入场券。

### Phase 1 · 网页作品落地(进行中)
1. PROJECT_MASTER 升级到 v0.7.0,撤"两产物"框架
2. **9 章段落页文本样式调整(当前任务)** —— 三层文字声音的层级统一
3. 正文 v3 的"河流 / 水系 / 支流"语言清理
4. 联系方式占位补上(邮箱 / 即刻 / 小红书 ID)
5. HTML / React 路线拍板。Claude 倾向 HTML 直接发布
6. 部署 + 域名

### Phase 2 · 9 张海报封面(Phase 1 完成后)
- 落"方向 C 音乐签名":错位音 / 辐射线 / 长短拍 / 密集竖线 / 长横线 / 钉合 / 空心圆 / 散点 / 闪电
- 小红书 9 卡轮播 + 公众号头图 + 文内插图,同一套素材复用
- 每张图带网页链接 / 二维码,功能是入场券

### 之后
基本上是渠道运营事,不是设计事。

### 字体层:已收敛,可继续微调
- 流派名缩进规则:**全 9 段统一为"name LEFT edge = year 3rd digit LEFT edge"**
- 左侧 Ragtime / 新奥尔良用了镜像规则(name 的 RIGHT edge 对到 3rd digit,因为往左伸远离鼓边)——这个细节可以再讨论是否要改成和其它 7 段完全一致

---

## 四、本窗口被否决的方向(留作历史)

1. **黑胶 metaphor**(time_dial_v1 / snare_dial_v1):cc "用的有点儿烂大街了"
2. **侧面 3/4 视角**(v4_side):cc "没有俯视效果好"
3. **9 段流派名全 italic**:cc "鼓棒同款斜线,集体歪"
4. **"年份大流派名小"的博物馆铭牌式**:cc "年份字号小,文字大"才对
5. **底部邻居卡"和我说话的人"**:cc 说有鼓面就不需要重复入口
6. **editorial minimalism / 克制长文风**(早期 sample_section_1.html):cc "满网都是"
7. **工作稿装饰满版**(早期 sample_X_workingdoc.html):cc "对点味道但太乱"
8. **电台软件 UI**(早期 sample_Z_radio.html):cc "走偏成赛博朋克仪表盘"

---

## 五、未做、暂搁、未来想做

### 未做(在路线图上但本窗口未启动)
- **9 张海报封面**(原计划方向 C / 音乐签名):每段一张作品级封面,留给后续
- **其它 3 章串场词**(开场 / Blues→Hip-hop / Electronic / 鼓手视角 / 收束)
- **正文 v3 里"河流/水系/支流"语言清理**(从 metaphor 已换到军鼓,语言未跟上)

### 已搁置但有备忘
- 方向三(9 张作品级图,Hipgnosis / ECM 调) —— cc 自己探索
- 手势 / 语音 / 3D 交互作品 —— 未来项目
- 移动端适配 —— 鼓面和段落都是桌面优先,触控/小屏未做断点

---

## 六、本窗口踩过的教训

1. **不要原地覆盖版本**:本窗口在 v3 上原地改了 N 次,中间状态全部丢失。cc 在做侧面实验时才提醒我"保留这个版本啊"——这之后才意识到应该每次大改另存版本号
2. **iframe 内的子段落如果引用父页面的链接,会出现 iframe 递归嵌套**——靠 postMessage + back link 拦截解决
3. **SVG 中 transform / 渐变 stroke / 圆点 vs 方块的 hover** 各有各的坑——比如圆点用 `r` 属性,矩形用 `transform: scale()` 或 `filter: brightness()`
4. **字体设计感不是来自装饰**,是来自"每个差异都在替内容说话"(粗细 / 大小 / italic / 字距 / 颜色每一处都对应一个判断)
5. **左右镜像规则在不同侧的标签上要慎重**——同一条"name 对齐到 year 3rd digit"在左右两侧的视觉表现不同,需要明确是 LEFT edge 对 LEFT edge 还是 RIGHT edge 对 LEFT edge


---

# 项目状态盘点 · 2026-05-12

> 这一份是单次盘点(一次性快照),不是 PROJECT_MASTER 的替代。
> 用途:cc 一眼看清"现在到底有什么、停在哪一步、下一步要决定什么"。
> 不写检讨,不写复盘文学,只列事实。

---

## 一、文件清单(项目根目录 sound-water-system/)

### 项目顶级文档(4 个)

| 文件 | 行数 | 内容摘要 | 当前状态 |
|---|---|---|---|
| `README.md` | 32 | 项目概览、目录说明、读文件顺序 | **过时** —— 写的是"DJ MVP 降级版",未反映 v0.6.0 战略调整 |
| `PROJECT_MASTER.md` | 149 | 项目身份、铁律、待办、用户偏好、版本号 | v0.6.0(本窗口更新),顶部"开窗第一句"+ 两产物结构 |
| `CHANGELOG.md` | 353 | 从 v0.1 到 v0.6.0 的逐版变更与教训 | 最新 v0.6.0 条目(本窗口写入) |
| `NEXT_SESSION_KICKOFF.md` | — | 上一窗口结束时的交接文 | **已失效** —— 它是为本窗口"战略对齐"写的,本窗口已完成;下一窗口需要新版 |

### 文章正文(article/)

| 文件 | 体量 | 内容 | 状态 |
|---|---|---|---|
| `music_map_article_v3.md` | 849 行 / 13,658 中文字 | 全文 v3,6 章结构:开场 / Blues→Hip-hop / Jazz / Electronic / 鼓手视角 / 收束 | **正文 v3 已定稿**,文字层不再迭代 |
| `dj_intros/jazz_chapter.md` | 200 行 | Jazz 章 9 段 DJ 串场词(开篇 / ragtime / 新奥尔良 / Swing / Bebop / Cool-HardBop / Modal / Free Jazz / Fusion) | **9 段全部定稿** |

> Jazz 章在正文里位置:第 192-389 行附近,约 4,000-5,000 字。

### 设计 / 原型(design/)

| 文件 | 内容 | 在项目中的角色 |
|---|---|---|
| `design_judgment_framework_v1.md` | 视觉决策四层框架(目标/约束/方案/判断) | **方法论文档**,仍有效 |
| `prototypes/divider_card_jazz_v6.html` | 早期 divider card(Jazz 段间隔卡)第 6 版 | **历史版本**,被本窗口的视觉方向探索取代 |
| `prototypes/divider_flow_bebop_to_coolhardbop_v1.html` | divider 在段间过渡的流程演示 | **历史版本**,同上 |
| `sample_section_1.html` | 本窗口第一稿:editorial minimalism / 米黄克制 | **被否** —— cc 反馈"满网都是" |
| `sample_X_workingdoc.html` | 本窗口方向 X:节目工作稿(A4 + 打字机 + 手写批注 + 装饰元素 11 种) | **方向对、执行偏** —— cc 反馈"对点味道但太乱" |
| `sample_Z_radio.html` | 本窗口方向 Z:深夜电台软件 UI(暗背景 + 琥珀色 + 调频刻度) | **被否** —— cc 反馈"这活你能不能做" |
| `sample_X_v2.html` | X 的克制简化版 + 加入正文区(放法 A) | **被否** —— cc 指出本质仍是"克制 editorial"家族,我没有从内容长出形式 |

### 参考素材(references/)

- `INDEX.md` —— 每张参考图的来源、内容、触发的决策(已建索引)
- 15 张图 + 1 张 JPG —— 包括 The Pudding 的 music-dna / happy-map、Dorothy 电路板海报、divider card 历史截图、cc 自购的 BOUND-LESS ECHO 黑胶相框

### 空目录

- `docs/` —— 存在但为空。预留位置。

---

## 二、当前进度

### 文字层

- **v3 正文 13,658 字定稿**,不再迭代
- **Jazz 章 9 段 DJ 串场词全部定稿**
- 文字层在 v0.5.3 已达成"准确 + 不学术 + 像人讲话"的底线

### 战略层(v0.6.0 本窗口产出)

- 项目从"长文 + 视觉"拆成两个独立产物:
  - **产物 A · Jazz 章独立发布**(当前聚焦)
  - **产物 B · "声音水系"视觉作品**(暂时搁置,等 A 反馈后启动)
- 产物 A 的载体:小红书 + 公众号双发
- 产物 A 内部结构:主体 = 可滚动网页 / 宣传物 = 9 张轮播图(从网页衍生)
- 工作切成三块:块 1 内容钩子 → 块 2 视觉语言 → 块 3 落地执行

### 视觉层

- **已尝试 4 个方向,均未通过**:editorial minimalism / 工作稿(装饰满版)/ 电台软件 UI / 工作稿简化版
- **cc 最后一次反馈指出根本问题**:本窗口 Claude 把"克制"当万能解药,所有尝试都是网页类型的调整,**没有一稿从"声音水系 / 9 段不同流派 / 形式呼应内容"的本体出发**
- 视觉方向**尚未定**

### 协作机制

- PROJECT_MASTER 顶部新增"开窗第一句",列出 Claude 默认倾向、三类典型诱惑、cc"停"是一字否决
- 本窗口暴露的新问题:**Claude 反复"检讨 / 自省 / 复盘"本身也是一种逃避**——把"承认错误"做成了产出形态,占用 cc 的精力,等价于不出活

---

## 三、决策卡点(下一步在哪里停)

视觉方向是当前唯一的卡点。其他事项都在等视觉方向落定。

### cc 已经否决的方向

1. editorial minimalism / 克制长文风(满网都是)
2. 装饰满版的工作稿(太乱)
3. 电台软件 UI(走偏成赛博朋克仪表盘)
4. 克制版工作稿(仍是 editorial 家族)

### Claude 在最后一轮提出的"未验证方向"

**形式呼应内容 / 9 段差异化设计** —— 不是 1 个 template 套 9 次内容,而是每段视觉本身就是那段音乐的本体:

- ragtime → 错位重音 → 版面错位
- bebop → 高速密度 → 信息突然爆炸 / 字号变小
- cool jazz → 降温 → 留白爆炸 / 字距变宽
- free jazz → 拆规矩 → 版式直接崩坏
- modal(Kind of Blue)→ 留白 + 一句话
- fusion → 插电 → 颜色饱和度突然变高

**这个方向 cc 尚未确认,Claude 尚未做出真稿**。

### 待决策事项

1. 上述"形式呼应内容"方向,cc 是否认?
2. 如果认,从哪一段切入(Kind of Blue 是开篇,但它的"安静空"特性能否作为"基准"让后面 8 段的反差成立)?
3. 9 段差异化的工程量是 1 段 template 的 5 倍以上,cc 是否接受这个量级?
4. 如果不认,cc 给一个新方向

---

## 四、未来想做但暂不做的事(cc 已提及,留作备忘)

- 方向三(9 张作品级图,Hipgnosis / Cosmo Sheldrake / ECM 调) —— cc 表示"自己探索",不在协作内
- 方向四(手势 / 语音 / 3D 交互作品) —— cc 表示"很不成熟",未来项目
- 产物 B "声音水系"视觉作品 —— 等产物 A 反馈后启动
- 其他 5 章串场词(开场 / Blues→Hip-hop / Electronic / 鼓手视角 / 收束) —— 等 Jazz 章发出去拿反馈后定节奏

---

## 五、给下一窗口 Claude 的硬话

1. **先读 PROJECT_MASTER.md 顶部"开窗第一句"。**
2. **再读 CHANGELOG.md 顶部 v0.6.0 条目。**
3. **再读本文件(STATUS_2026-05-12.md)。**
4. **不要立刻开干。视觉方向尚未定,这是当前唯一卡点。**
5. **不要堆"检讨 / 自省 / 复盘"段落。cc 已明确说过"不要总跟我检讨"。出结果。**
6. **不要做"克制 editorial"任何变体。cc 已否决整个家族。**
7. **想做视觉?先回答一个问题:这一稿是从"网页类型"出发的,还是从"这段音乐 / 这段内容的本体"出发的?如果是前者,停。**
