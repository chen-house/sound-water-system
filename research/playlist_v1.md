# 歌单 · 三个视图的内容清单

> 数据源:**DownBeat 国际乐评人票选 · 年度专辑 · 第 54–73 届(2006–2025)**
> 20 张 = 20 颗星。**届次年一年一张,不重不漏**(发行年会有重号,所以标签一律用届次)。
> 鼓手与生年逐张 credits 核实,查不到就留空,不推算。
> 最后更新:**2026-08-11**(v32)

---

## 〇、本轮变更(2026-08-11)

1. **天鹅第一颗换碟**:Sons of Kemet 从《Your Queen Is a Reptile》/ My Queen Is Harriet Tubman → **《Burn》(2013) / Inner Babylon**。鼓手随之变成 **Seb Rochford + Tom Skinner**(全碟双鼓,无逐轨例外)。
2. **天鹅八首的卡片第一行换成 cc 写的那版**,北斗七首的「鼓的处境」同步更新(⚠️ 北斗那七条目前**混音台里没有地方显示**,只在本文档里——要不要上页面待定)。
3. **天鹅表删掉「来源」列** —— 八首平等,不再按「在不在那 20 张里」区分。
4. **Jesup Wagon 改用整轨源 + 跳到高潮**,详见第六节。
5. **点别的星会打断当前播放**(之前两个音源元素可能叠着响)。
6. **天鹅视图的卡片改成以「曲目」为标题**,专辑退到副行。之前卡片报的是碟名(Burn),而 playlist 和右下角播放条报的是曲名(Inner Babylon)——页面自己内部就不一致。天鹅这一版是按**曲子**挑的,单位就该是曲子;星轨和北斗的单位是年度专辑,那两个视图仍以碟名为题。
7. **开场曲换成 2025 届《Breaking Stretch》/ Five Suns**。它走 iTunes 预览:实测点门到出声 253ms、有 CORS(脉动是真频谱)、不依赖网易云。原来的 Jesup Wagon 因为改走整轨源,开场要等好几 MB 下完。
8. **整轨源不再做假脉动**。网易云外链没有 CORS(`fetch` 直接 TypeError,已实测),分析器读不到波形,原来用 112 BPM 的合成正弦顶上——那就是"这颗星一直在闪"。现在改成不动。带控制组量过:整轨源那颗半径波动 **0%**,iTunes 那颗 **11.9%**。
9. **鼓手连线改画整条链**。原来只画「以当前专辑为端点」的那一段,所以悬停 Breaking Stretch 时 Historicity–Accelerando 那段不画,看上去像"明明也是他打的却没连线"。
10. **Data Lords 接上音源**。之前标着哑星,其实网易云有全碟(fee 0)。走整轨源,从高潮点前 5 秒进(高潮点 60.5 秒 → 起播 55.5 秒),卡片上写明「Apple Music 上没有,但艺人并未拒绝流媒体」。**全库现在只剩 Road Shows Vol.1 一颗哑星**——那张还没定代表曲,定了就能接。
11. **两个星座的星都按真实视星等排大小**,且**星与线的占比对齐**,详见第三节。
12. **删掉「领衔者本人」标注**(三处:Carrington / Kendrick Scott / Makaya McCraven)。艺人行已经写着这个名字了,鼓手行再标一次是同一句话说两遍。
13. **卡片上清掉「跟音乐无关的话」**。规则:界面上每一行都得在讲这张唱片的音乐/鼓;榜单名次、发行渠道属于本文档,不属于卡片。
    - 删 Waiting Game 的「二十张里唯一一张鼓手领衔的年度专辑」(榜单名次)
    - 删 Data Lords 的「Apple Music 上没有,但艺人并未拒绝流媒体 —— 网易云有全碟」(发行渠道)
    - Road Shows 的 ✕ 改成「暂无音源」(那是点了没声时的**功能提示**,不是评论,留;但不讲渠道故事)
    - 保留的四条都在讲编制/鼓法:双鼓·三碟·合唱团与弦乐 / 两套鼓+大号+萨克斯,没有和声乐器 / 鼓手领衔·五重奏加了唱盘手 / 把现场打的鼓切碎再拼回去
