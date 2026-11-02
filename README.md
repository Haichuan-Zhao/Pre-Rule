# Pre-Rule：项目规范

**当前版本：0.1.1**

Pre-Rule 是一项项目探索规范。Codex 根据当前任务和已有目录，安排代码、数据、结果与图片的位置，有逻辑地开展实验和绘图，并解释主要产物。使用时无需额外准备输入文件或固定模板。

## 使用

首次安装时，可以直接向 Codex 发送：

```text
请从 GitHub 仓库 https://github.com/Haichuan-Zhao/Pre-Rule 安装 .agents/skills/pre-rule 技能，供我的 Codex 使用。
```

安装后，在项目中调用 `$pre-rule`，例如：

```text
使用 $pre-rule，完成当前任务，按实际工作阶段组织文件，并说明实验结果与主要产物。
```

技能允许自动选择，但不能保证每次请求都会自动触发；需要明确使用时直接写 `$pre-rule`。用户本次指定的文件结构和其他具体要求优先。

也可以手动安装：

```bash
git clone https://github.com/Haichuan-Zhao/Pre-Rule.git
cd Pre-Rule
mkdir -p ~/.codex/skills
cp -R .agents/skills/pre-rule ~/.codex/skills/
```

安装后如果技能未显示，可尝试重启 Codex。详见 [Codex 技能文档](https://learn.chatgpt.com/docs/build-skills)。

## 目录示例

原始和预处理数据集中存放，实验 notebook 直接读取；代码、结果和图片按实验阶段组织。每个项目内容目录都有简短的 `readme.md`。以下只是示例，文件和目录按实际需要创建。

```text
proj/                            # 项目名称按具体用途取简称
├── readme.md
├── data/
│   ├── readme.md
│   ├── raw/                     # 原始数据
│   │   ├── readme.md
│   │   └── obs.csv
│   ├── pre/                     # 处理后数据
│   │   ├── readme.md
│   │   └── obs.csv
│   └── pre.ipynb
└── exp/
    ├── readme.md
    └── 01_feat/
        ├── readme.md
        ├── feat.ipynb
        ├── res/                 # 本阶段实验结果
        │   ├── readme.md
        │   └── met.csv
        └── fig/
            ├── readme.md
            └── feat.jpg
```

## 主要规则

- 集中管理原始与预处理数据，按实验阶段组织代码、结果和图表。
- 在 notebook 中编写科研分析和绘图代码，记录方法、结果及必要局限。
- 绘制直观、可追溯的图表，并用简洁的目录说明交代文件作用与数据流向。
- 按任务创建文件，复用已有数据和结果，避免不必要的副本。

完整规则和目录示例见 [SKILL.md](.agents/skills/pre-rule/SKILL.md)。

## 绘图偏好

- 以直观易懂为首要目标，优先使用折线图、散点图、柱状图等常见二维图表；图中说清比较对象、工况、变量和单位。
- 优先白底、清晰坐标轴和少量配色；对比曲线同时使用不同颜色、线型或标记，多个子图按工况或变量有规律地排列。
- 图表默认中文标注、高质量 JPG；投稿要求或用户指定的格式、语言优先。图表数据可追溯到原始或结果文件，绘图代码保存在所属 notebook 中。

视觉参考包括 [Tao 等（2024）](https://www.nature.com/articles/s41467-024-54454-0)和 [Che 等（2026）](https://www.nature.com/articles/s41467-025-67565-z)论文中的分组和对比图，以及用户提供的多工况曲线示例。规则优先采用其中清楚、易读的做法。

## 版本与许可

技能版本号以 [SKILL.md](.agents/skills/pre-rule/SKILL.md) 为准；日常修改、检查和同步不递增版本号。项目采用 [MIT 许可证](LICENSE)。
