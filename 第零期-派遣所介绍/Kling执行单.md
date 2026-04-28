# 第零期 Kling 执行单

目标：尽量少手动，尽量不进剪映，优先用 `Kling VIDEO 3.0` 的 `Custom Multi-Shot` 一次生成一条完整的品牌短片。

## 推荐策略

先做两轮：

1. 粗剪版
   - `VIDEO 3.0`
   - `No Native Audio`
   - `720p`
   - `9:16`
   - `15s`
   - `Multi-Shot: ON`
   - `Custom Multi-Shot: ON`

2. 定稿版
   - 只有在粗剪版视觉成立后再做
   - 可选：
     - 保持 `No Native Audio`，最省额度
     - 或改成 `Native Audio`，只加环境音和最后一句旁白

这样做的原因很简单：
- 先确定画面和故事线对不对
- 再决定要不要为音频多花额度
- 避免一开始就在音频、口型、角色一致性上一起烧额度

## 如果首尾帧一次只能上传两张图

这就不要再试图把 `8` 张静帧一口气串成一条视频。

正确做法是：

- 不走“整片首尾帧”
- 改成“`3 段生成 + Kling 内部拼接` 或 `导出后简单拼接`”

最稳的分段是：

1. `办公室段`
   - 内容：
     - 镜头1 纸团陨石砸桌
     - 镜头2 派遣所瞬间炸锅
     - 镜头3 所长下令
     - 镜头4 员工鱼贯而出
   - 起始帧：`镜头1-纸团陨石砸桌.png`
   - 结束帧：`镜头4-员工鱼贯而出.png`
   - 时长：`6s`

2. `入户 montage 段`
   - 内容：
     - 镜头5A 客厅
     - 镜头5B 厨房
     - 镜头5C 书房
   - 起始帧：`镜头5A-客厅现场乱忙.png`
   - 结束帧：`镜头5C-书房现场乱忙.png`
   - 时长：`5s`
   - 在 prompt 里明确要求“中间快速切到厨房，再切到书房”

3. `品牌收尾段`
   - 内容：
     - 镜头6 品牌收尾
   - 做法一：
     - 直接用 `镜头6-品牌收尾.png` 做 `Image-to-Video`
   - 做法二：
     - 起始帧和结束帧都用 `镜头6-品牌收尾.png`
   - 时长：`4s`

这样整片就是：
- `6s + 5s + 4s = 15s`

这比硬让 Kling 在一条里穿越 8 张图更稳很多。

## 官方能力依据

根据 Kling 官方 `VIDEO 3.0` 指南：
- 支持 `Image-to-Video`
- 支持 `Start & End Frames-to-Video`
- 支持 `Multi-Shot`
- 支持 `Custom Multi-Shot`
- 支持 `Native Audio`
- 支持 `15s` 输出

参考：
- `https://app.klingai.com/cn/quickstart/klingai-video-3-model-user-guide`

同一份官方指南里，`720p No Native Audio` 的价格最低，适合先做粗剪版。

## 建议不要做的事

- 不要一开始就开 `1080p`
- 不要一开始就开 `Voice Control`
- 不要让角色全程说话
- 不要要求每个镜头都大动作
- 不要先做多个版本再挑

先只跑一条最小可用版。

## 现有静帧素材

位于：

- `原图/镜头1-纸团陨石砸桌.png`
- `原图/镜头2-派遣所瞬间炸锅.png`
- `原图/镜头3-所长下令全军出击.png`
- `原图/镜头4-员工鱼贯而出.png`
- `原图/镜头5A-客厅现场乱忙.png`
- `原图/镜头5B-厨房现场乱忙.png`
- `原图/镜头5C-书房现场乱忙.png`
- `原图/镜头6-品牌收尾.png`

## 最省操作路线

### 路线 A：一条 15 秒直接成片

适合先试。

操作：

