# 缺报有序标签的一致性与分歧定位

本项目是虚构台架数据分析需求的初始输入材料。只有Python文件读取器，尚未实现题目要求的统计检验、求解、配准或分析功能。所有仪器、试件、对象与人工标签均为合成，不涉及模型训练、生成结果或运动轨迹。

## 字段与单位

每行含unit_id、rater、revision和category，空类别未报。重复键高版本替代低版本，平级内容冲突拒绝；刻度顺序由labels.json给定。

material-index.json记录全部输入内容哈希；fixtures是只读原始资料，计算输出应放.workspace-output。手算例和配置口径在完整User Prompt中，输入读取测试不代表分析功能已完成。

## 运行已有读取器

Python 3.11以上，标准库即可，不需安装第三方依赖。

    python -m src.label_reader fixtures/labels.csv
    python -m compileall -q src tests
    python -m unittest discover -s tests -v

## 固定容器

    docker build -t ordinal-agreement:local .
    docker run --rm ordinal-agreement:local

容器镜像以完整digest固定，默认仅检查输入契约；实现新增分析功能所需依赖由开发者明确登记。
