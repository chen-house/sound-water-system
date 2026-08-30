# 展现形式调研 · 虚拟设备 / 手势 / 空间音频 / 同类作品盘点(v1)

> 五路并行调研的汇总,服务于第二段节目(1976—2026 平行水文)的形式决策。
> 出处标在内容旁;标"未核实"的地方就是没核到,别当数。
> 调研时间:2026-07-05

---

## 〇、最重要的三个发现(先说结论)

**1. "多轨 fader 讲故事"是空白地带。** 专门搜了"用混音台/channel strip 承载叙事内容"的先例——**没有找到**。最接近的只有 Google《Inside Abbey Road》(2015)里一个混音台小游戏(给你分轨推子,调 mix 打分,混音台只是关卡道具不承载故事;insideabbeyroad.withgoogle.com),和《In Bb 2.0》(2009,inbflat.net,20 个 YouTube 视频让用户自己当混音师,无叙事线)。"推子推起来,一段音乐史浮出来"——**没人做过**。这对我们是好消息:混音台方案不只是保底,它本身就有首创性。

**2. D(dub send)不是升级项,是白送的。** 原以为效果 send 会加复杂度,调研结果恰好相反:Tone.js 的 `FeedbackDelay` / `Reverb` / `CrossFade` 都是一行代码级别(tonejs.github.io;MDN 的 DelayNode 反馈环是文档级标准写法)。**D 的技术难度 ≈ 容易,比 C(双转盘)还简单。**"太复杂就保 C"这个担心可以放下——C 和 D 都在容易档,可以都要。

**3. 真正的墙不是技术,是版权/音源。** 这是全场唯一的红灯,必须现在正视:
- Spotify iframe embed **没有音量接口**(官方 iFrame API 只有 play/pause/seek;community.spotify.com 多帖确认)——**fader 推不动 Spotify**。第一件作品用 Spotify embed 是"点开听",混音台要的是"程序控制音量叠加",这条路线根本不通。
- Spotify 30 秒 preview_url 对新应用**已于 2024-11 废弃**(developer.spotify.com 官方公告)。
- 自托管 30 秒片段:**"30 秒合理使用"是讹传**,法律上不存在这条规则(studentpress.org/nspa),自托管商业录音有真实侵权风险。
- 可行出路:**(a) SoundCloud Widget API 有 setVolume(0-100)**(developers.soundcloud.com),是"第三方音源+可控音量"唯一现实选项,但移动端表现未核实;**(b) 自制/风格化音频**(自己弹/请人弹/AI 生成"风格示意"短循环),法律最干净、技术最顺;**(c) YouTube iframe 有 setVolume 但 iOS 上无效**(developers.google.com;Apple 不许网页改媒体元素音量)。
- **这个决定比选形式更优先**:音源不定,混音台就是个哑巴面板。

---

## 一、同类作品盘点(别人怎么做的)

### 1a. 音乐历史/流派全景类

| 作品                                   | 形式                                                 | 核心动作           | 得失                      | 现状                                                                                                  |
| ------------------------------------ | -------------------------------------------------- | -------------- | ----------------------- | --------------------------------------------------------------------------------------------------- |
| Every Noise at Once (everynoise.com) | 6000+ 流派按声音特征铺成二维文字云                               | 点流派名→播代表片段     | 全宇宙感无人能及;败于平台依赖         | **已冻结**:维护者 Glenn McDonald 2023-12 被 Spotify 裁员失去数据管线,现为静态存档(TechCrunch 2024-02 报道)                 |
| Musicmap (musicmap.info)             | 1870—2016 流派家谱画成"城市天际线",比利时人 Kwinten Crauwels 十年手工 | 缩放下钻,点流派看简介+歌单 | 编辑深度最强;败于不可持续,数据止于 2016 | 在线                                                                                                  |
| Radio Garden (radio.garden)          | 3D 地球仪,4 万+ 电台钉在真实地理位置                             | 转地球对准城市即听直播    | 零学习成本、具身感天花板;无历史叙事层     | 在线,活跃维护                                                                                             |
| The Pudding 音乐互动文                    | 滚动叙事+图表+短音频                                        | 滚动             | 配方=尖锐小论点+滚动+内嵌短音频,不做大全景 | 在线;2025-04 的 Music DNA(pudding.cool/2025/04/music-dna)是"采样谱系叙事"最新范本,和我们第 13 节"渗透"主题直接相关,**值得亲自看一遍** |
| Poolsuite (poolsuite.net)            | 复古 Mac OS 拟物"永夏电台"                                 | 播放器本身即交互       | 氛围+拟物人格立得住;2025-06 出 V3 | 在线,活跃                                                                                               |

**规律(五个案例对照)**:数据驱动全景死于平台依赖(Every Noise),人工大全景死于不可持续(Musicmap);**活得久的是"轻数据、重氛围、具身交互"**(Radio Garden、Poolsuite)。叙事类(Pudding)靠尖锐小切口而非大而全。我们的"电台+设备拟物"路线恰好站在幸存者这一侧。