14. **Waiting Game 的评论改成 cc 自己写的**:「力量与优雅的领队,用节奏把控着整张专辑的情绪走向。」PopMatters 那句不保留。
    ⚠️ 这一条**不是乐评人原话,是 cc 的**,所以没有出处标注。**借来的乐评原话仍是 7/23 张。**
15. **信息卡加「鼓手」抬头**,编制说明独立成行(不然 The Epic 的第三个名字 Leon Mobley 看着像第三位鼓手,他其实是打击乐)。

16. **2022(Jesup Wagon)点击慢 + 播放时闪烁 —— 查到的原因和改法(v33)**

    先量,再改。在 cc 自己的 Chrome 里,对同一个网易云整轨链接连发 5 次(2026-08-12):

    | 第几次 | 到 canplay |
    |---|---|
    | 1 | 3.2 秒无字节 → **10.4 秒报错** |
    | 2 | 239 ms |
    | 3 | 129 ms |
    | 4 | 269 ms |
    | 5 | 180 ms |

    紧接着换 Data Lords(同一端点、不同歌)是 243 ms —— 所以**贵的是这个端点在一个页面里的第一次,不是某一首歌**。

    这次冷启动落在谁头上,谁就出这两个症状:
    - **慢**:页面里 6 秒的兜底定时器还没到,声音就是出不来。本地按实测数值复刻,v32 第一声 **6376 ms**。
    - **闪**:6 秒一到就退回 iTunes 那 30 秒预览,`El` 从 au2 换成 au,频谱分析器接管 → 这颗星开始跟着频谱一涨一缩。而且**兜底定时器还会再点一次火**,把已经在放的预览从头重放 —— 测到那颗星的半径在第 6–8 秒突然缩回原大小(摆幅 55.7%)。

    改两处:
    - 开场那几秒,用一个一次性 `<audio>`(只要 metadata,不占 au2)替他挨掉那次冷启动,失败再补一次。等他点到 2022,连接已经是热的。
    - 退回只准发生一次(`settled` 闸),并且退回时把卡住的那几 MB 释放掉。

    同一条件下复测 v33:第一声 **439 ms**,走的是 au2(即真的从 77.5 秒高潮进,不是退回预览放开头),整段 15 秒半径摆幅 **0%**。

17. **v34:Jesup Wagon 退回 iTunes 预览,「高潮起点」这条需求作废**

    cc 试过 v33 之后的判断:体感还是不好,而且**段落根本没变**。后一点说明他那边一直在走退回路径 ——
    真正响的是 iTunes 那 30 秒预览,77.5 秒的高潮点从来没生效过。

    所以砍掉:Jesup Wagon 的 `raw` / `at` 删除,只留 iTunes 预览。第一声 **411 ms**。

    连带作废的:**iTunes 预览一共就 30 秒,段落是 Apple 切好的,选不了。**
    "取网易云高潮点前 5 秒"这个做法,只在整轨源上成立;现在整轨源只剩 Data Lords 一首。

    **Data Lords 留着网易云** —— 查过 iTunes Search API(2026-08-12,`term=Maria Schneider Data Lords`,
    song 和 album 两种 entity):**没有这张专辑**。要么走网易云,要么这颗星是哑的。开场预热现在预热的就是它。

18. **为什么之前 snare_dial_v5 的 Spotify 能放整首**

    查过那个原型的源码:里面是 `https://open.spotify.com/embed/track/<id>` 的 **iframe**,
    没有 `<audio>`、也没有 Web Playback SDK。

    也就是说,放音的不是我们的播放器,是 Spotify 自己的播放器跑在 iframe 里,
    用的是**打开这个页面的人自己的 Spotify 登录态**:Premium 账号 → 整首;没登录/免费 → 还是 30 秒。

    代价:iframe 里是 Spotify 的界面,拿不到音频波形(星星就不能跟着频谱跳),
    也控制不了它长什么样。这是一个真选项,但要用它,星的脉动那套就得换个做法。

---

## 一、星轨 · 全部 20 张

★ = 北斗七首(cc 用耳朵挑的) · △ = 天鹅座第八颗(旧标记,已被下面第三节取代)

