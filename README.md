# shiyiagi-director-action · 动作片 AI 视频导演提示词

> 把「AI 扮演动作片导演」从一句口号，固化成可复用的提示词结构。专治打斗看不懂、连续打斗抽搐穿模、形容词废词。

动作戏是 AI 视频最容易翻车的类型。本 skill 用「设计层 + 生成层」两层判断，把连续打斗拆成可生成的镜头，并把「炸裂 / 帅气 / 瞬移 / 升格」这类观感词翻译成模型读得懂的镜头元件。

## 它解决什么

| 崩点 | 表现 | 解法 |
|---|---|---|
| 打得热闹但看不懂 | 两人糊在一起，不知谁打谁、打到哪 | 「看得懂」标准：力量对比 + 空间 + 一攻一应表 → `fight-design.md` |
| 连续打斗抽搐穿模 | 一镜拍完整场，肢体互相穿插 | 四拍拆解：预备→冲击→结果→反应，一镜只放一拍 |
| 多人同框物理错乱 | 近身缠斗时两人肢体穿插 | 接触即切：复杂接触移出画面或只拍单人反应 |
| 形容词废词 | "炸裂""帅气"直接写进提示词被忽略 | 概念转译法：感受词→镜头/构图/运镜/光线/物理反馈 五类元件 |

## 两层判断

1. **设计层**：质量八成来自「开打前想清楚打什么」。院线级标准是 **「看得懂，看得爽」**。
2. **生成层**：不靠写得热血，靠把力度落成具体的重心位移、形变、碎屑、定格。

> ⚠️ 最易犯的错：把专业术语当专业度。**剪辑 / 节奏 / 轴线属「镜间」，只进分镜表；动作 / 镜头 / 光线 / 物理结果属「镜内」，才进单镜提示词。**

## 交付物

本 skill 产出两类提示词（结构不同，勿混用）：

- **导演提示词** → 喂给 LLM，产出打斗设计表 + 分镜表 + 逐镜提示词
- **单镜头生成提示词** → 喂给视频模型（即梦 / 可灵 / Seedance / Grok）出片

## 目录结构

```
shiyiagi-director-action/
├── SKILL.md                       # 主入口：触发条件 + 四步流程 + 自检清单
├── README.md
└── references/
    ├── action-director-prompt.md      # 主模板（四要素契约）
    ├── fight-design.md                # 写实打斗设计地基
    ├── supernatural-fight.md          # 超现实提示词层（瞬移/连闪/升格）
    ├── supernatural-fight-design.md   # 超现实设计层（能力契约/情报战）
    ├── environment-atmosphere.md      # 环境氛围层（第五个角色）
    ├── multi-opponent-design.md       # 一对多/围攻/枪战/追车
    ├── weapon-design.md               # 武器层（9 类 + AI 崩点）
    ├── concept-translation.md         # 概念转译法（镜间镜内分流）
    ├── ai-video-prompt.md             # 七段顺序铁律
    ├── lens-grammar.md                # 镜头语法七维
    ├── compliance.md                  # 合规边界
    ├── production.md                  # 生产层结论
    ├── platform-specs.md             # 引擎规格
    ├── style-anchors.md              # 风格锚点
    ├── troubleshooting.md            # 常见翻车与修复
    ├── walkthrough-realistic.md      # 茶楼夜战端到端示例
    └── walkthrough-supernatural.md   # 仙侠竹林夜战端到端示例
```

## 怎么用

1. 把 `SKILL.md` 作为指令交给 LLM（或粘贴进对话）。
2. LLM 按四步流程产出：打斗设计表 → 分镜表 → 逐镜提示词。
3. 把逐镜提示词喂给视频生成模型出片；按 `troubleshooting.md` 抽卡迭代。

## 适用 / 不适用

- ✅ 武打、格斗、战斗、动作戏、奇幻武侠、超现实打斗、一对多、围攻、混战、枪战、地面技
- ❌ 品牌形象片 → `shiyiagi-director-ad-tvc`
- ❌ 剧情带货（要转化 / CTA） → `shiyiagi-director-story-selling`
- ❌ 叙事 / 故事类 → `shiyiagi-director-film`

## 版本与授权

- 版本：**v1.7.0**
- 作者：十一AGI（柳十一 / 十一AGI认知圈）
- 授权：学习与非商业用途可自由使用；商用请先联系作者授权。

## 系列导航

| Skill | 定位 |
|---|---|
| [shiyiagi-director-ad-tvc](https://github.com/shiyi-TNT-SOS/shiyiagi-director-ad-tvc) | 品牌广告片 / TVC / 形象片 |
| [shiyiagi-director-film](https://github.com/shiyi-TNT-SOS/shiyiagi-director-film) | 故事片 / 叙事短片 |
| [shiyiagi-director-story-selling](https://github.com/shiyi-TNT-SOS/shiyiagi-director-story-selling) | 剧情化带货短视频（独立付费发布线） |
| **shiyiagi-director-action（本仓库）** | 武打 / 格斗 / 动作戏 |