### 1b. 虚拟音乐设备类

| 作品 | 形式 | 对我们的参考点 | 现状 |
|---|---|---|---|
| Ableton **Learning Music / Learning Synths**(learningmusic.ableton.com / learningsynths.ableton.com) | 网页交互教程,边玩边学,终点是迷你 DAW/合成器 Playground | "逐步解锁控件"的教学节奏被公认最佳——**串场词逐段解锁 fader** 可以借这个思路 | 在线 |
| Chrome Music Lab (musiclab.chromeexperiments.com) | 13 个音乐小实验 | Song Maker/Rhythm 的零门槛网格;刻意去专业化,和我们拟物方向相反 | 在线 |
| Incredibox (incredibox.com) | 拖音色图标给角色,组合出 beatbox | **"叠加=快乐"的交互被 1 亿人验证过**(官方 press 页:免费 demo 超 1.06 亿玩家)——它本质就是"多轨同时在场",是混音台方案的民间旁证 | 在线 |
| iO-808 (io808.com) | 像素级 TR-808 网页复刻,声音全部实时合成 | 拟物复刻的工艺标杆;开源可研究(github.com/vincentriemer/io-808) | 在线,开源 |
| YouDJ (you.dj) / Transitions DJ (transitions.dj) | 完整网页双转盘+crossfader+EQ+效果 | **C 方案的现成参照物**,证明双盘网页完全可行;但它们是工具不是叙事 | 在线 |
| Webamp (webamp.org) | 像素级 Winamp 复刻,被 Internet Archive 官方采用 | "软件拟物→文化保存"的最强范本 | 在线,活跃 |
| Splice Beatmaker / Chppr (chppr.app) | 网页 MPC 风采样 pad | E 里"采样 pad"的现成参照 | 在线 |
| Stem Player 网页生态 (stemplayer-js.com 等) | 四分轨滑条混音组件 | 证明"分轨推子"组件已成熟,**但无人拿它讲故事**(再次确认空白) | 在线 |
| OP-1 网页致敬(CodePen 一批 + op1kenobi) | 多为 CSS 画得像、能发声的少 | Teenage Engineering 审美在网页有人试,无产品级作品 | 零散 |

---

## 二、技术与新交互评估(每项:结论 + 难度)

> 难度均按"非工程师 + Claude Code 开发"口径。来源见各行。

### 基础层(全绿)

| 项 | 结论 | 难度 |
|---|---|---|
| 多轨同步 + fader(A/B 地基) | Tone.js 15.x 在维护(npm;GitHub 2025-2026 有活动),`Player`+`Transport` 采样级同步,`Channel` 自带 volume/pan/solo/mute——**channel strip 几乎是它的原生词汇** | **容易** |
| D:dub send/return | `Tone.FeedbackDelay`/`Tone.Reverb` 一行;裸 Web Audio 的 DelayNode 反馈环也是 MDN 文档级写法 | **容易** |
| C:crossfade | `Tone.CrossFade` 等功率交叉渐变,设一个 0-1 的值 | **容易** |
| iOS/移动端 | 需"点一下开始"解锁 AudioContext(所有浏览器通行政策,MDN);多轨混音必须走 Web Audio 而非 `<audio>` 标签(iOS 限制,恰好我们本来就走) | **中等**(固定套路,留真机测试时间) |

### E 拆开评(不能笼统说"多模态难")

| 项 | 结论 | 难度 |
|---|---|---|
| 采样 pad(MPC 感) | 就是"按键→播短样本+亮灯",Splice/Sampulator/Chppr 都是先例 | **容易** |
| 空间音频(耳机方位感) | 原生 `PannerNode` 设 `panningModel:'hrtf'` 即可,MDN 有官方 demo;左右+距离感可靠,前后上下因人而异。Google 的 Omnitone/Resonance 库**已停更/归档**(GitHub:Resonance 2026-04 归档)——**别押,用原生就够**。先例:Google《Inside Music》(2017,把一首歌的分轨环绕在你四周,开源,experiments.withgoogle.com/webvr/inside-music)——**和"多条流环绕在场"的气质非常近,值得看** | **容易~中等** |
| 麦克风:音量检测 | getUserMedia + AnalyserNode,约 20 行 | **容易** |
| 麦克风:音高检测(哼一句) | pitchy 库(McLeod 算法,在维护)可行;ml5 的 CREPE 已废,别用 | **中等** |
| 麦克风:节拍检测 / 哼唱匹配曲库 | 无鼓点信号节拍检测很不可靠;哼唱搜歌靠服务端大曲库(midomi 那种) | **中等偏难 / 不现实——放弃** |
| 手势(摄像头) | **成熟度超预期**。MediaPipe Hand Landmarker 官方 JS 包纯浏览器跑,21 个 3D 关键点实时(ai.google.dev 官方文档);先例:Google《Semi-Conductor》(2018,挥手指挥乐团,PoseNet+Tone.js,仍在线)、IBM Veremin(网页 theremin)、MediaPipe theremin 独立复盘(issledova.tel/posts/theremin)。theremin 式连续控制(手的 x/y→参数)一天出原型;坑在打磨:光线、抖动平滑、iOS 双重授权(dev.to 复盘)。**关键:独立艺术家的"挥手控音乐"知名网页作品——没找到。又一个空白。** | **原型容易,演出级中等** |
| WebMIDI(实体推子控网页) | Chrome/Edge/Firefox 可,**Safari 全版本明确拒绝**(caniuse 2026-05;Apple 以隐私为由)。做彩蛋可以,别当主交互 | **Chrome 容易/全兼容无解** |