| 届 | 发行 | 专辑 | 艺人 | 代表曲 | 鼓手(生年) | 跨榜 | |
|---|---|---|---|---|---|---|---|
| 2006 | 2006 | Time Lines | Andrew Hill | Time Lines | Eric McPherson 1970 | 1 | |
| 2007 | 2006 | Sound Grammar | Ornette Coleman | Sleep Talking | Denardo Coleman 1956 | 2 | |
| 2008 | 2007 | Sky Blue | Maria Schneider | Cerulean Skies | Clarence Penn 1968 | 2 | |
| 2009 | 2008 | Road Shows, Vol. 1 | Sonny Rollins | — | Roy Haynes 1925–2024 / Al Foster 1943–2025 / Steve Jordan 1957 / Perry Wilson(生年不详) | 2 | **Apple Music 无** |
| 2010 | 2009 | Historicity | Vijay Iyer | Historicity | Marcus Gilmore 1986 | 2 | |
| **2011** | 2010 | **Ten** | Jason Moran | Crepuscule With Nellie | Nasheet Waits 1971 | 2 | **★ 摇光** |
| **2012** | 2012 | **Accelerando** | Vijay Iyer | Human Nature (Trio Extension) | Marcus Gilmore 1986 | 2 | **★ 开阳** |
| 2013 | 2013 | Without a Net | Wayne Shorter | Orbits | Brian Blade 1970 | 2 | |
| 2014 | 2013 | WomanChild | Cécile McLorin Salvant | WomanChild | Herlin Riley 1957 | 1 | |
| 2015 | 2015 | Bird Calls | Rudresh Mahanthappa | On the DL | Rudy Royston(约 1970–71,未确认) | 2 | |
| **2016** | 2015 | **The Epic** | Kamasi Washington | Change of the Guard | Tony Austin(生年不详)/ Ronald Bruner Jr. 1982 / Leon Mobley 打击乐 | 1 | **★ 玉衡** · 双鼓 |
| 2017 | 2016 | America's National Parks | Wadada Leo Smith | Yellowstone | Pheeroan akLaff 1955 | 1 | |
| 2018 | 2017 | Dreams and Daggers | Cécile McLorin Salvant | Devil May Care | Lawrence Leathers 1981–2019 | 1 | |
| 2019 | 2018 | Emanon | Wayne Shorter | Pegasus | Brian Blade 1970 | **3** | **天鹅 · Deneb** |
| **2020** | 2019 | **Waiting Game** | Terri Lyne Carrington & Social Science | Bells (Ring Loudly) | **Terri Lyne Carrington 1965(领衔者本人)** | 1 | **★ 天权** · 唯一鼓手领衔 |
| 2021 | 2020 | Data Lords | Maria Schneider | — | Johnathan Blake 1976 | **3** | **Apple Music 无** |
| **2022** | 2021 | **Jesup Wagon** | James Brandon Lewis | Jesup Wagon | Chad Taylor 1973 | 2 | **★ 天玑** |
| **2023** | 2022 | **Amaryllis** | Mary Halvorson | Night Shift | Tomas Fujiwara 1977 | 2 | **★ 天璇** |
| 2024 | 2024 | The Sky Will Still Be There Tomorrow | Charles Lloyd | Defiant, Tender Warrior | Brian Blade 1970 | 1 | |
| **2025** | 2024 | **Breaking Stretch** | Patricia Brennan | Five Suns | Marcus Gilmore 1986 + Mauricio Herrera 打击乐 | 2 | **★ 天枢** |

**跨榜列** = 有几个榜同时认可,决定星的亮度:
**3** = DownBeat + Davis 第一 + 格莱美获奖(Emanon、Data Lords)
**2** = DownBeat + Davis 第一(11 张) · **1** = 只有 DownBeat(7 张)

---

## 二、北斗 · 七首

斗柄 → 斗魁,**正好是编年**。