1. 打开 Kling `VIDEO 3.0`
2. 选择 `Multi-Shot`
3. 打开 `Custom Multi-Shot`
4. 画幅选 `9:16`
5. 时长选 `15s`
6. 分辨率选 `720p`
7. 先选 `No Native Audio`
8. 如果界面允许上传起始图，用 `镜头1-纸团陨石砸桌.png` 当 `Start Frame`
9. 粘贴下面的 `Custom Multi-Shot Prompt`
10. 生成第一条粗剪版

注意：
如果你的界面在 `Start & End Frames-to-Video` 里一次只能放 `2` 张图，这条路线就只适合拿来测试，不适合作为最终正片方案。

最终还是优先用上面的 `3 段式`。

### 路线 B：更稳的版本

如果路线 A 的角色一致性不好，再做这一步。

额外动作：

1. 创建一个 `Director` 元素
   - 用：
     - `所长参考图-2026-04-27.png`
     - `镜头3-所长下令全军出击.png`
     - `镜头6-品牌收尾.png`

2. 创建一个 `Worker Team` 元素
   - 用：
     - `镜头4-员工鱼贯而出.png`
     - `镜头5A-客厅现场乱忙.png`
     - `镜头5B-厨房现场乱忙.png`
     - `镜头5C-书房现场乱忙.png`

3. 重新跑同一条 `Custom Multi-Shot`

这条更稳，但手动步骤更多。

## 推荐成片节奏

总时长控制在 `14-15 秒`。

- Shot 1: `2.0s`
- Shot 2: `2.0s`
- Shot 3: `2.0s`
- Shot 4: `2.0s`
- Shot 5 montage: `4.5s`
- Shot 6: `2.5s`

## Kling Custom Multi-Shot Prompt

直接粘贴，先跑粗剪版：

```text
shot 1, dramatic falling perspective inside a whimsical dispatch office, a gigantic crumpled paper-ball request crashes downward toward the director's desk like an office meteor, tiny yellow computer worker robots look up in panic, premium theatrical family-animation tone, warm cinematic lighting, absurd but funny, 2 seconds.

shot 2, the paper-ball request has burst open across the desk and the whole office instantly erupts into frantic activity, tiny yellow worker robots are panicking, jumping, flailing, and scrambling, while the white robot director remains calm at the center, 2 seconds.

shot 3, 45-degree side view, the white robot director stands behind the desk on the left side, leaning forward and forcefully giving the order to move out, one arm thrust forward, worker robots lined up and awaiting command on the right, tense command-center atmosphere, 2 seconds.

shot 4, low-angle heroic comedy shot from near floor level, tiny yellow computer worker robots march out through the dispatch office doorway like a clumsy little office army, carrying files, tablets, tools, and task sheets, eager and determined, 2 seconds.

shot 5, quick montage across three different homes: a warm living room, a bright kitchen, and a quiet study. In each home, only a tiny team of 3 to 4 worker robots is present. They are all sincerely busy, but slightly making things worse: in the living room they inspect the wrong objects and leave a small mess; in the kitchen a faucet sprays and a bowl is broken; in the study books are on the floor and ink has spilled. Funny, harmless, overhelpful, incompetent, 4.5 seconds.

shot 6, final brand-closing shot inside dispatch office headquarters, the white robot director stands calmly in the foreground with a clipboard, while many yellow worker robots continue working frantically but imperfectly in the background, warm premium office, polished 3D materials, strong foreground/background separation, closing-shot energy, 2.5 seconds.
```

## 两帧约束下的分段 Prompt

### A. 办公室段（镜头1-4）

起始帧：
- `镜头1-纸团陨石砸桌.png`

结束帧：
- `镜头4-员工鱼贯而出.png`

建议时长：
- `6s`

Prompt：

```text
The gigantic crumpled paper-ball customer request crashes into the whimsical dispatch office like an office meteor. The office instantly erupts into panic. Tiny yellow computer-worker robots scramble in confusion while the white robot director regains control, leans forward, and gives a forceful dispatch order. Then the workers organize and rush out through the doorway like a clumsy little office army. Premium theatrical family animation, polished toy-like 3D materials, warm cinematic lighting, controlled comic chaos, vertical 9:16.
```

