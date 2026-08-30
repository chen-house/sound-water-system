# 第二段节目 · 决策记录(判断历史)

> 仿 PROJECT_MASTER"已被否的方向"的做法,给第二段(1976—2026 平行水文/混音台)单独立一份决策账。新窗口 Claude 先读这个,不要翻案。

## 2026-07-06 · 音频模式:定路线一

**决定**:混音台走**路线一**——播真实代表曲,一次一条为主,轨道切换用 crossfade 优雅过渡;"平行流动"靠视觉表达(多条 channel strip 同时在场、可随时切换),不靠多首真歌同时出声。

**理由(cc 原话要点)**:
1. 作品重心是**展现音乐发展过程**;路线二(可叠加自制 loop,用户亲手混出融合)虽好,但会把重心带偏到"音乐制作过程"
2. 保证作品不难产——先落地,效果好再考虑路线二

**路线二的处置**:不是否掉,是**放进 v2 储备**。触发条件:路线一上线且效果不错。

**连带结论(之前已论证,一并封存)**:
- 两首真歌同时播放 = 浆糊,音乐上无意义,不做
- D(dub send)技术白送,保留;C(crossfade)就是路线一的核心过渡动作
- "太复杂就保 C"的担心解除:C/D 都是容易档

## 2026-07-06 · 追加:fader 语义改判,"音量墙"拆除(cc 拍板)

**cc 原话**:"推起 B 直接触发 A stop 啊,你要从音量控制这里跳出来。"

**决定**:fader 的语义从"连续音量控制"改为**触发器**——推起 B 越过阈值 = B 上台、A 直接 stop。不追求真 crossfade 的音频渐变。

**连带效果(这一刀解开的东西)**:
- **Spotify embed 复活**:切换只需 play/pause/换曲,不需要音量接口——第一件作品的音源模式可以平移,SoundCloud 依赖解除,音源问题基本消失
- **各流可以各用各的速度**:反正一次只响一条,不存在 BPM 兼容问题
- 过渡的"优雅"从音频层挪到**视觉层**(fader 回落动画、VU 灯熄灭)——顺畅感靠眼睛给
- 此前"SoundCloud crossfade PoC"计划**作废**,不做

**下一步**:做混音台 v1 交互原型(fader 触发切换 + 让位动画),合成音色占位,验证手感。

## 2026-07-06 · 追加:过渡语法(cc 提出)

**决定**:频道切换分两种——
- **无交集的两条流**:普通切换(fader 触发,让位动画)
- **有交集的两条流**:过渡用**打碟(转盘 spin/scratch)或采样 pad** 演出来,交叉点信息(谁连的线、哪一年)随过渡浮现

**为什么好**:把"渗透"从内容层(第 13 节交叉点)搬进了**交互语法**——过渡本身讲历史。且形式与内容对位:Herbie〈Rockit〉那条线用 scratch(他本人玩的就是搓碟),采样文化那条线用 MPC pad。C(转盘)和 pad 由此找到了正确的位置:不是常驻设备,是**交叉点专属的过渡仪式**。

## 2026-07-06 · 追加:版式定上下结构,真歌在上(cc 拍板)

**决定**:上下结构。上 = ON AIR 面板(真歌 embed + 段落标题 + 串场词,对应真调音台的 meter bridge/监听位),下 = channel strip 一排(推子,手的区域)。

**理由**:(1) "手在下、眼在上"是真调音台的身体逻辑;(2) 8—11 条 strip 需要吃满横向宽度,左右结构会挤;(3) 上下天然适配移动端竖屏(第一件左中右三栏在手机上吃过亏)。原型:`design/prototypes/mixer_v3_layout.html`。

## 2026-07-14 · 第二段大改:选曲转精选 + 视觉重定基调(cc 拍板)