| 斗宿        | 届    | 专辑               | 鼓手                                  | 鼓的处境                |
| --------- | ---- | ---------------- | ----------------------------------- | ------------------- |
| 摇光 Alkaid | 2011 | Ten              | Nasheet Waits                       | **复杂的复合节奏**和微妙的音色纹理 |
| 开阳 Mizar  | 2012 | Accelerando      | Marcus Gilmore                      | 与舞蹈对话               |
| 玉衡 Alioth | 2016 | The Epic         | **Ronald Bruner Jr. & Tony Austin** | 双重引擎，史诗律动           |
| 天权 Megrez | 2020 | Waiting Game     | Terri Lyne Carrington               | 力与美结合，极具创意的领袖       |
| 天玑 Phecda | 2022 | Jesup Wagon      | Chad Taylor                         | 无和声乐器的 groove       |
| 天璇 Merak  | 2023 | Amaryllis        | Tomas Fujiwara                      | 将节奏的“中心”铺展开来        |
| 天枢 Dubhe  | 2025 | Breaking Stretch | Marcus Gilmore + Herrera            | 鼓与打击乐交融             |

⚠️ 勺子**不封口**(天枢–天权那一边是断的),依 北斗.png 参考图。
⚠️ 这七首**不是数据算出来的,是我们挑的**——这本身是主题的一部分。

---

## 三、天鹅座 · 骨架 8(2026-08-09 定稿)

**选择依据:鼓。** 不是榜单算出来的。八首平等,不按「在不在那 20 张里」区分——那是榜单的视角,不是耳朵的视角。

| 槽位         | 曲目                            | 专辑(发行年)                   | 艺人                    | 鼓手                                | 视星等            | 卡片第一行             |
| ---------- | ----------------------------- | ------------------------- | --------------------- | --------------------------------- | ---------------- | ----------------- |
| Albireo(喙) | **Inner Babylon**             | **Burn (2013)**           | Sons of Kemet         | **Seb Rochford + Tom Skinner**    | **3.21**   | 双鼓 · 宣言的节奏        |
| η          | Human Nature (Trio Extension) | Accelerando (2012)        | Vijay Iyer            | Marcus Gilmore                    | **3.889**  | 精准而富有张力           |
| Sadr(胸)    | Mocean                        | A Wall Becomes A Bridge (2019) | Kendrick Scott Oracle | Kendrick Scott(领衔)           | **2.23**   | 内省克制,流畅且细腻,灵巧而厚重  |
| Deneb(尾)   | Pegasus                       | Emanon (2018)             | Wayne Shorter         | Brian Blade                       | **1.25**   | 刚柔并进,用鼓声在唱歌       |
| Gienah(翼)  | Dream Another                 | In These Times (2022)     | Makaya McCraven       | Makaya McCraven(领衔)          | **2.480**  | 节拍科学家,即兴的录音再拼贴和创作 |
| ζ          | Jesup Wagon                   | Jesup Wagon (2021)        | James Brandon Lewis   | Chad Taylor                       | **3.26**   | 自由即兴中的色彩大师,也擅长拇指琴 |
| δ          | Night Shift                   | Amaryllis (2022)          | Mary Halvorson        | Tomas Fujiwara                    | **2.87**   | 用管弦乐骨架构建架子鼓律动     |
| ι          | Five Suns                     | Breaking Stretch (2024)   | Patricia Brennan      | Marcus Gilmore + Mauricio Herrera | **3.76**   | 鼓 + 打击乐双层         |

### 星的大小:两个星座一套规则(2026-08-11 定)

**问题**:天鹅原来沿用星轨的 `lit`(跨榜数),结果 Data Lords 靠三榜加持成了全场最大(它既不在骨架里、当时还放不出声),而 Sadr(胸口,四条线交汇处)掉到倒数第六——十三颗背景星排在骨架星前面。北斗也一样:**背景最大的 4.07 比骨架最小的 2.32 还大**,玉衡和天权融进背景里。榜单的尺子量不了鼓。

**规则**(两个星座通用):

| | 依据 |
|---|---|
| **骨架** | **真实视星等**(维基各恒星条目信息框,V 波段) |
| **背景** | 跨榜档 3/2/1,再让透视深度浮动 ±12%(同档一模一样会像盖章) |

**关键一条:骨架半径按「该视图连线中位长的比例」给,不是绝对值** —— 高 4.6% / 低 3.1%。这样两个星座的「星与线的占比」一致,天鹅不会比北斗胖一圈。

改前后:

