### 001. 常见饮用水类型中英文对照
| 中文名称    | 英文表达                    | 音标（英式 / 美式）                                         |
| ------- | ----------------------- | --------------------------------------------------- |
| 自来水     | **tap water**           | /tæp ˈwɔːtə/（英） /tæp ˈwɔːtər/（美）                    |
| 矿泉水     | **mineral water**       | /ˈmɪnərəl ˈwɔːtə/（英） /ˈmɪnərəl ˈwɔːtər/（美）          |
| 纯净水     | **purified water**      | /ˈpjʊərɪfaɪd ˈwɔːtə/（英） /ˈpjʊrəfaɪd ˈwɔːtər/（美）     |
| 蒸馏水     | **distilled water**     | /dɪˈstɪld ˈwɔːtə/（英） /dɪˈstɪld ˈwɔːtər/（美）          |
| 开水（白开水） | **boiled water**        | /bɔɪld ˈwɔːtə/（英） /bɔɪld ˈwɔːtər/（美）                |
| 凉白开     | **cooled boiled water** | /kuːld bɔɪld ˈwɔːtə/（英） /kuːld bɔɪld ˈwɔːtər/（美）    |
| 温水      | **warm water**          | /wɔːm ˈwɔːtə/（英） /wɔːrm ˈwɔːtər/（美）                 |
| 热水      | **hot water**           | /hɒt ˈwɔːtə/（英） /hɑːt ˈwɔːtər/（美）                   |
| 冷水（凉水）  | **cold water**          | /kəʊld ˈwɔːtə/（英） /koʊld ˈwɔːtər/（美）                |
| 冰水      | **iced water**          | /aɪst ˈwɔːtə/（英） /aɪst ˈwɔːtər/（美）                  |
| 桶装水     | **bottled water**       | /ˈbɒtld ˈwɔːtə/（英） /ˈbɑːtld ˈwɔːtər/（美）             |
| 山泉水     | **spring water**        | /sprɪŋ ˈwɔːtə/（英） /sprɪŋ ˈwɔːtər/（美）                |
| 过滤水     | **filtered water**      | /ˈfɪltəd ˈwɔːtə/（英） /ˈfɪltərd ˈwɔːtər/（美）           |
| 气泡水     | **sparkling water**     | /ˈspɑːklɪŋ ˈwɔːtə/（英） /ˈspɑːrklɪŋ ˈwɔːtər/（美）       |
| 电解质水    | **electrolyte water**   | /ɪˈlɛktrəlaɪt ˈwɔːtə/（英） /ɪˈlɛktroʊlaɪt ˈwɔːtər/（美） |

---
### 002. nonage
* **nonage 未成年的阶段**
| 中文    | 英文              | 说明                                     |
| ----- | --------------- | -------------------------------------- |
| 未成年人  | **minor**       | 最常见的法律用词，表示未达法定年龄的人                    |
| 未成年   | **underage**    | 形容词，表示“未达法定年龄”的状态（如：underage drinking） |
| 青少年   | **juvenile**    | 多用于法律、社会学中，侧重“青少年违法”情境                 |
| 未成年时期 | **nonage**（较正式） | 书面语，或文学、法律中使用，表示“未成年状态”                |
* **示例**
  - He is still a minor and cannot sign legal documents.
  > 他还是未成年人，不能签署法律文件。

  - Selling alcohol to underage people is illegal.
  > 向未成年人售卖酒类是违法的。

  - The juvenile court handled the case.
  > 这起案件由少年法庭审理。

---
### 003. decode衍生
* **编码（Encoding） vs 加密（Encryption）对比表**
| 项目        | 编码（Encoding）                  | 加密（Encryption）                |
| --------- | ----------------------------- | ----------------------------- |
| 📌 目的     | 数据格式转换，便于传输、存储或读取             | 数据保密，防止未授权访问                  |
| 🧠 是否可逆   | ✅ 可逆（可用解码 decode 还原）          | ✅ 可逆（需正确密钥或算法 decrypt）        |
| 🔑 是否需要密钥 | ❌ 不需要密钥                       | ✅ 需要密钥（公钥 / 私钥 / 对称密钥）        |
| 📄 举例格式   | Base64, URL编码, Unicode, ASCII | AES, RSA, DES, TLS, HTTPS     |
| 📦 常见用途   | 网络传输、文件保存、邮件编码                | 网络安全、隐私保护、加密通信                |
| 🧩 英文动词   | `encode`（编码） / `decode`（解码）   | `encrypt`（加密） / `decrypt`（解密） |
| 💡 举例     | 把图片编码成Base64文本                | 把聊天记录加密后通过微信传输                |
| 👀 可读性    | 通常可读（如 Base64 是可打印字符）         | 通常不可读（加密数据是乱码）                |
* **示例图**
``` css
[原始数据]
     ↓
 ┌─────────────┐         ┌─────────────┐
 │   编码 encode│         │   加密 encrypt│
 └─────────────┘         └─────────────┘
     ↓                       ↓
 [编码数据]           [加密数据（乱码）]
     ↓                       ↓
 ┌─────────────┐         ┌─────────────┐
 │   解码 decode│         │   解密 decrypt│
 └─────────────┘         └─────────────┘
     ↓                       ↓
[原始数据]            [原始数据]
```
* **总结类比**
| 中文 | 常用英文          | 说明         |
| -- | ------------- | ---------- |
| 编码 | code / encode | 编程、通信、存储数据 |
| 解码 | decode        | 还原编码的信息    |
| 加密 | encrypt       | 更强调保密性     |
| 解密 | decrypt       | 与加密相对      |
* **code（作动词）**
  - 通常表示 “编码” 或 “用代码表示”
  - 并 不特指加密，但可以是加密的一种表现形式
  - 示例:
    * The message was coded in Morse.（这条消息是用摩尔斯电码编码的。）
    * He coded the data before transmission.（他在传输前对数据进行了编码。）
  > 在某些语境中，“code” 可泛指“加密”或“使信息不易理解”，但通常更广义。
