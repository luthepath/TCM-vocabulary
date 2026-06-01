# 中医输入法词库
由于中医术语生僻词和古汉语较多，普通输入法无法满足，所以整理了一个词库供所有中医从业/爱好者使用。

本词库基于目前对中文及古汉语支持最好的开源输入法引擎 **RIME (中州韵)** 构建。支持跨平台多系统同步，你可以在以下系统的常用 RIME 客户端中导入本项目：

1. macOS系统：推荐使用 「Squirrel输入法」；
2. Windows系统： 推荐使用「Weasel小狼毫输入法」；
3. Iphone/Ipad：推荐使用「Hamster输入法」；
4. Andriod：推荐使用「Trime同文输入法」或 「Fcitx5输入法」；

   
## 1.📚词库内容分类
按中医内容分类，共包含四个分支：
1. **中医基础 (`TCM_basics.dict.yaml`)**：藏象、气血津液、阴阳五行、诊法等基础理论词汇。
2. **中药方剂 (`TCM_herbs.dict.yaml`)**：单味中药、经典方剂、中成药及古籍药名。
3. **针灸穴位 (`TCM_acupoints.dict.yaml`)**：十二经脉、奇经八脉、常用腧穴及国际标准代号。
4. **中医治疗 (`TCM_treatment.dict.yaml`)**：治则治法、针灸手法、推拿拔罐等临床词汇。

## 2.📖如何使用：(以 macOS (Squirrel)为例)

### 第一步：下载并放置文件
1. 下载本仓库中的所有以 `.dict.yaml` 结尾的词库文件。
2. 点击 Mac 右上角输入法图标，选择 **「Settings... / 用户设定」**，系统会自动打开一个配置文件夹。
3. 将下载的文件全部复制到该文件夹中。

### 第二步：挂载词库（请根据你使用的 Rime 配置选择方案）

#### 💡 方案 A：如果你使用的是目前主流的「雾凇拼音 (Rime-ice)」配置
雾凇拼音自带完美的自定义扩展机制，最推荐此方法：
1. 在刚刚打开的配置文件夹中，**新建**一个纯文本文件，命名为 `rime_ice.custom.dict.yaml`。
2. 将以下内容复制进去并保存：
   ```yaml
   # Rime dictionary
   ---
   name: rime_ice.custom
   version: "2026.06"
   sort: by_weight
   use_preset_vocabulary: true
   import_tables:
     - TCM_basics
     - TCM_herbs
     - TCM_acupoints
     - TCM_treatment
   ...
#### 💡 方案 B：如果你使用的是 Rime 默认的「朙月拼音 (luna_pinyin)」

1. 在配置文件夹中，新建一个纯文本文件，命名为 `luna_pinyin.extended.dict.yaml`，复制以下内容并保存：
   ```yaml
   # Rime dictionary
   ---
   name: luna_pinyin.extended
   version: "2026.06"
   sort: by_weight
   use_preset_vocabulary: true
   import_tables:
     - luna_pinyin
     - rime_tcm
   ...

2. 找到或新建 `luna_pinyin_simp.custom.yaml` 文件，在 patch: 下方添加以下代码：
   ```yaml
   patch:
     "translator/dictionary": luna_pinyin.extended
   ...

### 第三步：重新部署生效
完成上述操作后，点击 Mac 右上角输入法图标，点击 「Deploy / 重新部署」，即可开始使用。