| | 骨架半径 | 背景半径 | 星半径/连线长 | 骨架最小 ÷ 背景最大 |
|---|---|---|---|---|
| 北斗 · 改前 | 2.32 – 4.90 | 1.55 – 4.07 | 2.51% | **0.57x**(被压住) |
| 北斗 · 改后 | **4.24 – 6.29** | 1.85 – 2.90 | 4.33% | **1.46x** |
| 天鹅 · 改前 | 6.40 – 11.00 | 2.75 – 4.87 | **5.56%**(胖一倍) | 1.31x |
| 天鹅 · 改后 | **4.56 – 6.77** | 1.92 – 3.50 | **3.68%** | **1.30x** |

**星等取值**(全部来自维基各恒星条目信息框):

- 北斗:玉衡 Alioth **1.77** · 天枢 Dubhe **1.79** · 摇光 Alkaid **1.86** · 开阳 Mizar **2.04** · 天璇 Merak **2.37** · 天玑 Phecda **2.438** · 天权 Megrez **3.312**
  (天璇要查 Beta Ursae Majoris,Merak 是消歧义页。天权本来就是北斗里最暗的一颗。)
- 天鹅:Deneb **1.25** · Sadr **2.23** · Gienah **2.480** · δ **2.87** · Albireo **3.21** · ζ **3.26** · ι² **3.76** · η **3.889**
  (ι Cygni 是消歧义页,骨架用较亮的 **ι²** 3.76;ι¹ 是 5.73。)

**为什么用真实星等**:坐标本来就是真实星表 RA/Dec 投影的——大小用同一份数据,层次不是我们编的,是天上的。这跟本节末尾那句"这些不对称是天上本来就有的,不是我们加的"是同一条原则。

⚠️ 骨架的大小**不受透视缩放影响**(代码里除掉了 sc)。深度在星座里能差近一倍,不抵消掉会把刚排好的层次重新打乱;深度仍然体现在**位置**上。
⚠️ **星轨视图不动** —— 那 20 颗本来就是主体,没有骨架/背景之分,仍按 `lit`。

**被换下去的三首**:Ten、The Epic、Waiting Game。它们退回天鹅的背景星,**在北斗里的位置不变**(仍是摇光 / 玉衡 / 天权)。

**坐标来自真实星表(RA/Dec 投影),整体倾 20°。** 头臂是尾臂的 2.5 倍、两翼一高一低、横杆不垂直于长轴——**这些不对称是天上本来就有的,不是我们加的。**

### 核实记录