---

## 三、把结论装回我们的 A—E

| 方案 | 调研后的重新定位 |
|---|---|
| A 混音台 | 地基,Tone.Channel 原生支持。**且"fader 叙事"无先例——A 本身就有首创性,不只是保底** |
| B 路由矩阵 | 技术只是节点连线(容易),难在视觉别做成炫技关系网。Pudding Music DNA 是内容侧参照 |
| C 双转盘 crossfader | 技术容易,YouDJ 等证明可行。**但注意:C 是"二选一渐变",A 是"多轨叠加"——表达"平行流动"其实 A 比 C 更贴**。C 适合做局部场景(如讲"采样/融合"某个交叉点时出现),不必是整体框架 |
| D dub send | **从"升级项"改判为"标配"**:技术白送,且 dub/echo 和 UK 那条流的血统直接呼应——一个旋钮讲一段历史 |
| E 多模态 | 拆开:**采样 pad=容易(讲 hip-hop 采样文化那段可用);空间音频=容易~中等(耳机彩蛋);手势=原型容易+题材空白,最有"新"的潜力;麦克风=音量可玩、音高慎用、节拍/哼唱匹配放弃** |

### 一个综合想象(不锁定,供发散)

设备不必同时全上——**"每条流自带它的设备"**:混音台是主控台(A+D 常驻);讲到 hip-hop 融合,台面上滑出一排 MPC pad;讲到 acid jazz/俱乐部,浮出 crossfader;讲到 spiritual,戴耳机进入空间音频的"环绕圣光";手势留给一个哇时刻(比如终章"你来指挥这片水")。这正好呼应第一件作品"每段独立设计形式呼应内容"的既有原则——只是把"每段一个版式"升级成"每段一件设备"。

### 落地顺序建议(按依赖关系,不是 KPI)

1. **先解决音源**(版权红灯,决定一切):自制风格循环 / SoundCloud / 混合方案——需要 cc 拍板
2. A+D 一起做(同一层技术,dub send 白送)
3. C 和采样 pad 作为"流专属设备"逐段加
4. 手势/空间音频原型各花一天试,行就留,不行就砍——成本低到值得赌

---

## 四、值得亲自打开看的 6 个(按优先级)

1. **Inside Music**(experiments.withgoogle.com/webvr/inside-music)——分轨环绕空间,气质最近
2. **Pudding Music DNA**(pudding.cool/2025/04/music-dna)——"采样谱系"叙事,内容侧同题
3. **iO-808**(io808.com)——拟物工艺标杆
4. **Learning Synths**(learningsynths.ableton.com)——"逐步解锁控件"的节奏
5. **Semi-Conductor**(semiconductor.withgoogle.com)——挥手控乐团,手势天花板长什么样
6. **In Bb 2.0**(inbflat.net)——最朴素的"用户当混音师",2009 年至今在线

---

## 附:主要来源

- 叙事/全景类:TechCrunch(Every Noise 冻结,2024-02)、musicmap.info、en.wikipedia.org/wiki/Radio_Garden、pudding.cool 各文、poolsuite.net
- 设备类:learningmusic/learningsynths.ableton.com、github.com/vincentriemer/io-808、you.dj、transitions.dj、webamp.org、incredibox.com/info/press、insideabbeyroad.withgoogle.com、inbflat.net、stemplayer-js.com
- 技术:developer.mozilla.org(Web Audio/DelayNode/ConvolverNode/Autoplay)、tonejs.github.io、npmjs.com/package/tone、caniuse.com/midi、developer.spotify.com(iFrame API + 2024-11 preview 废弃公告)、developers.soundcloud.com/docs/api/html5-widget、studentpress.org/nspa("30秒规则"讹传)
- 手势:ai.google.dev/edge/mediapipe(Hand Landmarker Web JS)、experiments.withgoogle.com/semi-conductor、github.com/vabarbosa/veremin、issledova.tel/posts/theremin、dev.to(MediaPipe 坑点复盘)
- 空间音频/麦克风:developer.mozilla.org(PannerNode HRTF)、github.com/GoogleChrome/omnitone(停更)、github.com/resonance-audio(已归档 2026-04)、experiments.withgoogle.com/webvr/inside-music、github.com/ianprime0509/pitchy
