# 中医输入法词库
由于中医术语生僻词和古汉语较多，普通输入法无法满足，所以整理了一个词库供所有中医从业/爱好者使用。

本词库基于目前支持中文古汉语相关最好的输入法引擎 **RIME (中州韵输入法引擎)** ，mac/iphone/windows/andriod等多平台多系统都可以找到能够使用本词库（支持Rime引擎）的输入法;

-macOS系统： Squirrel输入法；
-Windows系统： Weasel小狼毫输入法；
-Iphone/Ipad：Hamster输入法；
-Andriod：Trime同文输入法 ；

## 1.📚词库内容分类
按中医内容分类，共包含四个分支：
1. **中医基础 (`TCM_basics.dict.yaml`)**：藏象、气血津液、阴阳五行、诊法等基础理论词汇。
2. **中药方剂 (`TCM_herbs.dict.yaml`)**：单味中药、经典方剂、中成药及古籍药名。
3. **针灸穴位 (`TCM_acupoints.dict.yaml`)**：十二经脉、奇经八脉、常用腧穴及国际标准代号。
4. **中医治疗 (`TCM_treatment.dict.yaml`)**：治则治法、针灸手法、推拿拔罐等临床词汇。
## 2.📖如何使用：
(以 macOS (Squirrel)为例)

### 第一步：下载并放置文件
1. 下载本仓库中的所有 `.dict.yaml` 文件。
2. 点击 Mac 右上角输入法图标，选择 **「用户设定」 (User Settings)**，系统会自动打开一个文件夹（路径通常为 `~/Library/Rime/`）。
3. 将下载的 5 个文件全部复制到该文件夹中。

### 第二步：挂载词库
在你的用户设定文件夹中，找到你正在使用的输入方案补丁文件（例如 `luna_pinyin.custom.yaml`）。在 `patch` 下方添加依赖或导入该词库：
```yaml
patch:
  # 以导入扩展词包为例（具体配置可根据个人方案调整）
  "translator/dictionary": luna_pinyin.extended