### B. 入户 montage 段（镜头5A-5C）

起始帧：
- `镜头5A-客厅现场乱忙.png`

结束帧：
- `镜头5C-书房现场乱忙.png`

建议时长：
- `5s`

Prompt：

```text
Quick comedic montage across three different homes. First, in a warm living room, a tiny team of yellow computer-worker robots works very hard but focuses on the wrong things and creates a small new problem. Then cut to a brighter kitchen, where another tiny team is busy while a faucet sprays and a bowl is broken. Then cut to a quiet study, where books are on the floor and ink has spilled while the robots sincerely try to help. All teams are earnest, overhelpful, and slightly incompetent. Premium theatrical family animation, polished toy-like 3D materials, cinematic domestic comedy, vertical 9:16.
```

### C. 品牌收尾段（镜头6）

起始帧：
- `镜头6-品牌收尾.png`

如果必须填结束帧：
- 仍然使用 `镜头6-品牌收尾.png`

建议时长：
- `4s`

Prompt：

```text
Closing brand shot inside dispatch office headquarters. The white robot director stands calmly in the foreground holding a clipboard while many tiny yellow worker robots continue working frantically but imperfectly in the background. Warm premium office, polished 3D materials, elegant depth of field, calm authority in front and overloaded chaos behind. Strong brand-closing energy, vertical 9:16.
```

## 全局风格补充词

如果 Kling 允许额外补充全局风格描述，再加这一段：

```text
premium theatrical family animation, polished toy-like 3D materials, warm cinematic lighting, chaotic office comedy, original animated short-film look, clear silhouette staging, controlled comic chaos, readable storytelling, no humans, no text, no logo, no watermark
```

## 如果 Kling 支持负面约束

可加：

```text
no direct imitation of copyrighted characters or studios, no gore, no destruction, no fire, no war, no random visual noise, no chaotic camera shake, no excessive facial distortion, no extra limbs, no lip-sync closeups
```

## 音频怎么做

结论先说：

- 第一版不用全程对白
- 最稳的是：`环境音 + 最后一条深沉旁白`
- 不建议全片角色说话

原因：
- 你这条片子靠的是画面设定和节奏，不靠台词推进
- 一旦所有角色都说话，额度更高，失控概率也更高
- 员工的“叽里呱啦”只需要当作氛围

### 音频方案 1：最省额度

直接选：
- `No Native Audio`

先只看画面。

如果这条视觉成立，再决定要不要做带音频版。

### 音频方案 2：推荐定稿方案

选：
- `Native Audio`
- 但不要开 `Voice Control`

提示里只要求：
- 小机器人办公室环境音
- 纸张、脚步、小工具碰撞声
- 员工含混不清的忙乱 chatter
- 结尾一条深沉男中音旁白

### 推荐音频提示

如果你准备跑带音频版，把下面这段额外加在 prompt 末尾：

```text
Audio direction: playful office chaos ambience with tiny robot chatter, fast little footsteps, paper rustling, tablet beeps, light household clatter, and a subtle cinematic music bed. No full dialogue scenes. At the final shot, add one deep, calm, authoritative male voice-over in Chinese: “人工智障派遣所。不正常，很正常。”
```

## 旁白建议

只保留最后一句最稳：

- `人工智障派遣所。`
- `不正常，很正常。`

不要在前面加太多解释。

如果你想要两句版，也可以：

- 镜头 2 或镜头 3：`需求，已送达。`
- 结尾：`人工智障派遣所。不正常，很正常。`

但最低风险还是只保留最后一句。

## 你实际操作时的顺序

### 先跑这个

1. `VIDEO 3.0`
2. `720p`
3. `15s`
4. `No Native Audio`
5. `Multi-Shot ON`
6. `Custom Multi-Shot ON`
7. 粘贴主 prompt
8. 生成一条

