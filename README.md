# AE Motion Production

**用 AI 协作制作可编辑的二维动效：从参考拆解、矢量分件到控制器、动作精修和 After Effects 工程交付。**

这是一个面向 Codex 的工作流技能。它指导代理分析参考、组织素材、编写或执行适合当前环境的制作脚本，并检查实际输出。技能本身是 Markdown 指令和参考文档，不是 AE 插件，也不内置一键生成动画的程序。

## 适合做什么

| 场景 | 重点 |
| --- | --- |
| 人物 / IP 表情 | 身体挤压伸展、五官跟随、卷毛回弹、手脚配合、不同情绪的动作节奏 |
| 图标与道具动效 | 分件关系、铰链位置、开合路径、边界和遮挡 |
| 游戏反馈 / UI 动效 | 预备、触发、主动作、回弹、停留及有来源的光效 |
| 横向装备轮播 | 连续速度、中央聚焦、准确停中、揭晓反馈 |
| 已有 AE 工程精修 | 在原工程上增量修改、中文命名、有效控制器、实际渲染验收 |
| 已确认动效的前端还原 | 用户明确需要交互版本时，沿用矢量素材和实际时间线 |

不用于仅做网页 CSS 动画或单纯生成一段无法编辑的视频。网页还原和作品发布是按用户请求启动的附加流程。

## 核心原则

1. **先看连续动作。** 分镜图能检查形状，不能代替播放检查节奏。
2. **分层不等于灵活。** 身体、五官和四肢围绕同一次发力配合，柔软末端有跟随与回弹。
3. **动画入口真实有效。** 关键帧放在真正驱动子层或路径的控制器上，按 U 能找到。
4. **形状细节可编辑。** 优先软件原生形状和矢量分件，检查曲线、切线、接缝与遮挡。
5. **交付包含检查结果。** 保存成功、表达式无错误和渲染成功，都不能单独证明动作自然。

## 环境要求

- 能发现并读取本地技能的 Codex 环境。
- 制作、保存和渲染 AEP 时，需要可用且合法安装的 Adobe After Effects，以及当前环境允许的脚本或桌面操作能力。技能不会自动安装软件或提供许可证。
- Illustrator 是修改静态矢量的可选工具；SVG 是否正确导入 AE 需实际验证。
- Python、Node.js、视频编码器或相关图像库属于按任务选择的辅助工具，并非阅读或安装本技能的必需依赖。
- 记录中包含 Windows / AE 22.0.1 的实践经验；其他系统和版本需要检查安装路径、脚本接口和输出模板，不保证所有案例参数直接通用。

## 安装

### 方法一：让 Codex 安装

在支持内置技能安装器的 Codex 环境中发送：

```text
$skill-installer 请从 https://github.com/mengkong30/ae-motion-production 安装 skills/ae-motion-production 目录中的技能。
```

也可以提供固定版本目录，便于复现：

```text
$skill-installer 请安装 https://github.com/mengkong30/ae-motion-production/tree/v1.0.1/skills/ae-motion-production 中的技能。
```

### 方法二：手动复制

