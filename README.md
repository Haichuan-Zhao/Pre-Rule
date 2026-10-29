# Pre-Rule：项目文件规范

**当前版本：0.1.0**

Pre-Rule 是一项项目文件规划规范。Codex 根据当前任务和已有目录，安排代码、数据、结果与图片的位置，避免产生无用途文件。使用时无需额外准备输入文件或固定模板。

## 使用

在项目中调用 `$pre-rule`，例如：

```text
使用 $pre-rule，完成当前任务，并按实际工作阶段组织项目文件。
```

技能允许自动选择，但不能保证每次请求都会自动触发；需要明确使用时直接写 `$pre-rule`。用户本次指定的文件结构和其他具体要求优先。

首次安装时，克隆本仓库并将技能复制到 Codex 的技能目录：

```bash
git clone https://github.com/Haichuan-Zhao/Pre-Rule.git
cd Pre-Rule
mkdir -p ~/.codex/skills
cp -R .agents/skills/pre-rule ~/.codex/skills/
```

如果使用 Skills Manager 管理技能，也可以在本仓库目录向 Codex 发送：

```text
使用 $manage-skills，将本项目 .agents/skills/pre-rule 作为本地来源安装并部署到 Codex。
```

已通过 Skills Manager 安装的技能，在修改源文件后用同一管理器更新并检查 Codex 部署状态。

## 目录示例

数据准备和各实验阶段分别组织；每个阶段的入口、数据、结果和图片放在一起。以下只是示例，文件和目录按实际需要创建。

```text
proj/                            # 项目名称按具体用途取简称
├── README.md                    # 按需维护
├── data/
│   ├── raw/                     # 原始数据
│   ├── pro/                     # 公共处理结果
│   ├── fig/                     # 数据准备阶段的图
│   └── pre.ipynb
└── exp/
    ├── 01_feat/
    │   ├── feat.ipynb
    │   ├── data/                # 阶段专用数据
    │   ├── res/                 # 阶段结果
    │   ├── fig/                 # 阶段图片
    │   └── README.md            # 按需维护
    └── 02_win/                  # 需要时创建
```

## 主要规则

- 按任务创建文件，不预建空目录、占位文件、演示数据或多余的计划、日志和报告。说明文件在确有用途时创建或更新。
- 项目、目录和文件使用简洁、易理解的名称，优先采用英文单词或常用缩写；自编代码文件名不得用 `run` 表示运行入口，不区分大小写。
- 已有项目优先沿用合适的结构；共享数据优先引用同一来源。移动、覆盖或清理前核对依赖和保留用途。
- 所有自编科研和分析逻辑直接写在相应阶段的 notebook 代码单元中，不能用自编脚本或命令行计算后再补 notebook。第三方库可正常使用，非科研分析的工程代码按项目需要组织。
- 图片仅在任务需要时生成，保存在相应阶段；默认中文标注、高质量 JPG，特殊交付格式按用户要求调整。

详细规则见 [技能入口](.agents/skills/pre-rule/SKILL.md)、[项目文件规划](.agents/skills/pre-rule/references/project-layout.md)和[图片文件管理](.agents/skills/pre-rule/references/figures.md)。

## 版本与许可

技能版本号以 [SKILL.md](.agents/skills/pre-rule/SKILL.md) 为准；日常修改、检查和同步不递增版本号。项目采用 [MIT 许可证](LICENSE)。
