# 中医输入法词库
由于中医专业词汇和古汉语较多，普通输入法无法满足，所以整理了一个词库供所有中医从业/爱好者使用。

本词库基于目前对中文及古汉语支持最好的开源输入法引擎 **RIME** 构建。支持mac/ios/windows/andriod等多种常见平台/系统，可以在以下系统的常用 RIME 客户端中导入使用本项目：

1. macOS系统：推荐使用 「Squirrel输入法」；
2. Windows系统： 推荐使用「Weasel小狼毫输入法」；
3. Iphone/Ipad：推荐使用「Hamster输入法」；
4. Andriod：推荐使用「Trime同文输入法」或 「Fcitx5输入法」；

   
## 1.📚词库内容分类
计划按中医内容分类：（内容动态更新，如资料增多可能会分多个文件单独存放，比如穴位文件就分了3个文件来管理：14正经的362个穴位+51经外奇穴+董氏奇穴。可以按需要单独选择，比如只需362正经穴位的，就只把TCM_acupoints_standard362.dict.yaml这个文件放进你的输入法包即可）
1. **中医基础 (`TCM_basics.dict.yaml`)**：藏象、气血津液、阴阳五行、诊法等基础理论词汇。
2. **中药方剂 (`TCM_herbs.dict.yaml`)**：单味中药、经典方剂、中成药及古籍药名。
3. **针灸穴位_362 (`TCM_acupoints_standard362.dict.yaml`)**：十四正经的穴位（362个腧穴及国际标准代号）。
4. **针灸穴位_51 (`TCM_acupoints_extra51.dict.yaml`)**：经外奇穴（51个未归经的穴位及国际标准代号）。
5. **针灸穴位_dong (`TCM_acupoints_dong.dict.yaml`)**：董氏奇穴（董氏奇穴合集）。
6. **中医治疗 (`TCM_treatment.dict.yaml`)**：治则治法、针灸手法、推拿拔罐等临床词汇。

## 2.📖如何使用：(以 macOS (Squirrel)为例)

### 第一步：下载并放置文件
1. 下载本仓库中所有以`TCM_xxxx.dict.yaml`格式命名的文件。（可按自己的需要选择下载，配置过程完全一样，需要哪个下载哪个，每个文件都是独立无关联的）
2. 点击 Mac 右上角输入法图标，选择 **「Settings... / 用户设定」**，系统会自动打开一个配置文件夹。
3. 将下载的4个词库文件全部复制到该文件夹中。

### 第二步：挂载词库（请根据你使用的 Rime 配置选择方案）

#### 💡 方案 A：如果你使用的是目前主流的「雾凇拼音 (Rime-ice)」配置
雾凇拼音自带完美的自定义扩展机制，最推荐此方法：
1. 在打开的配置文件夹中，找到 rime_ice.dict.yaml（雾凇主词库入口）文件。
2. 在文件中的 import_tables: 列表末尾（建议在 cn_dicts/others 之后）追加你需要的文件名称：
   ```yaml
      - TCM_basics
      - TCM_herbs
      - TCM_treatment
   ...
3. 保存
#### 💡 方案 B：如果你使用的是 Rime 默认的「朙月拼音 (luna_pinyin)」

1. 在打开的配置文件夹中，新建 luna_pinyin.extended.dict.yaml文件：
   ```yaml
   # Rime dictionary
   # encoding: utf-8
   ---
   name: luna_pinyin.extended
   version: "1.0"
   sort: by_weight
   import_tables:
     - luna_pinyin
     - TCM_basics
     - TCM_herbs
     - TCM_treatment
   ...

2. 找到或新建 `luna_pinyin.custom.yaml`（简体可用 luna_pinyin_simp.custom.yaml）文件，在 patch: 下方添加以下代码：
   ```yaml
   patch:
     "translator/dictionary": luna_pinyin.extended
   ...
3. 保存
   
### 第三步：重新部署生效
完成上述操作后，点击 Mac 右上角输入法图标，点击 「Deploy / 重新部署」，即可开始使用。

### 第四步：测试是否成功：
在每个词库中都添加了一个不存在的长词条作为输入法验证方式，`气室门天牖	qi shi men tian you` 请直接输入拼音看是否可以显示出来，可显示即为成功安装。