### 如果第一条能看

第二步：

1. 不改分镜
2. 只把 `No Native Audio` 改成 `Native Audio`
3. 加音频提示
4. 再跑一条

### 如果第一条问题很大

优先改这 3 个，不要全改：

1. 缩短镜头 5 montage 的描述
2. 去掉复杂的角色行为细节
3. 增加元素一致性参考

## 最后判断标准

第一条粗剪版只看 4 件事：

- 故事线是不是顺的
- 所长是不是认得出来
- 员工是不是一眼就是派遣所员工
- 最后结尾是不是有品牌感

只要这四条成立，这条片子就值得再跑带音频版。

## 7图版 omni 自定义分镜时长

如果你现在用的是支持：
- `omni`
- `自定义分镜`
- `给每个分镜单独设置时长`

那就不要用一整段大 prompt 去赌它自己切镜头。  
直接按下面的 `6 段式时长` 来填。

### 总时长建议

- `15秒`

### 分镜时长分配

1. 镜头1：`2.0秒`
2. 镜头2：`2.0秒`
3. 镜头3：`2.0秒`
4. 镜头4：`2.0秒`
5. 镜头5 montage：`4.5秒`
6. 镜头6：`2.5秒`

合计：
- `15.0秒`

## 7图版 omni 自定义分镜文案

上传这 7 张图：

1. `镜头1-纸团陨石砸桌.png`
2. `镜头2-派遣所瞬间炸锅.png`
3. `镜头3-所长下令全军出击.png`
4. `镜头4-员工鱼贯而出.png`
5. `镜头5B-厨房现场乱忙.png`
6. `镜头5C-书房现场乱忙.png`
7. `镜头6-品牌收尾.png`

然后在 `自定义分镜` 里这样填：

### 分镜1

- 参考图：`镜头1-纸团陨石砸桌.png`
- 时长：`2.0秒`
- 文案：

```text
巨大的纸团需求像陨石一样砸进人工智障派遣所办公室，从高空俯冲向所长桌面，员工们抬头慌乱，画面有强烈下坠感和喜剧冲击力。
```

### 分镜2

- 参考图：`镜头2-派遣所瞬间炸锅.png`
- 时长：`2.0秒`
- 文案：

```text
需求刚落下，整个派遣所瞬间炸锅。黄色小电脑员工慌乱启动、四处忙乱，办公室一秒进入超负荷运转，但所长仍然是唯一稳定的中心。
```

### 分镜3

- 参考图：`镜头3-所长下令全军出击.png`
- 时长：`2.0秒`
- 文案：

```text
45度侧向镜头，所长站在桌后前倾大吼，下达全军出击的命令。员工列阵待命，地面散落工单，气氛像办公室版出征前一秒。
```

### 分镜4

- 参考图：`镜头4-员工鱼贯而出.png`
- 时长：`2.0秒`
- 文案：

```text
低机位仰视镜头，员工们像一支笨拙但认真的小队鱼贯而出，穿过大门奔赴现场，手里拿着工单、平板和工具，既有出征感又有喜剧感。
```

### 分镜5

- 参考图：优先放 `镜头5B-厨房现场乱忙.png`，如果界面支持同分镜多图，再同时放 `镜头5C-书房现场乱忙.png`
- 时长：`4.5秒`
- 文案：

```text
快速 montage 切到不同家庭现场。先是厨房，小机器人们认真帮忙却把事情搞复杂了：水龙头呲水、碗碎了、柜门开着；然后切到书房，书掉在地上、墨水洒了，大家都非常努力，但明显在帮倒忙。整体要像高质量动画喜剧，不要像灾难现场。
```

### 分镜6

- 参考图：`镜头6-品牌收尾.png`
- 时长：`2.5秒`
- 文案：