* **encode 与 decode（更标准表达）**
  - encode = 编码 / 加密
  - decode = 解码 / 解密
  - 示例:
    * The file is encoded in Base64.（这个文件是 Base64 编码的。）
    * I used a tool to decode the message.（我用工具解码了这条消息。）
* **encrypt 与 decrypt（更明确表示“加密 / 解密”）**
  - encrypt = 加密（安全性、机密性）
  - decrypt = 解密
  - 示例:
    * This email is encrypted for security.（这封邮件已加密以确保安全。）
    * He decrypted the password.（他解密了密码。）

---
### 004. treat 衍生
* **treat 的常见含义（动词）**
| 含义        | 中文解释         | 例句                                                      |
| --------- | ------------ | ------------------------------------------------------- |
| 1. **治疗** | 对疾病、伤情等进行处理  | The doctor **treated** the patient for flu.（医生为病人治疗流感。） |
| 2. 对待     | 以某种方式对待某人/某事 | He **treats** her with respect.（他对她很尊重。）                |
| 3. 请客     | 付款替他人买东西或吃饭等 | Let me **treat** you to lunch.（让我请你吃午饭吧。）               |
| 4. 处理     | 技术或物理上的加工或处理 | The wood was **treated** with chemicals.（木材经过化学处理。）     |
* **衍生词**
| 单词            | 词性  | 含义        |
| ------------- | --- | --------- |
| **treatment** | 名词  | 治疗，处理方式   |
| **treatable** | 形容词 | 可治疗的      |
| **untreated** | 形容词 | 未治疗的，未加工的 |
* **更多“治疗”相关的英文表达对比****
| 中文   | 英文             | 说明               |
| ---- | -------------- | ---------------- |
| 治疗   | **treat**      | 泛指诊治，适用于医生、药物等处理 |
| 治疗   | **cure**       | 强调“治愈”，使完全恢复健康   |
| 疗法   | **therapy**    | 系统性治疗，尤指心理/物理疗法  |
| 药物治疗 | **medication** | 使用药物来治疗          |
| 手术治疗 | **surgery**    | 通过手术手段治疗         |
* **mistreat 的意思**
  - 动词：虐待、虐待对待、不公对待
  - 即 “不当对待” 或 “以粗暴/残酷方式对人或动物等进行对待”
  - 词源拆解
    * | 部分                          | 含义    |
| --------------------------- | ----- |
| **mis-**                    | 错误，坏  |
| **treat**                   | 对待，处理 |
| → **mistreat = 错误地对待 → 虐待** |       |
    * 示例
      - He was mistreated by his employer. 他被雇主虐待了。
      - It’s cruel to mistreat animals. 虐待动物是一种残忍行为。
* **类比记忆**
| 单词                | 含义        | 对应中文 |
| ----------------- | --------- | ---- |
| **treat**         | 对待 / 治疗   | 对待   |
| **mistreat**      | 不当对待 / 虐待 | 虐待   |
| **maltreat**（更正式） | 虐待        | 虐待   |
| **entreat**       | 恳求、乞求     | 恳求   |
| **retreat**       | 撤退、退却     | 撤退   |
*  **treat 词根词汇树**
  > 核心词根：treat --> 来自拉丁语 tractare，意为 “对待、处理、拉、引导”
  - **常见派生词汇**
  | 单词               | 构词结构           | 中文含义       | 说明/记忆点                |
| ---------------- | -------------- | ---------- | --------------------- |
| **treat**        | treat          | 对待；治疗      | 最基本形式                 |
| **treatment**    | treat + -ment  | 治疗；处理方式    | “-ment”表行为或结果         |
| **mistreat**     | mis- + treat   | 虐待，不当对待    | “mis-” 表错误            |
| **maltreat**     | mal- + treat   | 虐待         | “mal-” 也表坏/恶劣（法语词根）   |
| **retreat**      | re- + treat    | 撤退；退却      | “re-”表示回、向后           |
| **entreat**      | en- + treat    | 恳求、祈求      | “en-”表示使进入某状态；=使对待→恳求 |
| **treatable**    | treat + -able  | 可治疗的       | “-able”表示“可……”        |
| **untreated**    | un- + treated  | 未治疗的；未经处理的 | “un-”表示否定             |
| **well-treated** | well + treated | 被善待的       | “well”表示良好            |
| **ill-treated**  | ill + treated  | 被虐待的       | “ill”=坏（不好的方式）        |
* **特别说明**
| 前缀       | 含义    | 示例              |
| -------- | ----- | --------------- |
| **mis-** | 错误，坏  | mistreat = 错误对待 |
| **mal-** | 恶劣，坏  | maltreat = 恶劣对待 |
| **re-**  | 向后，再次 | retreat = 后退    |
| **en-**  | 使进入   | entreat = 恳求    |
*  ****一句话记忆口诀****
> treat 是“对待”，加上 mis 就变坏，加上 en 就成“恳求”，加上 re 就“退”。