1. 从 [Releases](https://github.com/mengkong30/ae-motion-production/releases) 下载 `ae-motion-production-v1.0.1.zip` 并解压。
2. 找到 `skills/ae-motion-production`，将这个完整目录放进用户级 `~/.agents/skills/`，或目标项目的 `.agents/skills/`。
3. 检查最终结构为 `.agents/skills/ae-motion-production/SKILL.md`，同级保留 `agents/` 和 `references/`。
4. 在 Codex 中检查技能是否可见；未出现时重启后再查看。已有同名版本时先备份自己的修改，避免重复安装造成选择混淆。

例如 Windows 用户级目录为 `%USERPROFILE%\.agents\skills\ae-motion-production`，macOS/Linux 为 `~/.agents/skills/ae-motion-production`。部分现有安装器或环境使用 `$CODEX_HOME/skills`（通常为 `~/.codex/skills`），以该环境实际识别的位置为准，不需要同时安装两份。

本仓库的 `skills/` 是分发目录；安装时复制其中的技能文件夹，不是只复制 README，也不是把整个仓库当成技能目录。安装位置与显式调用方式参见 [OpenAI 官方技能文档](https://learn.chatgpt.com/docs/build-skills)。

## 快速开始

安装后，附上参考视频、矢量素材或已有工程，再发送：

```text
使用 $ae-motion-production 制作这份参考中的二维动效。
先拆解参考的动作顺序和分件关系，再制作基础动作并自行检查。
关键帧集中到真正有效的中文控制器上。
交付可编辑 AEP、可播放预览和简短控件说明。
保留已有工程，另存新版本。
```

为减少来回补充，建议提供：素材路径、参考重点、需要保留的造型、画布尺寸、帧率、时长或循环要求、AE 版本、输出位置和最终格式。缺少的非关键参数可以让代理根据参考提出合理默认值。

**人物表情示例：**

```text
使用 $ae-motion-production，将已有角色的开心、好奇和舞动表情做成循环动画。
不要只让整个人物左右摇摆：身体要有蓄力和伸展，眼睛能先看向目标，
五官适度跟随，卷毛延迟回弹，手脚围绕同一节拍配合。
先检查三种代表动作，再扩展其余表情。轮廓弧度、遮挡和透明边缘都要检查。
每个表情保留独立的原生矢量合成，提供 AEP、MP4 和透明动图。
```

更多可复制任务说明见 [使用指南](docs/USAGE.md)。

## 完整文件结构

```text
ae-motion-production/
├── README.md
├── CHANGELOG.md
├── docs/
│   └── USAGE.md
└── skills/
    └── ae-motion-production/
        ├── SKILL.md
        ├── agents/
        │   └── openai.yaml
        └── references/
            ├── ae-implementation.md
            └── character-motion.md
```

| 文件 | 用途 |
| --- | --- |
| [SKILL.md](skills/ae-motion-production/SKILL.md) | 技能触发说明、制作约定、控制器与交付原则 |
| [openai.yaml](skills/ae-motion-production/agents/openai.yaml) | 技能显示名称、简短描述和默认提示词 |
| [AE 工程实施要点](skills/ae-motion-production/references/ae-implementation.md) | SVG 转换、路径绑定、脚本兼容、渲染恢复、轮播与前端还原 |
| [角色柔性动效](skills/ae-motion-production/references/character-motion.md) | 部位协调、曲线连续、透明输出、循环检查和批量失败处理 |
| [使用指南](docs/USAGE.md) | 任务模板、实际操作、验收清单及排查方法 |

技能目录中的四个文件完整保留了发布时的本地版本。仓库不捆绑 AE/Illustrator 软件、历史项目 AEP、第三方参考视频或图片；这些不属于技能本体。

## 交付和限制

典型交付是中文命名的 AEP、必要的矢量源文件、视频/动图预览和控件说明；具体按任务约定。在 AE 中进入目标合成，选择相应控制器，按 U 查看关键帧，再通过效果控件调整幅度和节奏。

动态遮罩和密集路径表达式会增加计算负担。单个角色渲染成功不代表全套组合也稳定。出现问题时分阶段恢复，必要时用独立成片汇总展示视频，同时保留每个角色的原生工程，并明确说明预览的组织方式。

本仓库提供制作方法，不承诺任意参考的一键复现或所有软件版本的自动兼容。

## 免责声明

本项目为非官方辅助技能，不保证生成结果或软件兼容性。使用前请备份工程、检查输出，并确认软件和素材授权。完整的使用风险与责任说明见 [免责声明](DISCLAIMER.md)。

## 版本

当前发布版本：**v1.0.1**。变更说明见 [CHANGELOG](CHANGELOG.md)。Release 附带完整 ZIP 和 SHA-256 校验文件。