```text
回到派遣所总部，所长站在前景稳如泰山，手持夹板，背景黄色员工依旧忙得焦头烂额、文件堆积、屏幕闪烁，形成品牌收尾画面，留出适合结尾字幕的位置。
```

## 音频版填法

如果这一版你准备直接开 `原生音频`，建议在“整体说明”或“全局文案”里补这一段：

```text
全片有轻微电影配乐和办公室喜剧环境音：纸张翻动、小机器人脚步、平板提示音、工具碰撞声、含混不清的忙乱 chatter。不要做大量清晰对白。只在最后一个分镜加入一句深沉、稳重、低沉的中文男声旁白：人工智障派遣所。不正常，很正常。
```

## 最稳的操作建议

如果你想提高第一次成功率：

1. 第一版：
   - `720P`
   - `15秒`
   - `不开原生音频`
   - 先只测画面和转场

2. 第二版：
   - 画面满意后
   - 开 `原生音频`
   - 用同一套分镜时长
   - 只补最后一句旁白

这样最稳，也最省额度。

## 六分镜最终版（按单双图重写）

结论先说：

- `双图分镜` 的 prompt 要写成“从 A 过渡到 B”
- `单图分镜` 的 prompt 要写成“在这个场景里保持角色和氛围，做轻动作”

不要再沿用之前那种“一整段故事说明”去赌它自己拆。

### 分镜1：需求陨石砸进办公室

- 类型：`双图`
- 图：
  - 起始图：`镜头1-纸团陨石砸桌.png`
  - 结束图：`镜头2-派遣所瞬间炸锅.png`
- 时长：`2.0秒`

Prompt：

```text
从高空俯冲的视角开始，巨大的纸团需求像陨石一样砸进人工智障派遣所办公室，目标是所长桌面。随着纸团落下，办公室里的黄色小电脑员工抬头慌乱，最后过渡到需求落地后办公室瞬间炸锅的状态。画面有强烈下坠感、办公室喜剧冲击力、暖色电影光影和高质量三维动画质感。
```

### 分镜2：所长压住场子，下令出击

- 类型：`单图`
- 图：
  - 参考图：`镜头3-所长下令全军出击.png`
- 时长：`2.0秒`

Prompt：

```text
保持这一格的45度侧向分镜和构图，白色所长站在桌后前倾大吼下令，手臂向前方有力指挥。地面散落工单，右侧员工列阵待命。镜头只做轻微推进和角色细小动作，突出所长压住全场、发号施令的感觉，不要改变构图，不要让员工乱跑。
```

### 分镜3：员工鱼贯而出

- 类型：`双图`
- 图：
  - 起始图：`镜头3-所长下令全军出击.png`
  - 结束图：`镜头4-员工鱼贯而出.png`
- 时长：`2.0秒`

Prompt：

```text
从所长下令的紧张瞬间自然衔接到员工出发。前半秒仍然保留桌前下令的压迫感，随后黄色小电脑员工像一支笨拙但认真的小队鱼贯而出，穿过办公室大门奔赴现场。镜头应当逐渐切到低机位仰视的出征感，方向统一、动作利落、带一点蠢萌喜剧感。
```

### 分镜4：厨房现场乱忙

- 类型：`单图`
- 图：
  - 参考图：`镜头5B-厨房现场乱忙.png`
- 时长：`2.25秒`

Prompt：

```text
保持这个明亮厨房场景和小队规模，3到4个黄色小电脑员工都在认真工作，但明显把事情搞复杂了。一个在错误检查，另一个把厨房问题弄出小事故：水龙头轻微呲水、碗碎在地上、柜门开着。整体是高质量三维动画厨房喜剧，大家都很投入，但没有真的把问题解决。镜头只做轻微动态，不要变成灾难现场。
```

### 分镜5：书房现场乱忙

- 类型：`单图`
- 图：
  - 参考图：`镜头5C-书房现场乱忙.png`
- 时长：`2.25秒`

Prompt：