---
### 005. 词源项目
* **词源项目，词汇分析**
| 需求方向       | 推荐项目                          |
| ---------- | ----------------------------- |
| 探查单词词源树    | ety-python / etymology-viewer |
| 整篇文章里的词源统计 | macro-etym / etymrs           |
| 自建词源数据库或服务 | etymology-db + 自定义开发          |
| 命令行快速查词源   | etym-cli                      |
| 学习词根整体列表   | generated-english-roots-list  |
| 多语言高级分析    | Etymon（深度学习）                  |
* **项目表格**
| 项目名称                         | 简要介绍                   | 地址链接                                                                     |
| ---------------------------- | ---------------------- | ------------------------------------------------------------------------ |
| ety-python                   | 单词词源树分析工具（Python）      | [点此访问](https://github.com/jmsv/ety-python)                               |
| etymology-viewer             | 词源可视化 Web 应用           | [点此访问](https://github.com/thepushkarp/etymology-viewer)                  |
| etym-cli                     | 命令行词源查询（基于 etymonline） | [点此访问](https://github.com/agmmnn/etym-cli)                               |
| macro-etym                   | 对整篇文章做词源统计分析           | [点此访问](https://github.com/JonathanReeve/macro-etym)                      |
| etymrs                       | Rust 实现的大规模词源统计分析工具    | [点此访问](https://github.com/DKenefake/etymrs)                              |
| etymology-db                 | 英语词源数据库，结构化数据          | [点此访问](https://github.com/droher/etymology-db)                           |
| word\_etymologist            | 用 AI 判断单词来自哪种语言        | [点此访问](https://github.com/kpsychas/word_etymologist)                     |
| generated-english-roots-list | 英语常见词根词表，适合学习构词法       | [点此访问](https://github.com/WithEnglishWeCan/generated-english-roots-list) |
| Etymon                       | 词源深度学习项目，多语言支持         | [点此访问](https://github.com/Merterm/Etymon)                                |
* **英语词源分析项目推荐（带项目地址）**
1. **ety-python**
  - 🔗 项目地址：https://github.com/jmsv/ety-python
  - 📖 介绍：
    * 一个 Python 库，用于分析英文单词的词源树（etymology tree），支持命令行操作。可以递归追踪词源至拉丁语、希腊语或其他语言源头。
✅ 示例命令：ety tree democracy

2. **etymology-viewer**
  - 🔗 项目地址：https://github.com/thepushkarp/etymology-viewer
  - 📖 介绍：
    * 一个词源可视化 Web 应用，输入英文单词后生成词源分支图。前端界面友好，适合学生和语言爱好者快速查看词源。

3. **etym-cli**
  - 🔗 项目地址：https://github.com/agmmnn/etym-cli
  - 📖 介绍：
    * 基于 etymonline.com 官网的命令行词源查询工具。
✅ 快捷命令：etym love 直接返回 love 的词源解释（需联网）。

4. **macro-etym**
  - 🔗 项目地址：https://github.com/JonathanReeve/macro-etym
  - 📖 介绍：
    * 可以对整篇英文文章或文本文件进行词源统计分析，比如分析其中多少词源来自希腊语、法语、拉丁语等。适合语言研究或词源兴趣者。

5. **etymrs**
  - 🔗 项目地址：https://github.com/DKenefake/etymrs
  - 📖 介绍：
    * 一个用 Rust 编写的高性能英文文本词源分析工具。能快速处理大文本数据并生成词源统计。

6. **etymology-db**
  - 🔗 项目地址：https://github.com/droher/etymology-db
  - 📖 介绍：
    * 一个开放的英语词源数据库，包含超过 380 万条词源路径数据，可供自建词源服务或用作语言研究数据源。

7. **word_etymologist**
  - 🔗 项目地址：https://github.com/kpsychas/word_etymologist
  - 📖 介绍：
    * 使用神经网络模型自动预测英文单词的来源语言（例如来自拉丁语还是希腊语），适合构词学和自然语言处理研究。

8. **generated-english-roots-list**
  - 🔗 项目地址：https://github.com/WithEnglishWeCan/  - generated-english-roots-list
📖 介绍：
    * 一个由教育组织维护的常见英语词根表，包含常见前缀、词根、后缀及示例单词，适合学习构词法。

9. **Etymon**
  - 🔗 项目地址：https://github.com/Merterm/Etymon
  - 📖 介绍：
    * 结合深度学习和词源数据库的项目，可生成多语言词源树，分析语言演变路径。适合高级语言研究者使用。

---
### 006. formation
* ****information的构词分析:****
| 单词              | 构词结构                                         | 含义说明                           |
| --------------- | -------------------------------------------- | ------------------------------ |
| **information** | **in-**（进入） + **form**（形成）+ **-ation**（名词后缀） | 指“将内容**组织、形成**进入大脑”的过程 → 信息、知识 |
  - 本义类似于：被组织起来的知识
  - 也可以理解为“被形成的东西” → 信息。
* ****formation 的构词分析:****
| 单词            | 构词结构                             | 含义说明               |
| ------------- | -------------------------------- | ------------------ |
| **formation** | **form**（形成） + **-ation**（过程、结果） | “形成”的过程或结果，强调结构、组织 |
  - 表达 事物的形成、构成或排列，常用于军事、地质、组织结构等领域。
  - 示例:
    * The formation of clouds（云的形成）
    * The troops marched in formation（部队按队形行进）
* ****malformation 的构词分析:****
| 单词               | 构词结构                               | 含义说明               |
| ---------------- | ---------------------------------- | ------------------ |
| **malformation** | **mal-**（坏，错误） + **formation**（形成） | 错误或异常的形成 → 畸形、发育不良 |
  - 📘 词根 mal- 来自拉丁语，表示“坏的，恶劣的”（同类如：malware, malfunction, malnutrition）
  - 示例:
    * malformation = 坏的形成 → 身体或结构的发育异常 → 畸形
    * The baby was born with a heart malformation. 这个婴儿出生时心脏畸形。
* ****总结对比表****
| 单词               | 构词结构                | 含义           |
| ---------------- | ------------------- | ------------ |
| **form**         | 拉丁词根，意为“形状，形成”      | 形成；表格；形式     |
| **formation**    | form + -ation       | 形成；结构；队形     |
| **information**  | in- + form + -ation | 信息（被组织起来的知识） |
| **malformation** | mal- + formation    | 畸形（错误的形成）    |
* 类似的构词模式
| 单词                 | 解释                 |
| ------------------ | ------------------ |
| **transformation** | 转变（trans- = 横过、变）  |
| **reformation**    | 改革、改良（re- = again） |
| **deformation**    | 变形（de- = 向下/失去）    |
| **conformation**   | 构造、构型（con- = 一起）   |

---
### 007. form 词根家族词汇表
* ****form 词根词汇树****
  - 🔤 词根：form
  - 📖 来源：拉丁语 forma，意为 形状、外观、构造、形成。
* ****核心词汇表(含构词法)****
| 单词                 | 构词结构                   | 中文含义      | 举例                                          |
| ------------------ | ---------------------- | --------- | ------------------------------------------- |
| **form**           | -                      | 形式；表格；构成  | Please fill out the **form**.               |
| **formation**      | form + -ation          | 形成；构造；队形  | Cloud **formation** is fascinating.         |
| **information**    | in-（进入）+ form + -ation | 信息，资料     | We need more **information**.               |
| **malformation**   | mal-（坏）+ formation     | 畸形；发育异常   | The scan showed a heart **malformation**.   |
| **transformation** | trans-（转变）+ formation  | 转变；变形；改革  | A dramatic **transformation** occurred.     |
| **reformation**    | re-（再次）+ formation     | 改革；改良     | The school went through a **reformation**.  |
| **deformation**    | de-（脱离/变坏）+ formation  | 变形；畸形；损毁  | The metal showed signs of **deformation**.  |
| **conformation**   | con-（一起）+ formation    | 构型；一致性    | The molecule’s **conformation** is crucial. |
| **uniform**        | uni-（统一）+ form         | 制服；统一的    | Students wear a school **uniform**.         |
| **perform**        | per-（彻底）+ form         | 表演；执行     | He will **perform** a song tonight.         |
| **platform**       | plat(eau) + form       | 平台；舞台     | Twitter is a social media **platform**.     |
| **formulate**      | form + -ulate（使成为）     | 制定；规划     | Scientists **formulate** theories.          |
| **formality**      | form + -ality          | 礼节；正式手续   | Skip the **formalities** and begin.         |
| **formless**       | form + -less（无）        | 无形的；杂乱无章的 | The poem had a **formless** structure.      |
* **构词法总结**
| 前缀/后缀      | 含义      | 示例词                       |
| ---------- | ------- | ------------------------- |
| **in-**    | 进入、内部   | information               |
| **mal-**   | 错误、坏    | malformation              |
| **re-**    | 再次、重新   | reformation               |
| **trans-** | 横越、转变   | transformation            |
| **de-**    | 去掉、向下   | deformation               |
| **con-**   | 一起、共同   | conformation              |
| **uni-**   | 一，统一    | uniform                   |
| **per-**   | 彻底、完全   | perform                   |
| **-ation** | 名词后缀    | formation, transformation |
| **-less**  | 无、不具有   | formless                  |
| **-ality** | 性质，状态   | formality                 |
| **-ulate** | 使成为（动词） | formulate                 |
* **口诀**
  > form 是形，前缀后缀来变形；formation 是形成，malformation 出畸形；transformation 转型，reformation 是革新。

---
### 008. 常见前缀 mis- 和 mal- 的对比学习表
* **mis- vs mal- 前缀词根对比表**
| 维度   | **mis-**          | **mal-**             |
| ---- | ----------------- | -------------------- |
| 含义   | 错误地、不当地（mismatch） | 恶劣地、有害地（malfunction） |
| 来源   | 古英语 mis-          | 拉丁语 malus（坏）         |
| 语气强度 | 较轻，偏向“错误”         | 较重，偏向“有害、恶意”         |
| 使用风格 | 口语、日常较多           | 正式、医学、法律较多           |
* **对应词汇对比**
| mis- 词汇        | 中文    | mal- 词汇           | 中文         |
| -------------- | ----- | ----------------- | ---------- |
| **mistreat**   | 不当对待  | **maltreat**      | 恶意虐待       |
| **misuse**     | 误用，滥用 | **maluse**（少见）    | —（少使用）     |
| **mislead**    | 误导    | **malinform**（稀）  | 错误信息传播（罕见） |
| **misbehave**  | 行为不端  | **malconduct**（稀） | 不正行为（法律）   |
| **misfortune** | 不幸，厄运 | **malfortune**（无） | —          |
| **misspell**   | 拼写错误  | —                 | —          |
| **misfire**    | 失效，打偏 | **malfunction**   | 故障，功能失常    |
| **misjudge**   | 判断失误  | **maljudge**（罕）   | 不公判断（不常见）|
* **使用建议**
  - ✅ 日常、生活场景：优先使用 mis- 词汇
  - 📚 正式、书面语场景：使用 mal- 更合适
  - ❗️注意：某些 mal- 词更偏法律/医学，如 malpractice（渎职、医疗事故）
* **衍生词举例**
  - malnutrition（营养不良）← mal + nutrition
  - malicious（恶意的）← mal + -icious（形容词后缀）
  - malfunction（故障）← mal + function

---
### 009. "Brazier 铜匠" 解析
*  "**Brazier**" 这个词被翻译为“铜匠”其实是有历史和词源背景的。可以从词源、含义演变两个角度来看。
  - **词源（Etymology）**
    * **Brazier**（铜匠）这个词来自于：
      - **中世纪法语**：*brasier*，意为“炭火容器”，
      - 而其进一步源自于拉丁语 *brassarius*，含义是“黄铜工匠”，
      - *brass* 是“黄铜”的意思，-ier 是表示职业的人（相当于 -er，如 carpenter 木匠）。

  > **brazier 本义就是和黄铜 brass 打交道的人——即铜匠**。
  ---
  - **brazier 的双重含义**
    * 在现代英语中，**brazier** 这个词有两个主要意思：

      | 含义                             | 解释                            |
      | ------------------------------ | ----------------------------- |
      | 🔥 **炭火盆 / 火盆**                | 一个用来烧炭取暖或做饭的金属容器。常见于中东或古代场景中。 |
      | 🔧 **铜匠（brazier as a person）** | 一个加工黄铜或铜的工匠，常在历史文献或姓氏中出现。     |

      例如：

      * **a brazier full of coals**（一盆炭火）
      * **John the brazier**（铜匠约翰）
  ---
  - **为什么 “铜匠” 用 brazier，而不是 smith？**

    * "Smith" 是泛指金属工匠（如 blacksmith 铁匠，goldsmith 金匠），
    * "brazier" 专指和 **黄铜（brass）** 打交道的金属匠人。
      - 所以：
        * **blacksmith** 是打铁的
        * **silversmith** 是做银器的
        * **brazier** 是做铜器或黄铜器的（尤其是铜器工艺品）

  ---
  - **小结**
    > 🔍 **Brazier 是"铜匠"**，因为它词源于 "brass"（黄铜），原意是"加工黄铜的人"。
    * 不过现代英语中，"brazier" 更多指的是 "炭火盆"，作为"铜匠"的含义已较少使用，多见于历史、姓氏或某些职业称号中。
    * 如果你看到某人姓 **Brazier**，那基本可以推断他祖先可能是铜匠出身。

---
### 010. poet, citizen, actor, lion, host, shepherd
* **基础词 = 中性 / 默认男性**
* **加 -ess 后缀 = 女性专属形式**
* **类比**
| 基础词（中性或默认男性）      | 女性形式（加 -ess）  | 是否常用 -ess 形式 | 现代趋势                  |
| ----------------- | ------------- | ------------ | --------------------- |
| **poet**（诗人）      | poetess       | ❌ 不推荐（显老派）   | 用 poet 泛指所有性别         |
| **citizen**（公民）   | citizeness ⚠️ | ❌ 几乎不用（不自然）  | citizen 是完全中性的        |
| **actor**（演员）     | actress       | ✅ 仍常见        | 趋向性别中立，也常用 actor 代表女性 |
| **lion**（狮子）      | lioness       | ✅ 动物性别区分清晰   | 没有性别中立压力，lioness 常用   |
| **host**（主持人/主人）  | hostess       | ✅ 仍有使用       | 但在很多正式场合用 host 表男女    |
| **shepherd**（牧羊人） | shepherdess   | ✅ 历史文学中常见    | 现代也常用 shepherd 表男女皆可  |

* **统一规律**
| 类型        | 表达逻辑                                     |
| --------- | ---------------------------------------- |
| 职业 / 身份类词 | 原词多为中性（但传统默认男性）<br>加 `-ess` 形成女性专属形式     |
| 现代倾向      | **性别中立**：职业、身份、角色常省略 `-ess`，使用原词代指所有性别   |
| 动物        | `-ess`（如 lioness）仍广泛使用，因为自然界性别区分是生物学必要信息 |

* **常见的 -ess 结尾女性词（有用/不用）**
| 常用 / 中立  | 几乎不用或过时     | 说明                     |
| -------- | ----------- | ---------------------- |
| actress  | authoress   | actor 替代 actress 越来越普遍 |
| waitress | poetess     | 用 server 替代 waitress   |
| hostess  | manageress  | host 现在更常用为中性          |
| lioness  | empress（皇后） | 动物或王室角色通常保留 -ess 形式    |

> 这些词都遵循“原词中性或默认男性，加 -ess 表示女性”的规律，但现代英语趋向去性别化，职业/身份类词多省略 -ess，只保留中性词。

---
### 011. 英语的构词系统
* **英语的构词系统确实遵循一种非常高效的机制：有限的词根 + 丰富的词缀 = 无限的词汇变化。这正是英语词汇爆炸式增长的核心秘密之一。**
> 英语的词根数量有限，但通过前缀和后缀的组合变化，构建出成千上万的派生词。
* **相对来说，英语中常用的“词根”大概只有几百个核心单位（尤其是拉丁语和希腊语来源），远远少于我们日常词汇量的规模。**
  - **常用词根大约：300-500 个核心单位**
  - 再加上一些变体形式（词根变形、复合），可能接近 1000+
  - 比如:
    | 词根                 | 含义 | 示例                                   |
| ------------------ | -- | ------------------------------------ |
| **port**           | 搬运 | transport, import, export, portable  |
| **spect**          | 看  | inspect, respect, suspect, spectator |
| **scrib / script** | 写  | describe, manuscript, subscribe      |
| **dict**           | 说  | predict, contradict, dictionary      |
| **form**           | 形状 | transform, uniform, conform          |
* **词缀的魔力：增、减、反、方向、性质…**
| 类别        | 举例前缀 / 后缀            | 功能    | 示例                                       |
| --------- | -------------------- | ----- | ---------------------------------------- |
| **反/否定**  | un-, in-, dis-, non- | 否定原意  | unhappy, invisible, disconnect, nonexist |
| **增强/重复** | re-, over-, super-   | 加强、重复 | rewrite, overdo, superman                |
| **方向/位置** | sub-, inter-, trans- | 位置、方向 | subway, international, transport         |
| **人/职业**  | -er, -ist, -ian      | 表人    | writer, artist, musician                 |
| **状态/性质** | -ness, -ity, -ship   | 名词化   | kindness, ability, friendship            |
| **动词化**   | -ize, -ify           | 形成动词  | modernize, beautify                      |
| **形容词化**  | -ous, -ful, -less    | 表性质   | dangerous, hopeful, helpless             |
* **例子演示：一个词根衍生出一串词**
| 词汇            | 构词解释             | 含义     |
| ------------- | ---------------- | ------ |
| **form**      | 原始词根             | 形状，形式  |
| **reform**    | re-（重新）+ form    | 改革     |
| **transform** | trans-（横越）+ form | 改变，转变  |
| **inform**    | in-（向内）+ form    | 通知，使知情 |
| **uniform**   | uni-（统一）+ form   | 制服，一致性 |
| **conform**   | con-（共同）+ form   | 遵守，一致  |
| **deform**    | de-（偏离）+ form    | 变形，畸形  |
| **formless**  | form + -less（无）  | 无形的    |
> 能看到：一个 form + 多个前缀/后缀 = 词汇树🌲
* 英语就是这样造出来的
  - **借用词根（主要来自拉丁语/希腊语）**
  - **组合前缀 + 词根 + 后缀**
  - **根据语境、专业化、文化演变，赋予新含义**
> 这也让英语词汇学习变得系统可控——掌握词根+词缀，远胜死记硬背。
* **总结**
  - **英语的词根数量有限（几百个核心）**
  - **但通过系统化的前缀+后缀构词法，形成庞大的词汇体系**
  - **这种方法本质上就是“可复用结构的词语拼装”，逻辑清晰，极具规律性**

---
### 012. 整理一套核心词根 + 常见词缀的对照表
* **核心词根表（精选30个）**
| 词根                     | 含义      | 示例单词                                 | 词义               |
| ---------------------- | ------- | ------------------------------------ | ---------------- |
| **port**               | 搬运      | transport / import / export          | 运输 / 进口 / 出口     |
| **spect / spic**       | 看       | inspect / respect / suspicious       | 检查 / 尊敬 / 可疑的    |
| **dict**               | 说       | predict / contradict / dictionary    | 预言 / 反驳 / 字典     |
| **scrib / script**     | 写       | describe / manuscript / subscription | 描述 / 手稿 / 订阅     |
| **form**               | 形状、形式   | transform / uniform / reform         | 转变 / 制服 / 改革     |
| **vid / vis**          | 看       | video / visible / supervise          | 视频 / 可见的 / 监督    |
| **tele**               | 远       | telephone / television / telegraph   | 电话 / 电视 / 电报     |
| **aud**                | 听       | audio / audience / auditorium        | 音频 / 听众 / 礼堂     |
| **cred**               | 相信      | credit / incredible / credential     | 信用 / 难以置信 / 凭证   |
| **ped / pod**          | 脚       | pedestrian / tripod / pedal          | 行人 / 三脚架 / 踏板    |
| **mit / miss**         | 送       | transmit / dismiss / mission         | 传送 / 解散 / 使命     |
| **graph / gram**       | 写，画     | autograph / telegram / diagram       | 签名 / 电报 / 图表     |
| **man / manu**         | 手       | manual / manufacture / manipulate    | 手工的 / 制造 / 操控    |
| **bio**                | 生命      | biology / biography / antibiotic     | 生物学 / 传记 / 抗生素   |
| **geo**                | 地球      | geography / geology / geothermal     | 地理 / 地质 / 地热的    |
| **chron**              | 时间      | chronology / synchronize / chronic   | 年表 / 同步 / 慢性的    |
| **therm**              | 热       | thermometer / thermal / hypothermia  | 温度计 / 热的 / 体温过低  |
| **phon**               | 声音      | telephone / phonetic / symphony      | 电话 / 语音的 / 交响乐   |
| **auto**               | 自己      | autograph / automatic / autonomy     | 签名 / 自动的 / 自主权   |
| **rupt**               | 破裂      | disrupt / erupt / bankrupt           | 打断 / 喷发 / 破产     |
| **struct**             | 建造      | construct / structure / destruct     | 建造 / 结构 / 破坏     |
| **log / logy**         | 说话 / 学科 | logic / biology / dialogue           | 逻辑 / 生物学 / 对话    |
| **bene / bon**         | 好       | benefit / bonus / benevolent         | 好处 / 奖金 / 仁慈的    |
| **mal**                | 坏       | malfunction / malnutrition / malign  | 故障 / 营养不良 / 恶性的  |
| **tact / tang**        | 触摸      | contact / tangible / intact          | 接触 / 可触的 / 完整无损的 |
| **ceed / cess**        | 行进      | proceed / succeed / access           | 继续 / 成功 / 进入     |
| **cap / cept**         | 拿，抓     | capture / accept / intercept         | 抓住 / 接受 / 拦截     |
| **vers / vert**        | 转       | reverse / convert / versatile        | 反转 / 转变 / 多才多艺的  |
| **cede / ceed / cess** | 走       | precede / exceed / recession         | 领先 / 超过 / 衰退     |
| **voc / vok**          | 叫喊      | vocal / invoke / provoke             | 发声的 / 引起 / 挑衅    |

* **常见词缀表（前缀 + 后缀）**
  - **常见前缀（prefix）**
  | 前缀                        | 含义    | 示例单词                                      | 含义                       |
| ------------------------- | ----- | ----------------------------------------- | ------------------------ |
| **un-**                   | 否定    | unhappy / undo                            | 不快乐 / 撤销                 |
| **in- / im- / il- / ir-** | 否定    | invisible / immoral / illegal / irregular | 看不见的 / 不道德的 / 非法的 / 不规则的 |
| **dis-**                  | 否定、反对 | disagree / disappear                      | 不同意 / 消失                 |
| **re-**                   | 再，反复  | rewrite / return                          | 重写 / 返回                  |
| **pre-**                  | 之前    | preview / predict                         | 预览 / 预言                  |
| **post-**                 | 之后    | postpone / postwar                        | 推迟 / 战后的                 |
| **sub-**                  | 下     | subway / submarine                        | 地铁 / 潜水艇                 |
| **super-**                | 上、超越  | superstar / superpower                    | 巨星 / 超级大国                |
| **inter-**                | 之间    | international / interact                  | 国际的 / 互动                 |
| **trans-**                | 穿越    | transport / translate                     | 运输 / 翻译                  |
| **anti-**                 | 反对    | antiwar / antisocial                      | 反战的 / 不合群的               |
| **auto-**                 | 自己    | autobiography / automatic                 | 自传 / 自动的                 |

  - **常见后缀（suffix）**
  | 后缀                               | 词性  | 含义           | 示例                                    |
| -------------------------------- | --- | ------------ | ------------------------------------- |
| **-er / -or / -ist**             | 名词  | 表人           | teacher / actor / artist              |
| **-ness / -ity / -tion / -sion** | 名词  | 状态 / 行为 / 性质 | kindness / reality / action / tension |
| **-ment / -ship / -age**         | 名词  | 结果 / 状态 / 集合 | development / friendship / percentage |
| **-ful / -less**                 | 形容词 | 充满 / 缺乏      | hopeful / powerless                   |
| **-able / -ible**                | 形容词 | 能…的          | readable / visible                    |
| **-ous / -ive / -al / -ic**      | 形容词 | 有…性质的        | dangerous / active / natural / poetic |
| **-ize / -ify / -en**            | 动词  | 使成为          | realize / beautify / strengthen       |

---
### 013. 做一个"构词法速查表"或"词根词缀词汇图谱"

---
### 014. ruination 毁灭 destory的区别
* **核心区别速查表**
| 项目       | **ruination**                         | **destroy / destruction**                     |
| -------- | ------------------------------------- | --------------------------------------------- |
| **词性**   | 名词（抽象、文学化）                            | destroy 是动词，destruction 是名词                   |
| **含义**   | 完全毁灭导致**衰败或失败**                       | 消灭、摧毁某物，偏重**破坏行为**                            |
| **语气**   | 正式、文学性强，带悲剧感                          | 常用词，语气中性或强烈                                   |
| **强调重点** | 后果：毁灭带来的损失、没落、终结                      | 行为本身：摧毁某物或让其无法存在                              |
| **使用场景** | 抽象概念：名誉的毁灭、国家的灭亡                      | 可具体也可抽象：摧毁建筑、关系、希望等                           |
| **搭配常见** | ruination of a life / career / nation | destroy a city / destroy hope / destroy trust |
* **词根与构成**
  - ruination：
    * 来自动词 ruin（毁灭、破产）+ 后缀 -ation（名词）
    * 含义更抽象、文学、带宿命感
    * 例：The scandal led to the ruination of his political career.

  - destroy / destruction：
    * destroy = dis-（分离）+ -struct（建造） → 拆掉 → 毁灭
    * destruction 是其名词形式
    * 更常见，强调彻底消除的行为
    * 例：The earthquake destroyed the entire village.
* **例句对比**
  - 抽象毁灭
    * Ruination：
      > Years of addiction led to his total ruination.
      > 多年的上瘾最终导致他彻底的毁灭。

    * Destruction：

      > The war brought about the destruction of ancient culture.
      > 战争导致了古老文化的摧毁。

  - 具体破坏
    * Destroy（动词）：

      > The bomb destroyed the entire building.
      > 炸弹摧毁了整栋建筑。

    * Ruination 不适合用于“炸弹毁楼”这种场景。会显得不自然或夸张。

  - 语义细腻度（更文学或悲剧化）
    * Her pride was the cause of her ruination
      （她的骄傲导致了她的败亡）

    * 相同意思换成 destruction：
      Her pride led to her destruction（较直接，但文学色彩弱）
* 小结
  - | 你想表达的意思         | 推荐用词                    |
| --------------- | ----------------------- |
| **具体破坏**（建筑/物品） | destroy/destruction     |
| **抽象失败或败亡**     | ruination（更文雅/悲剧）       |
| **强调行为过程**      | destroy（动词）             |
| **强调毁灭带来的结果**   | ruination 或 destruction |

* 总体判断
| 场景          | 推荐用词        | 原因说明                       |
| ----------- | ----------- | -------------------------- |
| **战争带来的毁灭** | destruction | 更常用于战争背景，强调大规模破坏（城市、文明）    |
| **某人精神被摧垮** | ruination   | 更文学化，强调“慢性地走向崩溃”或“个人命运的败亡” |

  - **战争场景用 destruction**
  - 示例：
    > The war brought destruction to the entire region.
      战争给整个地区带来了毁灭。

    > The destruction of the city left thousands homeless.
      城市的毁灭让数千人流离失所。

    * 不推荐用 destroying 或 ruination 替代上面两句。虽然语法可以，但语气不合场景：
      - destroying 更强调动作过程，不适合总结性陈述；
      - ruination 更抽象、更文学，战争语境下太“弱”。

  - **精神或命运的崩溃用 ruination**
  - 示例：
    > Years of emotional abuse led to her psychological ruination.
      多年的情感虐待导致了她心理上的彻底崩溃。

    > His addiction was the beginning of his ultimate ruination.
      他的上瘾是他最终败亡的开端。

    > 也可以说：the ruination of his soul / life / career
      非常常见于文学、心理、历史叙述中。

---
### 015. contention 争论与argument
* contend 与 argue 的差异
| 对比点      | **contention**             | **argument**            |
| -------- | -------------------------- | ----------------------- |
| **词性**   | 名词（正式/书面）                  | 名词（常用/通俗）；也可作动词（argue）  |
| **基本含义** | 主张、争议焦点；争论中的**观点立场**       | 争论、辩论本身；也指**吵架或讨论**本身   |
| **语气风格** | 正式、书面、学术、抽象                | 中性或口语化，可以激烈或理性          |
| **常见搭配** | a point of contention（争议点） | a heated argument（激烈争吵） |
| **强调重点** | 谁“持有什么观点”                  | 争论的过程或事件                |
| **适用场景** | 法律、学术、政策争论、立场分歧            | 日常争吵、辩论、争执、说理           |

  - **contend → contention = 观点 / 主张 / 争议点**
    * 语义更抽象、更正式
    * 强调"主张某种立场"或"观点的冲突"
    * 示例:
      > It is my contention that the policy is unfair.
         我的主张是这项政策不公平。

      > The main point of contention was who should be in charge.
         主要争议点是谁应当负责。

      > There is a long-standing contention over the ownership of the land.
         对这片土地的归属问题一直存在争议。

  - **argument = 争论 / 争吵 / 说理**
    * 可以正式也可以日常
    * 既可以指“吵架”，也可以指"逻辑推理过程"
    * 示例（不同语气）：
      > They had a loud argument about money again.
         他们又为钱大声争吵。

      > In her argument, she presented strong evidence.
         她在论证中提出了有力证据。

      > Your argument is not convincing.
         你的论点不够有说服力。

  - **一句话总结**
    > contention 更像是“你站哪边、你坚持什么”；
    > argument 更像是“你怎么吵、你如何说理”。

  - **使用建议**
  | 场景               | 推荐用词           |
| ---------------- | -------------- |
| 强调**争论过程/吵架**    | argument       |
| 强调**观点主张/立场冲突**  | contention     |
| 需要**书面/正式/学术表达** | contention 更合适 |
| 需要**日常/轻松表达**    | argument 更合适   |

  - **拓展词汇推荐**
  | 单词            | 含义             |
| ------------- | -------------- |
| dispute       | 正式用词，表示争议或异议   |
| debate        | 有结构的辩论，一般较理性   |
| quarrel       | 小题大做的争吵，多指口头冲突 |
| confrontation | 面对面的冲突或对抗      |
| disagreement  | 一般的意见不合，语气最温和  |

* **精准对比**
| 概念     | **contention**                    | **argument**                                |
| ------ | --------------------------------- | ------------------------------------------- |
| 中文直观理解 | **主张/立场**，争议的焦点                   | **口头争执**，也可指**说理/辩论过程**                     |
| 本质     | 一种**观点的表达**（可能引发争议）               | 一种**行为/事件**，通常是口头上的冲突或辩论                    |
| 语气     | 正式、书面，学术或法律常用                     | 通用性强，日常口语中最常见的“争吵”用词                        |
| 例子     | "My contention is that..."（我的主张是） | "They had an argument last night."（他们昨晚吵架了） |
| 强调点    | “你认为什么？”——主张和争议点                  | “你和别人吵了什么？”——口头冲突或逻辑辩论                      |


---
![alt text](https://upload-bbs.miyoushe.com/upload/2022/11/01/266607709/6cc988d046df34315681e50f9c9f299c_1259576169906078498.PNG?x-oss-process=image//resize,s_600/quality,q_80/auto-orient,0/interlace,1/format,png)
