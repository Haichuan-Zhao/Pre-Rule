# Pre-Rule：项目规范

**当前版本：0.1.2**

Pre-Rule 是一项项目探索规范。Codex 根据当前任务和已有目录，以人容易理解的用途和数据流安排代码、数据、结果与图片，尽量减少文件和目录，并解释主要产物。使用时无需额外准备输入文件或固定模板。

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

数据、处理 notebook 和数据可视化放在 `data/`；实验代码、结果和图表就近放在 `exp/` 下。以下只是单个实验的一种示例，不要求固定子目录、编号或文件名；只按实际需要创建目录，每个项目自有内容目录维护简短的 `readme.md`。

```text
proj/                            # 项目名称按具体用途取简称
├── readme.md
├── data/                        # 数据及其处理、可视化
│   ├── readme.md
│   ├── pre.ipynb                # 数据处理、参数辨识及可视化代码
│   ├── raw/                     # 原始数据，可按需分类
│   │   ├── readme.md
│   │   └── obs.csv
│   ├── pre/                     # 处理后数据，可按需分类
│   │   ├── readme.md
│   │   └── obs.csv
│   └── data.jpg                 # 数据可视化图片
└── exp/
    ├── readme.md
    ├── model.ipynb              # 读取 data/ 中的数据，进行实验
    ├── met.csv                  # 实验结果
    └── model.jpg                # 实验图表
```

多个实验可在 `exp/` 下按主题分别建目录；文件较多时，也可在对应实验目录内按需建立结果或图片子目录。单纯的数据准备任务无需创建 `exp/`。

## 主要规则

- 原始数据、处理后数据，以及数据处理、检查、可视化的 notebook 和图片放在 `data/`；可按需使用 `raw/`、`pre/` 分类。
- 数据参数辨识、拟合和标定默认属于数据准备，代码、必要参数结果及图表放在 `data/`，即使当前任务只做辨识，也不因此创建 `exp/`。
- 实验 notebook 放在 `exp/` 下，直接读取数据；每项实验的结果和图表与其实验代码就近存放，不复制输入数据或把数据处理流程写进实验目录。
- 在 notebook 中编写科研分析和绘图代码，记录方法、结果及必要局限。
- 绘制直观、可追溯的图表，并用简洁的目录说明交代文件作用与数据流向。
- 按容易查找和理解的用途将相关文件就近存放；优先复用已有 notebook，只在确有助于阅读或查找时拆分文件或目录。
- 仅保存用户需要、后续要使用或复现结果所必需的文件，不为每次拟合或检查单独生成文件；合并结果时保持条件、单位和必要证据清楚。

完整规则和目录示例见 [SKILL.md](.agents/skills/pre-rule/SKILL.md)。

## 绘图偏好

- 以直观易懂为首要目标，优先使用折线图、散点图、柱状图等常见二维图表；图中说清比较对象、工况、变量和单位。
- 优先白底、清晰坐标轴和少量配色；对比曲线同时使用不同颜色、线型或标记，多个子图按工况或变量有规律地排列。
- 图表默认中文标注、高质量 JPG；投稿要求或用户指定的格式、语言优先。图表数据可追溯到原始或结果文件，绘图代码保存在所属 notebook 中。

视觉参考包括 [Tao 等（2024）](https://www.nature.com/articles/s41467-024-54454-0)和 [Che 等（2026）](https://www.nature.com/articles/s41467-025-67565-z)论文中的分组和对比图，以及用户提供的多工况曲线示例。规则优先采用其中清楚、易读的做法。

## 版本与许可

技能版本号以 [SKILL.md](.agents/skills/pre-rule/SKILL.md) 为准；日常修改、检查和同步不递增版本号。项目采用 [MIT 许可证](LICENSE)。