**一、选曲从"全景"转"精选"**
- cc 明确:名单要"我想点"不是"我知道"。**砍 SMOOTH**(知道但不点)、**砍 NEO-TRAD/Wynton**(精选路线里最不给惊喜)。
- **加拉丁**——之前把拉丁"留 v2"是判断失误,它是与 fusion 并列的主动脉,不是补充。走 **Afro-Cuban 钢琴一脉**(Irakere/Chucho Valdés/Gonzalo Rubalcaba),贴 cc 靶心(罗宁那种)。
- **加 jam**(jazz-funk/jam band),代表 **Snarky Puppy**(当代、格莱美、现场炸),= fusion 插电后"现场把即兴玩活"的延续。
- 结果仍 10 条:FUSION / ECM / ACID JAZZ / HIP-HOP / NU JAZZ / JAPAN / SPIRITUAL / UK WAVE / LATIN / JAM。house 并入 NU JAZZ(St Germain 本就是 house×jazz)。

**二、配色:离开纯黑**
- cc 依据自收参考(design 的「参考颜色」文件夹,流白 Livo 一系 + 马蒂斯 + 平涂风景)。整体走 **A 纸基调**,但**往冷淡压、要居家舒适(非工业)**;**跳色取 B 暗底那种高饱和艳度**。
- 真实取色:基调偏冷灰(参考「冷淡」#A0A5A4/#D1CCC9,落地压到暖冷灰 ~#C4C3BB);跳色从马蒂斯(红 #A3022B/橙 #E98C01/松绿 #1A4E41/黄 #F0B863)+ 平涂风景(雾青 #5E8A9E/珊瑚 #CB5A48/莓紫 #6A5365)取,高饱和不降艳。

**三、推子异形(cc 提出,很赞)**
- 推子不再等宽等高:**按支流份量给尺寸**——主干大流=宽高推子,小众支流=窄矮推子。全部塞得下(含拉丁/jam),且尺寸本身编码"大带小、谁主谁支",不用额外标注。

**四、立体**:轻透视暗示(屏幕正视保可读,台面微躺+地台阴影),不做真 3D(移动端/命中/可读性风险)。

> 落地产物:`design/prototypes/mixer_v5_*.html`。上一版 v4(纯黑等宽)封存。

## 2026-07-14(二)· v7:电气化三区 + 光谱推子 + 压轴创作流(cc 拍板)

**一、按电气化程度分三区**(取代平铺):原声·活人 / 电声·插电乐队 / 电子·采样编程。三行分区省横向空间,且分区本身讲历史(这段=三种发声方式并存,对照第一段的线性接力)。地域退成推子小标签。
- 原声:ECM、SPIRITUAL、LATIN、JAM、NEW STANDARD(压轴)
- 电声:FUSION、JAPAN、ACID JAZZ、UK WAVE
- 电子:HIP-HOP、NU JAZZ

**二、光谱推子(新交互语法)**:主流内部有子光谱的,用**推子行程本身**表达,不加子推子。
- HIP-HOP:采样端(ATCQ〈Excursions〉)→ 过渡(Us3〈Cantaloop〉)→ 活乐队端(Robert Glasper〈Afro Blue〉7e0j6jReCfN5KJkDNLHyHQ)。
- NU JAZZ:house 端(St Germain〈Rose Rouge〉)→ 实验端(Jaga Jazzist〈Airborne〉60W51PvuIPnEZFeDxUQYvZ)。house-jazz 由此收进 NU JAZZ 的一端,不单列。
- 技术:推子位置分段 → loadUri 换曲,复用既有 play/pause 架构,零新依赖。其余流仍是触发器推子。

**三、加压轴流 NEW STANDARD(当代创作型 · 最高级别)**:代表 **Ambrose Akinmusire〈Henya〉(2011)6j5z2GM4BCDBYlHoryFrki**(前沿首选),备选 Aaron Parks〈Nemesis〉3pHi49H2DjfnpqX6iOaLC8(温暖)。放原声区、压轴。与 Wynton(活人博物馆/复刻)划清:它是活人、原声、但往前探的创作,不是回头正典。命名"NEW STANDARD"双关(新标准 / 新的 standard 标准曲),待 cc 确认。

**四、连带**:Nujabes 从 JAPAN 移除,只作 HIP-HOP×JAPAN 交叉点(血统=hip-hop);JAPAN 代表锁 Casiopea,辨识度改锚"精密工艺 + 自成生态"而非独特声音(city pop 全球辨识度更高但离 jazz 远,不换);jazz-rock=fusion 别名,并入 FUSION 一句带过;当代 jazz-punk 不收。

> 产物:`design/prototypes/mixer_v7_zones.html`。v4/v5/v6 封存。

## 2026-07-14(三)· v8:整体布局重做(cc 批"没设计,乱丢内容"后)

**教训**:此前一直"推一步走一步、局部补丁",cc 明确要整体布局设计。v8 是一次成型重做,不再补丁。

- **屏幕 = 血缘星图背景 + 前景文字/播放器**:11 流作节点、7 条交集连线作淡背景星图(SVG,opacity 低,"看不清也行,能看清更好")。当前流上台→其节点点亮(流色+发光);交集过渡→对应连线亮起。文字仍在固定文本区(不硬贴节点,保可读),加文字阴影压在星图上。血缘由此化进背景,不做独立卡片(cc:血缘卡贴上去很怪,调音台要纯粹)。
- **调音台俯视 B**:桌面 rotateX 46° 往纵深躺,strip counter-rotate(-46°)立直——拖拽手感不丢、推子高矮(份量)仍可见。调音台下移(margin-top 70)填下方空白。
- **技术坑预判**:backdrop-filter 与 preserve-3d 冲突→玻璃改半透明纯色(去 backdrop-filter),保玻璃感用边框高光+半透明。
- **只做桌面端**(cc:先把网页端做好,暂不管移动端)。
- 文字待 cc 精简。逻辑/选曲/光谱/交集全承 v7。

> 产物:`design/prototypes/mixer_v8_starmap.html`。3D 俯视观感需 cc 本机看,jsdom 测不了渲染。

## 2026-07-14(四)· v9:血缘水系图=整页底图 + 俯视A(cc 追问"星图做什么/空白没理解")

**关键认知修正**:血缘星图不是屏幕角落的装饰背景,而是**整段的地图/底图**——把"平行水文/三角洲"变成能看见的水系图。正确位置=**铺满整页当底图**,屏幕和调音台都浮在其上;之前的空白就是因为把星图闷在屏幕小盒里没铺开。星图铺满=空白变"水域"。
**立体修正**:cc 要的是**推子跟台面一起俯视躺下、沉进纵深**(方案A),不是 v8 的"推子立直"(B)。glass rotateX 60° 整台躺,推子随台面躺。拖拽在俯视下会斜,以点击上台兜底。

- `#watermap` 移到 body 直属,position fixed 铺满视口,viewBox 1000×600,11 节点按年代/区位分布整页,7 连线跨越空白区;当前流节点亮、过渡连线亮(带流色)。
- 屏幕半透明深色浮水上;调音台俯视 A 坐落水面(半透明玻璃透出水系)。
- 产物:`design/prototypes/mixer_v9_watermap.html`。v8(星图在屏内+俯视B)封存。3D 俯视观感/星图疏密/文字可读需 cc 本机看。

## 2026-07-14(五)· v10:打掉星图/屏幕盒子,重立底子 = 平行河流时间图 + 底部调音台(cc 强推翻)

**cc 明确**:跳出"屏幕盒子+星图"旧框架。空白不是不能写,是没安排真内容。新骨架:
- **上=时间图**(占上部):血缘星图换成**十一条平行河流带**——横轴 1975→2026,每条流从源头年份一路流到今天(都还活着),粗细=份量,源头点+流名+年份+一句话。这是"平行水文/三角洲"第一次被字面画出。按源头年从上到下排。
- **下=调音台**:俯视,拉到页面最底。
- **音频暂屏蔽**(去 embed/Tone/spotify),点推子只做视觉高亮对应河流带。**文字面板"上面那块"待底子定稿再放**;血缘交集点待接到时间轴对应年份;音频最后解封。
- 产物:`design/prototypes/mixer_v10_timeline.html`。v9 及以前(星图路线)封存。

> 教训沉淀:cc 反复纠同一点——不要被现有框架困住、不要用飘忽装饰糊弄空白、每块空间要有真内容与意义。远未收工。

## 2026-07-14(六)· v11:背景改暖色坐标星空(cc 授权"按领会做")

cc 要背景有"星系/空间/坐标/镜头感"(不是尺子),授权我领会着做。产物 `mixer_v11_starfield.html`:
- 背景从"平行河流带"→**暖色坐标星空**:横轴=时间(1976–2026),纵轴=声音层(电子/电声/原声),每条流=一颗**发光天体**(诞生年×声音层定位、大小=份量、拖淡尾迹表示仍在流),**血缘=天体间星座连线**,星尘+径向聚焦给镜头纵深。点天体/推子→该天体亮、它的血缘星座线亮、其余变暗。
- 暖纸不丢、时间坐标不丢,但有了星系呼吸。调音台保留在下。音频/播放器/标签卡待背景确认后合并(播放器 demo=player_demo.html 已验证可用)。
- v10(河流带)封存。

## 2026-07-15 · 台签换名(cc 原则:"可以不说,说了就核实严谨";全部有出处,已核)

- **UK WAVE → UK JAZZ**("UK Wave"公论指英伦青年文化统称 bass/garage/grime/drill,挂爵士是错的;这个场景通行叫法 UK jazz / "British jazz explosion",Guardian 2018)
- **HIP-HOP → JAZZ RAP**(hip-hop 是音乐大类,单挂误读;融合流正式名 Jazz rap,Wikipedia 条目名 + AllMusic subgenre,伞罩住采样→活乐队全光谱)
- **NEW STD → POST-BOP**(自造名撞车:「new standard(s)」在爵士已专指"新标准曲",Herbie 1996 专辑 + Carrington 2022 曲集;正解 AllMusic 给 Mehldau/Akinmusire 的流派栏=Post-Bop。排雷:"contemporary jazz"≈smooth 歧义、"modern creative"=Zorn 系 free,均不可用)
- **JAM → JAZZ-FUNK**(Snarky 官方 bio 原话 "definitely not a jam band";jam band 专指 Dead/Phish 巡演文化。JAZZ-FUNK 为既有流派词,贴"现场为王 groove 管够")
- **JAPAN 保留**(诚实地理称呼,不冒充流派名;J-Jazz 是 BBE 合集带火的圈内叫法,联想绑 60s–80s deep/modal,弃)
- **CH5 NU JAZZ 年份 1990s末→1990s**(Wikipedia 信息框 Early 1990s;"90年代末"只是词流行的时间)
- Nu Jazz 多国起源(含日本)已核属实;Jazztronik/Indigo Jam Unit 真实、日本 club jazz 谱系(UFO/Kyoto Jazz Massive 签 Compost)成立 → 为 JAPAN×NU JAZZ 潜在血缘线留据。
- **cc 拍板:走语法方案(升级版)**——血缘线分两型:**实线=事件血缘**(某年某作品,7条)、**虚线=演化血缘**(基因传承,2条:ACID⇢NU"近亲往电子更深处"、JAPAN⇢NU"Kyoto Jazz Massive→Compost")。v13 已实现(LineDashedMaterial),左上角加图例。
- copy 文件(ep2_channel_copy_v6.md)已由 Claude 全面对齐:标题换名、CH5 年份+半句、CH6 Nujabes 注、新增 CH11 POST-BOP、连线章分两型。
- **主动扫雷修正两处**(cc 原则:核实是 Claude 的责任):①《We Like It Here》= 2013-10 荷兰乌得勒支 Kytopia 录音室、观众在场连录四晚,2014 发行(原文"2014年录"错);②acid jazz 命名玩笑话出自 Chris Bangs(与 Gilles Peterson 搭档,"If that was acid house, this is acid jazz"),只写 Peterson 不完整,已补。jazz 喫茶"几百家"(楠瀬克昌估计~600)、Khmer 1997 ECM、Casiopea 1979 连发两张,复核均成立。

## 2026-07-15(二)· **铁律:两层分开——内容不创新,视觉才创新**(cc 定)

> **内容层 = 零创新**。分类、命名、谱系一律**拿圈内公认的直接用**;我们没有资格也没有必要自定义分类,自造只会招争议。凡是自造名,一律换成有百科/AllMusic 级条目的现成名;没有公认名的,要么退到最接近的公认名,要么明确标注"这是场景标签,非流派"。
> **视觉/交互层 = 创新点**。**调音台推子 + 星座**是我们的原创所在,力气花这儿。
> 前人作品调研结论(同日):完全对应的组合无先例,但多语义连线(Musicmap 的 primary/secondary/anti-link)、点节点即听(Every Noise/Radiooooo/Music Galaxy)、深色发光节点图(Genre Genealogy)、平行支流(Garofalo 1977)都是成熟范式,**不要当自己的创新**;真正空白只有三处:①推子作探索控件(NIME 2025 才有论文把 mixer 隐喻用于非音乐对象)②星座作叙事骨架 ③**1976 后这段爵士在可视化领域完全没被覆盖过**(现存爵士可视化重心全在 1940–60s)。

### 11 条名称对照公认分类表(AllMusic jazz styles + Wikipedia List of jazz genres)
- **完全站得住(AllMusic + Wikipedia 双命中,直接用)**:FUSION、SPIRITUAL JAZZ、LATIN JAZZ、JAZZ-FUNK、POST-BOP
- **有条目但 AllMusic 门类不在 Jazz 下(不影响使用,标注即可)**:ACID JAZZ(AllMusic 归 Electronic)、JAZZ RAP(归 Rap)、NU JAZZ(仅 Wikipedia 有,AllMusic 无此 style)
- **需改全称**:JAPAN → **Japanese jazz**(Wikipedia 有条目,但归 Category:Music scenes=场景非流派;地理命名在爵士分类里很常见:AllMusic Global Jazz 下有 Brazilian/Afro-Cuban/Cuban/African/Israeli/Latin Jazz,故合法)
- **无公认名(必须处理)**:
  - **ECM** = 厂牌名不是流派名(AllMusic 无、"ECM sound" 无条目)。→ 建议换 **Nordic jazz**(Wikipedia 有条目并在 Category:Jazz genres;条目原文即用 "Nordic tone"/"the ECM sound" 描述 Garbarek/Rypdal/Molvær 一脉;学术背书:Fabian Holt 2019 *Nordlit* 42;Medbøe;NPR)。注意 chamber jazz **不是**它的同义词(AllMusic 的 chamber jazz 代表艺人半数是 Windham Hill new age)。
  - **UK JAZZ** = 无百科级条目("UK jazz"/"London jazz scene" 在 Wikipedia 均 missing);唯一正式条目 British jazz 是 1920s 起的国别史,范围不符。→ 只能**自认场景标签**或退用 British jazz,待 cc 定。

## 2026-07-15(三)· **转向:弃流派分类,改用现成榜单数据**(cc 定,骨架级)

**cc 的判断(原话要点)**:流派本身不存在,更确切说是"某个时代的人们表达的方式",且边界永远划不清——我们这一路的反复就是证据(UK Wave 错、ECM 是厂牌非流派、acid jazz 词条正文与信息框自相矛盾)。花大力气去划一条划不清的线,收益极低、风险自揽。**改按已有的榜单/评选数据走**:内容层彻底不加工,数据是谁的就是谁的。

**v1 定位**:呈现事物本来的面貌——**用数据呈现爵士这些年变化的样子**。浪潮的形状由数据自己浮现(某几年冒出一批灵性爵士、某几年全是伦敦名字),我们一个字都不下判断。
**v2 储备(cc:是个不错的点,放第二版)**:**商业榜 × 评论榜的落差 = 被忽视的好作品**。评论界排名高却从未进商业榜的唱片,就是被埋没的好东西;这个判断不是我们说的,是两份现成数据的差值。做这版需多抓一份商业榜数据。

**用户需求锚点**:大众对爵士的认知停在《Kind of Blue》,想听新的无从下手;而现有权威榜单都是丑陋的纯文字长列表,没人看也听不了。把它变成能看见形状、能立刻听 30 秒的东西——本身就有用,且无人做过(前轮调研:现存爵士可视化全压在 1940–60s)。

**三条可用数据线(时间深度不同)**:DownBeat 票选(读者票选 1936 起,最长)· 格莱美爵士奖项(1959 起,机构盖章)· Francis Davis 爵士评论家票选(2006 起,最当代最精准;Davis 2025-04 去世,存档在 hullworks.net/jazzpoll)。**时间跨度不必被"近 20 年"限制**,取决于讲哪个故事。

## 参考作品分析存档

Pudding《Music DNA》的分析(音频处理方式 + 可偷的三招)记在 `research/idea.md`。核心结论:它机制上就是"一次一段、滚动切换"(= 我们的路线一),证明"渗透"不需要同时出声,靠**前后对听**就能讲透。