```text
保持这个安静书房的空间和深色木质气质，3到4个黄色小电脑员工正在认真帮忙，但把事情弄得更麻烦。地上有掉落的书，桌上和地面有明显墨水洒出的痕迹。员工们都很努力、很专注，但明显在帮倒忙。镜头突出安静书房被认真搞乱一点点的反差感，保持电影感和可爱荒诞感。
```

### 分镜6：品牌收尾

- 类型：`单图`
- 图：
  - 参考图：`镜头6-品牌收尾.png`
- 时长：`4.5秒`

Prompt：

```text
保持品牌收尾构图，白色所长站在前景中央稳如泰山，手持夹板，背景黄色员工依旧在忙碌工作、搬运文件、翻看工单、盯着屏幕，整个派遣所显得过载却又像日常状态。镜头缓慢推进，突出所长的稳定和背景员工的持续忙乱，形成高质量品牌海报式结尾。为后期落字保留清晰的中心和下方空间。
```

## 这版时长合计

- 分镜1：`2.0秒`
- 分镜2：`2.0秒`
- 分镜3：`2.0秒`
- 分镜4：`2.25秒`
- 分镜5：`2.25秒`
- 分镜6：`4.5秒`

合计：
- `15.0秒`

## 六分镜音频 Prompt（可直接粘贴）

### 全局音频 Prompt

如果中国版可灵有：
- `整体音频说明`
- `音频提示词`
- `原生音频说明`

就直接粘这一段：

```text
整条片子的音频要像一支高质量动画品牌短片。

音乐：
有轻微电影感配乐，节奏忙碌、荒诞、可爱，带一点办公室喜剧感，但不要太吵，不要史诗感，不要儿童片过度可爱风。

环境音：
前半段办公室有纸张翻动声、小机器人快速脚步声、设备提示音、轻微碰撞声、工位忙乱声、含混不清的叽里呱啦 chatter，整体像一群非常忙但不太聪明的小员工在高压开工。

中段家庭场景有轻微生活音效：
厨房有小水声、水龙头呲水、很轻的瓷器碎裂声、柜门开合声；
书房有书本落地声、纸张滑落声、墨水瓶碰倒和轻微液体洒出的声音。

对白要求：
不要做大量清晰对白，不要让角色一直说完整句子。员工只需要模糊、含混、快速、像小机器人忙乱交流的声音氛围。

最后一个镜头加入一句深沉、稳重、低沉、带一点冷幽默的中文男声旁白：
“人工智障派遣所。不正常，很正常。”
```

### 如果它支持分镜单独写音频

#### 分镜1 音频

```text
纸团下坠呼啸声，办公室被突袭时的小机器人慌乱环境音，音乐快速起势。
```

#### 分镜2 音频

```text
办公室炸锅，小机器人忙乱脚步、翻纸、轻微碰撞、设备提示音、含混 chatter。
```

#### 分镜3 音频

```text
音乐压一下，突出所长下令的气势，背景员工只有轻微待命和压抑忙乱声，不要大段对白。
```

#### 分镜4 音频

```text
一群小机器人鱼贯而出的脚步声、文件和工具轻响，带一点办公室小队出征感。
```

#### 分镜5 音频

```text
厨房有轻微水声和小瓷器碎裂声，书房有书本掉落和墨水瓶碰倒的小声音，整体仍然轻快荒诞，不要做成灾难片。
```

#### 分镜6 音频

```text
背景保持忙乱但克制的办公室环境音，音乐收束，最后加入一句深沉、稳重、低沉的中文男声旁白：人工智障派遣所。不正常，很正常。
```

### 极简版音频 Prompt

如果它的音频输入框很短，就用这版：

```text
轻微电影感配乐，办公室忙乱环境音，小机器人含混 chatter，厨房有轻微水声和瓷器碎声，书房有书本掉落和墨水洒出声。不要大量对白。最后一句深沉中文男声旁白：人工智障派遣所。不正常，很正常。
```