- ✅ **Inner Babylon** = 《Burn》(Naim Records, 2013-09-09)**第 3 轨**,5:20。编制:Shabaka Hutchings 萨克斯/单簧管 + Oren Marshall 大号 + **Seb Rochford 与 Tom Skinner 双鼓**;Dave Okumu 的吉他只在第 4、5 轨,所以**这一轨仍然没有和声乐器**。[Wikipedia](https://en.wikipedia.org/wiki/Burn_(Sons_of_Kemet_album))
- ⛔️ *(2026-08-11 作废)* 原第一位是《Your Queen Is a Reptile》的 My Queen Is Harriet Tubman,cc 改成 Burn 的 Inner Babylon。那张的逐轨鼓手争议(Skinner 在不在第 3 轨)随之作废——Burn 是全碟双鼓,没有逐轨例外。
- ✅ **Mocean** = 《A Wall Becomes A Bridge》(Blue Note, 2019-04-05)**第 2 轨**,Apple 上曲名为 `>>>>>>>>>>>Mocean`。Taylor Eigsti 作曲,制作人 Derrick Hodge。乐队:Mike Moreno 吉他 / Taylor Eigsti 钢琴 / John Ellis 管乐 / Joe Sanders 贝斯 / **Jahi Sundance 唱盘**。[Blue Note 官方](https://www.bluenote.com/kendrick-scott-oracle-to-release-inspiring-new-album-a-wall-becomes-a-bridge-out-april-5/)
- ✅ **Dream Another** = 《In These Times》(International Anthem / Nonesuch / XL, 2022-09-23)**第 4 轨**,2022-07-19 作为第二支单曲发行。[Nonesuch](https://www.nonesuch.com/journal/makaya-mccraven-releases-new-single-video-dream-another-these-times-2022-07-19) · [Wikipedia](https://en.wikipedia.org/wiki/In_These_Times_(Makaya_McCraven_album))
- ✅ **Locked in a Basement** = HEERNT 2006 年首张专辑的标题曲。**HEERNT 正是 cc 口味靶心里的那个 Heernt。**(备选,未进骨架)
- ❌ **Jack DeJohnette《Tribal Dance》查不到。** 搜到的同名曲是印尼吉他手 Tohpati 的。DeJohnette 有《Dancing with Nature Spirits》(ECM, 1996)主题相近但曲目对不上。**仍需 cc 说明在哪张上听到的。**

### 更正记录(2026-08-09)

| 原来写的 | 实际 | 依据 |
|---|---|---|
| Sons of Kemet 双鼓 = **Tom Skinner / Eddie Hick** | 第 3 轨是 **Eddie Hick + Moses Boyd** | [Wikipedia 人员表](https://en.wikipedia.org/wiki/Your_Queen_Is_a_Reptile):Seb Rochford 鼓(**除第 3、7 轨**)、Tom Skinner 鼓、Moses Boyd 鼓(**第 3、7、8 轨**)、Eddie Hick 鼓(**第 3、7 轨**) |
| 曲目 **My Queen Is Ada Eastman**(旧笔记块里) | **My Queen Is Harriet Tubman** | 骨架定稿表为准;Ada Eastman 是第 1 轨,Harriet Tubman 是第 3 轨,两首都真实存在 |
| Marcus Gilmore **1983**(旧笔记块里) | **1986** | [SmallsLIVE](https://www.smallslive.com/artists/289-marcus-gilmore/) · [Wikipedia](https://en.wikipedia.org/wiki/Marcus_Gilmore) |
| Kendrick Scott 代表作《Corridors》(2023) | Mocean 不在那张上 | 见上方核实记录 |



---

## 四、鼓手档案

> 以下多数是 cc 的听感笔记,**没有逐条核实**。标 ✅ 的是这轮查过的。

### 已在视图里的

**Brian Blade** 1970 ✅ ·《Emanon》
刚柔并济。兼具爆炸性的力量与细腻的抒情性,"**不抢戏**"却**包容万物**——鼓像一张大网,轻松兜住所有不同个性的音符。极善用**音色层次(shading)**和**缓慢积累的张力**驱动音乐,让 Wayne Shorter 的经典曲目焕发新生。令人联想到 Tony Williams。自己的团:Brian Blade Fellowship。
*搭档 Wayne Shorter(已故)*:萨克斯、作曲,20 世纪最具影响力的爵士音乐家之一。从 Art Blakey 的 Jazz Messengers,到 Miles Davis 第二伟大五重奏,再到 Weather Report。《Emanon》是他晚年集大成之作。

**Marcus Gilmore** 1986 ✅ ·《Accelerando》《Breaking Stretch》《Historicity》
承袭传奇血脉的现代律动革新者。演奏**敏感而富有旋律性**,把传统爵士鼓语汇与全球打击乐元素融合。
- 鼓王 **Roy Haynes 的孙子**,10 岁时祖父送了他第一套鼓
- 毕业于 LaGuardia 音乐艺术高中,拿过茱莉亚与曼哈顿音乐学院全额奖学金
- 16 岁起职业巡演。合作过 Chick Corea、Vijay Iyer、Pharoah Sanders、Pat Metheny、Robert Glasper、Flying Lotus、Thundercat
- Vijay Iyer 三重奏长期鼓手
- ⚠️ *未核实*:首张个人专辑《Journey to the New: Live at the Village Vanguard》被《纽约时报》评为 2025 年度最佳爵士专辑第一
*搭档 Vijay Iyer*:美籍印裔钢琴家、作曲家,曾是物理学高材生。音乐根植于南亚、西非节奏传统与 60–70 年代非裔美国创意音乐运动。**节奏强劲、旋律优美**。

**Terri Lyne Carrington** 1965 ·《Waiting Game》
力与美结合。鼓技精湛且充满律动感,标志性放克风格被广泛模仿;同时是极具创意的乐队领袖和制作人。另见《The Mosaic Project》。
**20 张里唯一一张鼓手领衔的年度专辑。**

**Chad Taylor** 1973 ·《Jesup Wagon》
自由即兴中的色彩大师。不仅是出色的爵士鼓手,还擅长非洲拇指琴(Mbira),为音乐添入独特的打击乐色彩和实验性。另见《Myths and Morals》。
*搭档 James Brandon Lewis* 1983,萨克斯。

**Nasheet Waits** 1971 ·《Ten》
平衡传统与现代的节奏大师。传奇鼓手 Freddie Waits 之子,演奏以**复杂的复合节奏**和**微妙的音色纹理**著称,既能精准保持时间,又能以爆发性的填充打破常规。另见《Between Nothingness and Infinity》。

**Mauricio Herrera** 1972 ·《Breaking Stretch》打击乐
植根于古巴的拉丁打击乐专家。7 岁学小提琴,14 岁转打击乐,纽约非洲-古巴爵士领域顶尖打击乐手之一,擅长康加。
*搭档 Patricia Brennan*:墨西哥裔美籍颤音琴、马林巴演奏家、作曲家。正在重新定义颤音琴在当代音乐中的角色,融合**精准槌法、弓拉琴键、预制音色**。

**Ronald Bruner Jr.** 1982 + **Tony Austin** ·《The Epic》双鼓
Bruner:力量与速度的化身,2 岁习鼓,从爵士、融合横跨到朋克摇滚,爆炸性能量、清晰的 articulation。
Austin:洛杉矶音乐场景核心鼓手,与 Kamasi Washington 长期合作,稳健、富律动。⚠️ *生年冲突*:星轨表记"生年不详",旧笔记块写 1978,来源不明,未采用。

**Seb Rochford + Tom Skinner** ·《Burn》双鼓 ✅
两套鼓 + 大号 + 萨克斯,**没有和声乐器**。《Burn》(2013)是 Sons of Kemet 首张,伦敦那一拨的起点。乐队已解散(不影响推荐)。
⚠️ 两位生年都没查到,留空。

**Kendrick Scott** ·《A Wall Becomes A Bridge》领衔 ✅
cc 听感:*大提琴是节奏,鼓成了主旋律,sax 是变奏了。*

**Makaya McCraven** ·《In These Times》领衔 ✅
把现场打的鼓切碎再拼回去,"beat scientist",**鼓是作曲工具不是伴奏**。cc 听感:*鼓更抢角色了,鼓也更碎更丰富了。*

**Johnathan Blake** 1976 ·《Data Lords》
(档案空着,待补)

---

## 五、备选池(听过、有想法,尚未进任何视图)

| 鼓手 | 专辑 / 曲目 | 为什么留着 | cc 的判断 |
|---|---|---|---|
| **Mark Guiliana** | HEERNT《Locked in a Basement》同名曲(Razdaz, 2006) | 三重奏:Guiliana 鼓 / Neal Persiani 电贝斯 / Zac Colwell 萨克斯 + Juno-60。**cc 口味靶心** | ✅ 已核实。[AllAboutJazz](https://www.allaboutjazz.com/locked-in-a-basement-mark-guiliana-razdaz-recordz-review-by-paul-olson) · [Discogs](https://www.discogs.com/release/886566-Heernt-Locked-In-A-Basement) |
| **Tyshawn Sorey** | Mesmerism (2022) / Enchantment | 自己领衔。DownBeat Drums 2023 第三、2024 第二,**从没夺冠,专辑也从没进前一**——"鼓打得很棒但没拿过 top1"的标本 | ❌ 辨识度不高,听感传统 jazz |
| **Aaron Parks** | Little Big (2018) / Kid,鼓 Tommy Crane | **靶心正中**——Parks 就是 Heernt 那条线,和 Blade 的 Fellowship 同源 | 待定 |
| **Femi Koleoso** | Ezra Collective《Where I'm Meant to Be》(2022) / Victory Dance | 鼓手当队长,拿了 Mercury Prize——**爵士乐队第一次拿** | 待定 |
| **JD Beck** | DOMi & JD Beck《NOT TiGHT》(2022) / SMiLE | 两个二十出头的人把 Blue Note 签下来了。手速和分解是这几年最被讨论的鼓 | 待定 |
| **Chris Dave** | Robert Glasper《Black Radio》(2012) / Afro Blue | "垮着打、拍点故意错位",过去十五年被抄得最多的鼓语言 | 待定 |
| **Oscar Seaton** | Terence Blanchard《Absence》(2021) 同名曲 | 25th Hour 配乐那条线 | 律动感很强 |
| **Jack DeJohnette** | 曲目待定(《Tribal Dance》查无) | 钢琴基础、旋律鼓,服务三代知名乐队。**1942–2025**,2025 年 10 月离世 ✅ | 需 cc 指认曲目 |

DeJohnette 那条另见 `drums_vs_album.md`:**他被同一批乐评人选了 7 次年度鼓手,而在他们选出的 20 张年度专辑里一次都没出现过。**

---

## 六、音源

**天鹅骨架 8 首全部可播。** 但从 2026-08-11 起分成两类:

| 类型 | 用在哪 | 取什么 | 脉动 |
|---|---|---|---|
| **iTunes 30 秒预览** | 其余 7 首 + 星轨 18 张 | Apple 定的那 30 秒,位置改不了 | **真频谱**(有 CORS,接得进 Web Audio) |
| **整轨 + 跳到高潮** | **Jesup Wagon** | 网易云外链整轨,从高潮点**前 5 秒**进,放满 30 秒收 | **合成正弦**(无 CORS,接进分析器会出静音,只能绕开) |

**为什么 Jesup Wagon 要换**:iTunes 那 30 秒截的是开头,cc 要高潮那段。而 iTunes 预览是一个**独立的 30 秒文件**,没有偏移参数——想换位置只能换成整轨源再 seek。

**网易云高潮点接口**(2026-08-11 验通):
`GET /api/song/chorus?ids=[songId]` → `{chorus:[{startTime, endTime}]}`,单位毫秒。
- Jesup Wagon(id 1832319407):startTime **82500** → 起播 77.5 秒
- Data Lords(id 2101418922):startTime 60500 → 起播 55.5 秒(**还没接**)

⚠️ 参数必须写成 `ids=[...]`;写 `id=` 或 `songId=` 都返回「参数错误」。

**跨域实测**(在 example.com 这种无 CSP 的页面上,同时跑 iTunes 作对照组):
外链能加载、能 seek 到 77.5 秒。⚠️ 只在 cc 这台机器、这条网络上验过;**别人的浏览器、海外网络没验**。

**兜底**:整轨源拿不到时自动退回该曲的 iTunes 预览,不让这颗星哑掉。另外 seek 完会**回读确认**——源不支持 Range 时 seek 会被静默夹回 0(实测桩里就中过一次),这时按实际起点算进度,不谎报。

**还没接整轨的两张**(它们只在星轨里,现在仍是哑的):

| 专辑 | Apple Music | 网易云 |
|---|---|---|
| 2009 届《Road Shows, Vol. 1》 | 查无(只有 Vol.3 / Vol.4) | 有,专辑 id 1992228 |
| 2021 届《Data Lords》 | 查无 | 有,song id 2101418922,fee 0 |

## 七、真正还没决的

1. **《Tribal Dance》是哪张** —— 需要 cc 说在哪听到的。
2. **Road Shows Vol.1 / Data Lords 要不要也接整轨** —— 路已经趟通了(见第六节),接了这两颗星就能响,代价是脉动是合成的。
3. ~~Jesup Wagon 是开场曲~~ **已解决**:开场改成 2025 届 Breaking Stretch,不再依赖网易云。
4. **天鹅视图里非骨架的 15 颗背景星,信息卡第一行显示什么** —— 现在是空的。
5. **竖屏星座偏右** —— 三个视图在设计坐标里中心不一致(星轨 517 / 北斗 504 / 天鹅 605),按并集居中是折中值。两条修法待选:数据层各自归一化 / viewBox 跟着视图走。
6. **信息卡封面 56px 够不够看** —— cc 要先看真图再判断。
7. 每张的**乐评人写鼓的原话**目前只挂了 9 条(借来的,不是我们写的),其余留空。
8. Rudy Royston / Tony Austin / Perry Wilson / Mauricio Herrera / Seb Rochford / Tom Skinner **生年查不到**,页面上留白。
9. 《Dreams and Daggers》AllMusic credits 未单列 Salvant 的乐器行,按人声处理属推断。
