# **AI 数字衣橱与虚拟时尚社区**

# **产品需求文档 V1.0**

正式研发规格 · 完整合并版 · 原始 V0.1 基线 + V1.0 研发补充 + 品牌与 UI 视觉规范

**文档基本信息**

| 项目     | 内容                                 |
| ------ | ---------------------------------- |
| 产品暂定名称 | 衣间星河 VESTORIA（品牌提案，待检索）            |
| 产品类型   | AI 数字衣橱 / 虚拟角色换装 / 时尚创作社区          |
| 文档版本   | V1.0                               |
| 文档性质   | 产品需求、技术设计、验收标准                     |
| 目标读者   | 管理层、产品、UI/UX、客户端、后端、AI、3D、美术、测试、运营 |
| 原始基线   | 《AI 智能穿搭与虚拟衣橱产品规划 V0.1》            |
| 版本原则   | 原始内容保留，新增内容追加，不以摘要替代原始需求           |

## **文档阅读与版本规则**

本文档包含三类内容，研发评审时必须区分：

- **[PRD 产品需求]**：定义用户为什么使用、页面展示什么、用户可以做什么、交互如何发生。
- **[TECH 技术设计]**：定义数据结构、服务架构、接口、算法、任务状态、渲染和权限实现。
- **[AC 验收标准]**：定义功能完成的判定条件、异常处理要求和测试方法。

技术方案中出现的候选技术、性能数字和模型能力，若没有完成 PoC 或压测，均属于建议目标，不得直接视为已经验证的事实。

# **第一部分：原始产品规划基线**

## **一、产品定位：不只是 AI 穿搭，而是一个可以养娃、换装、分享和创造的虚拟时尚世界**

**[PRD 产品需求]**

本产品不应被定义成传统的 AI 穿搭工具，也不应简单理解成一个给人物模型换衣服的 3D 换装游戏。

它应该是一个由以下能力组成的综合产品：

- 个人数字衣橱。
- AI 穿搭助手。
- 虚拟角色养成。
- 角色换装与服装收藏。
- UGC 时尚社区。
- 数字服装资产和创作者生态。

核心使用方式：

1. 用户把现实中拥有的衣服、鞋子、包包、首饰上传，建立自己的数字衣橱。
2. AI 识别衣物属性，自动分类、生成虚拟服装素材，建立可供角色穿戴的数字资产。
3. 用户拥有一个或多个可自定义的虚拟角色，可以调整脸型、发型、身材、肤色等。
4. 用户既可以给自己搭配，也可以给虚拟女儿、儿子、娃娃搭配。
5. AI 能理解衣橱中的衣物、用户偏好、天气、场景和季节，主动推荐穿搭，也能通过聊天完成搭配。
6. 用户可以将搭配、角色、服装和饰品制作成作品，分享给其他用户，甚至形成服装设计师、穿搭创作者和虚拟时尚市场。

**核心产品判断：**

> 现实衣橱负责建立使用价值，虚拟角色负责建立情感价值，AI 负责降低搭配成本，社区和资产分享负责建立长期内容生态。

如果只做现实衣橱，用户可能使用几次就失去兴趣；如果只做换装游戏，又会与大量传统换装产品竞争。两者结合才有机会形成差异化。

### **1.1 产品核心价值结构**

## **产品价值飞轮**

# **现实衣橱**

真实衣物数字化 · 建立使用价值

# **AI 智能穿搭**

理解需求 · 组合衣物 · 降低搭配成本

# **虚拟角色与换装**

角色身份 · 个性表达 · 情感价值

# **作品社区与数字资产**

创作 · 分享 · 复用 · 授权 · 商业生态

社区内容反向带动衣橱扩充、角色养成和再次创作

### **1.2 产品目标与非目标**

**V1.0 目标**

- 建立真实衣物数字化流程。
- 建立用户可持续编辑的虚拟角色。
- 让用户上传的衣物能够转化为可穿戴素材。
- 实现角色换装、穿搭保存和历史恢复。
- AI 能从用户实际衣橱中选取衣物并生成可执行搭配。
- 提供基础作品分享、隐私和内容审核能力。

**V1.0 非目标**

- 不承诺任意衣物照片自动生成完美 360° 3D 服装。
- 不要求首期实现真实布料物理模拟。
- 不要求首期上线完整虚拟货币交易。
- 不要求首期支持多人实时虚拟空间。
- 不把复杂剧情、恋爱陪伴作为首期主线。
- 不将用户上传的真实服装图片默认用于模型训练。
- 不把社区公开等同于原始资产授权。

### **1.3 核心用户场景**

| 场景      | 用户行为           | 产品价值     |
| ------- | -------------- | -------- |
| 建立数字衣橱  | 拍摄、上传衣服，确认识别结果 | 管理真实衣物   |
| 今日穿搭    | 选择天气、场景和风格     | 提供实际搭配建议 |
| 虚拟角色养成  | 创建角色、编辑脸型和身材   | 建立情感连接   |
| 角色换装    | 将衣橱服装穿到角色身上    | 提供可视化表达  |
| AI 聊天搭配 | 用自然语言提出穿搭需求    | 降低操作成本   |
| 作品创作    | 保存角色造型、背景和姿势   | 形成可分享内容  |
| 社区浏览    | 浏览、收藏、关注创作者    | 获取灵感     |
| 资产复用    | 在授权范围内复用服装或搭配  | 形成内容流动   |
| 创作者商业化  | 发布原创服饰和素材      | 形成长期生态   |

## **二、竞品参考与产品机制**

**[PRD 产品需求]**

竞品分析不是照搬页面，而是拆解各产品已经验证的用户行为、体验机制和商业逻辑。

### **2.1 竞品参考矩阵**

![《奇迹暖暖》测评：暖暖终于有了第二种“姿势”-小米游戏中心](https://images.openai.com/static-rsc-4/FrU_qRUnLGP8bhFUPdX2476n4fi2i78lNkfk5UkgG0plubh0BlsejuK5T0QfzRiDKBnc0EUT3olwctCHYsvRK2DL1EEXp1CL3dpAhHqxzJajgijZwC2FJ8X5vh5xGUr_8UmoHgbJuRCmHgrKlBjCOVXzsMF4RPXLi5sI3qq8S30?purpose=inline)

**《奇迹暖暖》**

借鉴机制：服装部件分类、套装收集、主题搭配、服装稀有度、图鉴、搭配评分、活动内容。

核心价值：服装收集与审美表达。

![燕云十六声怎么重新创建角色_重新创建角色方法_3DM网游](https://images.openai.com/static-rsc-4/wKxG6Osct2nM500nPzLqd3v8BO6h8uSCNNEHnL6Pokn1RU0JXOYWWPvngsmpS9Aj3G5BUmSS9jSBmhxhvYfmoyA11201P68AIoU28V_WNj7g4s4NGvkXMR_8c12OE91SPIKR_xkXBpsEFyChiVIV6PljOdo49JrVcJ4JRiKkVpg?purpose=inline)

**《燕云十六声》**

借鉴机制：角色外观、捏脸、服装展示、染色、角色个性化、社交展示。

核心价值：角色本身成为用户长期经营的数字身份。

![(제페토)캐릭터 의상 코디저장, 스타일 올리고 인기 스타일 따라하기 - 언니네 정보다방](https://images.openai.com/static-rsc-4/DEQBPI_cIxhk68LSB-iIs_YIT2hmur27mCK1VF1GuZmhZWgGCOh0T_oUMeLVp_TSYqr1rl8pSKFoTHzMMgjQx69PEgS7RBz3gf5eUct5COB1pxEKu0th9wrj-w5mN-xG3bAcYOopyUXEKhs0R94nenD0ibcn5iSNPEvyYgG05oc?purpose=inline)

**ZEPETO**

借鉴机制：虚拟人物、UGC 服饰、角色摄影、社交分享、创作者生态。

核心价值：虚拟角色与内容社区结合。

![ИИ-гардероб: как я собирала образы на каждый день с помощью нейросетей](https://images.openai.com/static-rsc-4/P3hLFEDDPS63Q4xa6auitajCwSHAw7GK1GfIXX2QGTOoh6iuM2NZRkVAIFvzTzamJlyp4GXLPOiLNb7ALRDjWc17g_giAjuqhuHz2bHQuI6Rycpuqw3DJibXhSVBJ1JwHpXtfHgwnuSZfnO1sd71dEQMmKcib1QxZRFeA4eAuBE?purpose=inline)

**Acloset**

借鉴机制：真实衣物上传、服装识别、数字衣橱、搭配推荐、穿衣记录。

核心价值：现实衣物数字化与实用价值。

### **2.2 竞品机制与本产品差异化**

| 产品方向   | 借鉴机制     | 本产品差异化             |
| ------ | -------- | ------------------ |
| 换装游戏   | 部件、套装、图鉴 | 用户真实衣服也能成为游戏资产     |
| 角色养成   | 捏脸、外观、个性 | 角色拥有持续穿搭历史与记忆      |
| 数字衣橱   | 识别、分类、推荐 | 衣服能够真正穿到虚拟角色身上     |
| AI 助手  | 对话、推荐    | 能直接调用衣橱资产完成搭配      |
| UGC 社区 | 作品、关注、分享 | 用户可以分享衣物资产和可复用穿搭方案 |

### **2.3 可借鉴与不可照搬的部分**

| 机制          | 是否借鉴   | 本产品实现原则        |
| ----------- | ------ | -------------- |
| 服装分类与套装图鉴   | 是      | 服装资产有统一分类和收藏体系 |
| 主题搭配挑战      | 是      | 主题条件可以由运营后台配置  |
| 角色捏脸        | 是      | 采用可扩展的参数化角色系统  |
| 角色社交展示      | 是      | 角色主页与作品权限分离    |
| 传统抽卡获取服装    | 暂不作为核心 | 避免稀释真实衣橱价值     |
| 完全封闭的游戏服装资产 | 否      | 需要支持用户真实衣物转化   |
| 纯粹电商商品展示    | 否      | 商品购买不是产品主线     |
| 纯聊天式 AI     | 否      | AI 必须能够执行穿搭动作  |

### **2.4 竞品研究需要持续验证的问题**

1. 用户愿意花多少时间建立数字衣橱？
2. 角色的情感价值是否能提升周活跃？
3. 真实衣物和虚拟服装是否会产生混淆？
4. 用户是否愿意把现实衣物照片公开？
5. 用户是否愿意授权其他人复用自己的数字资产？
6. 用户对角色外观的精细化编辑需求有多高？
7. 社区用户主要消费真实穿搭、虚拟角色作品还是原创服饰？
8. 用户愿意为 AI 生成、角色定制还是数字服饰付费？

## **三、核心产品结构**

建议产品分成六大业务模块，底层由统一的用户、角色、衣物资产、AI 服务和内容资产系统支撑。

### **3.1 产品整体架构**

**用户入口与体验层**

首页 · 我的衣橱 · 角色工坊 · AI 穿搭 · 作品社区

**数字衣橱**

衣物上传、识别、分类、标签、尺码、季节

**角色工坊**

捏脸、身材、发型、角色、身体比例

**AI 穿搭**

智能推荐、聊天搭配、自动换装、场景搭配

**换装系统**

服装部件、穿戴锚点、2.5D 渲染、动作

**作品社区**

穿搭分享、角色主页、收藏、投稿、关注

**资产与商业化**

服饰素材、创作者、版权、积分、商城

**统一底层能力**

用户与权限系统 · 衣物资产数据库 · 角色模型与骨骼 · AI 视觉识别 · 内容安全审核 · 推荐与匹配引擎 · 素材生成与存储 · 分享授权与交易

### **3.2 首页：让用户有持续打开产品的理由**

首页不能只是一排功能入口，应该围绕角色和穿搭内容展开。

建议布局：

1. 顶部：当前角色展示、切换角色、天气及今日穿搭提示。
2. 今日推荐：根据天气、季节、场景、用户衣橱推荐一套搭配。
3. 我的角色：展示用户养成的角色，可以切换不同娃娃。
4. 穿搭灵感：其他用户发布的搭配作品。
5. 每日主题：例如秋日学院风、甜酷风、古风、约会穿搭。
6. 快捷入口：添加衣物、AI 帮我搭配、进入换装工坊。

首页应该有一个比较强的视觉中心：用户的虚拟角色。

![Hướng dẫn cách cài đặt Shining Nikki trên Android và iOS](https://images.openai.com/static-rsc-4/kS9d5x7ww8mmKbmlC1JdpU2od4Jw290kLypsUUGU6JvF3__6Dcpw5LLMib1-cU6j49KomZgryO7koqouJRSp_O_uHLmSBS_Nbni2N-lc663y3qpek96vNbHhsD-7O79bTuQvhKC0LEz6FJjQaq1gE1rs3hq2zNcU3bv7XL2GwNY?purpose=inline)

![AURA Mobile App - UX/UI Case Study :: Behance](https://images.openai.com/static-rsc-4/Gb57uIGP7f879zcwr3zm2RKsF3WxV2yVO3oNhCCYhaIzQh9Gl439rmMRlVu45cNiKrxdwr4QrkS9S5Cl2Q99cN6Vw_1zeX6hU8iWEPXzGOsQmS_2f_hdl4N0_3sJiWi_72fMB5Wx5S5xmT_wX2DdVflVJPf510xR9sndH7kQKm8?purpose=inline)

![Студия Луч · кейсы · дизайн iOS-приложения 12storeez](https://images.openai.com/static-rsc-4/I6mD1ITLEhEI6ras-gDXFmEO7g3iA40w8Pf3W36C_U66Ea1gbZEFwsjR28kbhShnb3oc2OrQHHebNZFV3Zb9vrWBbDe3uf1LqPnB4AKs0zFaus9H25LwXKZldzblbj3rv3pVi3uRbU9pCPSzymFnYM_jktBpdO90mDG_r5dXe2o?purpose=inline)

8

### **3.3 数字衣橱：整个产品最重要的基础模块**

这是后续 AI 推荐、自动换装、穿搭搜索、服装分享的基础。

不能只把用户上传的图片存起来。我们必须将每一件衣物转换为结构化数字资产。

每件衣物都需要有：

- 原始图片。
- 去背景后的服装素材。
- 分类与子分类。
- 颜色和材质。
- 季节和适用场景。
- 尺码与适配身材。
- 身体穿戴部位。
- 穿戴锚点。
- 图层顺序。
- 2.5D 贴图。
- 用户自定义信息。
- AI 识别置信度。
- 审核状态。
- 资产授权状态。

**我的衣橱分类：**

![Top up up view white shirt folded isolated on pink background. suitable for your design project.](https://images.openai.com/static-rsc-4/eb2v0xce1vmrXy-Ttz2qHxm414aTtOj_zbMsN_pCsa3IhMAyUmhdA3tP6uPpvqRo-1KGOoO_jDF2XlJlWsjU4A569FQjKPqMC8mK6UotKwc0dU2XM04rbLaU-0FIoAOgqCL-t0dflNGFAJnP8CwTMxX2ACDoV44fBt8YPgYGXraPWwNv9hpjmd4dfckct12x?purpose=inline)

上装

![Women's Bottoms Collection | Lookzlike](https://images.openai.com/static-rsc-4/jd4OP5KsqwwHWACexKWIPYCSUY2zVuWBXZEkD0bCcGaIF2cx3BfVDakvMcbeenGLUTKGUl00La8eS8NucCLPRdIuqLJ1iHfAr689MjGBiM_GwWWqfvcyKG9Y6n2rjW4aDN0WwISyyoMMkROAmRzxoT6Ya6l2FQs3ZSaMLLL1Ijs?purpose=inline)

下装

![Denim summer dress on a white background. Isolate. Fashionable concept](https://images.openai.com/static-rsc-4/qKNX4yEq-AZYJWoKmyFTTeWbhAt-m_kNIBdRgFnsAYkqDlPhJzxmLa5koWPkrgHLPNTaHzhDY1D9E11d_7FEvd7R3J48vH_RiWznZCP5rEKI-Ub8pKE8EDyAs_dD2DzVorJo1O9aCGjRCWljrYrtKxvDzPcPXyXct55x-F5ONNMYKxt170atvgZynXRDukqb?purpose=inline)

连衣裙

![Sophie Coat in Camel | Cashmere‑Blend Double‑Breasted Coat                      – Lindsay Nicholas New York](https://images.openai.com/static-rsc-4/4hoa3aFqf6sEXgh7HKXngvMN_D4Y1GQ74L5ssN7u11ZUjy2OwZqk0FsnU4wtadlq4UjMbRVLoOsO-gLLGWEln56HuHFq0AKRYVTpD11kvH4piifJ1cefl6NMRyGWBxTk1JfYfharg5lahZMyBkOmexdiCdZWeWQcnqRr-JhXQ9Q?purpose=inline)

外套

![women's boots](https://images.openai.com/static-rsc-4/pr_gYVC_LpSyOkbs2VPo0pb0NYcCcmA9G73g-AqKIuzjUpLzFgR_3Lmrg8m0nSw_uqTjIyAEWgQ2oiPypAjH0AKgAEEoxcZlXRuKhUlU94Miqe9CRaGRQPsFvRNYVNO4B7EaqlTjKZWihHZefS9pwb3Tp1xhLuZuEv9_qTof0Jr4etSDleTq53uwGnbPyhdN?purpose=inline)

鞋靴

![Trendy blue or turquoise female top-handle leather bag with metal clasp and tag isolated against a white background. Elegant summer accessories. Mock-up for advertising poster. Discount, season sales.](https://images.openai.com/static-rsc-4/rjldl3puXuNPa6hPwhOktn8XXZBmK0OAmYk1q0X528EfMW-e6xup-9A9rTwef_ffS69rlrflCmli5Y5LvVGYOrhaAmFKAmhVllKO-18vLBH0aXEjxEqUxNwiun71c1WSUcrHsq0rJNc1g968jhW9RczA6Gpb-HvA7VsueABnB6dGSM760zSohRSni1LMPhJG?purpose=inline)

包袋

![Best Realtor Outfits for 2026 (Cute, Comfortable, and Actually Professional) — The Real Estate Resource Hub](https://images.openai.com/static-rsc-4/rwvVzlsbAhq6sY8a4Ypm5XAl23wpKbLJ-LKgLZpNShhKLi4Q_QtjoJtIEnJl5P0zqBfMcuKEXhRFUscbQFKBBRIknGFtg8D7bmx94E3WKxvu_5L2RpZGOniO5tJOZxx7Mx3OkE_wPbH7Bf3D-t2RPGLs1GrcWTHyVq0weOarL1w?purpose=inline)

首饰

![Hair Accessories, Extensions & Styling Tool - Shop here](https://images.openai.com/static-rsc-4/MSlv360LYeQGwq_1OpT0T6zujsy_i7fgqC2RFIDXBAkz4vbcoPeVxdJe9Y5H49ZsElIPECSbaJx0F6c3fUysrlTgB_6Yc6_0xjNTd65UTXaSFGlZUWg5xEJPoSK3CAGqxSlEwvlh1gQNgZjXVFXXQQBMK-XQ-eRoUFI8Tn3HKB0?purpose=inline)

发饰

**完整分类树：**

| 一级分类 | 二级分类                | 身体部位   |
| ---- | ------------------- | ------ |
| 上装   | T 恤、衬衫、针织衫、卫衣、背心、吊带 | 躯干、上臂  |
| 下装   | 长裤、短裤、半身裙、牛仔裤、打底裤   | 腰部、腿部  |
| 连体装  | 连衣裙、背带裤、连体衣         | 全身     |
| 外套   | 西装、夹克、大衣、羽绒服、风衣     | 躯干、手臂  |
| 鞋靴   | 运动鞋、皮鞋、凉鞋、靴子、高跟鞋    | 左右脚    |
| 袜类   | 短袜、长袜、丝袜、连裤袜        | 脚部、腿部  |
| 头部   | 帽子、发箍、头巾、发夹、发簪      | 头部、头发  |
| 耳饰   | 耳钉、耳环、耳坠            | 左右耳    |
| 项饰   | 项链、锁骨链、choker、围巾    | 颈部、胸前  |
| 手饰   | 手链、手镯、戒指、手套         | 左右手、手指 |
| 腰饰   | 腰带、腰链、挂饰            | 腰部     |
| 其他   | 眼镜、眼罩、胸针、翅膀、装饰挂件    | 指定锚点   |

特别注意：一件服装可能占据多个部位，不能只用一个 `body_part` 字段。

例如：

- 连衣裙：躯干 + 腰部 + 腿部。
- 长手套：手部 + 前臂。
- 过膝靴：脚部 + 小腿 + 膝部。
- 披肩：肩部 + 上臂。
- 长耳坠：耳部，但需要根据头部旋转调整位置。

因此应该使用多部位占用关系和锚点系统。

### **3.4 角色工坊：用户养成的娃娃**

角色工坊是整个产品的情感价值中心。

建议支持一个账号创建多个角色，而不是一个账号只能绑定一个人物。

例如：

- 我的女儿：甜美、可爱、日系。
- 我的儿子：少年感、清爽、学院风。
- 我的收藏娃娃：洛丽塔、古风、幻想风。
- 我的原创角色：完全自定义。

角色要拥有独立的：

- 名字、性格、简介。
- 脸部与五官参数。
- 发型与发色。
- 身材参数。
- 肤色。
- 默认服装。
- 穿搭历史。
- 收藏衣物。
- 角色照片及分享主页。

![Cute Chibi Avatar Creator AI Image Generator](https://images.openai.com/static-rsc-4/bGUXFTkw9rcvcdqjiMS1pTz2iw5ZWpKJpORZADFW-b1KxeV1UYQjfCwmLPHBQuc3uZIW2Z_oQLcIvjpHT7eyc0KsRRcdHjfLOAFdcmgWeoRbqipKcAkBPEnubee_ZboSitB7sW1Hnn4M4v_H46xWjJKwC3SVANf6Eq--63k3xyY?purpose=inline)

![Anime Doll Avatar Maker Game - release date, videos, screenshots, reviews on RAWG](https://images.openai.com/static-rsc-4/VrUMcgWKszsAZBqBKexxamhI-4o9GKp1sI2V_w12Mh3IRoTpttJ8ErmQLaMJJmeBnVLpD-3RiIDuXhRxPHudYskCvuF2tO9_LZ5Mz4MDvDMOIOBrZ7fEdo1xz52Uy13HmiG4OV90zMYVN0Ec23BQUOlM_P7f8iH9c2snrm1wYN0?purpose=inline)

![My Fashion Design APK for Android - Download](https://images.openai.com/static-rsc-4/-m_bhQZNwOAHszu8YRPR2gz19w7pd-oQWVrDQDBQ6ArRNhviZBH5hKgEIuDNac2kSjcdW6w0rOW1QL5mHAdS56bUk9HpBKIxdKbd4hqijGzIgDQNKfg1KtXZpMXskbjLVkRlK7KUVhzPkswi5IYXR1C7NJfEwSnP7oxBhH3TPBI?purpose=inline)

18

**人物脸部的设计优先级应该非常高。**

不建议直接使用普通写实人体模型。第一版更适合采用：

- 大眼睛、柔和面部轮廓。
- 适度夸张的头身比例。
- 可爱、精致、具有辨识度的五官。
- 支持多种审美风格，而非全部都是同一张网红脸。
- 能够适配不同发型、头饰、眼镜和表情。

建议第一版使用 3D 卡通角色，最终渲染采用偏 2.5D 的展示效果。这样既能自由旋转角色，也能控制角色的画风和视觉品质。

### **3.5 身材与体型系统**

身材不能仅仅是一个胖瘦滑块。

需要将人物模型参数与服装适配逻辑分离。

**第一层：快捷身材模板**

![Chloe :: Behance](https://images.openai.com/static-rsc-4/pxygdrnxNoN7I3yaVNPc56wqlwpd1TJrd99pfS8inLZnftxZ6WE3iQRn5YCUBS6-oS_Ikvcuy8vrEeJQEMI6IlWqFB7Bi-MPJqoTQ-XN-Uu4ck_LGi1tVhBtRLNZJNzeQcwNWn3cMN-WUQHeQEr4B68lCq-3sfzx3et3DhX_pZs?purpose=inline)

纤细型

![Front View Of An Animated Girl Standing Wearing Tshirt Character Design, Full Body, Drawing A Face In Maximum Quality, High-Quality Drawing Of The Face,Clipart, Full Illustration, 4K, Sharp Focus, Smooth Soft Skin, Symmetrical, Detailed Face, Concept Art, Style Fairy Tales, Chibi Kawaii, . Octane Rendering, 3D, Perfect Face, Detailed Face, Delicate Face, Perfect Sharp Lips, Detailed Eyes. – Free Clipart #4243932 | Clipart Library](https://images.openai.com/static-rsc-4/P7CuDX2IjmDZEi8RyeG26TPoHhJDkabrUreg0e8sNkElgDfGgiWuA6KvfgnYX6ttTXr4tshcI4_UqMJHQcRYWtZr2Eb9w0reOEmDXSVvMc5qD4HFA4Otn6Nf2O0HYxZ3zTodwVtYYyBp-1upZNh15XyBFQalwrTzFatE241a5b4?purpose=inline)

标准型

![Realistic Young Woman Character For Youtube Thumbnail Transparent Background, Realistic Female Character, Youtube Thumbnail Woman Transparent, Casual Young Woman PNG Transparent Image and Clipart for Free Download](https://images.openai.com/static-rsc-4/nRKaAsC6wK_JKdkQQObJShCewufxMDNgV8Ztr_5s81eolN04aU3oA6UMAvE5LfT7gr8LQWU_smlE1nMDIKiyx6-AtZX6UyGupFXsZod-qAu5XBMWKei3kFe9Xk7083S4bB1xNUqAPSWzP2smxpfbMzMbszSW16gCg1lyFzwrT8g?purpose=inline)

丰润型

模板可以进一步包含：

- 娇小型。
- 高挑型。
- 运动型。
- 丰满型。
- 自定义型。

**第二层：自由参数调整**

| 参数   | 调整内容       |
| ---- | ---------- |
| 整体身高 | 人物整体纵向比例   |
| 肩宽   | 肩部宽度       |
| 胸围   | 上半身轮廓      |
| 腰围   | 腰部宽度       |
| 臀围   | 臀部轮廓       |
| 腿长   | 腿部占比       |
| 大腿围  | 大腿粗细       |
| 小腿围  | 小腿粗细       |
| 手臂粗细 | 手臂轮廓       |
| 头身比例 | 头部相对于身体的大小 |

**第三层：现实身材数据（完全可选）**

用户可以选择输入：

- 身高。
- 体重。
- 胸围。
- 腰围。
- 臀围。

不需要强迫用户填写三围。

用户只填写身高、体重时，可以通过基础体型模板生成初始比例，再让用户微调。身高和体重不能准确推导胸围、腰围、臀围，AI 只能生成视觉初始估计，不能将其当作真实测量结果。

现实身体数据应作为私密配置，不默认公开，也不应该成为社区排名或身材评价依据。

### **3.6 换装工坊：用户真正玩起来的地方**

这是产品的主要交互模块。

用户选择角色后，进入全屏换装界面。

![Download & Play Anime Dress Up: Fashion Game on PC & Mac (Emulator)](https://images.openai.com/static-rsc-4/ZCcL_mspa4L33ufFII_EokcVFfhGYz24rl-4HjHj5xHs0KvTV5XYil22z2IEO-APGfYsYMHkErLLGZ0lHbD0_uOOyTlN-jtf4HJZ1DXE-R1z0MwC_buR-wGkNe78gpeTQB6T82sRLuiH2MTHEsgEukAgl0o1hnLDuoMypsuAsd8?purpose=inline)

![ミラクルニキ-着せ替えコーデRPG for Android -  Download](https://images.openai.com/static-rsc-4/Miz-ItFHFggjruWVtUq314DlSS-9BweupPd6ZKVX2BhUtR3DuItbKytlWm8ntTbwy_VDeoYmKHGwGt3B4aTTVokjA-tDJure6oN3Zyl4EiIHG_jb0TJWzhqSYjx6Yfz-r-KSLHhqk1zdjhal9x_6jUe73RsU9q0qmW95tGJLkQQ?purpose=inline)

![MAC版 inZOI まとめページ](https://images.openai.com/static-rsc-4/7B7uK3feIlYZjNMVGx8Pe40M4M8SB7IrLZ-qg_67YEpqAEq2mAT1i_ZMukpwGMBqX3UMv7HK7sT88HHGMMq7EaBC9R1PyDCpjiGuSia05ghmx37dAPdaxVx-LziE9LX9UQWFQAPT9pbwajWKwVfdLn1TkkIHCJbK4TkxGA_bUAk?purpose=inline)

17

建议布局：

- 中间：角色展示，支持旋转、缩放、姿势切换。
- 左侧：服装大分类。
- 底部：当前分类的衣物横向列表。
- 右侧：服装详细属性、颜色和尺寸调整。
- 顶部：保存搭配、随机搭配、AI 建议、拍照分享。

具体功能：

1. 单件服装穿戴和脱下。
2. 多件饰品叠加。
3. 服装颜色调整（需要支持的素材才开放）。
4. 衣服尺寸、位置、旋转调整。
5. 左右对称饰品单独调整。
6. 穿搭方案保存。
7. 一键随机穿搭。
8. AI 自动搭配。
9. 角色姿势和表情调整。
10. 穿搭截图和背景场景切换。

尤其需要支持服装之间的冲突检测：

- 穿了长外套，里面的衣服不能完全消失。
- 戴了耳环，长发不能将其全部遮挡。
- 穿了长裙，鞋子应根据裙摆位置合理显示。
- 头饰不能穿透头发。
- 项链不能悬浮在身体外面。

因此换装系统必须有明确的穿戴层级和遮挡规则。

## **四、衣物上传：完整的 AI 资产生产流程**

这部分是产品中最值得提前做好技术规划的部分。

用户上传的不是一张图片，而是未来角色可以穿戴的资产原料。

### **4.1 上传入口与拍照规范**

支持两种方式：

- 直接上传已有衣物图片。
- 按照指定引导拍摄实物衣物。

![Men's white shirt](https://images.openai.com/static-rsc-4/LlMaZzljQh4aJtzBNQGKYCRbRJe_iadKmqBHYvmr1Li-dYCyRFxcstNJokkx0bi8zZm2Sl-tg62cboA1GrWSNVUgnwtEZqaw668c_1lG4O1okyRwCfhPtoaM9YZzE0pRn_1qc0dmcGeAgZh7jMoyeBwBs1Tp7K5j5kWk_QLU0TVFijhXxQJFcH6vbaYuLSTE?purpose=inline)

![Lighting for Clothing Photography (2026 Guide)](https://images.openai.com/static-rsc-4/7HE2haNypEmBIxQNHSbpyQgZW_tHBx0D0nFQ6UEyMYR1Fwala892Xz7fIvxDDA-6KsMxMFHMUwfuJWih-uamW8_U2J997khujHOnKoFOI4tit90QhWqmXLVLvJckJDkOEXYxOBLjFV4DL9s0XZn2NPGT3Um3Q3m6_dA7fVtZsLM?purpose=inline)

![Flat Lay Clothes Photography Ideas (2026 Guide)](https://images.openai.com/static-rsc-4/4ZxQ1N72KOCi4OdLhznMzcnMmV4N6L7ngjTinsAnzKYtYGwAkV4Ke_1sYaLR0YNjBlRFS1-bQOPNMWRkp32g5UE9E3LtswGoPlbWHX7IMQ5XM3KLkYsCuWg2ZGK6UzOE0UoEpW6ePoIB1XWv3NumU1hbM6Bsi-YCouICv95AkLw?purpose=inline)

14

拍摄引导分级：

| 拍摄类型 | 是否必须 | 用途           |
| ---- | ---- | ------------ |
| 正面全貌 | 必须   | 主要服装识别和素材生成  |
| 背面   | 推荐   | 背部结构、图案和领口识别 |
| 侧面   | 可选   | 厚度、版型和侧面细节   |
| 局部细节 | 可选   | 印花、材质、纽扣、装饰  |
| 穿着效果 | 可选   | 衣物实际版型参考     |

初期不要强制每件衣服拍五张照片。第一版只要求正面全貌，其余按服装类别和识别置信度决定是否补拍。

拍摄时通过相机界面实时提示：

- 光线不足。
- 图片模糊。
- 衣服没有完整进入画面。
- 衣服被其他物体遮挡。
- 背景与衣服颜色过于接近。
- 衣服存在明显褶皱。
- 衣物摆放不平整。
- 画面角度不符合要求。

### **4.2 上传审核与图像质量检查**

审核拆成三个不同阶段，不能全部依赖一个 AI 审核模型。

1. **文件安全检查**：文件格式、文件大小、MIME、恶意文件、图片解码异常、EXIF 信息处理。
2. **内容安全审核**：检查色情、裸露、性暗示、暴力、违法内容、未成年人不适宜内容及侵权风险。
3. **图像质量检测**：检查清晰度、曝光、光线、遮挡、完整度、拍摄角度、背景复杂度。
4. **服装识别**：识别衣物主体、分类、颜色、材质、图案、穿戴部位。
5. **用户确认**：展示识别结果并允许用户修改。
6. **素材生产**：分割、抠图、贴图、锚点预测、适配配置。
7. **资产验收**：质量检查后进入正式衣橱资产。

### **4.3 衣物属性结构**

| 信息类别 | 字段内容                 |
| ---- | -------------------- |
| 基础信息 | 名称、一级分类、二级分类、品牌（可选）  |
| 颜色信息 | 主色、辅色、HEX、色彩标签       |
| 外观信息 | 图案、领型、袖型、裙长、裤型       |
| 材质信息 | 棉、麻、羊毛、皮革、针织、雪纺      |
| 季节信息 | 春、夏、秋、冬、四季           |
| 风格信息 | 甜美、学院、休闲、运动、复古、通勤、古风 |
| 场景信息 | 日常、约会、工作、派对、旅行、运动    |
| 尺码信息 | XS、S、M、L、XL、自定义      |
| 版型信息 | 紧身、修身、标准、宽松、Oversize |
| 温度信息 | 适用温度区间、保暖程度          |
| 搭配信息 | 可搭配类别、冲突类别、推荐组合      |
| 资产信息 | 原图、抠图、贴图、缩略图、图层      |
| 模型信息 | 锚点、缩放、偏移、旋转、适配体型     |
| 质量信息 | 清晰度、置信度、生成质量         |
| 权限信息 | 私有、公开、允许分享、允许复用      |

还应该额外建立：

- `wear_layer`
- `occlusion_group`
- `anchor_points`
- `compatible_body_types`
- `supported_character_styles`
- `asset_version`

这不是为了第一版把所有字段都做成用户可见的表单，而是为了保证后续 AI 推荐和换装引擎可以直接使用这些数据。

### **4.4 2.5D 服装贴图生成**

这里建议不要一上来追求完整的 3D 衣物重建。

可以采用 **3D 角色模型 + 2D/2.5D 服装资产** 的混合方案。

![Girl Sprites for Visual Novels by Pepo Kukuru](https://images.openai.com/static-rsc-4/JgodHtNQCJ3-UYv-8tkBGIO0zweatguUX2o6QIoujvxNZzRSryb3qmWsSOUxYrN-Q37YdsG4_HXx0xf260XHyBWKZn2p8A9w6Ya8PdGUwz0_UIdutf8itM4sDndXRcRrb10DyNiJvk4UIi9rGwRjSHi6itPWbLs5omuReDX-IgA?purpose=inline)

![Create custom clothing for your Fuse character](https://images.openai.com/static-rsc-4/lr_rpBI7_ITKJRB7oOxb4kAi52470Y2IdapJmUMBP4uRGim8IfVQFlLd8qW5En6ItqN8IPWFgQPT0j8xA6sjCVM3mqXCt0a8iMVu1DxurkOi1RxdgTB2vhxns7QejlO0bByx8_YEX7jqZPNJk58AK7XQdq2hH_mHBC2DwDRZhGM?purpose=inline)

![Twilight Murmuring - Love Nikki - Mobile - The Spriters Resource](https://images.openai.com/static-rsc-4/al0Ai_8fRWq7tnr9DkQeLcf8lFZpx7UJ1HhIcMgDysH43ut_WB-zqsktsaWeXppf5UwnMPkBIOoeHsS8UL9FMS6bGDG3kjwno40WioRtLQbdqsXZpkZIvcC3_Iwepnpq3RBJUMDXxHD2l-RmdhJvyD94iXXROMkRX4cMPooXGvs?purpose=inline)

15

基本思路：

1. 用户上传衣物照片。
2. AI 自动识别衣物边缘和轮廓。
3. 去除背景。
4. 保留衣服真实颜色、图案和纹理。
5. 生成适合角色比例的正面贴图。
6. 根据需要生成背面和局部贴图。
7. 标注衣物的身体覆盖范围。
8. 标注衣物挂载锚点。
9. 根据角色体型生成适配变形参数。
10. 在角色模型上进行渲染和遮挡测试。

**路径 A：2D 分层服装**

适合耳饰、项链、发饰、帽子、眼镜、简单上衣、鞋袜和正面固定视角换装。

优点是开发快、素材生成成本低。

**路径 B：3D 服装网格或 2.5D 网格贴图**

适合连衣裙、长裤、外套和需要角色旋转展示的复杂衣物。可以使用简化网格、骨骼绑定、UV 贴图和法线效果，让衣服随着人物身体比例变化。

首期不要追求用户上传的任意衣服都能自动生成完美的 360° 服装。第一版先做好正面和有限角度展示，必要时用 AI 补全背面，但需要标注生成内容属于估算，不能把 AI 补全的背面当成实物真实细节。

### **4.5 衣服适配与自由调整**

需要为每件服装建立一套独立的适配配置。

```
{
  "asset_id": "cloth_0001",
  "category": "top",
  "body_parts": ["torso", "left_arm", "right_arm"],
  "anchor_points": [
    "neck",
    "left_shoulder",
    "right_shoulder",
    "waist"
  ],
  "layer_order": 30,
  "transform": {
    "scale_x": 1.0,
    "scale_y": 1.0,
    "offset_x": 0,
    "offset_y": 0,
    "rotation": 0
  },
  "fit_constraints": {
    "min_scale": 0.65,
    "max_scale": 1.65,
    "allow_rotation": true,
    "allow_position_adjustment": true
  }
}
```

以上是概念示例，实际字段应由渲染引擎和角色骨骼体系确定。

调整范围可以较大，但不应该允许无限缩放和无限移动，否则容易把衣服拖到角色身体之外。

建议：

- 位置：支持自由拖动。
- 缩放：支持较大范围调整。
- 旋转：支持自由旋转。
- 透明度：部分装饰素材支持。
- 图层：支持前后调整。
- 左右镜像：根据服装类型决定是否允许。
- 重置：一键恢复默认适配。
- 自动吸附：拖动接近身体锚点时自动对齐。

这里尤其要解决一个问题：**同一件衣服在不同身材角色上的适配。**

例如同一件宽松卫衣：

- 瘦型角色：肩线可能下垂。
- 标准型角色：正常宽松。
- 丰满型角色：衣服宽度需要增加。

因此不能只用统一的图片缩放，而应支持角色身材参数到服装形变参数的映射。

## **五、AI 穿搭助手：从聊天建议到真正执行搭配**

AI 不能只是一个聊天机器人。

它必须能够调用衣橱资产、理解用户偏好、选择服装、执行换装，并返回可操作的穿搭方案。

### **5.1 AI 穿搭的三种使用方式**

![Aesty — AI Stylist, Outfit Planner & Virtual Try-On](https://images.openai.com/static-rsc-4/T1ahLQj0j5I9Nw4bdQpOwHJSAo9kZ6sxEn4Jcw6g9j-hT50Jbi8tf-zIV8N56Mt6VI-hsNlwfIrscKhvYbToJtQqI-18jM7dq2vf-kmg1gZXhVALEvJaExnxuL1VkdL46kvFEFezyDIDdOV7k4DdcpGv1XXxhnKobYkTFKzFeZY?purpose=inline)

**主动推荐**

无需输入文字，结合天气、季节、偏好和衣橱推荐今日穿搭。

![AI-powered fashion app | UI/UX by Karina Bondarenko for Farba Digital on Dribbble](https://images.openai.com/static-rsc-4/ECybkxVslR7BcNbtd6qtNYOlcibHnWbh5gumypeVSXBBYb4QYdNTXh0LE-HkKOVwJS_ztnQIRFpiW7YHbczWYbQQI63h5PH8bSl_dmfBTqeidRsvSjru7g5FYp-24lylpABJaXXgu07IF5cvyEVYv1ZLylcQzaB6ZHqNcsYFln0?purpose=inline)

**聊天搭配**

用户通过自然语言提出要求，AI 从真实衣橱中选择服装。

![Free Virtual Try-On AI - Try On Outfits in Photos Online (No Sign Up) | Magic Hour](https://images.openai.com/static-rsc-4/-CWQAQqtInJbgjGgIR-GPj9uoAEH0nYv9SXMF92sBuW_ojewRCx-GgvTZIe2NOdplo7bdKpyzqnYSRG2QcoqVH6VDBTXpOrzOjQHVyOocWHEIfGJx5Jq2_H7Iobqn09Aiz9oDIH-hfLqZQlor-Y5VX1rZqdg_eVbV0sJEBfcCCM?purpose=inline)

**AI 自动换装**

AI 生成多套方案，调用换装引擎试穿、修改和保存。

### **5.2 AI 必须具备的上下文**

建议将上下文拆成五个部分：

| 上下文   | 主要内容              |
| ----- | ----------------- |
| 用户画像  | 风格偏好、喜欢的颜色、穿搭习惯   |
| 数字衣橱  | 所有衣物、鞋子、饰品及属性     |
| 角色画像  | 身材、角色审美、角色设定      |
| 环境上下文 | 天气、温度、季节、场景       |
| 历史上下文 | 历史穿搭、用户反馈、收藏、否定偏好 |

例如用户经常拒绝过于暴露的搭配，AI 应当逐渐理解这一偏好，而不是每次都重新询问。

角色和用户的偏好也要分开：

- 用户喜欢甜美风。
- 女儿角色喜欢古风。
- 儿子角色喜欢运动风。

不能把所有角色的穿搭偏好混成一个用户画像。

### **5.3 AI 穿搭的执行流程**

\#chatgpt-mermaid-\_r_6qb\_{font-family:-apple-system-body,ui-sans-serif,-apple-system,system-ui,"Segoe UI",Helvetica,"Apple Color Emoji",Arial,sans-serif,"Segoe UI Emoji","Segoe UI Symbol";font-size:16px;fill:rgb(13, 13, 13);}@keyframes edge-animation-frame{from{stroke-dashoffset:0;}}@keyframes dash{to{stroke-dashoffset:0;}}#chatgpt-mermaid-\_r_6qb\_ .edge-animation-slow{stroke-dasharray:9,5!important;stroke-dashoffset:900;animation:dash 50s linear infinite;stroke-linecap:round;}#chatgpt-mermaid-\_r_6qb\_ .edge-animation-fast{stroke-dasharray:9,5!important;stroke-dashoffset:900;animation:dash 20s linear infinite;stroke-linecap:round;}#chatgpt-mermaid-\_r_6qb\_ .error-icon{fill:rgb(243, 243, 243);}#chatgpt-mermaid-\_r_6qb\_ .error-text{fill:rgb(13, 13, 13);stroke:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_6qb\_ .edge-thickness-normal{stroke-width:1px;}#chatgpt-mermaid-\_r_6qb\_ .edge-thickness-thick{stroke-width:3.5px;}#chatgpt-mermaid-\_r_6qb\_ .edge-pattern-solid{stroke-dasharray:0;}#chatgpt-mermaid-\_r_6qb\_ .edge-thickness-invisible{stroke-width:0;fill:none;}#chatgpt-mermaid-\_r_6qb\_ .edge-pattern-dashed{stroke-dasharray:3;}#chatgpt-mermaid-\_r_6qb\_ .edge-pattern-dotted{stroke-dasharray:2;}#chatgpt-mermaid-\_r_6qb\_ .marker{fill:rgb(143, 143, 143);stroke:rgb(143, 143, 143);}#chatgpt-mermaid-\_r_6qb\_ .marker.cross{stroke:rgb(143, 143, 143);}#chatgpt-mermaid-\_r_6qb\_ svg{font-family:-apple-system-body,ui-sans-serif,-apple-system,system-ui,"Segoe UI",Helvetica,"Apple Color Emoji",Arial,sans-serif,"Segoe UI Emoji","Segoe UI Symbol";font-size:16px;}#chatgpt-mermaid-\_r_6qb\_ p{margin:0;}#chatgpt-mermaid-\_r_6qb\_ .label{font-family:-apple-system-body,ui-sans-serif,-apple-system,system-ui,"Segoe UI",Helvetica,"Apple Color Emoji",Arial,sans-serif,"Segoe UI Emoji","Segoe UI Symbol";color:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_6qb\_ .cluster-label text{fill:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_6qb\_ .cluster-label span{color:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_6qb\_ .cluster-label span p{background-color:transparent;}#chatgpt-mermaid-\_r_6qb\_ .label text,#chatgpt-mermaid-\_r_6qb\_ span{fill:rgb(13, 13, 13);color:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_6qb\_ .node rect,#chatgpt-mermaid-\_r_6qb\_ .node circle,#chatgpt-mermaid-\_r_6qb\_ .node ellipse,#chatgpt-mermaid-\_r_6qb\_ .node polygon,#chatgpt-mermaid-\_r_6qb\_ .node path{fill:rgb(222, 234, 251);stroke:rgb(83, 154, 248);stroke-width:1px;}#chatgpt-mermaid-\_r_6qb\_ .rough-node .label text,#chatgpt-mermaid-\_r_6qb\_ .node .label text,#chatgpt-mermaid-\_r_6qb\_ .image-shape .label,#chatgpt-mermaid-\_r_6qb\_ .icon-shape .label{text-anchor:middle;}#chatgpt-mermaid-\_r_6qb\_ .node .katex path{fill:#000;stroke:#000;stroke-width:1px;}#chatgpt-mermaid-\_r_6qb\_ .rough-node .label,#chatgpt-mermaid-\_r_6qb\_ .node .label,#chatgpt-mermaid-\_r_6qb\_ .image-shape .label,#chatgpt-mermaid-\_r_6qb\_ .icon-shape .label{text-align:center;}#chatgpt-mermaid-\_r_6qb\_ .node.clickable{cursor:pointer;}#chatgpt-mermaid-\_r_6qb\_ .root .anchor path{fill:rgb(143, 143, 143)!important;stroke-width:0;stroke:rgb(143, 143, 143);}#chatgpt-mermaid-\_r_6qb\_ .arrowheadPath{fill:rgb(143, 143, 143);}#chatgpt-mermaid-\_r_6qb\_ .edgePath .path{stroke:rgb(143, 143, 143);stroke-width:1px;}#chatgpt-mermaid-\_r_6qb\_ .flowchart-link{stroke:rgb(143, 143, 143);fill:none;}#chatgpt-mermaid-\_r_6qb\_ .edgeLabel{background-color:rgb(252, 252, 252);text-align:center;}#chatgpt-mermaid-\_r_6qb\_ .edgeLabel p{background-color:rgb(252, 252, 252);}#chatgpt-mermaid-\_r_6qb\_ .edgeLabel rect{opacity:0.5;background-color:rgb(252, 252, 252);fill:rgb(252, 252, 252);}#chatgpt-mermaid-\_r_6qb\_ .labelBkg{background-color:rgba(252, 252, 252, 0.5);}#chatgpt-mermaid-\_r_6qb\_ .cluster rect{fill:rgb(243, 243, 243);stroke:rgba(0, 0, 0, 0.1);stroke-width:1px;}#chatgpt-mermaid-\_r_6qb\_ .cluster text{fill:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_6qb\_ .cluster span{color:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_6qb\_ div.mermaidTooltip{position:absolute;text-align:center;max-width:200px;padding:2px;font-family:-apple-system-body,ui-sans-serif,-apple-system,system-ui,"Segoe UI",Helvetica,"Apple Color Emoji",Arial,sans-serif,"Segoe UI Emoji","Segoe UI Symbol";font-size:12px;background:rgb(243, 243, 243);border:1px solid rgba(0, 0, 0, 0.1);border-radius:2px;pointer-events:none;z-index:100;}#chatgpt-mermaid-\_r_6qb\_ .flowchartTitleText{text-anchor:middle;font-size:18px;fill:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_6qb\_ rect.text{fill:none;stroke-width:0;}#chatgpt-mermaid-\_r_6qb\_ .icon-shape,#chatgpt-mermaid-\_r_6qb\_ .image-shape{background-color:rgb(252, 252, 252);text-align:center;}#chatgpt-mermaid-\_r_6qb\_ .icon-shape p,#chatgpt-mermaid-\_r_6qb\_ .image-shape p{background-color:rgb(252, 252, 252);padding:2px;}#chatgpt-mermaid-\_r_6qb\_ .icon-shape .label rect,#chatgpt-mermaid-\_r_6qb\_ .image-shape .label rect{opacity:0.5;background-color:rgb(252, 252, 252);fill:rgb(252, 252, 252);}#chatgpt-mermaid-\_r_6qb\_ .label-icon{display:inline-block;height:1em;overflow:visible;vertical-align:-0.125em;}#chatgpt-mermaid-\_r_6qb\_ .node .label-icon path{fill:currentColor;stroke:revert;stroke-width:revert;}#chatgpt-mermaid-\_r_6qb\_ .node .neo-node{stroke:rgb(83, 154, 248);}#chatgpt-mermaid-\_r_6qb\_ [data-look="neo"].node rect,#chatgpt-mermaid-\_r_6qb\_ [data-look="neo"].cluster rect,#chatgpt-mermaid-\_r_6qb\_ [data-look="neo"].node polygon{stroke:url(#chatgpt-mermaid-\_r_6qb\_-gradient);filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-\_r_6qb\_ [data-look="neo"].swimlane.cluster rect{filter:none;}#chatgpt-mermaid-\_r_6qb\_ [data-look="neo"].node path{stroke:url(#chatgpt-mermaid-\_r_6qb\_-gradient);stroke-width:1px;}#chatgpt-mermaid-\_r_6qb\_ [data-look="neo"].node .outer-path{filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-\_r_6qb\_ [data-look="neo"].node .neo-line path{stroke:rgb(83, 154, 248);filter:none;}#chatgpt-mermaid-\_r_6qb\_ [data-look="neo"].node circle{stroke:url(#chatgpt-mermaid-\_r_6qb\_-gradient);filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-\_r_6qb\_ [data-look="neo"].node circle .state-start{fill:#000000;}#chatgpt-mermaid-\_r_6qb\_ [data-look="neo"].icon-shape .icon{fill:url(#chatgpt-mermaid-\_r_6qb\_-gradient);filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-\_r_6qb\_ [data-look="neo"].icon-shape .icon-neo path{stroke:url(#chatgpt-mermaid-\_r_6qb\_-gradient);filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-\_r_6qb\_ .node text{font-size:14px;font-weight:600;letter-spacing:normal;fill:rgb(0, 79, 153);}#chatgpt-mermaid-\_r_6qb\_ .edgeLabels text{font-size:13px;font-weight:600;letter-spacing:-0.08px;fill:rgb(0, 79, 153);}#chatgpt-mermaid-\_r_6qb\_ .node tspan[font-weight="normal"],#chatgpt-mermaid-\_r_6qb\_ .edgeLabels tspan[font-weight="normal"]{font-weight:600;}#chatgpt-mermaid-\_r_6qb\_ .edgeLabel .label rect{opacity:1;rx:13px;ry:13px;fill:rgb(245, 250, 255);stroke:rgb(206, 219, 229);stroke-width:1px;}#chatgpt-mermaid-\_r_6qb\_ .node rect,#chatgpt-mermaid-\_r_6qb\_ .node circle,#chatgpt-mermaid-\_r_6qb\_ .node ellipse,#chatgpt-mermaid-\_r_6qb\_ .node polygon,#chatgpt-mermaid-\_r_6qb\_ .node path{fill:rgb(229, 243, 255);stroke:rgba(0, 0, 0, 0.1);stroke-width:1px;}#chatgpt-mermaid-\_r_6qb\_ .node rect{rx:16px;ry:16px;}#chatgpt-mermaid-\_r_6qb\_ .mermaid-decision .label-container{fill:rgb(245, 250, 255);stroke:rgb(206, 219, 229);stroke-dasharray:2,2;}#chatgpt-mermaid-\_r_6qb\_ .edgePaths .flowchart-link{stroke:rgb(143, 143, 143);stroke-width:1px;stroke-linecap:round;stroke-linejoin:round;}#chatgpt-mermaid-\_r_6qb\_ .marker{fill:rgb(143, 143, 143);stroke:rgb(143, 143, 143);}#chatgpt-mermaid-\_r_6qb\_ :root{--mermaid-font-family:-apple-system-body,ui-sans-serif,-apple-system,system-ui,"Segoe UI",Helvetica,"Apple Color Emoji",Arial,sans-serif,"Segoe UI Emoji","Segoe UI Symbol";}用户提出穿搭需求意图识别与需求结构化检索衣橱资产与可用服装规则过滤：季节、颜色、身材、场景搭配组合生成与排序调用换装引擎渲染多个方案用户试穿、反馈、保存反馈结果回流到个人偏好模型

### **5.4 搭配引擎不能完全依赖 LLM**

建议采用混合推荐架构。

**第一层：规则过滤**

- 服装部位是否兼容。
- 当前季节是否适合。
- 是否满足用户的场景需求。
- 服装是否已被删除或禁用。
- 是否与其他服装存在硬冲突。

**第二层：属性匹配**

- 颜色协调。
- 风格一致性。
- 版型协调。
- 材质协调。
- 季节与温度匹配。

**第三层：LLM 语义理解**

理解用户的自然语言意图，例如：

- 想要显高。
- 想要温柔。
- 不想太正式。
- 想要日系学院风。
- 想要有一点复古感。

**第四层：排序与反馈**

根据用户历史点击、收藏、保存、换装、拒绝等行为优化推荐结果。

关键原则：**AI 负责理解和决策，确定性规则负责约束，换装引擎负责执行。**

不能让 LLM 直接凭空编造一套衣服，更不能让它返回不存在的衣物 ID。

### **5.5 AI 的后续扩展**

未来可以继续扩展：

- AI 识别穿搭照片，推荐相似风格。
- AI 分析用户已有衣服的搭配潜力。
- AI 发现衣橱中的闲置衣物。
- AI 推荐缺少的基础款。
- AI 根据某件衣服生成多套搭配。
- AI 帮角色设计专属穿搭风格。
- AI 生成主题套装和活动穿搭。
- AI 与角色进行日常聊天，形成长期陪伴。

其中最后一项可以作为后续的情感养成方向，但不要在首期把它做成复杂的虚拟恋爱或陪伴系统，以免稀释核心穿搭价值。

## **六、分享与社区：让用户的资产能够流动**

这一部分需要提前设计，因为分享权限决定后续商业模式。

建议不要简单地设置一个公开 / 私密开关，而是将内容和资产的使用权分开。

### **6.1 分享对象**

用户可以分享四种不同类型的内容：

| 分享类型 | 其他用户看到什么   | 是否可以复用 |
| ---- | ---------- | ------ |
| 穿搭作品 | 角色和整套搭配展示  | 根据授权   |
| 单件衣服 | 衣物展示及属性    | 根据授权   |
| 饰品资产 | 饰品展示及穿戴效果  | 根据授权   |
| 角色主页 | 角色形象、简介、作品 | 根据授权   |

还可以扩展：

- 穿搭合集。
- 主题衣橱。
- 角色设定卡。
- AI 穿搭方案。
- 创作者作品集。

### **6.2 分享权限体系**

建议设计四档：

**仅自己可见**

默认安全。仅本人查看和使用，不能被其他用户搜索、引用或下载。

**公开展示**

其他用户可以浏览、点赞、收藏，但不能直接将资产添加到自己的衣橱。

**允许免费复用**

其他用户可以将授权资产添加到自己的虚拟衣橱和角色中，保留原作者信息。

**允许商业使用或付费获取**

创作者设置价格和授权范围，平台记录交易与收益分配。需建立额外的版权审核和授权协议。

最重要的是：

> 分享穿搭作品，不等于分享作品中所有服装资产的使用权。

例如用户用自己的 5 件私有衣服做了一套漂亮穿搭，分享后别人应该能看到整套效果，但不应该自动获得这 5 件衣服的可穿戴素材。

建议分享时显示：

- 作品展示权限。
- 是否允许复用整套搭配。
- 是否允许单独复用其中的服装。
- 是否允许二次创作。
- 是否允许商业使用。
- 是否允许下载原始素材。

还需要区分现实衣物照片和 AI 生成的虚拟贴图：用户拥有上传照片，并不代表其自动拥有服装品牌图案、商标或他人设计的商业使用权。

### **6.3 社区页面**

![Қытай ЖИ бәйгесінде үнсіз алға шығып бара ма? | Aikyn.kz](https://images.openai.com/static-rsc-4/1mhf9wEY5Z55tUAI7qjCUgvdw5IQe2ZYujfNYniaj0pr1sYGwb-DGDY-w-BFr3DJaHAv69cNSEEc7KFHsdAGu3wJHbDE2gN8Vf6LXknS_5HqVDMU1D-jUlsTMR3ufwO1eFSqD_grcsqU6_Phgs9Oi-7dtIIx-GASRn2v-xhWFP8?purpose=inline)

![5 ways to use Whering Social to elevate your style – Whering](https://images.openai.com/static-rsc-4/zuE4h4RkUw21_vHL986dR7jWYgD8nO0NLrxJKbGKY6a6e_L1C_9YNsRgEJ83BiVT89swZ9AmcvzqkasN49eZ7aiFra-jd16JZRd7rra2XuhfgcLtRgCgSzNc8sxPjZAOXlYa2EkFxV-9lYGY-17kJrx7uS3nIZsgo1mWB_d7F40?purpose=inline)

![Hannah - SLAY - BOOTH](https://images.openai.com/static-rsc-4/zQ3b__nwXAykojk8KpAg-dQZnUXgsatsYQLxIPmHVC1Pf1so-TrtWuo2a_JsmY1u81R4oSl8pkyFAScj-eRthYV4KECvvIjQH8iRehF5hOhtIVNWL65nxkh8sY8No7AtfZNYCcWKq7SJ-kA0yY98g77RQnxmBDZomCQhOPsOhh0?purpose=inline)

17

建议社区内容结构：

- 推荐：热门穿搭。
- 关注：关注的创作者和朋友。
- 主题：每日搭配挑战。
- 角色：热门角色展示。
- 创作：原创服装、饰品和素材。
- 收藏：用户收藏的穿搭。

互动机制：

- 点赞。
- 评论。
- 收藏。
- 关注。
- 分享。
- 复用搭配。
- 复用单件资产。
- 二次创作。
- 作品举报。

对于复用其他用户的资产，应该能够追溯来源和授权状态。

例如 A 创作的项链被 B 使用，B 再将穿搭分享给 C，C 应该仍能查看原始创作者和授权信息。

## **七、角色和服装素材的技术选型**

这一部分需要尽早验证，不建议直接让研发从零开始写角色系统。

### **7.1 开源角色系统调研**

**M3-org CharacterStudio**

优先技术验证。

- GitHub：![CharacterStudio](https://github.com/M3-org/CharacterStudio?utm_source=chatgpt.com)
- 文档：![CharacterStudio Docs](https://m3-org.github.io/characterstudio-docs/docs/about/?utm_source=chatgpt.com)

基于 Three.js，适合研究角色创建器的基础结构。需要验证角色部件选择、颜色调整、VRM/GLB 导入导出和角色优化能力是否符合本项目需求。

**Character Creator 3D MVP**

\- GitHub：![开源仓库](https://github.com/whelal/character-creator-3d-mvp?utm_source=chatgpt.com)

有 JSON 驱动的角色部件、体型滑块、随机生成、保存预设等基础能力，适合研究快速原型。其身体比例目前主要是简化缩放，不是成熟的生产级人体形变系统。

**VRM + Three.js**

- Three.js：![GLTFLoader 文档](https://threejs.org/docs/pages/GLTFLoader.html?utm_source=chatgpt.com)
- three-vrm：[GitHub](https://github.com/pixiv/three-vrm?utm_source=chatgpt.com)

适合统一角色模型、骨骼、表情、动作和资源格式。需要进一步验证角色编辑和服装挂载的适配能力。

我的建议是：

**优先验证 CharacterStudio + Three.js + VRM 的技术组合，但不要直接把现有开源项目当成完整产品。**

重点要检查：

1. 能否实现我们需要的可爱脸型。
2. 能否支持真正的身体 Morph Targets。
3. 能否支持服装部件的独立挂载。
4. 能否支持多个角色体型。
5. 能否支持复杂的衣物遮挡。
6. 能否在移动端稳定运行。
7. 开源代码、模型、贴图、素材是否分别具备可商用授权。

注意：代码仓库是 MIT 许可，不代表它引用的所有人物模型和美术素材也都是 MIT 许可。必须逐项核查。

### **7.2 建议技术架构**

| 技术层   | 建议方案                        | 主要职责        |
| ----- | --------------------------- | ----------- |
| 前端    | Flutter / WebView 或原生 3D 模块 | App 业务界面    |
| 3D 渲染 | Three.js / WebGL            | 角色展示和换装     |
| 角色格式  | VRM / GLB                   | 角色资产标准化     |
| 图像识别  | 视觉模型 + 分类模型                 | 衣物识别        |
| 图片处理  | SAM 类分割模型 / 专用抠图            | 衣物分割        |
| AI 生成 | 图像生成模型                      | 2.5D 服装素材生成 |
| 推荐系统  | 规则引擎 + 向量检索 + LLM           | 搭配推荐        |
| 资产存储  | 对象存储 + CDN                  | 原图、贴图、模型    |
| 业务数据  | 关系型数据库                      | 用户、衣物、角色、授权 |
| 异步任务  | 消息队列 / 任务调度                 | 图片处理、审核、生成  |

需要单独强调：如果 App 使用 Flutter，建议将 3D 角色渲染做成独立的渲染模块，不要让所有换装、骨骼、贴图和碰撞逻辑都堆在 Flutter 业务层。

### **7.3 一个重要的技术决策：角色与服装必须解耦**

不能为每一种身材重新制作一套衣服。

建议建立统一角色骨骼和身体形变体系。

例如：

- 角色 A：标准体型。
- 角色 B：纤细体型。
- 角色 C：丰满体型。

三者共享同一套服装资产，通过骨骼、形变参数和适配配置完成穿戴。

不过饰品不一定需要骨骼绑定，例如耳钉、项链、眼镜可以直接绑定到头部或对应锚点。

这样才能让用户上传一次衣服，给自己的多个角色使用。

## **八、产品商业模式设计**

不建议首期直接把产品做成付费换装游戏。

应该先建立使用价值，再引入内容和资产消费。

### **8.1 可能的商业模式**

| 模式      | 收入来源                | 优先级 |
| ------- | ------------------- | --- |
| 会员订阅    | AI 搭配次数、角色数量、素材生成额度 | P1  |
| 虚拟服饰商城  | 官方服装、饰品、发型、场景       | P1  |
| 创作者市场   | 用户出售原创服装和素材         | P2  |
| 角色装扮包   | 主题角色、动作、表情、背景       | P2  |
| AI 高级服务 | 高质量素材生成、个性化设计       | P2  |
| 品牌合作    | 品牌服装数字化、联名活动        | P3  |
| 电商导购    | 根据真实衣橱推荐购买商品        | P3  |

### **8.2 会员体系**

可以考虑免费版和会员版：

| 能力     | 免费版    | 会员版  |
| ------ | ------ | ---- |
| 基础衣橱   | 支持     | 支持   |
| 角色数量   | 限量     | 更多角色 |
| 基础换装   | 支持     | 支持   |
| AI 搭配  | 每日有限次数 | 更高额度 |
| 服装素材生成 | 有限额度   | 更多额度 |
| 高级角色定制 | 基础功能   | 高级选项 |
| 私人穿搭记录 | 支持     | 支持   |
| 高级分享模板 | 基础     | 更多模板 |

这里需要注意生成成本。图片生成、图像分割和 AI 对话都可能产生实际成本，不能采用没有上限的无限免费生成。

### **8.3 虚拟资产经济体系**

后续可以引入积分或虚拟货币：

- 用户上传真实衣服：获得基础积分奖励。
- 用户完成角色创建：获得新手奖励。
- 用户发布优质穿搭：获得创作积分。
- 用户参与主题挑战：获得活动奖励。
- 用户创作原创服饰：获得市场收益。

但不能简单地通过上传图片刷积分，否则会导致大量低质量、重复甚至违规素材。

需要配合有效性判断、审核、重复检测和行为风控。

## **九、版本规划：不要第一版就把所有能力都做完**

核心原则是：先验证衣物数字化和角色换装是否真正成立，再扩展 AI 和社区，最后做资产生态。

### **V0.1 — 技术验证与产品原型**

最高优先级

目标：验证核心技术链路，不追求完整商业化。

- 确定角色美术风格和基础角色模型。
- 实现基础捏脸、身材模板。
- 实现上装、下装、鞋子、饰品的穿戴。
- 验证衣物上传、抠图、分类。
- 验证 AI 生成 2.5D 服装素材。
- 建立服装部位、锚点和图层规范。
- 验证不同身材下的服装适配。
- 实现基础衣橱和穿搭保存。

### **V1.0 — 可用产品 MVP**

核心交付

目标：用户可以真正使用自己的衣服给角色搭配。

- 用户注册、登录和个人资料。
- 创建多个角色。
- 衣物拍摄引导和上传审核。
- AI 衣物识别和属性编辑。
- 数字衣橱管理。
- 核心品类完整换装。
- 角色身材与服装尺寸调整。
- 穿搭保存、历史记录。
- AI 对话式穿搭推荐。
- AI 自动生成多套搭配。
- 穿搭作品图片分享。
- 基础举报、内容审核和隐私设置。

### **V1.5 — 社区与内容生态**

目标：让用户持续创作、浏览和复用内容。

- 穿搭社区和推荐 Feed。
- 角色主页和关注系统。
- 穿搭作品收藏、评论。
- 单件衣物和饰品分享。
- 资产复用授权。
- 每日穿搭挑战。
- 官方服饰素材库。
- 多种角色风格和高级捏脸。
- 主题场景和拍照动作。

### **V2.0 — 创作者市场与商业化**

目标：形成虚拟时尚资产交易和创作者生态。

- 原创服装创作工具。
- 创作者主页及认证。
- 虚拟服饰市场。
- 免费复用和付费授权。
- 服装、角色和场景素材交易。
- 品牌联名与数字服装。
- AI 个性化服装设计。
- 角色长期成长和互动玩法。
- 更完整的 3D 服装物理效果。

### **9.1 MVP 应该明确砍掉什么**

首期不建议做：

1. 完整 360° 任意服装 3D 重建。
2. 复杂的布料物理模拟。
3. 用户之间的虚拟货币交易。
4. 完整创作者市场。
5. 实时多人角色互动。
6. 复杂的虚拟恋爱和剧情养成。
7. 完整的 AR 试穿。
8. 复杂的服装编辑器和专业建模工具。

这些都可以是未来的方向，但不应该成为首版上线的阻碍。

### **9.2 首版必须验证的四个技术难题**

| 技术问题      | 验证标准                 |
| --------- | -------------------- |
| 衣物识别和分割   | 普通手机拍摄的衣服能否稳定提取主体    |
| 2.5D 素材生成 | 是否能保留衣物的颜色、图案、轮廓和细节  |
| 角色身材适配    | 同一件衣服能否在多种身材下正常显示    |
| 饰品锚点和遮挡   | 耳饰、项链、发饰等能否正确挂载并避免穿模 |

我建议在正式立项后，单独安排一轮技术 PoC。

特别是第二和第三项：如果用户上传衣服后，生成的虚拟衣服已经完全变样，或者一换身材就穿模，整个产品最重要的体验就无法成立。

## **十、产品指标与数据埋点**

不能只看注册用户数和日活。

这款产品的核心是用户能否完成从现实衣服到虚拟穿搭的转化。

### **10.1 核心北极星指标**

**每周有效穿搭创作用户数（Weekly Active Outfit Creators）**

定义：一周内至少完成一次有效穿搭，并保存、分享或记录穿搭的去重用户数。

相比单纯打开 App，这个指标更能反映产品核心价值。

### **10.2 关键指标**

| 指标        | 计算方式                | 关注问题     |
| --------- | ------------------- | -------- |
| 衣物上传转化率   | 完成上传人数 / 进入上传人数     | 上传成本是否过高 |
| 衣物识别成功率   | 成功识别数量 / 上传数量       | AI 识别质量  |
| 衣物素材生成成功率 | 成功生成数量 / 发起生成数量     | 资产生产能力   |
| 衣橱激活率     | 完成规定数量衣物入库人数 / 注册人数 | 用户是否建立衣橱 |
| 首次穿搭完成率   | 完成第一套搭配人数 / 注册人数    | 核心体验是否顺畅 |
| AI 推荐采纳率  | 被保存或实际应用的推荐 / 推荐总量  | 推荐是否有价值  |
| 穿搭复用率     | 使用已有资产再次搭配的用户比例     | 长期使用价值   |
| 分享率       | 分享作品人数 / 活跃用户数      | 社交传播能力   |
| 次周留存率     | 次周回访用户 / 首周新增用户     | 持续使用能力   |
| 付费转化率     | 付费人数 / 活跃用户数        | 商业化能力    |

### **10.3 建议重点埋点**

- `wardrobe_upload_started`
- `wardrobe_upload_completed`
- `garment_recognition_completed`
- `garment_asset_generated`
- `garment_asset_corrected`
- `avatar_created`
- `avatar_body_changed`
- `outfit_item_equipped`
- `outfit_saved`
- `ai_recommendation_requested`
- `ai_recommendation_applied`
- `outfit_shared`
- `shared_asset_reused`
- `asset_license_changed`

尤其要关注用户反复修改 AI 识别结果的行为。如果某类衣服经常识别错误，就要针对该类别优化模型或补充拍摄引导。

### **10.4 指标口径补充**

所有指标必须明确统计对象、去重规则、时间窗口和异常过滤规则。

例如：

- 上传转化率：以进入上传流程的去重用户为分母，不能用上传任务次数替代用户数。
- 识别成功率：区分模型完成识别与用户认可识别结果，不能把模型返回结果当成业务成功。
- 素材生成成功率：必须以资产通过质量检查并进入可用状态为成功。
- 首次穿搭完成率：必须有有效角色、有效服装和保存成功记录。
- AI 推荐采纳率：区分点击方案、应用方案和最终保存方案。
- 分享率：区分系统分享面板打开、链接复制和真实发布成功。

### **10.5 成本指标**

必须单独跟踪：

- 每次衣物识别成本。
- 每次图像分割成本。
- 每次服装素材生成成本。
- 每次 AI 搭配成本。
- 每个有效用户的 AI 成本。
- 每套有效穿搭的 AI 成本。
- 失败任务成本。
- 重试成本。
- 缓存命中率。

避免只看 API 单价，而忽略重试、失败、人工复核、对象存储和渲染成本。

## **十一、必须提前考虑的边界条件和风险**

服装资产涉及大量图片上传、AI 生成、用户创作和跨用户复用，边界条件非常多。

| 风险类型   | 可能出现的问题      | 产品处理机制        |
| ------ | ------------ | ------------- |
| 图片安全   | 上传色情、裸露、违法图片 | 上传前后双重审核      |
| 未成年人保护 | 上传未成年人不适宜图片  | 严格内容审核和账号保护   |
| 图片质量   | 模糊、遮挡、过曝     | 质量检测和补拍引导     |
| 分类错误   | 连衣裙识别成上衣     | 用户确认和手动修改     |
| 部位错误   | 长靴只绑定脚部      | 多部位占用关系       |
| 素材生成   | 服装图案被 AI 改写  | 原图纹理优先保留，质量校验 |
| 适配问题   | 衣服穿模、悬浮      | 锚点校准和人工微调     |
| 身材问题   | 身材调整后衣服变形    | 体型兼容性配置       |
| 数据安全   | 私人衣橱泄露       | 私有资产权限隔离      |
| 分享侵权   | 未经授权的品牌图案    | 版权投诉和下架机制     |
| 资产盗用   | 其他用户擅自下载素材   | 权限控制、溯源、授权记录  |
| AI 幻觉  | 推荐不存在的衣服     | 只能使用衣橱真实资产 ID |
| 服务失败   | AI 超时、生成失败   | 任务状态、重试、失败恢复  |
| 成本问题   | 大量图片重复生成     | 缓存、额度、任务去重    |
| 社区风险   | 垃圾内容、刷赞、恶意评论 | 举报、风控、内容治理    |

### **11.1 删除衣物之后，历史穿搭怎么办？**

建议删除衣物时采用软删除机制。

- 用户衣橱中不再显示。
- 历史穿搭保留原有展示快照。
- 已公开作品根据授权状态决定是否保留。
- 如果涉及侵权或违规，应支持同步下架。
- 用户可在规定期限内恢复误删资产。

### **11.2 分享出去的衣服，原作者删除了怎么办？**

需要区分：

- 公开展示作品。
- 已授权复用资产。
- 已经被其他用户添加的资产。
- 付费授权资产。

不能简单地因为作者删除原图，就让所有使用该资产的用户出现无法显示的空白。

建议使用资产版本和授权快照，并设置撤销授权、停止新下载和存量使用处理规则。

### **11.3 AI 生成失败怎么办？**

不能让用户一直停留在转圈页面。

每个生成任务都应该有：

- 任务 ID。
- 当前阶段。
- 进度状态。
- 失败原因。
- 重试次数。
- 是否可以继续处理。
- 任务超时时间。
- 生成结果地址。

上传、审核、生成、适配都应该是可以独立重试的任务。

## **十二、最终产品形态：我们到底要做成什么样？**

建议最终将产品体验设计成四个主要空间。

![梦幻装扮间_梦幻装扮间秒玩入口_在线玩_雷电模拟器](https://images.openai.com/static-rsc-4/OJpjNnX9mI3rP7PpMobwmGa3r98mrbV8Nx5z9mxphhnRmlywASeTg6gfvJTtOg1Ndj0rEsoL559Zx3Auu0lnt65S2C0wigWgs9lQBij8C0WkC4sDZ8m69NdQQrk3JIRw-mNAt7q0AygkRdjD_HL63AT8FBAJICgvwuditd8mNGk?purpose=inline)

**空间一：我的世界**

角色展示、每日穿搭、角色切换、日常互动、天气和推荐。

![Digital Wardrobe Organization: How I Transformed My Closet in 2025 | by Juliette Moreau | Medium](https://images.openai.com/static-rsc-4/nlK9_zoCuF-d9obi5xJf0TmB_J9_KI-YoHSV_3w_YW6IdHfUujA2sMkhvU98_GfBgBb7kvdBNmhiYLWul_LeTGBuWBHaJwQAPg3RUUjRvkMJw8nbWEP1xSWUO5NBTRSso30BN01DO6lXjjZxzT3k844tJ92lgeKpj9fz_bEbjDY?purpose=inline)

**空间二：我的衣橱**

现实衣服数字化、衣物管理、AI 识别、衣物标签、穿搭记录。

![Download & Play Anime Dress Up: Fashion Game on PC & Mac (Emulator)](https://images.openai.com/static-rsc-4/ZCcL_mspa4L33ufFII_EokcVFfhGYz24rl-4HjHj5xHs0KvTV5XYil22z2IEO-APGfYsYMHkErLLGZ0lHbD0_uOOyTlN-jtf4HJZ1DXE-R1z0MwC_buR-wGkNe78gpeTQB6T82sRLuiH2MTHEsgEukAgl0o1hnLDuoMypsuAsd8?purpose=inline)

**空间三：换装工坊**

捏脸、体型、发型、服饰、饰品、AI 搭配、角色拍照。

![Fashion Social App | Style Sharing Platform | Outfit Inspiration by ByteTown for ByteTown Agency on Dribbble](https://images.openai.com/static-rsc-4/CvddkJpFv5zTnyfP9hcFJU8VqUan4xfAyt3iy0Tb6M1IxCH85QyfJMkWPJ-vJJBzKonBb5woKAoHGLQVXMHGbDduaeYUvvrnJDMxk6UPJlfnMC_lx7hrJNDj8ljA9onyXZ5YmUlb5WmG30IUpF1POoL9YJMzM8o3VVAGJWTHmZ8?purpose=inline)

**空间四：时尚社区**

作品浏览、主题挑战、创作者、角色展示、服装资产分享和复用。

## **十三、给领导汇报时的立项结论**

建议汇报时不要把它说成一个功能堆叠项目，而是强调它具备三层价值。

# **AI 数字衣橱与虚拟时尚社区**

**一句话定位：**

将用户的真实衣物转化为可识别、可管理、可穿戴、可分享的数字服装资产，通过 AI 穿搭和虚拟角色养成，打造连接现实衣橱与虚拟时尚世界的产品。

**第一层：现实价值**

帮助用户管理真实衣橱，解决不知道穿什么、衣服不会搭配、衣物利用率低的问题。

**第二层：情感价值**

用户能够创建并长期养成自己的虚拟角色，将其作为女儿、儿子、娃娃或原创角色，通过服装、饰品和形象设计进行个性化表达。

**第三层：生态价值**

通过穿搭分享、数字服装资产复用、创作者市场和品牌合作，形成用户内容生产、资产流通和商业化闭环。

### **首期建议投入重点**

最重要的不是先把社区和商城做出来，而是先把以下三个东西做好：

1. **衣物数字化能力：** 用户随手拍一件衣服，AI 能识别、抠图、分类并生成可以使用的服装资产。
2. **角色换装能力：** 用户能创建一个足够可爱、足够有辨识度的角色，能够自由调整身材，并把自己的衣服穿到角色身上。
3. **AI 搭配能力：** AI 能真正理解用户的衣橱和需求，调用已有衣物完成搭配，而不只是聊天和生成几张图片。

这三个环节跑通，产品就已经具备了最基本的差异化。

## **十四、立项后建议立即安排的工作**

| 工作项      | 产出物                 | 优先级 |
| -------- | ------------------- | --- |
| 产品需求梳理   | 完整 PRD 和功能清单        | P0  |
| 角色技术验证   | 可捏脸、可调身材的角色 Demo    | P0  |
| 服装资产验证   | 上传图片到可穿戴贴图的 Demo    | P0  |
| 换装引擎验证   | 多部位、锚点、图层、遮挡 Demo   | P0  |
| 数据模型设计   | 用户、角色、衣物、资产、授权 ERD  | P0  |
| UI/UX 设计 | 首页、衣橱、换装、AI、社区原型    | P0  |
| AI 方案验证  | 识别、分割、生成、推荐技术方案     | P0  |
| 内容安全方案   | 图片审核、权限和版权规则        | P0  |
| 版本规划     | V0.1、V1.0、V1.5、V2.0 | P1  |
| 商业模式验证   | 会员、素材商城、创作者经济       | P2  |

**我的最终建议：先做一个完整的垂直体验 Demo。**

例如，用户上传一件真实的白色衬衫，系统识别出它属于上装、白色、棉质、春秋适用；生成虚拟服装素材；用户创建一个可爱的娃娃；把衬衫穿到娃娃身上；调整角色身材和衣服比例；再让 AI 从衣橱中挑选一条裙子、一双鞋和一套饰品，自动组合成完整穿搭，最后保存并分享。

只要这一整条链路体验足够好，我们就有了一个可以拿给领导看、也可以拿给研发评估的真正产品原型，而不是一堆概念页面。

# **第二部分：V1.0 研发规格**

## **十五、产品范围、角色权限与核心业务规则**

### **15.1 产品边界**

**[PRD 产品需求]**

V1.0 是一款可实际使用的数字衣橱与虚拟换装产品。其核心不是简单的图片管理，也不是传统换装游戏，而是让用户真实衣物进入虚拟角色穿搭流程。

首期核心闭环：

1. 用户注册并建立个人空间。
2. 创建一个或多个虚拟角色。
3. 上传真实衣物。
4. 系统完成文件检查、内容审核、质量检测和衣物识别。
5. 用户确认衣物分类、颜色、材质、季节、场景等属性。
6. 系统生成可供角色使用的 2D/2.5D 服装资产。
7. 用户将服装穿戴到角色身上。
8. 用户调整服装位置、尺寸、层级和角色身材。
9. 保存穿搭方案。
10. AI 根据衣橱和用户要求生成搭配。
11. 用户选择是否将作品分享给社区。

### **15.2 用户类型**

| 用户类型  | 权限范围              | 核心场景  |
| ----- | ----------------- | ----- |
| 游客    | 浏览公开内容、查看产品介绍     | 了解产品  |
| 普通用户  | 管理个人衣橱、创建角色、换装、保存 | 核心使用者 |
| 会员用户  | 使用会员额度内的高级生成和定制能力 | 高频用户  |
| 创作者   | 发布作品、管理授权、经营原创资产  | 内容生产者 |
| 社区审核员 | 审核投稿、处理举报和申诉      | 内容治理  |
| 资产审核员 | 审核服装素材、版权和商业授权    | 资产治理  |
| 运营管理员 | 管理活动、主题、推荐内容      | 运营    |
| 系统管理员 | 系统配置、账号权限、任务监控    | 系统运维  |

**[TECH 技术设计]**

所有业务数据必须具备明确的所有权字段：

- `owner_user_id`
- `tenant_id`（如未来支持机构或团队）
- `visibility`
- `created_by`
- `updated_by`

所有权校验必须在服务端执行。前端隐藏入口不构成权限控制。

### **15.3 账号与资产权限模型**

建议采用 RBAC 角色权限控制与资源所有权校验组合的方式。

- 用户只能访问自己拥有的私有衣物、角色、穿搭和任务。
- 公开作品可以被浏览，但作品中引用的私有资产不因此变为公开。
- 创作者只能管理自己创建或获得授权的资产。
- 审核员只能访问完成审核工作所必需的内容。
- 管理员的高风险操作必须记录审计日志。
- 系统任务只能通过受控服务账号执行，不允许客户端伪造任务所有者。

### **15.4 核心业务规则**

| 规则 ID  | 规则               | 处理要求        |
| ------ | ---------------- | ----------- |
| BR-001 | 新建衣物默认私有         | 不进入公开搜索     |
| BR-002 | 新建角色默认私有         | 不自动生成公开主页   |
| BR-003 | 公开作品不代表资产公开      | 作品和资产分别授权   |
| BR-004 | AI 生成结果必须关联原始任务  | 可追踪输入和模型版本  |
| BR-005 | 用户删除衣物采用软删除与清理流程 | 历史作品按快照规则处理 |
| BR-006 | 用户不能复用无授权资产      | 服务端校验授权有效性  |
| BR-007 | 服装资产必须声明适配部位     | 未配置不能进入正式穿戴 |
| BR-008 | 角色切换不能修改其他角色穿搭   | 角色穿搭数据独立    |
| BR-009 | AI 不得编造衣物 ID     | 只能引用有效资产    |
| BR-010 | 审核未通过不能发布        | 发布前必须检查状态   |
| BR-011 | 生成失败不能重复扣除无效额度   | 任务和计费幂等     |
| BR-012 | 用户撤销授权后停止新增复用    | 存量使用按协议处理   |

## **十六、产品信息架构与页面清单**

### **16.1 全局导航**

**[PRD 产品需求]**

底部主导航建议保留五个一级入口：

| 页面 ID         | 一级入口 | 页面职责           |
| ------------- | ---- | -------------- |
| HOME-001      | 首页   | 角色展示、今日穿搭、快捷入口 |
| WARD-001      | 衣橱   | 真实衣物和数字服装资产管理  |
| DRESS-001     | 换装   | 角色选择、换装、保存     |
| COMMUNITY-001 | 发现   | 公开作品、主题、创作者    |
| PROFILE-001   | 我的   | 账号、角色管理、会员、设置  |

AI 穿搭可以通过首页快捷入口、衣橱页操作入口和换装页工具入口进入，不一定需要独占一个底部 Tab。

### **16.2 页面完整清单**

| 页面 ID         | 页面名称    | 核心功能           | 主要依赖     |
| ------------- | ------- | -------------- | -------- |
| HOME-001      | 首页      | 今日推荐、角色展示、快捷入口 | 角色、天气、推荐 |
| WARD-001      | 衣橱首页    | 分类、筛选、搜索       | 衣物资产     |
| WARD-002      | 衣物详情    | 属性、图片、标签、授权    | 衣物资产     |
| WARD-003      | 上传入口    | 拍摄、相册选择        | 上传服务     |
| WARD-004      | 拍摄引导    | 拍摄规范、实时提示      | 相机       |
| WARD-005      | 上传处理进度  | 安全检查、识别、生成状态   | 任务系统     |
| WARD-006      | AI 识别确认 | 分类、颜色、材质、季节确认  | 视觉识别     |
| WARD-007      | 素材预览    | 抠图、贴图、锚点预览     | 资产生成     |
| WARD-008      | 衣物编辑    | 属性修改、删除、重试     | 衣物服务     |
| AVATAR-001    | 角色列表    | 创建、切换、删除       | 角色服务     |
| AVATAR-002    | 角色创建    | 模板、基础外观        | 角色模型     |
| AVATAR-003    | 捏脸编辑    | 五官、肤色、发型       | 角色参数     |
| AVATAR-004    | 身材编辑    | 身高比例、肩腰臀、四肢    | Morph 系统 |
| AVATAR-005    | 角色主页    | 角色展示、历史作品      | 社区       |
| DRESS-001     | 换装主界面   | 角色展示和服装选择      | 渲染引擎     |
| DRESS-002     | 服装分类面板  | 分类和筛选          | 服装资产     |
| DRESS-003     | 服装调整面板  | 缩放、旋转、位置、层级    | 渲染引擎     |
| DRESS-004     | 穿搭保存    | 命名、标签、封面       | 穿搭服务     |
| DRESS-005     | 穿搭历史    | 历史版本、恢复        | 穿搭服务     |
| AI-001        | AI 对话搭配 | 自然语言搭配         | AI 编排    |
| AI-002        | AI 方案结果 | 多套方案、试穿、保存     | 推荐引擎     |
| SHARE-001     | 分享设置    | 可见性和授权         | 授权服务     |
| SHARE-002     | 分享预览    | 发布前检查          | 内容审核     |
| COMMUNITY-001 | 推荐 Feed | 公开作品           | 社区服务     |
| COMMUNITY-002 | 作品详情    | 点赞、收藏、评论、复用    | 社区服务     |
| PROFILE-001   | 个人中心    | 资料、会员、设置       | 用户服务     |
| ADMIN-001     | 管理后台    | 用户、资产、审核、任务    | 管理服务     |

### **16.3 页面跳转关系**

\#chatgpt-mermaid-\_r_72o\_{font-family:-apple-system-body,ui-sans-serif,-apple-system,system-ui,"Segoe UI",Helvetica,"Apple Color Emoji",Arial,sans-serif,"Segoe UI Emoji","Segoe UI Symbol";font-size:16px;fill:rgb(13, 13, 13);}@keyframes edge-animation-frame{from{stroke-dashoffset:0;}}@keyframes dash{to{stroke-dashoffset:0;}}#chatgpt-mermaid-\_r_72o\_ .edge-animation-slow{stroke-dasharray:9,5!important;stroke-dashoffset:900;animation:dash 50s linear infinite;stroke-linecap:round;}#chatgpt-mermaid-\_r_72o\_ .edge-animation-fast{stroke-dasharray:9,5!important;stroke-dashoffset:900;animation:dash 20s linear infinite;stroke-linecap:round;}#chatgpt-mermaid-\_r_72o\_ .error-icon{fill:rgb(243, 243, 243);}#chatgpt-mermaid-\_r_72o\_ .error-text{fill:rgb(13, 13, 13);stroke:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_72o\_ .edge-thickness-normal{stroke-width:1px;}#chatgpt-mermaid-\_r_72o\_ .edge-thickness-thick{stroke-width:3.5px;}#chatgpt-mermaid-\_r_72o\_ .edge-pattern-solid{stroke-dasharray:0;}#chatgpt-mermaid-\_r_72o\_ .edge-thickness-invisible{stroke-width:0;fill:none;}#chatgpt-mermaid-\_r_72o\_ .edge-pattern-dashed{stroke-dasharray:3;}#chatgpt-mermaid-\_r_72o\_ .edge-pattern-dotted{stroke-dasharray:2;}#chatgpt-mermaid-\_r_72o\_ .marker{fill:rgb(143, 143, 143);stroke:rgb(143, 143, 143);}#chatgpt-mermaid-\_r_72o\_ .marker.cross{stroke:rgb(143, 143, 143);}#chatgpt-mermaid-\_r_72o\_ svg{font-family:-apple-system-body,ui-sans-serif,-apple-system,system-ui,"Segoe UI",Helvetica,"Apple Color Emoji",Arial,sans-serif,"Segoe UI Emoji","Segoe UI Symbol";font-size:16px;}#chatgpt-mermaid-\_r_72o\_ p{margin:0;}#chatgpt-mermaid-\_r_72o\_ .label{font-family:-apple-system-body,ui-sans-serif,-apple-system,system-ui,"Segoe UI",Helvetica,"Apple Color Emoji",Arial,sans-serif,"Segoe UI Emoji","Segoe UI Symbol";color:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_72o\_ .cluster-label text{fill:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_72o\_ .cluster-label span{color:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_72o\_ .cluster-label span p{background-color:transparent;}#chatgpt-mermaid-\_r_72o\_ .label text,#chatgpt-mermaid-\_r_72o\_ span{fill:rgb(13, 13, 13);color:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_72o\_ .node rect,#chatgpt-mermaid-\_r_72o\_ .node circle,#chatgpt-mermaid-\_r_72o\_ .node ellipse,#chatgpt-mermaid-\_r_72o\_ .node polygon,#chatgpt-mermaid-\_r_72o\_ .node path{fill:rgb(222, 234, 251);stroke:rgb(83, 154, 248);stroke-width:1px;}#chatgpt-mermaid-\_r_72o\_ .rough-node .label text,#chatgpt-mermaid-\_r_72o\_ .node .label text,#chatgpt-mermaid-\_r_72o\_ .image-shape .label,#chatgpt-mermaid-\_r_72o\_ .icon-shape .label{text-anchor:middle;}#chatgpt-mermaid-\_r_72o\_ .node .katex path{fill:#000;stroke:#000;stroke-width:1px;}#chatgpt-mermaid-\_r_72o\_ .rough-node .label,#chatgpt-mermaid-\_r_72o\_ .node .label,#chatgpt-mermaid-\_r_72o\_ .image-shape .label,#chatgpt-mermaid-\_r_72o\_ .icon-shape .label{text-align:center;}#chatgpt-mermaid-\_r_72o\_ .node.clickable{cursor:pointer;}#chatgpt-mermaid-\_r_72o\_ .root .anchor path{fill:rgb(143, 143, 143)!important;stroke-width:0;stroke:rgb(143, 143, 143);}#chatgpt-mermaid-\_r_72o\_ .arrowheadPath{fill:rgb(143, 143, 143);}#chatgpt-mermaid-\_r_72o\_ .edgePath .path{stroke:rgb(143, 143, 143);stroke-width:1px;}#chatgpt-mermaid-\_r_72o\_ .flowchart-link{stroke:rgb(143, 143, 143);fill:none;}#chatgpt-mermaid-\_r_72o\_ .edgeLabel{background-color:rgb(252, 252, 252);text-align:center;}#chatgpt-mermaid-\_r_72o\_ .edgeLabel p{background-color:rgb(252, 252, 252);}#chatgpt-mermaid-\_r_72o\_ .edgeLabel rect{opacity:0.5;background-color:rgb(252, 252, 252);fill:rgb(252, 252, 252);}#chatgpt-mermaid-\_r_72o\_ .labelBkg{background-color:rgba(252, 252, 252, 0.5);}#chatgpt-mermaid-\_r_72o\_ .cluster rect{fill:rgb(243, 243, 243);stroke:rgba(0, 0, 0, 0.1);stroke-width:1px;}#chatgpt-mermaid-\_r_72o\_ .cluster text{fill:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_72o\_ .cluster span{color:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_72o\_ div.mermaidTooltip{position:absolute;text-align:center;max-width:200px;padding:2px;font-family:-apple-system-body,ui-sans-serif,-apple-system,system-ui,"Segoe UI",Helvetica,"Apple Color Emoji",Arial,sans-serif,"Segoe UI Emoji","Segoe UI Symbol";font-size:12px;background:rgb(243, 243, 243);border:1px solid rgba(0, 0, 0, 0.1);border-radius:2px;pointer-events:none;z-index:100;}#chatgpt-mermaid-\_r_72o\_ .flowchartTitleText{text-anchor:middle;font-size:18px;fill:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_72o\_ rect.text{fill:none;stroke-width:0;}#chatgpt-mermaid-\_r_72o\_ .icon-shape,#chatgpt-mermaid-\_r_72o\_ .image-shape{background-color:rgb(252, 252, 252);text-align:center;}#chatgpt-mermaid-\_r_72o\_ .icon-shape p,#chatgpt-mermaid-\_r_72o\_ .image-shape p{background-color:rgb(252, 252, 252);padding:2px;}#chatgpt-mermaid-\_r_72o\_ .icon-shape .label rect,#chatgpt-mermaid-\_r_72o\_ .image-shape .label rect{opacity:0.5;background-color:rgb(252, 252, 252);fill:rgb(252, 252, 252);}#chatgpt-mermaid-\_r_72o\_ .label-icon{display:inline-block;height:1em;overflow:visible;vertical-align:-0.125em;}#chatgpt-mermaid-\_r_72o\_ .node .label-icon path{fill:currentColor;stroke:revert;stroke-width:revert;}#chatgpt-mermaid-\_r_72o\_ .node .neo-node{stroke:rgb(83, 154, 248);}#chatgpt-mermaid-\_r_72o\_ [data-look="neo"].node rect,#chatgpt-mermaid-\_r_72o\_ [data-look="neo"].cluster rect,#chatgpt-mermaid-\_r_72o\_ [data-look="neo"].node polygon{stroke:url(#chatgpt-mermaid-\_r_72o\_-gradient);filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-\_r_72o\_ [data-look="neo"].swimlane.cluster rect{filter:none;}#chatgpt-mermaid-\_r_72o\_ [data-look="neo"].node path{stroke:url(#chatgpt-mermaid-\_r_72o\_-gradient);stroke-width:1px;}#chatgpt-mermaid-\_r_72o\_ [data-look="neo"].node .outer-path{filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-\_r_72o\_ [data-look="neo"].node .neo-line path{stroke:rgb(83, 154, 248);filter:none;}#chatgpt-mermaid-\_r_72o\_ [data-look="neo"].node circle{stroke:url(#chatgpt-mermaid-\_r_72o\_-gradient);filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-\_r_72o\_ [data-look="neo"].node circle .state-start{fill:#000000;}#chatgpt-mermaid-\_r_72o\_ [data-look="neo"].icon-shape .icon{fill:url(#chatgpt-mermaid-\_r_72o\_-gradient);filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-\_r_72o\_ [data-look="neo"].icon-shape .icon-neo path{stroke:url(#chatgpt-mermaid-\_r_72o\_-gradient);filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-\_r_72o\_ .node text{font-size:14px;font-weight:600;letter-spacing:normal;fill:rgb(0, 79, 153);}#chatgpt-mermaid-\_r_72o\_ .edgeLabels text{font-size:13px;font-weight:600;letter-spacing:-0.08px;fill:rgb(0, 79, 153);}#chatgpt-mermaid-\_r_72o\_ .node tspan[font-weight="normal"],#chatgpt-mermaid-\_r_72o\_ .edgeLabels tspan[font-weight="normal"]{font-weight:600;}#chatgpt-mermaid-\_r_72o\_ .edgeLabel .label rect{opacity:1;rx:13px;ry:13px;fill:rgb(245, 250, 255);stroke:rgb(206, 219, 229);stroke-width:1px;}#chatgpt-mermaid-\_r_72o\_ .node rect,#chatgpt-mermaid-\_r_72o\_ .node circle,#chatgpt-mermaid-\_r_72o\_ .node ellipse,#chatgpt-mermaid-\_r_72o\_ .node polygon,#chatgpt-mermaid-\_r_72o\_ .node path{fill:rgb(229, 243, 255);stroke:rgba(0, 0, 0, 0.1);stroke-width:1px;}#chatgpt-mermaid-\_r_72o\_ .node rect{rx:16px;ry:16px;}#chatgpt-mermaid-\_r_72o\_ .mermaid-decision .label-container{fill:rgb(245, 250, 255);stroke:rgb(206, 219, 229);stroke-dasharray:2,2;}#chatgpt-mermaid-\_r_72o\_ .edgePaths .flowchart-link{stroke:rgb(143, 143, 143);stroke-width:1px;stroke-linecap:round;stroke-linejoin:round;}#chatgpt-mermaid-\_r_72o\_ .marker{fill:rgb(143, 143, 143);stroke:rgb(143, 143, 143);}#chatgpt-mermaid-\_r_72o\_ :root{--mermaid-font-family:-apple-system-body,ui-sans-serif,-apple-system,system-ui,"Segoe UI",Helvetica,"Apple Color Emoji",Arial,sans-serif,"Segoe UI Emoji","Segoe UI Symbol";}HOME-001 首页WARD-001 衣橱AVATAR-001 角色列表DRESS-001 换装AI-001 AI 搭配COMMUNITY-001 发现PROFILE-001 我的

### **16.4 HOME-001 首页交互规格**

页面区域：

1. 顶部角色卡片：当前角色、角色切换、进入角色主页。
2. 今日穿搭：推荐搭配、天气信息、推荐理由。
3. 快捷操作：添加衣物、AI 搭配、进入换装。
4. 我的角色：展示多个角色的缩略卡片。
5. 灵感 Feed：公开穿搭内容。
6. 每日主题：活动入口。

交互：

| 控件    | 操作      | 结果         |
| ----- | ------- | ---------- |
| 当前角色卡 | 点击      | 进入角色详情     |
| 角色切换  | 左右滑动/点击 | 切换当前角色     |
| 今日穿搭  | 点击      | 进入搭配详情     |
| 添加衣物  | 点击      | 进入上传入口     |
| AI 搭配 | 点击      | 进入 AI 需求输入 |
| 换装    | 点击      | 打开当前角色换装   |
| 灵感作品  | 点击      | 进入作品详情     |

异常：

- 无角色：展示创建角色引导。
- 无衣物：展示添加衣物引导，不展示伪造的个人推荐。
- 天气服务失败：隐藏天气依赖信息，仍允许按季节和场景推荐。
- 推荐服务失败：展示历史穿搭或静态主题内容。
- Feed 加载失败：允许重试，不影响个人衣橱功能。

**[AC 验收标准]**

- 首页必须在无角色、无衣物、无网络、推荐服务失败情况下可正常展示。
- 角色切换后，首页所有角色相关内容同步更新。
- 不得把其他用户的私有衣物展示在推荐区域。
- 点击快捷入口必须进入对应业务流程，不得出现无响应控件。

### **16.5 WARD-003 上传入口交互规格**

上传方式：

- 拍摄新照片。
- 从相册选择。
- 后续可支持多图批量导入，但首期建议一次处理一件衣物。

交互步骤：

1. 用户选择上传方式。
2. 用户选择衣物类型（可跳过，由 AI 识别）。
3. 拍摄或选择图片。
4. 前端检查格式、尺寸并展示预览。
5. 用户确认提交。
6. 服务端创建上传任务。
7. 页面进入处理进度。
8. 完成后进入识别确认页。

必须支持：

- 取消上传。
- 上传失败重试。
- 上传中断恢复。
- 重复文件提示。
- 删除待处理任务。
- 查看处理失败原因。

### **16.6 WARD-006 AI 识别确认交互规格**

页面展示：

- 原始衣物照片。
- 去背景预览。
- 一级分类、二级分类。
- 主色、辅助色。
- 材质推测。
- 季节。
- 风格。
- 适用场景。
- 身体部位。
- AI 识别置信度提示。

用户操作：

- 修改分类。
- 修改颜色。
- 添加标签。
- 修改季节。
- 补充尺码。
- 标记是否为套装。
- 选择是否生成虚拟服装素材。
- 提交确认。

关键规则：

AI 识别置信度低时，不得静默自动确认。应提示用户检查关键字段。

**[AC 验收标准]**

- 用户修改后保存的数据必须覆盖 AI 初始建议，但保留 AI 识别历史。
- 用户可以跳过非必要属性。
- 分类修改后，相关身体部位和锚点配置应重新计算。
- 识别失败时仍允许用户手动录入衣物。
- 用户未确认之前，不得将资产标记为正式可穿戴。

### **16.7 AVATAR-004 身材编辑交互规格**

可调整参数：

- 身高比例。
- 头身比。
- 肩宽。
- 胸部轮廓。
- 腰部轮廓。
- 臀部轮廓。
- 腿长。
- 大腿围。
- 小腿围。
- 手臂粗细。

交互要求：

- 提供快捷模板。
- 提供滑块微调。
- 提供恢复默认。
- 提供实时预览。
- 提供保存和取消。
- 保存前展示穿戴适配变化。
- 角色身材配置不等同于真实身体数据。

**[TECH 技术设计]**

身材参数采用归一化数值，例如 0—1。前端滑块值必须由后端保存的参数范围校验，不接受任意浮点值。

角色身材配置版本应记录：

- `body_profile_id`
- `avatar_id`
- `body_template_id`
- `morph_parameters`
- `version`
- `created_at`
- `updated_at`

## **十七、核心业务流程与状态机**

### **17.1 端到端衣物数字化流程**

\#chatgpt-mermaid-\_r_72v\_{font-family:-apple-system-body,ui-sans-serif,-apple-system,system-ui,"Segoe UI",Helvetica,"Apple Color Emoji",Arial,sans-serif,"Segoe UI Emoji","Segoe UI Symbol";font-size:16px;fill:rgb(13, 13, 13);}@keyframes edge-animation-frame{from{stroke-dashoffset:0;}}@keyframes dash{to{stroke-dashoffset:0;}}#chatgpt-mermaid-\_r_72v\_ .edge-animation-slow{stroke-dasharray:9,5!important;stroke-dashoffset:900;animation:dash 50s linear infinite;stroke-linecap:round;}#chatgpt-mermaid-\_r_72v\_ .edge-animation-fast{stroke-dasharray:9,5!important;stroke-dashoffset:900;animation:dash 20s linear infinite;stroke-linecap:round;}#chatgpt-mermaid-\_r_72v\_ .error-icon{fill:rgb(243, 243, 243);}#chatgpt-mermaid-\_r_72v\_ .error-text{fill:rgb(13, 13, 13);stroke:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_72v\_ .edge-thickness-normal{stroke-width:1px;}#chatgpt-mermaid-\_r_72v\_ .edge-thickness-thick{stroke-width:3.5px;}#chatgpt-mermaid-\_r_72v\_ .edge-pattern-solid{stroke-dasharray:0;}#chatgpt-mermaid-\_r_72v\_ .edge-thickness-invisible{stroke-width:0;fill:none;}#chatgpt-mermaid-\_r_72v\_ .edge-pattern-dashed{stroke-dasharray:3;}#chatgpt-mermaid-\_r_72v\_ .edge-pattern-dotted{stroke-dasharray:2;}#chatgpt-mermaid-\_r_72v\_ .marker{fill:rgb(143, 143, 143);stroke:rgb(143, 143, 143);}#chatgpt-mermaid-\_r_72v\_ .marker.cross{stroke:rgb(143, 143, 143);}#chatgpt-mermaid-\_r_72v\_ svg{font-family:-apple-system-body,ui-sans-serif,-apple-system,system-ui,"Segoe UI",Helvetica,"Apple Color Emoji",Arial,sans-serif,"Segoe UI Emoji","Segoe UI Symbol";font-size:16px;}#chatgpt-mermaid-\_r_72v\_ p{margin:0;}#chatgpt-mermaid-\_r_72v\_ .label{font-family:-apple-system-body,ui-sans-serif,-apple-system,system-ui,"Segoe UI",Helvetica,"Apple Color Emoji",Arial,sans-serif,"Segoe UI Emoji","Segoe UI Symbol";color:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_72v\_ .cluster-label text{fill:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_72v\_ .cluster-label span{color:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_72v\_ .cluster-label span p{background-color:transparent;}#chatgpt-mermaid-\_r_72v\_ .label text,#chatgpt-mermaid-\_r_72v\_ span{fill:rgb(13, 13, 13);color:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_72v\_ .node rect,#chatgpt-mermaid-\_r_72v\_ .node circle,#chatgpt-mermaid-\_r_72v\_ .node ellipse,#chatgpt-mermaid-\_r_72v\_ .node polygon,#chatgpt-mermaid-\_r_72v\_ .node path{fill:rgb(222, 234, 251);stroke:rgb(83, 154, 248);stroke-width:1px;}#chatgpt-mermaid-\_r_72v\_ .rough-node .label text,#chatgpt-mermaid-\_r_72v\_ .node .label text,#chatgpt-mermaid-\_r_72v\_ .image-shape .label,#chatgpt-mermaid-\_r_72v\_ .icon-shape .label{text-anchor:middle;}#chatgpt-mermaid-\_r_72v\_ .node .katex path{fill:#000;stroke:#000;stroke-width:1px;}#chatgpt-mermaid-\_r_72v\_ .rough-node .label,#chatgpt-mermaid-\_r_72v\_ .node .label,#chatgpt-mermaid-\_r_72v\_ .image-shape .label,#chatgpt-mermaid-\_r_72v\_ .icon-shape .label{text-align:center;}#chatgpt-mermaid-\_r_72v\_ .node.clickable{cursor:pointer;}#chatgpt-mermaid-\_r_72v\_ .root .anchor path{fill:rgb(143, 143, 143)!important;stroke-width:0;stroke:rgb(143, 143, 143);}#chatgpt-mermaid-\_r_72v\_ .arrowheadPath{fill:rgb(143, 143, 143);}#chatgpt-mermaid-\_r_72v\_ .edgePath .path{stroke:rgb(143, 143, 143);stroke-width:1px;}#chatgpt-mermaid-\_r_72v\_ .flowchart-link{stroke:rgb(143, 143, 143);fill:none;}#chatgpt-mermaid-\_r_72v\_ .edgeLabel{background-color:rgb(252, 252, 252);text-align:center;}#chatgpt-mermaid-\_r_72v\_ .edgeLabel p{background-color:rgb(252, 252, 252);}#chatgpt-mermaid-\_r_72v\_ .edgeLabel rect{opacity:0.5;background-color:rgb(252, 252, 252);fill:rgb(252, 252, 252);}#chatgpt-mermaid-\_r_72v\_ .labelBkg{background-color:rgba(252, 252, 252, 0.5);}#chatgpt-mermaid-\_r_72v\_ .cluster rect{fill:rgb(243, 243, 243);stroke:rgba(0, 0, 0, 0.1);stroke-width:1px;}#chatgpt-mermaid-\_r_72v\_ .cluster text{fill:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_72v\_ .cluster span{color:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_72v\_ div.mermaidTooltip{position:absolute;text-align:center;max-width:200px;padding:2px;font-family:-apple-system-body,ui-sans-serif,-apple-system,system-ui,"Segoe UI",Helvetica,"Apple Color Emoji",Arial,sans-serif,"Segoe UI Emoji","Segoe UI Symbol";font-size:12px;background:rgb(243, 243, 243);border:1px solid rgba(0, 0, 0, 0.1);border-radius:2px;pointer-events:none;z-index:100;}#chatgpt-mermaid-\_r_72v\_ .flowchartTitleText{text-anchor:middle;font-size:18px;fill:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_72v\_ rect.text{fill:none;stroke-width:0;}#chatgpt-mermaid-\_r_72v\_ .icon-shape,#chatgpt-mermaid-\_r_72v\_ .image-shape{background-color:rgb(252, 252, 252);text-align:center;}#chatgpt-mermaid-\_r_72v\_ .icon-shape p,#chatgpt-mermaid-\_r_72v\_ .image-shape p{background-color:rgb(252, 252, 252);padding:2px;}#chatgpt-mermaid-\_r_72v\_ .icon-shape .label rect,#chatgpt-mermaid-\_r_72v\_ .image-shape .label rect{opacity:0.5;background-color:rgb(252, 252, 252);fill:rgb(252, 252, 252);}#chatgpt-mermaid-\_r_72v\_ .label-icon{display:inline-block;height:1em;overflow:visible;vertical-align:-0.125em;}#chatgpt-mermaid-\_r_72v\_ .node .label-icon path{fill:currentColor;stroke:revert;stroke-width:revert;}#chatgpt-mermaid-\_r_72v\_ .node .neo-node{stroke:rgb(83, 154, 248);}#chatgpt-mermaid-\_r_72v\_ [data-look="neo"].node rect,#chatgpt-mermaid-\_r_72v\_ [data-look="neo"].cluster rect,#chatgpt-mermaid-\_r_72v\_ [data-look="neo"].node polygon{stroke:url(#chatgpt-mermaid-\_r_72v\_-gradient);filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-\_r_72v\_ [data-look="neo"].swimlane.cluster rect{filter:none;}#chatgpt-mermaid-\_r_72v\_ [data-look="neo"].node path{stroke:url(#chatgpt-mermaid-\_r_72v\_-gradient);stroke-width:1px;}#chatgpt-mermaid-\_r_72v\_ [data-look="neo"].node .outer-path{filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-\_r_72v\_ [data-look="neo"].node .neo-line path{stroke:rgb(83, 154, 248);filter:none;}#chatgpt-mermaid-\_r_72v\_ [data-look="neo"].node circle{stroke:url(#chatgpt-mermaid-\_r_72v\_-gradient);filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-\_r_72v\_ [data-look="neo"].node circle .state-start{fill:#000000;}#chatgpt-mermaid-\_r_72v\_ [data-look="neo"].icon-shape .icon{fill:url(#chatgpt-mermaid-\_r_72v\_-gradient);filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-\_r_72v\_ [data-look="neo"].icon-shape .icon-neo path{stroke:url(#chatgpt-mermaid-\_r_72v\_-gradient);filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-\_r_72v\_ .node text{font-size:14px;font-weight:600;letter-spacing:normal;fill:rgb(0, 79, 153);}#chatgpt-mermaid-\_r_72v\_ .edgeLabels text{font-size:13px;font-weight:600;letter-spacing:-0.08px;fill:rgb(0, 79, 153);}#chatgpt-mermaid-\_r_72v\_ .node tspan[font-weight="normal"],#chatgpt-mermaid-\_r_72v\_ .edgeLabels tspan[font-weight="normal"]{font-weight:600;}#chatgpt-mermaid-\_r_72v\_ .edgeLabel .label rect{opacity:1;rx:13px;ry:13px;fill:rgb(245, 250, 255);stroke:rgb(206, 219, 229);stroke-width:1px;}#chatgpt-mermaid-\_r_72v\_ .node rect,#chatgpt-mermaid-\_r_72v\_ .node circle,#chatgpt-mermaid-\_r_72v\_ .node ellipse,#chatgpt-mermaid-\_r_72v\_ .node polygon,#chatgpt-mermaid-\_r_72v\_ .node path{fill:rgb(229, 243, 255);stroke:rgba(0, 0, 0, 0.1);stroke-width:1px;}#chatgpt-mermaid-\_r_72v\_ .node rect{rx:16px;ry:16px;}#chatgpt-mermaid-\_r_72v\_ .mermaid-decision .label-container{fill:rgb(245, 250, 255);stroke:rgb(206, 219, 229);stroke-dasharray:2,2;}#chatgpt-mermaid-\_r_72v\_ .edgePaths .flowchart-link{stroke:rgb(143, 143, 143);stroke-width:1px;stroke-linecap:round;stroke-linejoin:round;}#chatgpt-mermaid-\_r_72v\_ .marker{fill:rgb(143, 143, 143);stroke:rgb(143, 143, 143);}#chatgpt-mermaid-\_r_72v\_ :root{--mermaid-font-family:-apple-system-body,ui-sans-serif,-apple-system,system-ui,"Segoe UI",Helvetica,"Apple Color Emoji",Arial,sans-serif,"Segoe UI Emoji","Segoe UI Symbol";}选择或拍摄衣物创建上传任务文件安全校验拒绝上传并提示内容安全审核审核拒绝人工复核图像质量检测提示补拍或人工处理AI 衣物识别用户确认属性主体分割与素材生成锚点预测和适配检查资产质量验收正式可穿戴资产人工修正或重新生成失败通过拒绝待复核通过通过不合格合格通过失败

### **17.2 上传任务状态机**

\#chatgpt-mermaid-\_r_736\_{font-family:-apple-system-body,ui-sans-serif,-apple-system,system-ui,"Segoe UI",Helvetica,"Apple Color Emoji",Arial,sans-serif,"Segoe UI Emoji","Segoe UI Symbol";font-size:16px;fill:rgb(13, 13, 13);}@keyframes edge-animation-frame{from{stroke-dashoffset:0;}}@keyframes dash{to{stroke-dashoffset:0;}}#chatgpt-mermaid-\_r_736\_ .edge-animation-slow{stroke-dasharray:9,5!important;stroke-dashoffset:900;animation:dash 50s linear infinite;stroke-linecap:round;}#chatgpt-mermaid-\_r_736\_ .edge-animation-fast{stroke-dasharray:9,5!important;stroke-dashoffset:900;animation:dash 20s linear infinite;stroke-linecap:round;}#chatgpt-mermaid-\_r_736\_ .error-icon{fill:rgb(243, 243, 243);}#chatgpt-mermaid-\_r_736\_ .error-text{fill:rgb(13, 13, 13);stroke:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_736\_ .edge-thickness-normal{stroke-width:1px;}#chatgpt-mermaid-\_r_736\_ .edge-thickness-thick{stroke-width:3.5px;}#chatgpt-mermaid-\_r_736\_ .edge-pattern-solid{stroke-dasharray:0;}#chatgpt-mermaid-\_r_736\_ .edge-thickness-invisible{stroke-width:0;fill:none;}#chatgpt-mermaid-\_r_736\_ .edge-pattern-dashed{stroke-dasharray:3;}#chatgpt-mermaid-\_r_736\_ .edge-pattern-dotted{stroke-dasharray:2;}#chatgpt-mermaid-\_r_736\_ .marker{fill:rgb(143, 143, 143);stroke:rgb(143, 143, 143);}#chatgpt-mermaid-\_r_736\_ .marker.cross{stroke:rgb(143, 143, 143);}#chatgpt-mermaid-\_r_736\_ svg{font-family:-apple-system-body,ui-sans-serif,-apple-system,system-ui,"Segoe UI",Helvetica,"Apple Color Emoji",Arial,sans-serif,"Segoe UI Emoji","Segoe UI Symbol";font-size:16px;}#chatgpt-mermaid-\_r_736\_ p{margin:0;}#chatgpt-mermaid-\_r_736\_ defs [id$="-barbEnd"]{fill:rgb(143, 143, 143);stroke:rgb(143, 143, 143);}#chatgpt-mermaid-\_r_736\_ g.stateGroup text{fill:rgb(83, 154, 248);stroke:none;font-size:10px;}#chatgpt-mermaid-\_r_736\_ g.stateGroup text{fill:rgb(13, 13, 13);stroke:none;font-size:10px;}#chatgpt-mermaid-\_r_736\_ g.stateGroup .state-title{font-weight:bolder;fill:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_736\_ g.stateGroup rect{fill:rgb(222, 234, 251);stroke:rgb(83, 154, 248);}#chatgpt-mermaid-\_r_736\_ g.stateGroup line{stroke:rgb(143, 143, 143);stroke-width:1;}#chatgpt-mermaid-\_r_736\_ .transition{stroke:rgb(143, 143, 143);stroke-width:1;fill:none;}#chatgpt-mermaid-\_r_736\_ .stateGroup .composit{fill:transparent;border-bottom:1px;}#chatgpt-mermaid-\_r_736\_ .stateGroup .alt-composit{fill:#e0e0e0;border-bottom:1px;}#chatgpt-mermaid-\_r_736\_ .state-note{stroke:rgb(107, 198, 127);fill:rgb(243, 243, 243);}#chatgpt-mermaid-\_r_736\_ .state-note text{fill:rgb(13, 13, 13);stroke:none;font-size:10px;}#chatgpt-mermaid-\_r_736\_ .stateLabel .box{stroke:none;stroke-width:0;fill:rgb(222, 234, 251);opacity:0.5;}#chatgpt-mermaid-\_r_736\_ .edgeLabel .label rect{fill:rgb(222, 234, 251);opacity:0.5;}#chatgpt-mermaid-\_r_736\_ .edgeLabel{background-color:rgb(252, 252, 252);text-align:center;}#chatgpt-mermaid-\_r_736\_ .edgeLabel p{background-color:rgb(252, 252, 252);}#chatgpt-mermaid-\_r_736\_ .edgeLabel rect{opacity:0.5;background-color:rgb(252, 252, 252);fill:rgb(252, 252, 252);}#chatgpt-mermaid-\_r_736\_ .edgeLabel .label text{fill:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_736\_ .label div .edgeLabel{color:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_736\_ .stateLabel text{fill:rgb(13, 13, 13);font-size:10px;font-weight:bold;}#chatgpt-mermaid-\_r_736\_ .node circle.state-start{fill:rgb(143, 143, 143);stroke:rgb(143, 143, 143);}#chatgpt-mermaid-\_r_736\_ .node .fork-join{fill:rgb(143, 143, 143);stroke:rgb(143, 143, 143);}#chatgpt-mermaid-\_r_736\_ .node circle.state-end{fill:rgb(83, 154, 248);stroke:transparent;stroke-width:1.5;}#chatgpt-mermaid-\_r_736\_ .end-state-inner{fill:transparent;stroke-width:1.5;}#chatgpt-mermaid-\_r_736\_ .node rect{fill:rgb(222, 234, 251);stroke:rgb(83, 154, 248);stroke-width:1px;}#chatgpt-mermaid-\_r_736\_ .node polygon{fill:rgb(222, 234, 251);stroke:rgb(83, 154, 248);stroke-width:1px;}#chatgpt-mermaid-\_r_736\_ [id$="-barbEnd"]{fill:rgb(143, 143, 143);}#chatgpt-mermaid-\_r_736\_ .statediagram-cluster rect{fill:rgb(222, 234, 251);stroke:rgb(83, 154, 248);stroke-width:1px;}#chatgpt-mermaid-\_r_736\_ .cluster-label,#chatgpt-mermaid-\_r_736\_ .nodeLabel{color:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_736\_ .statediagram-cluster rect.outer{rx:5px;ry:5px;}#chatgpt-mermaid-\_r_736\_ .statediagram-state .divider{stroke:rgb(83, 154, 248);}#chatgpt-mermaid-\_r_736\_ .statediagram-state .title-state{rx:5px;ry:5px;}#chatgpt-mermaid-\_r_736\_ .statediagram-cluster.statediagram-cluster .inner{fill:transparent;}#chatgpt-mermaid-\_r_736\_ .statediagram-cluster.statediagram-cluster-alt .inner{fill:rgb(243, 243, 243);}#chatgpt-mermaid-\_r_736\_ .statediagram-cluster .inner{rx:0;ry:0;}#chatgpt-mermaid-\_r_736\_ .statediagram-state rect.basic{rx:5px;ry:5px;}#chatgpt-mermaid-\_r_736\_ .statediagram-state rect.divider{stroke-dasharray:10,10;fill:rgb(243, 243, 243);}#chatgpt-mermaid-\_r_736\_ .note-edge{stroke-dasharray:5;}#chatgpt-mermaid-\_r_736\_ .statediagram-note rect{fill:rgb(243, 243, 243);stroke:rgb(107, 198, 127);stroke-width:1px;rx:0;ry:0;}#chatgpt-mermaid-\_r_736\_ .statediagram-note rect{fill:rgb(243, 243, 243);stroke:rgb(107, 198, 127);stroke-width:1px;rx:0;ry:0;}#chatgpt-mermaid-\_r_736\_ .statediagram-note text{fill:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_736\_ .statediagram-note .nodeLabel{color:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_736\_ .statediagram .edgeLabel{color:red;}#chatgpt-mermaid-\_r_736\_ [id$="-dependencyStart"],#chatgpt-mermaid-\_r_736\_ [id$="-dependencyEnd"]{fill:rgb(143, 143, 143);stroke:rgb(143, 143, 143);stroke-width:1;}#chatgpt-mermaid-\_r_736\_ .statediagramTitleText{text-anchor:middle;font-size:18px;fill:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_736\_ [data-look="neo"].statediagram-cluster rect{fill:rgb(222, 234, 251);stroke:url(#chatgpt-mermaid-\_r_736\_-gradient);stroke-width:1;}#chatgpt-mermaid-\_r_736\_ [data-look="neo"].statediagram-cluster rect.outer{rx:5px;ry:5px;filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-\_r_736\_ .node .neo-node{stroke:rgb(83, 154, 248);}#chatgpt-mermaid-\_r_736\_ [data-look="neo"].node rect,#chatgpt-mermaid-\_r_736\_ [data-look="neo"].cluster rect,#chatgpt-mermaid-\_r_736\_ [data-look="neo"].node polygon{stroke:url(#chatgpt-mermaid-\_r_736\_-gradient);filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-\_r_736\_ [data-look="neo"].swimlane.cluster rect{filter:none;}#chatgpt-mermaid-\_r_736\_ [data-look="neo"].node path{stroke:url(#chatgpt-mermaid-\_r_736\_-gradient);stroke-width:1px;}#chatgpt-mermaid-\_r_736\_ [data-look="neo"].node .outer-path{filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-\_r_736\_ [data-look="neo"].node .neo-line path{stroke:rgb(83, 154, 248);filter:none;}#chatgpt-mermaid-\_r_736\_ [data-look="neo"].node circle{stroke:url(#chatgpt-mermaid-\_r_736\_-gradient);filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-\_r_736\_ [data-look="neo"].node circle .state-start{fill:#000000;}#chatgpt-mermaid-\_r_736\_ [data-look="neo"].icon-shape .icon{fill:url(#chatgpt-mermaid-\_r_736\_-gradient);filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-\_r_736\_ [data-look="neo"].icon-shape .icon-neo path{stroke:url(#chatgpt-mermaid-\_r_736\_-gradient);filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-\_r_736\_ :root{--mermaid-font-family:-apple-system-body,ui-sans-serif,-apple-system,system-ui,"Segoe UI",Helvetica,"Apple Color Emoji",Arial,sans-serif,"Segoe UI Emoji","Segoe UI Symbol";}CREATEDUPLOADINGUPLOADEDFAILEDFILE_VALIDATINGFILE_REJECTEDMODERATION_PENDINGMODERATINGMODERATION_PASSEDMODERATION_REJECTEDREVIEW_REQUIREDQUALITY_CHECKINGQUALITY_FAILEDRECOGNIZINGUSER_CONFIRMINGGENERATINGGENERATION_FAILEDASSET_REVIEWREADYDELETED

### **17.3 状态定义与转换限制**

| 状态                  | 含义      | 用户可见 | 允许重试       |
| ------------------- | ------- | ---- | ---------- |
| CREATED             | 任务已创建   | 是    | 否          |
| UPLOADING           | 文件上传中   | 是    | 是          |
| UPLOADED            | 上传完成    | 是    | 否          |
| FILE_VALIDATING     | 文件安全检查  | 是    | 系统自动       |
| FILE_REJECTED       | 文件不符合要求 | 是    | 重新上传       |
| MODERATION_PENDING  | 等待内容审核  | 是    | 系统自动       |
| MODERATING          | 审核中     | 是    | 系统自动       |
| MODERATION_PASSED   | 审核通过    | 是    | 否          |
| MODERATION_REJECTED | 内容审核拒绝  | 是    | 不允许同文件直接重试 |
| REVIEW_REQUIRED     | 需要人工复核  | 是    | 人工处理       |
| QUALITY_CHECKING    | 图片质量检测  | 是    | 系统自动       |
| QUALITY_FAILED      | 图片质量不合格 | 是    | 重新上传       |
| RECOGNIZING         | AI 识别中  | 是    | 是          |
| USER_CONFIRMING     | 等待用户确认  | 是    | 用户操作       |
| GENERATING          | 素材生成中   | 是    | 是          |
| GENERATION_FAILED   | 生成失败    | 是    | 是          |
| ASSET_REVIEW        | 资产检查    | 是    | 是          |
| READY               | 正式可用    | 是    | 否          |
| DELETED             | 已删除     | 是    | 按恢复策略      |

### **17.4 AI 服装生成工作流**

将 AI 生成拆成多个独立任务，不能设计为一个无法恢复的长请求。

每个阶段必须保存：

- 输入资源 ID。
- 输出资源 ID。
- 任务 ID。
- 算法/模型版本。
- 参数版本。
- 执行耗时。
- 错误码。
- 重试次数。
- 结果质量评分。
- 人工修正记录。

### **17.5 AI 搭配工作流关键约束**

- LLM 只能从服务端提供的候选资产中选择。
- 不能让模型自由生成数据库 ID。
- 模型返回的资产 ID 必须二次校验。
- 推荐结果必须满足服装部位、层级和授权规则。
- 无合适衣物时明确告知用户，不得伪造库存。
- 用户拒绝某套方案时记录拒绝原因，但不得未经同意将其推断为长期偏好。

## **十八、数据库设计与 ERD**

### **18.1 数据库设计原则**

**[TECH 技术设计]**

建议关系型数据库作为业务主数据存储，图片、模型、贴图和渲染结果存储在对象存储中。

数据库保存资源引用，不直接保存大尺寸图片二进制内容。

核心实体：

1. 用户。
2. 用户偏好。
3. 角色。
4. 身材配置。
5. 衣物。
6. 衣物图片。
7. 服装数字资产。
8. 资产部件。
9. 穿戴锚点。
10. 角色穿搭。
11. 穿搭部件。
12. AI 任务。
13. 分享作品。
14. 资产授权。
15. 社区互动。
16. 审核事件。
17. 会员与额度。
18. 操作审计。

### **18.2 ERD**

\#chatgpt-mermaid-\_r_73d\_{font-family:-apple-system-body,ui-sans-serif,-apple-system,system-ui,"Segoe UI",Helvetica,"Apple Color Emoji",Arial,sans-serif,"Segoe UI Emoji","Segoe UI Symbol";font-size:16px;fill:rgb(13, 13, 13);}@keyframes edge-animation-frame{from{stroke-dashoffset:0;}}@keyframes dash{to{stroke-dashoffset:0;}}#chatgpt-mermaid-\_r_73d\_ .edge-animation-slow{stroke-dasharray:9,5!important;stroke-dashoffset:900;animation:dash 50s linear infinite;stroke-linecap:round;}#chatgpt-mermaid-\_r_73d\_ .edge-animation-fast{stroke-dasharray:9,5!important;stroke-dashoffset:900;animation:dash 20s linear infinite;stroke-linecap:round;}#chatgpt-mermaid-\_r_73d\_ .error-icon{fill:rgb(243, 243, 243);}#chatgpt-mermaid-\_r_73d\_ .error-text{fill:rgb(13, 13, 13);stroke:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_73d\_ .edge-thickness-normal{stroke-width:1px;}#chatgpt-mermaid-\_r_73d\_ .edge-thickness-thick{stroke-width:3.5px;}#chatgpt-mermaid-\_r_73d\_ .edge-pattern-solid{stroke-dasharray:0;}#chatgpt-mermaid-\_r_73d\_ .edge-thickness-invisible{stroke-width:0;fill:none;}#chatgpt-mermaid-\_r_73d\_ .edge-pattern-dashed{stroke-dasharray:3;}#chatgpt-mermaid-\_r_73d\_ .edge-pattern-dotted{stroke-dasharray:2;}#chatgpt-mermaid-\_r_73d\_ .marker{fill:rgb(143, 143, 143);stroke:rgb(143, 143, 143);}#chatgpt-mermaid-\_r_73d\_ .marker.cross{stroke:rgb(143, 143, 143);}#chatgpt-mermaid-\_r_73d\_ svg{font-family:-apple-system-body,ui-sans-serif,-apple-system,system-ui,"Segoe UI",Helvetica,"Apple Color Emoji",Arial,sans-serif,"Segoe UI Emoji","Segoe UI Symbol";font-size:16px;}#chatgpt-mermaid-\_r_73d\_ p{margin:0;}#chatgpt-mermaid-\_r_73d\_ .entityBox{fill:rgb(222, 234, 251);stroke:rgb(83, 154, 248);}#chatgpt-mermaid-\_r_73d\_ .relationshipLabelBox{fill:rgb(243, 243, 243);opacity:0.7;background-color:rgb(243, 243, 243);}#chatgpt-mermaid-\_r_73d\_ .relationshipLabelBox rect{opacity:0.5;}#chatgpt-mermaid-\_r_73d\_ .labelBkg{background-color:rgba(243, 243, 243, 0.5);}#chatgpt-mermaid-\_r_73d\_ .edgeLabel{background-color:rgb(252, 252, 252);}#chatgpt-mermaid-\_r_73d\_ .edgeLabel .label rect{fill:rgb(252, 252, 252);}#chatgpt-mermaid-\_r_73d\_ .edgeLabel .label text{fill:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_73d\_ .edgeLabel .label{fill:rgb(83, 154, 248);font-size:14px;}#chatgpt-mermaid-\_r_73d\_ .label{font-family:-apple-system-body,ui-sans-serif,-apple-system,system-ui,"Segoe UI",Helvetica,"Apple Color Emoji",Arial,sans-serif,"Segoe UI Emoji","Segoe UI Symbol";color:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_73d\_ .edge-pattern-dashed{stroke-dasharray:8,8;}#chatgpt-mermaid-\_r_73d\_ .node rect,#chatgpt-mermaid-\_r_73d\_ .node circle,#chatgpt-mermaid-\_r_73d\_ .node ellipse,#chatgpt-mermaid-\_r_73d\_ .node polygon{fill:rgb(222, 234, 251);stroke:rgb(83, 154, 248);stroke-width:1px;}#chatgpt-mermaid-\_r_73d\_ .relationshipLine{stroke:rgb(143, 143, 143);stroke-width:1px;fill:none;}#chatgpt-mermaid-\_r_73d\_ .marker{fill:none!important;stroke:rgb(143, 143, 143)!important;stroke-width:1;}#chatgpt-mermaid-\_r_73d\_ [data-look=neo].labelBkg{background-color:rgba(243, 243, 243, 0.5);}#chatgpt-mermaid-\_r_73d\_ .node .neo-node{stroke:rgb(83, 154, 248);}#chatgpt-mermaid-\_r_73d\_ [data-look="neo"].node rect,#chatgpt-mermaid-\_r_73d\_ [data-look="neo"].cluster rect,#chatgpt-mermaid-\_r_73d\_ [data-look="neo"].node polygon{stroke:url(#chatgpt-mermaid-\_r_73d\_-gradient);filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-\_r_73d\_ [data-look="neo"].swimlane.cluster rect{filter:none;}#chatgpt-mermaid-\_r_73d\_ [data-look="neo"].node path{stroke:url(#chatgpt-mermaid-\_r_73d\_-gradient);stroke-width:1px;}#chatgpt-mermaid-\_r_73d\_ [data-look="neo"].node .outer-path{filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-\_r_73d\_ [data-look="neo"].node .neo-line path{stroke:rgb(83, 154, 248);filter:none;}#chatgpt-mermaid-\_r_73d\_ [data-look="neo"].node circle{stroke:url(#chatgpt-mermaid-\_r_73d\_-gradient);filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-\_r_73d\_ [data-look="neo"].node circle .state-start{fill:#000000;}#chatgpt-mermaid-\_r_73d\_ [data-look="neo"].icon-shape .icon{fill:url(#chatgpt-mermaid-\_r_73d\_-gradient);filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-\_r_73d\_ [data-look="neo"].icon-shape .icon-neo path{stroke:url(#chatgpt-mermaid-\_r_73d\_-gradient);filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-\_r_73d\_ :root{--mermaid-font-family:-apple-system-body,ui-sans-serif,-apple-system,system-ui,"Segoe UI",Helvetica,"Apple Color Emoji",Arial,sans-serif,"Segoe UI Emoji","Segoe UI Symbol";}USERSAVATARSGARMENTSOUTFITSPOSTSAI_TASKSBODY_PROFILESGARMENT_IMAGESGARMENT_ASSETSASSET_ANCHORSOUTFIT_ITEMSLICENSESCOMMENTSLIKESAI_TASK_EVENTSMODERATION_EVENTSownsownscreatespublishesrequestshaswearscontainsproducesdefinesused_incontainsgrantsgrants_or_receivesreceiveswritescreatesreceivesrecordssubmitsreviewed

### **18.3 主要数据表规格**

#### `users`**&#x20;用户表**

| 字段         | 类型        | 说明                          |
| ---------- | --------- | --------------------------- |
| id         | UUID      | 主键                          |
| email      | VARCHAR   | 登录邮箱，可空                     |
| phone      | VARCHAR   | 手机号，可空                      |
| nickname   | VARCHAR   | 昵称                          |
| avatar_url | TEXT      | 头像资源                        |
| status     | ENUM      | ACTIVE / DISABLED / DELETED |
| created_at | TIMESTAMP | 创建时间                        |
| updated_at | TIMESTAMP | 更新时间                        |

约束：

- 邮箱、手机号按登录体系设置唯一性。
- 敏感字段不得明文出现在普通日志。
- 删除用户时必须触发关联数据处理流程。

#### `avatars`**&#x20;角色表**

| 字段                      | 类型        | 说明                          |
| ----------------------- | --------- | --------------------------- |
| id                      | UUID      | 角色 ID                       |
| owner_user_id           | UUID      | 所属用户                        |
| name                    | VARCHAR   | 角色名称                        |
| description             | TEXT      | 角色简介                        |
| model_id                | VARCHAR   | 基础模型                        |
| style_id                | VARCHAR   | 美术风格                        |
| current_body_profile_id | UUID      | 当前身材配置                      |
| face_config             | JSONB     | 五官配置                        |
| hair_config             | JSONB     | 发型配置                        |
| skin_config             | JSONB     | 肤色配置                        |
| visibility              | ENUM      | PRIVATE / PUBLIC            |
| status                  | ENUM      | ACTIVE / ARCHIVED / DELETED |
| created_at              | TIMESTAMP | 创建时间                        |

#### `garments`**&#x20;衣物表**

| 字段                     | 类型        | 说明       |
| ---------------------- | --------- | -------- |
| id                     | UUID      | 衣物 ID    |
| owner_user_id          | UUID      | 所属用户     |
| name                   | VARCHAR   | 用户自定义名称  |
| category               | VARCHAR   | 一级分类     |
| subcategory            | VARCHAR   | 二级分类     |
| colors                 | JSONB     | 颜色集合     |
| materials              | JSONB     | 材质       |
| seasons                | JSONB     | 季节       |
| occasions              | JSONB     | 场景       |
| style_tags             | JSONB     | 风格标签     |
| body_parts             | JSONB     | 身体部位集合   |
| size_info              | JSONB     | 尺码信息     |
| recognition_confidence | DECIMAL   | AI 识别置信度 |
| status                 | ENUM      | 处理状态     |
| visibility             | ENUM      | 私有/公开    |
| deleted_at             | TIMESTAMP | 软删除时间    |

#### `garment_assets`**&#x20;数字服装资产表**

| 字段             | 类型      | 说明                                        |
| -------------- | ------- | ----------------------------------------- |
| id             | UUID    | 资产 ID                                     |
| garment_id     | UUID    | 来源衣物                                      |
| asset_version  | INT     | 资产版本                                      |
| asset_type     | ENUM    | SPRITE / LAYERED_2D / MESH_2_5D / MESH_3D |
| manifest_key   | TEXT    | 资产清单地址                                    |
| texture_key    | TEXT    | 主贴图                                       |
| mask_key       | TEXT    | 分割遮罩                                      |
| normal_map_key | TEXT    | 法线贴图，可空                                   |
| anchor_config  | JSONB   | 锚点配置                                      |
| layer_config   | JSONB   | 图层配置                                      |
| fit_config     | JSONB   | 适配配置                                      |
| quality_score  | DECIMAL | 质量评分                                      |
| status         | ENUM    | DRAFT / REVIEW / READY / REJECTED         |

### **18.4 数据完整性约束**

- 每个 `garment` 必须归属于一个用户。
- 每个 `garment_asset` 必须关联来源衣物或明确的官方资产来源。
- 每个正式可穿戴资产必须具备 `manifest`。
- 每个 `outfit_item` 必须关联有效资产版本。
- 每个公开作品必须具备明确的可见性设置。
- 每次授权变更必须生成不可覆盖的授权事件。
- 每个 AI 任务必须保存模型版本与输入引用。
- 每个审核事件必须关联审核策略版本。
- 删除资产不能直接物理删除仍被有效历史作品引用的所有数据，必须走引用检查和生命周期策略。

### **18.5 资产版本策略**

服装素材生成后，用户可能多次修改锚点、遮罩和贴图。

不能直接覆盖旧版本。

例如：

- `garment_asset_id = GA001`
- `asset_version = 1`：首次生成。
- `asset_version = 2`：用户修正轮廓。
- `asset_version = 3`：调整锚点和图层。

历史穿搭应引用具体版本，避免资产升级后历史作品发生不可预期变化。

## **十九、API 接口规格**

### **19.1 API 通用规范**

建议统一采用 REST API，业务接口统一 JSON，文件采用 multipart 上传或预签名上传。

通用响应：

```
{
  "success": true,
  "data": {},
  "error": null,
  "requestId": "req_xxx"
}
```

错误响应：

```
{
  "success": false,
  "data": null,
  "error": {
    "code": "RESOURCE_NOT_FOUND",
    "message": "资源不存在或无权访问"
  },
  "requestId": "req_xxx"
}
```

接口必须具备：

- 登录鉴权。
- 资源所有权校验。
- 参数校验。
- 幂等策略。
- 统一错误码。
- 请求追踪 ID。
- 频率限制。
- 分页。
- 审计日志。

### **19.2 用户与角色 API**

| 方法     | 路径                                  | 说明     |
| ------ | ----------------------------------- | ------ |
| GET    | `/api/v1/me`                        | 获取当前用户 |
| PATCH  | `/api/v1/me`                        | 更新个人资料 |
| GET    | `/api/v1/avatars`                   | 获取角色列表 |
| POST   | `/api/v1/avatars`                   | 创建角色   |
| GET    | `/api/v1/avatars/{id}`              | 获取角色详情 |
| PATCH  | `/api/v1/avatars/{id}`              | 修改角色   |
| DELETE | `/api/v1/avatars/{id}`              | 删除角色   |
| PUT    | `/api/v1/avatars/{id}/body-profile` | 保存身材配置 |
| PUT    | `/api/v1/avatars/{id}/appearance`   | 保存外观配置 |
| POST   | `/api/v1/avatars/{id}/duplicate`    | 复制角色   |

创建角色请求：

```
{
  "name": "我的娃娃",
  "modelId": "base_chibi_01",
  "styleId": "anime_soft",
  "bodyTemplateId": "standard_01"
}
```

### **19.3 衣物 API**

| 方法     | 路径                                     | 说明     |
| ------ | -------------------------------------- | ------ |
| GET    | `/api/v1/garments`                     | 衣物列表   |
| POST   | `/api/v1/garments`                     | 创建衣物记录 |
| GET    | `/api/v1/garments/{id}`                | 衣物详情   |
| PATCH  | `/api/v1/garments/{id}`                | 更新属性   |
| DELETE | `/api/v1/garments/{id}`                | 软删除    |
| POST   | `/api/v1/garments/{id}/recognize`      | 重新识别   |
| POST   | `/api/v1/garments/{id}/generate-asset` | 生成数字资产 |
| GET    | `/api/v1/garments/{id}/tasks`          | 获取关联任务 |
| GET    | `/api/v1/garments/{id}/assets`         | 获取资产版本 |

衣物列表支持一级分类、二级分类、颜色、季节、场景、风格、资产状态、创建时间和关键词。

### **19.4 上传 API**

| 方法     | 路径                              | 说明        |
| ------ | ------------------------------- | --------- |
| POST   | `/api/v1/uploads`               | 创建上传任务    |
| POST   | `/api/v1/uploads/{id}/complete` | 确认上传完成    |
| GET    | `/api/v1/uploads/{id}`          | 查询上传状态    |
| POST   | `/api/v1/uploads/{id}/retry`    | 重试可恢复任务   |
| DELETE | `/api/v1/uploads/{id}`          | 取消/删除上传任务 |

上传响应：

```
{
  "uploadId": "UPL_001",
  "status": "UPLOADED",
  "nextStep": "FILE_VALIDATING",
  "createdAt": "2026-11-13T10:00:00Z"
}
```

### **19.5 穿搭 API**

| 方法     | 路径                                    | 说明    |
| ------ | ------------------------------------- | ----- |
| GET    | `/api/v1/outfits`                     | 穿搭列表  |
| POST   | `/api/v1/outfits`                     | 创建穿搭  |
| GET    | `/api/v1/outfits/{id}`                | 穿搭详情  |
| PATCH  | `/api/v1/outfits/{id}`                | 修改穿搭  |
| DELETE | `/api/v1/outfits/{id}`                | 删除穿搭  |
| POST   | `/api/v1/outfits/{id}/items`          | 添加服装  |
| DELETE | `/api/v1/outfits/{id}/items/{itemId}` | 移除服装  |
| POST   | `/api/v1/outfits/{id}/render`         | 生成预览图 |
| POST   | `/api/v1/outfits/{id}/duplicate`      | 复制穿搭  |

穿搭保存必须记录角色、资产 ID、资产版本、变换参数、图层顺序和渲染配置。

### **19.6 AI 搭配 API**

| 方法   | 路径                                         | 说明     |
| ---- | ------------------------------------------ | ------ |
| POST | `/api/v1/ai/outfit-recommendations`        | 发起搭配请求 |
| GET  | `/api/v1/ai/tasks/{taskId}`                | 查询任务状态 |
| POST | `/api/v1/ai/tasks/{taskId}/cancel`         | 取消任务   |
| POST | `/api/v1/ai/recommendations/{id}/feedback` | 用户反馈   |
| POST | `/api/v1/ai/recommendations/{id}/apply`    | 应用搭配方案 |

请求示例：

```
{
  "avatarId": "AVATAR_001",
  "occasion": "dinner",
  "style": ["sweet", "casual"],
  "season": "autumn",
  "constraints": {
    "avoid": ["high_heels"],
    "preferOwnedItems": true
  },
  "resultCount": 3
}
```

响应必须引用真实资产：

```
{
  "taskId": "TASK_001",
  "status": "COMPLETED",
  "recommendations": [
    {
      "recommendationId": "REC_001",
      "items": [
        {
          "garmentAssetId": "GA_TOP_001",
          "assetVersion": 2,
          "slot": "top"
        },
        {
          "garmentAssetId": "GA_SKIRT_001",
          "assetVersion": 1,
          "slot": "bottom"
        }
      ],
      "reason": "颜色协调，适合当前场景"
    }
  ]
}
```

### **19.7 分享与授权 API**

| 方法     | 路径                             | 说明   |
| ------ | ------------------------------ | ---- |
| POST   | `/api/v1/posts`                | 创建作品 |
| GET    | `/api/v1/posts/{id}`           | 作品详情 |
| PATCH  | `/api/v1/posts/{id}`           | 修改作品 |
| DELETE | `/api/v1/posts/{id}`           | 删除作品 |
| POST   | `/api/v1/posts/{id}/publish`   | 发布   |
| POST   | `/api/v1/assets/{id}/licenses` | 创建授权 |
| GET    | `/api/v1/assets/{id}/licenses` | 授权列表 |
| DELETE | `/api/v1/licenses/{id}`        | 撤销授权 |
| POST   | `/api/v1/assets/{id}/reuse`    | 复用资产 |

## **二十、角色系统独立技术方案**

**独立技术方案 A**

### **20.1 技术目标**

角色系统不是一张静态人物图片，而是可配置、可保存、可换装、可复用的角色模型。

角色系统必须解决：

1. 同一账号创建多个角色。
2. 角色脸部和外观可编辑。
3. 角色身体比例可调整。
4. 多个角色共享基础模型体系。
5. 服装能够挂载到角色骨骼或锚点。
6. 身材变化后服装可以重新适配。
7. 角色可旋转、缩放、切换动作和表情。
8. 角色配置可以保存、恢复和版本化。
9. 模型资源可以按需加载。
10. 移动端渲染性能可控。

### **20.2 技术架构**

建议采用独立的角色渲染模块，与 Flutter 业务界面解耦。

业务层负责角色创建、参数保存、资源管理和权限校验；渲染层负责模型加载、骨骼、Morph Targets、相机、灯光、材质、服装挂载和实时预览。

### **20.3 角色模型标准**

推荐优先验证：

- GLB/glTF：通用模型交付格式。
- VRM：角色模型、骨骼、表情等相关生态。
- Three.js：Web 端渲染。
- three-vrm：VRM 模型加载和运行时支持。

角色资源应明确区分：

| 资源             | 内容      | 是否必须   |
| -------------- | ------- | ------ |
| Base Mesh      | 基础人体网格  | 是      |
| Skeleton       | 骨骼结构    | 是      |
| Morph Targets  | 身体与脸部形变 | 是      |
| Face Materials | 面部材质    | 是      |
| Hair Mesh      | 发型模型    | 是      |
| Eye Materials  | 眼睛材质    | 是      |
| Clothing Slots | 服装挂载槽位  | 是      |
| Animation      | 动作资源    | MVP 可选 |
| Expressions    | 表情资源    | 建议     |
| Accessories    | 饰品挂载资源  | 是      |

### **20.4 身材形变系统**

不能把身材系统简单实现成对整个角色模型做 X/Y/Z 缩放。

这种方案会造成：

- 肢体比例异常。
- 服装拉伸。
- 骨骼位置偏移。
- 手脚比例不自然。
- 服装和身体碰撞。
- 不同身材下的模型失真。

推荐采用基础模型 + Morph Targets 的方式。

| 参数             | 对应形变             | 影响部位 |
| -------------- | ---------------- | ---- |
| height         | height_morph     | 整体身高 |
| shoulder_width | shoulder_morph   | 肩部   |
| chest_volume   | chest_morph      | 胸部   |
| waist_width    | waist_morph      | 腰部   |
| hip_width      | hip_morph        | 臀部   |
| leg_length     | leg_length_morph | 腿部   |
| thigh_volume   | thigh_morph      | 大腿   |
| calf_volume    | calf_morph       | 小腿   |
| arm_volume     | arm_morph        | 手臂   |
| head_ratio     | head_scale_morph | 头部比例 |

实际参数不能假设所有模型都能天然支持。需要美术和技术团队共同确定每个基础模型的 Morph Target 集合。

### **20.5 身材参数计算**

建议保存归一化参数：

```
{
  "bodyProfileId": "BP_001",
  "template": "standard",
  "parameters": {
    "height": 0.5,
    "shoulderWidth": 0.45,
    "chestVolume": 0.5,
    "waistWidth": 0.4,
    "hipWidth": 0.55,
    "legLength": 0.6,
    "thighVolume": 0.5,
    "calfVolume": 0.45,
    "armVolume": 0.45,
    "headRatio": 0.7
  }
}
```

渲染层将这些值映射到模型实际形变参数：

\\[ M = \sum\_{i=1}^{n} w_i \cdot T_i \\]

其中：

- \\(M\\)：最终角色网格形态。
- \\(T_i\\)：某一形变目标。
- \\(w_i\\)：形变权重。

实际实现应设置上下限，避免用户组合多个极端参数后产生不合法模型。

### **20.6 角色创建流程**

\#chatgpt-mermaid-\_r_74p\_{font-family:-apple-system-body,ui-sans-serif,-apple-system,system-ui,"Segoe UI",Helvetica,"Apple Color Emoji",Arial,sans-serif,"Segoe UI Emoji","Segoe UI Symbol";font-size:16px;fill:rgb(13, 13, 13);}@keyframes edge-animation-frame{from{stroke-dashoffset:0;}}@keyframes dash{to{stroke-dashoffset:0;}}#chatgpt-mermaid-\_r_74p\_ .edge-animation-slow{stroke-dasharray:9,5!important;stroke-dashoffset:900;animation:dash 50s linear infinite;stroke-linecap:round;}#chatgpt-mermaid-\_r_74p\_ .edge-animation-fast{stroke-dasharray:9,5!important;stroke-dashoffset:900;animation:dash 20s linear infinite;stroke-linecap:round;}#chatgpt-mermaid-\_r_74p\_ .error-icon{fill:rgb(243, 243, 243);}#chatgpt-mermaid-\_r_74p\_ .error-text{fill:rgb(13, 13, 13);stroke:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_74p\_ .edge-thickness-normal{stroke-width:1px;}#chatgpt-mermaid-\_r_74p\_ .edge-thickness-thick{stroke-width:3.5px;}#chatgpt-mermaid-\_r_74p\_ .edge-pattern-solid{stroke-dasharray:0;}#chatgpt-mermaid-\_r_74p\_ .edge-thickness-invisible{stroke-width:0;fill:none;}#chatgpt-mermaid-\_r_74p\_ .edge-pattern-dashed{stroke-dasharray:3;}#chatgpt-mermaid-\_r_74p\_ .edge-pattern-dotted{stroke-dasharray:2;}#chatgpt-mermaid-\_r_74p\_ .marker{fill:rgb(143, 143, 143);stroke:rgb(143, 143, 143);}#chatgpt-mermaid-\_r_74p\_ .marker.cross{stroke:rgb(143, 143, 143);}#chatgpt-mermaid-\_r_74p\_ svg{font-family:-apple-system-body,ui-sans-serif,-apple-system,system-ui,"Segoe UI",Helvetica,"Apple Color Emoji",Arial,sans-serif,"Segoe UI Emoji","Segoe UI Symbol";font-size:16px;}#chatgpt-mermaid-\_r_74p\_ p{margin:0;}#chatgpt-mermaid-\_r_74p\_ .label{font-family:-apple-system-body,ui-sans-serif,-apple-system,system-ui,"Segoe UI",Helvetica,"Apple Color Emoji",Arial,sans-serif,"Segoe UI Emoji","Segoe UI Symbol";color:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_74p\_ .cluster-label text{fill:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_74p\_ .cluster-label span{color:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_74p\_ .cluster-label span p{background-color:transparent;}#chatgpt-mermaid-\_r_74p\_ .label text,#chatgpt-mermaid-\_r_74p\_ span{fill:rgb(13, 13, 13);color:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_74p\_ .node rect,#chatgpt-mermaid-\_r_74p\_ .node circle,#chatgpt-mermaid-\_r_74p\_ .node ellipse,#chatgpt-mermaid-\_r_74p\_ .node polygon,#chatgpt-mermaid-\_r_74p\_ .node path{fill:rgb(222, 234, 251);stroke:rgb(83, 154, 248);stroke-width:1px;}#chatgpt-mermaid-\_r_74p\_ .rough-node .label text,#chatgpt-mermaid-\_r_74p\_ .node .label text,#chatgpt-mermaid-\_r_74p\_ .image-shape .label,#chatgpt-mermaid-\_r_74p\_ .icon-shape .label{text-anchor:middle;}#chatgpt-mermaid-\_r_74p\_ .node .katex path{fill:#000;stroke:#000;stroke-width:1px;}#chatgpt-mermaid-\_r_74p\_ .rough-node .label,#chatgpt-mermaid-\_r_74p\_ .node .label,#chatgpt-mermaid-\_r_74p\_ .image-shape .label,#chatgpt-mermaid-\_r_74p\_ .icon-shape .label{text-align:center;}#chatgpt-mermaid-\_r_74p\_ .node.clickable{cursor:pointer;}#chatgpt-mermaid-\_r_74p\_ .root .anchor path{fill:rgb(143, 143, 143)!important;stroke-width:0;stroke:rgb(143, 143, 143);}#chatgpt-mermaid-\_r_74p\_ .arrowheadPath{fill:rgb(143, 143, 143);}#chatgpt-mermaid-\_r_74p\_ .edgePath .path{stroke:rgb(143, 143, 143);stroke-width:1px;}#chatgpt-mermaid-\_r_74p\_ .flowchart-link{stroke:rgb(143, 143, 143);fill:none;}#chatgpt-mermaid-\_r_74p\_ .edgeLabel{background-color:rgb(252, 252, 252);text-align:center;}#chatgpt-mermaid-\_r_74p\_ .edgeLabel p{background-color:rgb(252, 252, 252);}#chatgpt-mermaid-\_r_74p\_ .edgeLabel rect{opacity:0.5;background-color:rgb(252, 252, 252);fill:rgb(252, 252, 252);}#chatgpt-mermaid-\_r_74p\_ .labelBkg{background-color:rgba(252, 252, 252, 0.5);}#chatgpt-mermaid-\_r_74p\_ .cluster rect{fill:rgb(243, 243, 243);stroke:rgba(0, 0, 0, 0.1);stroke-width:1px;}#chatgpt-mermaid-\_r_74p\_ .cluster text{fill:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_74p\_ .cluster span{color:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_74p\_ div.mermaidTooltip{position:absolute;text-align:center;max-width:200px;padding:2px;font-family:-apple-system-body,ui-sans-serif,-apple-system,system-ui,"Segoe UI",Helvetica,"Apple Color Emoji",Arial,sans-serif,"Segoe UI Emoji","Segoe UI Symbol";font-size:12px;background:rgb(243, 243, 243);border:1px solid rgba(0, 0, 0, 0.1);border-radius:2px;pointer-events:none;z-index:100;}#chatgpt-mermaid-\_r_74p\_ .flowchartTitleText{text-anchor:middle;font-size:18px;fill:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_74p\_ rect.text{fill:none;stroke-width:0;}#chatgpt-mermaid-\_r_74p\_ .icon-shape,#chatgpt-mermaid-\_r_74p\_ .image-shape{background-color:rgb(252, 252, 252);text-align:center;}#chatgpt-mermaid-\_r_74p\_ .icon-shape p,#chatgpt-mermaid-\_r_74p\_ .image-shape p{background-color:rgb(252, 252, 252);padding:2px;}#chatgpt-mermaid-\_r_74p\_ .icon-shape .label rect,#chatgpt-mermaid-\_r_74p\_ .image-shape .label rect{opacity:0.5;background-color:rgb(252, 252, 252);fill:rgb(252, 252, 252);}#chatgpt-mermaid-\_r_74p\_ .label-icon{display:inline-block;height:1em;overflow:visible;vertical-align:-0.125em;}#chatgpt-mermaid-\_r_74p\_ .node .label-icon path{fill:currentColor;stroke:revert;stroke-width:revert;}#chatgpt-mermaid-\_r_74p\_ .node .neo-node{stroke:rgb(83, 154, 248);}#chatgpt-mermaid-\_r_74p\_ [data-look="neo"].node rect,#chatgpt-mermaid-\_r_74p\_ [data-look="neo"].cluster rect,#chatgpt-mermaid-\_r_74p\_ [data-look="neo"].node polygon{stroke:url(#chatgpt-mermaid-\_r_74p\_-gradient);filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-\_r_74p\_ [data-look="neo"].swimlane.cluster rect{filter:none;}#chatgpt-mermaid-\_r_74p\_ [data-look="neo"].node path{stroke:url(#chatgpt-mermaid-\_r_74p\_-gradient);stroke-width:1px;}#chatgpt-mermaid-\_r_74p\_ [data-look="neo"].node .outer-path{filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-\_r_74p\_ [data-look="neo"].node .neo-line path{stroke:rgb(83, 154, 248);filter:none;}#chatgpt-mermaid-\_r_74p\_ [data-look="neo"].node circle{stroke:url(#chatgpt-mermaid-\_r_74p\_-gradient);filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-\_r_74p\_ [data-look="neo"].node circle .state-start{fill:#000000;}#chatgpt-mermaid-\_r_74p\_ [data-look="neo"].icon-shape .icon{fill:url(#chatgpt-mermaid-\_r_74p\_-gradient);filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-\_r_74p\_ [data-look="neo"].icon-shape .icon-neo path{stroke:url(#chatgpt-mermaid-\_r_74p\_-gradient);filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-\_r_74p\_ .node text{font-size:14px;font-weight:600;letter-spacing:normal;fill:rgb(0, 79, 153);}#chatgpt-mermaid-\_r_74p\_ .edgeLabels text{font-size:13px;font-weight:600;letter-spacing:-0.08px;fill:rgb(0, 79, 153);}#chatgpt-mermaid-\_r_74p\_ .node tspan[font-weight="normal"],#chatgpt-mermaid-\_r_74p\_ .edgeLabels tspan[font-weight="normal"]{font-weight:600;}#chatgpt-mermaid-\_r_74p\_ .edgeLabel .label rect{opacity:1;rx:13px;ry:13px;fill:rgb(245, 250, 255);stroke:rgb(206, 219, 229);stroke-width:1px;}#chatgpt-mermaid-\_r_74p\_ .node rect,#chatgpt-mermaid-\_r_74p\_ .node circle,#chatgpt-mermaid-\_r_74p\_ .node ellipse,#chatgpt-mermaid-\_r_74p\_ .node polygon,#chatgpt-mermaid-\_r_74p\_ .node path{fill:rgb(229, 243, 255);stroke:rgba(0, 0, 0, 0.1);stroke-width:1px;}#chatgpt-mermaid-\_r_74p\_ .node rect{rx:16px;ry:16px;}#chatgpt-mermaid-\_r_74p\_ .mermaid-decision .label-container{fill:rgb(245, 250, 255);stroke:rgb(206, 219, 229);stroke-dasharray:2,2;}#chatgpt-mermaid-\_r_74p\_ .edgePaths .flowchart-link{stroke:rgb(143, 143, 143);stroke-width:1px;stroke-linecap:round;stroke-linejoin:round;}#chatgpt-mermaid-\_r_74p\_ .marker{fill:rgb(143, 143, 143);stroke:rgb(143, 143, 143);}#chatgpt-mermaid-\_r_74p\_ :root{--mermaid-font-family:-apple-system-body,ui-sans-serif,-apple-system,system-ui,"Segoe UI",Helvetica,"Apple Color Emoji",Arial,sans-serif,"Segoe UI Emoji","Segoe UI Symbol";}选择角色模板设置角色名称选择基础脸型选择发型、发色、肤色选择身材模板进入自由参数编辑实时预览保存角色配置生成角色缩略图进入角色主页或换装

### **20.7 角色配置 JSON**

```
{
  "avatarId": "AVATAR_001",
  "model": {
    "modelId": "chibi_base_01",
    "format": "glb",
    "version": "1.0.0"
  },
  "appearance": {
    "facePreset": "face_03",
    "skinTone": "skin_02",
    "hairStyle": "hair_05",
    "hairColor": "#46372F",
    "eyePreset": "eye_04"
  },
  "bodyProfile": {
    "template": "standard",
    "morphs": {
      "height": 0.5,
      "shoulderWidth": 0.45,
      "waistWidth": 0.4,
      "hipWidth": 0.55,
      "legLength": 0.6
    }
  },
  "render": {
    "cameraPreset": "full_body_front",
    "lightingPreset": "soft_studio"
  }
}
```

### **20.8 角色系统性能要求**

以下为建议目标，需要在实际目标机型上压测：

| 项目       | 建议目标                           |
| -------- | ------------------------------ |
| 首次角色资源加载 | 常见网络下 3—5 秒内进入可交互状态            |
| 角色切换     | 已缓存角色尽量在 1 秒内显示                |
| 参数拖动     | 交互期间目标 30 FPS 以上，主力设备争取 60 FPS |
| 模型资源     | 分级加载，避免一次加载全部角色                |
| 贴图资源     | 支持压缩纹理与尺寸分级                    |
| 内存       | 设定低端机降级策略                      |
| 渲染失败     | 回退到角色静态预览或 2D 展示               |

### **20.9 角色系统异常场景**

| 场景              | 处理             |
| --------------- | -------------- |
| 模型资源下载失败        | 重试，必要时使用缓存     |
| 模型格式错误          | 拒绝加载，记录资源异常    |
| Morph Target 缺失 | 禁用对应滑块，不影响其他参数 |
| 角色参数越界          | 服务端和渲染层双重限制    |
| 角色保存失败          | 保留本地编辑状态，允许重试  |
| 角色切换中途退出        | 不自动覆盖未保存内容     |
| 渲染设备不支持         | 提供降级展示         |
| 角色模型版本升级        | 保留旧配置并执行兼容迁移   |

### **20.10 角色系统验收标准**

- 可以创建多个角色。
- 角色之间配置完全隔离。
- 五官、发型、肤色和身材可以保存。
- 同一角色重新进入后能恢复上次状态。
- 身材参数变化能够反映到模型。
- 极端参数组合不会导致模型崩溃。
- 不支持的模型参数不会导致整个角色无法加载。
- 角色模型、贴图和动画资源具有可追溯版本。
- 角色渲染模块可以独立升级，不影响 Flutter 其他页面。

## **二十一、服装系统独立技术方案**

**独立技术方案 B**

### **21.1 技术目标**

服装系统是产品最重要的技术壁垒之一。

它必须让现实衣物经过图像处理后，变成可以在虚拟角色上穿戴、调整、保存、分享和复用的数字资产。

核心技术问题：

1. 衣物主体如何从背景中分离。
2. 如何保留真实衣物颜色和图案。
3. 如何生成可穿戴素材。
4. 如何标记衣物覆盖身体的部位。
5. 如何定义锚点。
6. 如何定义图层顺序。
7. 如何处理遮挡。
8. 如何适配不同角色身材。
9. 如何处理衣物之间的冲突。
10. 如何保持资产版本和授权关系。

### **21.2 服装资产类型**

第一阶段不要把所有资产都当成同一种贴图。

| 类型         | 适用场景        | 技术方式         |
| ---------- | ----------- | ------------ |
| Sprite     | 帽子、耳饰、发夹、眼镜 | 透明 PNG/WebP  |
| Layered 2D | 上衣、下装、简单连衣裙 | 多层图片         |
| 2.5D Mesh  | 有旋转展示需求的服装  | 简化网格 + UV 贴图 |
| 3D Mesh    | 未来复杂服装      | 网格、骨骼、材质     |

建议首期优先实现：

- 头饰。
- 眼镜。
- 耳饰。
- 项链。
- 上装。
- 下装。
- 连衣裙。
- 鞋靴。

外套、复杂裙摆、带有大量褶皱和多层结构的衣物可以作为专项 PoC。

### **21.3 服装资产生产架构**

\#chatgpt-mermaid-\_r_755\_{font-family:-apple-system-body,ui-sans-serif,-apple-system,system-ui,"Segoe UI",Helvetica,"Apple Color Emoji",Arial,sans-serif,"Segoe UI Emoji","Segoe UI Symbol";font-size:16px;fill:rgb(13, 13, 13);}@keyframes edge-animation-frame{from{stroke-dashoffset:0;}}@keyframes dash{to{stroke-dashoffset:0;}}#chatgpt-mermaid-\_r_755\_ .edge-animation-slow{stroke-dasharray:9,5!important;stroke-dashoffset:900;animation:dash 50s linear infinite;stroke-linecap:round;}#chatgpt-mermaid-\_r_755\_ .edge-animation-fast{stroke-dasharray:9,5!important;stroke-dashoffset:900;animation:dash 20s linear infinite;stroke-linecap:round;}#chatgpt-mermaid-\_r_755\_ .error-icon{fill:rgb(243, 243, 243);}#chatgpt-mermaid-\_r_755\_ .error-text{fill:rgb(13, 13, 13);stroke:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_755\_ .edge-thickness-normal{stroke-width:1px;}#chatgpt-mermaid-\_r_755\_ .edge-thickness-thick{stroke-width:3.5px;}#chatgpt-mermaid-\_r_755\_ .edge-pattern-solid{stroke-dasharray:0;}#chatgpt-mermaid-\_r_755\_ .edge-thickness-invisible{stroke-width:0;fill:none;}#chatgpt-mermaid-\_r_755\_ .edge-pattern-dashed{stroke-dasharray:3;}#chatgpt-mermaid-\_r_755\_ .edge-pattern-dotted{stroke-dasharray:2;}#chatgpt-mermaid-\_r_755\_ .marker{fill:rgb(143, 143, 143);stroke:rgb(143, 143, 143);}#chatgpt-mermaid-\_r_755\_ .marker.cross{stroke:rgb(143, 143, 143);}#chatgpt-mermaid-\_r_755\_ svg{font-family:-apple-system-body,ui-sans-serif,-apple-system,system-ui,"Segoe UI",Helvetica,"Apple Color Emoji",Arial,sans-serif,"Segoe UI Emoji","Segoe UI Symbol";font-size:16px;}#chatgpt-mermaid-\_r_755\_ p{margin:0;}#chatgpt-mermaid-\_r_755\_ .label{font-family:-apple-system-body,ui-sans-serif,-apple-system,system-ui,"Segoe UI",Helvetica,"Apple Color Emoji",Arial,sans-serif,"Segoe UI Emoji","Segoe UI Symbol";color:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_755\_ .cluster-label text{fill:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_755\_ .cluster-label span{color:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_755\_ .cluster-label span p{background-color:transparent;}#chatgpt-mermaid-\_r_755\_ .label text,#chatgpt-mermaid-\_r_755\_ span{fill:rgb(13, 13, 13);color:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_755\_ .node rect,#chatgpt-mermaid-\_r_755\_ .node circle,#chatgpt-mermaid-\_r_755\_ .node ellipse,#chatgpt-mermaid-\_r_755\_ .node polygon,#chatgpt-mermaid-\_r_755\_ .node path{fill:rgb(222, 234, 251);stroke:rgb(83, 154, 248);stroke-width:1px;}#chatgpt-mermaid-\_r_755\_ .rough-node .label text,#chatgpt-mermaid-\_r_755\_ .node .label text,#chatgpt-mermaid-\_r_755\_ .image-shape .label,#chatgpt-mermaid-\_r_755\_ .icon-shape .label{text-anchor:middle;}#chatgpt-mermaid-\_r_755\_ .node .katex path{fill:#000;stroke:#000;stroke-width:1px;}#chatgpt-mermaid-\_r_755\_ .rough-node .label,#chatgpt-mermaid-\_r_755\_ .node .label,#chatgpt-mermaid-\_r_755\_ .image-shape .label,#chatgpt-mermaid-\_r_755\_ .icon-shape .label{text-align:center;}#chatgpt-mermaid-\_r_755\_ .node.clickable{cursor:pointer;}#chatgpt-mermaid-\_r_755\_ .root .anchor path{fill:rgb(143, 143, 143)!important;stroke-width:0;stroke:rgb(143, 143, 143);}#chatgpt-mermaid-\_r_755\_ .arrowheadPath{fill:rgb(143, 143, 143);}#chatgpt-mermaid-\_r_755\_ .edgePath .path{stroke:rgb(143, 143, 143);stroke-width:1px;}#chatgpt-mermaid-\_r_755\_ .flowchart-link{stroke:rgb(143, 143, 143);fill:none;}#chatgpt-mermaid-\_r_755\_ .edgeLabel{background-color:rgb(252, 252, 252);text-align:center;}#chatgpt-mermaid-\_r_755\_ .edgeLabel p{background-color:rgb(252, 252, 252);}#chatgpt-mermaid-\_r_755\_ .edgeLabel rect{opacity:0.5;background-color:rgb(252, 252, 252);fill:rgb(252, 252, 252);}#chatgpt-mermaid-\_r_755\_ .labelBkg{background-color:rgba(252, 252, 252, 0.5);}#chatgpt-mermaid-\_r_755\_ .cluster rect{fill:rgb(243, 243, 243);stroke:rgba(0, 0, 0, 0.1);stroke-width:1px;}#chatgpt-mermaid-\_r_755\_ .cluster text{fill:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_755\_ .cluster span{color:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_755\_ div.mermaidTooltip{position:absolute;text-align:center;max-width:200px;padding:2px;font-family:-apple-system-body,ui-sans-serif,-apple-system,system-ui,"Segoe UI",Helvetica,"Apple Color Emoji",Arial,sans-serif,"Segoe UI Emoji","Segoe UI Symbol";font-size:12px;background:rgb(243, 243, 243);border:1px solid rgba(0, 0, 0, 0.1);border-radius:2px;pointer-events:none;z-index:100;}#chatgpt-mermaid-\_r_755\_ .flowchartTitleText{text-anchor:middle;font-size:18px;fill:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_755\_ rect.text{fill:none;stroke-width:0;}#chatgpt-mermaid-\_r_755\_ .icon-shape,#chatgpt-mermaid-\_r_755\_ .image-shape{background-color:rgb(252, 252, 252);text-align:center;}#chatgpt-mermaid-\_r_755\_ .icon-shape p,#chatgpt-mermaid-\_r_755\_ .image-shape p{background-color:rgb(252, 252, 252);padding:2px;}#chatgpt-mermaid-\_r_755\_ .icon-shape .label rect,#chatgpt-mermaid-\_r_755\_ .image-shape .label rect{opacity:0.5;background-color:rgb(252, 252, 252);fill:rgb(252, 252, 252);}#chatgpt-mermaid-\_r_755\_ .label-icon{display:inline-block;height:1em;overflow:visible;vertical-align:-0.125em;}#chatgpt-mermaid-\_r_755\_ .node .label-icon path{fill:currentColor;stroke:revert;stroke-width:revert;}#chatgpt-mermaid-\_r_755\_ .node .neo-node{stroke:rgb(83, 154, 248);}#chatgpt-mermaid-\_r_755\_ [data-look="neo"].node rect,#chatgpt-mermaid-\_r_755\_ [data-look="neo"].cluster rect,#chatgpt-mermaid-\_r_755\_ [data-look="neo"].node polygon{stroke:url(#chatgpt-mermaid-\_r_755\_-gradient);filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-\_r_755\_ [data-look="neo"].swimlane.cluster rect{filter:none;}#chatgpt-mermaid-\_r_755\_ [data-look="neo"].node path{stroke:url(#chatgpt-mermaid-\_r_755\_-gradient);stroke-width:1px;}#chatgpt-mermaid-\_r_755\_ [data-look="neo"].node .outer-path{filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-\_r_755\_ [data-look="neo"].node .neo-line path{stroke:rgb(83, 154, 248);filter:none;}#chatgpt-mermaid-\_r_755\_ [data-look="neo"].node circle{stroke:url(#chatgpt-mermaid-\_r_755\_-gradient);filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-\_r_755\_ [data-look="neo"].node circle .state-start{fill:#000000;}#chatgpt-mermaid-\_r_755\_ [data-look="neo"].icon-shape .icon{fill:url(#chatgpt-mermaid-\_r_755\_-gradient);filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-\_r_755\_ [data-look="neo"].icon-shape .icon-neo path{stroke:url(#chatgpt-mermaid-\_r_755\_-gradient);filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-\_r_755\_ .node text{font-size:14px;font-weight:600;letter-spacing:normal;fill:rgb(0, 79, 153);}#chatgpt-mermaid-\_r_755\_ .edgeLabels text{font-size:13px;font-weight:600;letter-spacing:-0.08px;fill:rgb(0, 79, 153);}#chatgpt-mermaid-\_r_755\_ .node tspan[font-weight="normal"],#chatgpt-mermaid-\_r_755\_ .edgeLabels tspan[font-weight="normal"]{font-weight:600;}#chatgpt-mermaid-\_r_755\_ .edgeLabel .label rect{opacity:1;rx:13px;ry:13px;fill:rgb(245, 250, 255);stroke:rgb(206, 219, 229);stroke-width:1px;}#chatgpt-mermaid-\_r_755\_ .node rect,#chatgpt-mermaid-\_r_755\_ .node circle,#chatgpt-mermaid-\_r_755\_ .node ellipse,#chatgpt-mermaid-\_r_755\_ .node polygon,#chatgpt-mermaid-\_r_755\_ .node path{fill:rgb(229, 243, 255);stroke:rgba(0, 0, 0, 0.1);stroke-width:1px;}#chatgpt-mermaid-\_r_755\_ .node rect{rx:16px;ry:16px;}#chatgpt-mermaid-\_r_755\_ .mermaid-decision .label-container{fill:rgb(245, 250, 255);stroke:rgb(206, 219, 229);stroke-dasharray:2,2;}#chatgpt-mermaid-\_r_755\_ .edgePaths .flowchart-link{stroke:rgb(143, 143, 143);stroke-width:1px;stroke-linecap:round;stroke-linejoin:round;}#chatgpt-mermaid-\_r_755\_ .marker{fill:rgb(143, 143, 143);stroke:rgb(143, 143, 143);}#chatgpt-mermaid-\_r_755\_ :root{--mermaid-font-family:-apple-system-body,ui-sans-serif,-apple-system,system-ui,"Segoe UI",Helvetica,"Apple Color Emoji",Arial,sans-serif,"Segoe UI Emoji","Segoe UI Symbol";}原始衣物照片文件安全与内容审核图像质量检查衣物主体识别分割 Mask透明素材生成纹理保真检查分类与部位识别锚点预测图层与遮挡配置角色适配测试Manifest 生成资产质量验收正式资产入库

### **21.4 分割与抠图方案**

候选技术：

- ![SAM2](https://github.com/facebookresearch/sam2?utm_source=chatgpt.com)
- ![MediaPipe Image Segmenter](https://developers.google.cn/edge/mediapipe/solutions/vision/image_segmenter?utm_source=chatgpt.com)
- 商业图像分割 API。
- 专用服装分割模型。

选择标准：

| 维度   | 评价重点           |
| ---- | -------------- |
| 轮廓精度 | 领口、袖口、裤腿边缘是否完整 |
| 细节保留 | 蕾丝、透明材质、毛边     |
| 复杂背景 | 衣物与背景颜色相近时表现   |
| 多物体  | 衣物与鞋包饰品同时出现    |
| 推理速度 | 单张处理耗时         |
| 部署成本 | GPU、API、运维成本   |
| 商用授权 | 代码、模型、训练数据许可   |

必须区分：

- 分割模型负责识别像素区域。
- 生成模型负责补全和转换素材。
- 分类模型负责理解衣物属性。
- 适配引擎负责把资产挂到角色上。

不能把这四种任务全部交给一个图像生成模型。

### **21.5 纹理保真策略**

生成模型容易改变：

- 衣物颜色。
- 印花图案。
- 商标。
- 纽扣。
- 衣领。
- 袖口。
- 纹理。
- 衣服轮廓。

因此建议采用分层处理：

1. 原始图片作为真实信息来源。
2. 分割 Mask 决定服装边界。
3. 原图纹理尽量保留。
4. 生成模型仅用于必要的补全和视觉风格适配。
5. 不允许未经用户确认修改明显品牌图案和文字。
6. 生成背面时标注为 AI 推测，不作为真实商品信息。

建议建立资产质量指标：

| 指标                 | 含义       |
| ------------------ | -------- |
| Silhouette IoU     | 分割轮廓重合程度 |
| Color Similarity   | 颜色相似度    |
| Texture Similarity | 纹理保真度    |
| Edge Quality       | 边缘质量     |
| Anchor Accuracy    | 锚点位置准确度  |
| Fit Quality        | 角色适配效果   |
| Occlusion Quality  | 遮挡效果     |

这些指标需要通过人工标注样本集建立基准，不应直接把模型自评分当作客观质量。

### **21.6 服装锚点体系**

每件服装必须有锚点配置。

| 锚点             | 用途   |
| -------------- | ---- |
| HEAD_CENTER    | 头部中心 |
| HEAD_TOP       | 头顶   |
| NECK           | 颈部   |
| LEFT_EAR       | 左耳   |
| RIGHT_EAR      | 右耳   |
| LEFT_SHOULDER  | 左肩   |
| RIGHT_SHOULDER | 右肩   |
| CHEST          | 胸前   |
| WAIST          | 腰部   |
| LEFT_HIP       | 左髋   |
| RIGHT_HIP      | 右髋   |
| LEFT_HAND      | 左手   |
| RIGHT_HAND     | 右手   |
| LEFT_FOOT      | 左脚   |
| RIGHT_FOOT     | 右脚   |

锚点不只是一个坐标，还应包含坐标系、位置、旋转、缩放、父级骨骼、允许偏移范围和适配规则。

### **21.7 服装 Manifest**

每件正式服装都应该有一份机器可读的 Manifest。

```
{
  "assetId": "GA_TOP_001",
  "version": 1,
  "assetType": "LAYERED_2D",
  "category": "top",
  "bodyParts": ["torso", "left_arm", "right_arm"],
  "anchors": {
    "neck": {"x": 0.5, "y": 0.08},
    "leftShoulder": {"x": 0.22, "y": 0.18},
    "rightShoulder": {"x": 0.78, "y": 0.18},
    "waist": {"x": 0.5, "y": 0.82}
  },
  "layers": {
    "order": 30,
    "occlusionGroup": "upper_body"
  },
  "fit": {
    "supportedBodyTypes": ["slim", "standard", "curvy"],
    "scaleRange": {"min": 0.8, "max": 1.3},
    "allowPositionAdjustment": true,
    "allowRotation": true
  },
  "textures": {
    "front": "assets/front.webp",
    "mask": "assets/mask.webp"
  }
}
```

### **21.8 图层与遮挡系统**

推荐采用明确的穿戴层级，而不是简单地按用户添加顺序渲染。

| Layer | 内容                 |
| ----- | ------------------ |
| 10    | 身体基础               |
| 20    | 内衣/贴身层（仅按产品合规范围支持） |
| 30    | 上装                 |
| 40    | 下装                 |
| 50    | 连衣裙/主体外观           |
| 60    | 外套                 |
| 70    | 围巾、披肩              |
| 80    | 项链、胸针              |
| 90    | 发型                 |
| 100   | 帽子、头饰              |
| 110   | 眼镜                 |
| 120   | 耳饰前层               |
| 130   | 特殊前景饰品             |

真实渲染不能完全依靠固定 Layer 数字。

例如耳环有一部分应该在耳朵前面，另一部分应该在头发后面。长发也可能需要前发、后发分层。

因此应同时使用：

- `layer_order`
- `occlusion_group`
- `depth_order`
- `anchor_binding`
- `mask_reference`

### **21.9 服装冲突检测**

| 冲突类型  | 示例          | 处理方式      |
| ----- | ----------- | --------- |
| 同槽互斥  | 两件普通上衣      | 默认替换，用户确认 |
| 外层覆盖  | 外套覆盖上衣      | 允许叠穿      |
| 部位冲突  | 两件鞋靴        | 互斥        |
| 头部遮挡  | 帽子与高体积发型    | 提示或自动调整   |
| 饰品重叠  | 多条项链        | 允许但检查重叠   |
| 裙摆遮挡  | 长裙覆盖鞋子      | 根据深度与遮罩处理 |
| 贴图穿透  | 服装进入身体内部    | 自动修正或人工调整 |
| 身材不兼容 | 特殊服装不支持当前体型 | 禁用或显示适配提示 |

### **21.10 服装适配算法**

第一阶段可以采用规则映射 + 参数变换。

角色体型参数：

\\[ B = (h, s, c, w, hip, leg) \\]

服装适配参数：

\\[ F = (s_x, s_y, o_x, o_y, r, d) \\]

其中：

- \\(h\\)：身高比例。
- \\(s\\)：肩宽。
- \\(c\\)：胸部轮廓。
- \\(w\\)：腰部宽度。
- \\(hip\\)：臀部宽度。
- \\(leg\\)：腿长。
- \\(s_x,s_y\\)：服装缩放。
- \\(o_x,o_y\\)：位置偏移。
- \\(r\\)：旋转。
- \\(d\\)：深度/层级参数。

适配系统根据角色参数和服装配置计算初始变换：

\\[ F' = f(B, F, C) \\]

其中 \\(C\\) 是服装类别和适配规则。

这是一种初期工程抽象，不意味着只通过缩放就能解决真实 3D 布料适配。复杂服装后续仍需网格变形、骨骼绑定或重新生成资产。

### **21.11 换装渲染流程**

\#chatgpt-mermaid-\_r_75l\_{font-family:-apple-system-body,ui-sans-serif,-apple-system,system-ui,"Segoe UI",Helvetica,"Apple Color Emoji",Arial,sans-serif,"Segoe UI Emoji","Segoe UI Symbol";font-size:16px;fill:rgb(13, 13, 13);}@keyframes edge-animation-frame{from{stroke-dashoffset:0;}}@keyframes dash{to{stroke-dashoffset:0;}}#chatgpt-mermaid-\_r_75l\_ .edge-animation-slow{stroke-dasharray:9,5!important;stroke-dashoffset:900;animation:dash 50s linear infinite;stroke-linecap:round;}#chatgpt-mermaid-\_r_75l\_ .edge-animation-fast{stroke-dasharray:9,5!important;stroke-dashoffset:900;animation:dash 20s linear infinite;stroke-linecap:round;}#chatgpt-mermaid-\_r_75l\_ .error-icon{fill:rgb(243, 243, 243);}#chatgpt-mermaid-\_r_75l\_ .error-text{fill:rgb(13, 13, 13);stroke:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_75l\_ .edge-thickness-normal{stroke-width:1px;}#chatgpt-mermaid-\_r_75l\_ .edge-thickness-thick{stroke-width:3.5px;}#chatgpt-mermaid-\_r_75l\_ .edge-pattern-solid{stroke-dasharray:0;}#chatgpt-mermaid-\_r_75l\_ .edge-thickness-invisible{stroke-width:0;fill:none;}#chatgpt-mermaid-\_r_75l\_ .edge-pattern-dashed{stroke-dasharray:3;}#chatgpt-mermaid-\_r_75l\_ .edge-pattern-dotted{stroke-dasharray:2;}#chatgpt-mermaid-\_r_75l\_ .marker{fill:rgb(143, 143, 143);stroke:rgb(143, 143, 143);}#chatgpt-mermaid-\_r_75l\_ .marker.cross{stroke:rgb(143, 143, 143);}#chatgpt-mermaid-\_r_75l\_ svg{font-family:-apple-system-body,ui-sans-serif,-apple-system,system-ui,"Segoe UI",Helvetica,"Apple Color Emoji",Arial,sans-serif,"Segoe UI Emoji","Segoe UI Symbol";font-size:16px;}#chatgpt-mermaid-\_r_75l\_ p{margin:0;}#chatgpt-mermaid-\_r_75l\_ .label{font-family:-apple-system-body,ui-sans-serif,-apple-system,system-ui,"Segoe UI",Helvetica,"Apple Color Emoji",Arial,sans-serif,"Segoe UI Emoji","Segoe UI Symbol";color:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_75l\_ .cluster-label text{fill:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_75l\_ .cluster-label span{color:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_75l\_ .cluster-label span p{background-color:transparent;}#chatgpt-mermaid-\_r_75l\_ .label text,#chatgpt-mermaid-\_r_75l\_ span{fill:rgb(13, 13, 13);color:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_75l\_ .node rect,#chatgpt-mermaid-\_r_75l\_ .node circle,#chatgpt-mermaid-\_r_75l\_ .node ellipse,#chatgpt-mermaid-\_r_75l\_ .node polygon,#chatgpt-mermaid-\_r_75l\_ .node path{fill:rgb(222, 234, 251);stroke:rgb(83, 154, 248);stroke-width:1px;}#chatgpt-mermaid-\_r_75l\_ .rough-node .label text,#chatgpt-mermaid-\_r_75l\_ .node .label text,#chatgpt-mermaid-\_r_75l\_ .image-shape .label,#chatgpt-mermaid-\_r_75l\_ .icon-shape .label{text-anchor:middle;}#chatgpt-mermaid-\_r_75l\_ .node .katex path{fill:#000;stroke:#000;stroke-width:1px;}#chatgpt-mermaid-\_r_75l\_ .rough-node .label,#chatgpt-mermaid-\_r_75l\_ .node .label,#chatgpt-mermaid-\_r_75l\_ .image-shape .label,#chatgpt-mermaid-\_r_75l\_ .icon-shape .label{text-align:center;}#chatgpt-mermaid-\_r_75l\_ .node.clickable{cursor:pointer;}#chatgpt-mermaid-\_r_75l\_ .root .anchor path{fill:rgb(143, 143, 143)!important;stroke-width:0;stroke:rgb(143, 143, 143);}#chatgpt-mermaid-\_r_75l\_ .arrowheadPath{fill:rgb(143, 143, 143);}#chatgpt-mermaid-\_r_75l\_ .edgePath .path{stroke:rgb(143, 143, 143);stroke-width:1px;}#chatgpt-mermaid-\_r_75l\_ .flowchart-link{stroke:rgb(143, 143, 143);fill:none;}#chatgpt-mermaid-\_r_75l\_ .edgeLabel{background-color:rgb(252, 252, 252);text-align:center;}#chatgpt-mermaid-\_r_75l\_ .edgeLabel p{background-color:rgb(252, 252, 252);}#chatgpt-mermaid-\_r_75l\_ .edgeLabel rect{opacity:0.5;background-color:rgb(252, 252, 252);fill:rgb(252, 252, 252);}#chatgpt-mermaid-\_r_75l\_ .labelBkg{background-color:rgba(252, 252, 252, 0.5);}#chatgpt-mermaid-\_r_75l\_ .cluster rect{fill:rgb(243, 243, 243);stroke:rgba(0, 0, 0, 0.1);stroke-width:1px;}#chatgpt-mermaid-\_r_75l\_ .cluster text{fill:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_75l\_ .cluster span{color:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_75l\_ div.mermaidTooltip{position:absolute;text-align:center;max-width:200px;padding:2px;font-family:-apple-system-body,ui-sans-serif,-apple-system,system-ui,"Segoe UI",Helvetica,"Apple Color Emoji",Arial,sans-serif,"Segoe UI Emoji","Segoe UI Symbol";font-size:12px;background:rgb(243, 243, 243);border:1px solid rgba(0, 0, 0, 0.1);border-radius:2px;pointer-events:none;z-index:100;}#chatgpt-mermaid-\_r_75l\_ .flowchartTitleText{text-anchor:middle;font-size:18px;fill:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_75l\_ rect.text{fill:none;stroke-width:0;}#chatgpt-mermaid-\_r_75l\_ .icon-shape,#chatgpt-mermaid-\_r_75l\_ .image-shape{background-color:rgb(252, 252, 252);text-align:center;}#chatgpt-mermaid-\_r_75l\_ .icon-shape p,#chatgpt-mermaid-\_r_75l\_ .image-shape p{background-color:rgb(252, 252, 252);padding:2px;}#chatgpt-mermaid-\_r_75l\_ .icon-shape .label rect,#chatgpt-mermaid-\_r_75l\_ .image-shape .label rect{opacity:0.5;background-color:rgb(252, 252, 252);fill:rgb(252, 252, 252);}#chatgpt-mermaid-\_r_75l\_ .label-icon{display:inline-block;height:1em;overflow:visible;vertical-align:-0.125em;}#chatgpt-mermaid-\_r_75l\_ .node .label-icon path{fill:currentColor;stroke:revert;stroke-width:revert;}#chatgpt-mermaid-\_r_75l\_ .node .neo-node{stroke:rgb(83, 154, 248);}#chatgpt-mermaid-\_r_75l\_ [data-look="neo"].node rect,#chatgpt-mermaid-\_r_75l\_ [data-look="neo"].cluster rect,#chatgpt-mermaid-\_r_75l\_ [data-look="neo"].node polygon{stroke:url(#chatgpt-mermaid-\_r_75l\_-gradient);filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-\_r_75l\_ [data-look="neo"].swimlane.cluster rect{filter:none;}#chatgpt-mermaid-\_r_75l\_ [data-look="neo"].node path{stroke:url(#chatgpt-mermaid-\_r_75l\_-gradient);stroke-width:1px;}#chatgpt-mermaid-\_r_75l\_ [data-look="neo"].node .outer-path{filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-\_r_75l\_ [data-look="neo"].node .neo-line path{stroke:rgb(83, 154, 248);filter:none;}#chatgpt-mermaid-\_r_75l\_ [data-look="neo"].node circle{stroke:url(#chatgpt-mermaid-\_r_75l\_-gradient);filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-\_r_75l\_ [data-look="neo"].node circle .state-start{fill:#000000;}#chatgpt-mermaid-\_r_75l\_ [data-look="neo"].icon-shape .icon{fill:url(#chatgpt-mermaid-\_r_75l\_-gradient);filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-\_r_75l\_ [data-look="neo"].icon-shape .icon-neo path{stroke:url(#chatgpt-mermaid-\_r_75l\_-gradient);filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-\_r_75l\_ .node text{font-size:14px;font-weight:600;letter-spacing:normal;fill:rgb(0, 79, 153);}#chatgpt-mermaid-\_r_75l\_ .edgeLabels text{font-size:13px;font-weight:600;letter-spacing:-0.08px;fill:rgb(0, 79, 153);}#chatgpt-mermaid-\_r_75l\_ .node tspan[font-weight="normal"],#chatgpt-mermaid-\_r_75l\_ .edgeLabels tspan[font-weight="normal"]{font-weight:600;}#chatgpt-mermaid-\_r_75l\_ .edgeLabel .label rect{opacity:1;rx:13px;ry:13px;fill:rgb(245, 250, 255);stroke:rgb(206, 219, 229);stroke-width:1px;}#chatgpt-mermaid-\_r_75l\_ .node rect,#chatgpt-mermaid-\_r_75l\_ .node circle,#chatgpt-mermaid-\_r_75l\_ .node ellipse,#chatgpt-mermaid-\_r_75l\_ .node polygon,#chatgpt-mermaid-\_r_75l\_ .node path{fill:rgb(229, 243, 255);stroke:rgba(0, 0, 0, 0.1);stroke-width:1px;}#chatgpt-mermaid-\_r_75l\_ .node rect{rx:16px;ry:16px;}#chatgpt-mermaid-\_r_75l\_ .mermaid-decision .label-container{fill:rgb(245, 250, 255);stroke:rgb(206, 219, 229);stroke-dasharray:2,2;}#chatgpt-mermaid-\_r_75l\_ .edgePaths .flowchart-link{stroke:rgb(143, 143, 143);stroke-width:1px;stroke-linecap:round;stroke-linejoin:round;}#chatgpt-mermaid-\_r_75l\_ .marker{fill:rgb(143, 143, 143);stroke:rgb(143, 143, 143);}#chatgpt-mermaid-\_r_75l\_ :root{--mermaid-font-family:-apple-system-body,ui-sans-serif,-apple-system,system-ui,"Segoe UI",Helvetica,"Apple Color Emoji",Arial,sans-serif,"Segoe UI Emoji","Segoe UI Symbol";}用户选择服装检查资产状态与授权读取 Manifest检查角色兼容性计算锚点和适配参数加载纹理与遮罩执行图层和遮挡规则实时渲染用户调整保存穿搭配置

### **21.12 服装系统验收标准**

- 每个服装资产都能独立加载和卸载。
- 服装可以绑定到指定角色。
- 服装可以调整位置、旋转和缩放。
- 支持多部位服装。
- 支持多件饰品叠加。
- 支持互斥和覆盖规则。
- 服装适配参数可以保存。
- 切换角色后可重新计算适配。
- 资产版本升级不会破坏历史穿搭。
- 资源加载失败时不会导致整个角色渲染模块崩溃。

## **二十二、分享、社区与授权技术规格**

### **22.1 分享对象拆分**

**[PRD 产品需求]**

分享对象分为：

1. 作品展示。
2. 角色展示。
3. 单件服装展示。
4. 单件饰品展示。
5. 整套穿搭方案。
6. 创作者作品集。

每种对象有独立的授权。

### **22.2 授权维度**

| 权限         | 含义     |
| ---------- | ------ |
| VIEW       | 允许浏览   |
| LIKE       | 允许点赞   |
| COMMENT    | 允许评论   |
| COLLECT    | 允许收藏   |
| REUSE      | 允许复用   |
| REMIX      | 允许二次创作 |
| DOWNLOAD   | 允许下载素材 |
| COMMERCIAL | 允许商业使用 |

不能只存一个 `is_public` 字段。

### **22.3 授权状态机**

\#chatgpt-mermaid-\_r_75s\_{font-family:-apple-system-body,ui-sans-serif,-apple-system,system-ui,"Segoe UI",Helvetica,"Apple Color Emoji",Arial,sans-serif,"Segoe UI Emoji","Segoe UI Symbol";font-size:16px;fill:rgb(13, 13, 13);}@keyframes edge-animation-frame{from{stroke-dashoffset:0;}}@keyframes dash{to{stroke-dashoffset:0;}}#chatgpt-mermaid-\_r_75s\_ .edge-animation-slow{stroke-dasharray:9,5!important;stroke-dashoffset:900;animation:dash 50s linear infinite;stroke-linecap:round;}#chatgpt-mermaid-\_r_75s\_ .edge-animation-fast{stroke-dasharray:9,5!important;stroke-dashoffset:900;animation:dash 20s linear infinite;stroke-linecap:round;}#chatgpt-mermaid-\_r_75s\_ .error-icon{fill:rgb(243, 243, 243);}#chatgpt-mermaid-\_r_75s\_ .error-text{fill:rgb(13, 13, 13);stroke:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_75s\_ .edge-thickness-normal{stroke-width:1px;}#chatgpt-mermaid-\_r_75s\_ .edge-thickness-thick{stroke-width:3.5px;}#chatgpt-mermaid-\_r_75s\_ .edge-pattern-solid{stroke-dasharray:0;}#chatgpt-mermaid-\_r_75s\_ .edge-thickness-invisible{stroke-width:0;fill:none;}#chatgpt-mermaid-\_r_75s\_ .edge-pattern-dashed{stroke-dasharray:3;}#chatgpt-mermaid-\_r_75s\_ .edge-pattern-dotted{stroke-dasharray:2;}#chatgpt-mermaid-\_r_75s\_ .marker{fill:rgb(143, 143, 143);stroke:rgb(143, 143, 143);}#chatgpt-mermaid-\_r_75s\_ .marker.cross{stroke:rgb(143, 143, 143);}#chatgpt-mermaid-\_r_75s\_ svg{font-family:-apple-system-body,ui-sans-serif,-apple-system,system-ui,"Segoe UI",Helvetica,"Apple Color Emoji",Arial,sans-serif,"Segoe UI Emoji","Segoe UI Symbol";font-size:16px;}#chatgpt-mermaid-\_r_75s\_ p{margin:0;}#chatgpt-mermaid-\_r_75s\_ defs [id$="-barbEnd"]{fill:rgb(143, 143, 143);stroke:rgb(143, 143, 143);}#chatgpt-mermaid-\_r_75s\_ g.stateGroup text{fill:rgb(83, 154, 248);stroke:none;font-size:10px;}#chatgpt-mermaid-\_r_75s\_ g.stateGroup text{fill:rgb(13, 13, 13);stroke:none;font-size:10px;}#chatgpt-mermaid-\_r_75s\_ g.stateGroup .state-title{font-weight:bolder;fill:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_75s\_ g.stateGroup rect{fill:rgb(222, 234, 251);stroke:rgb(83, 154, 248);}#chatgpt-mermaid-\_r_75s\_ g.stateGroup line{stroke:rgb(143, 143, 143);stroke-width:1;}#chatgpt-mermaid-\_r_75s\_ .transition{stroke:rgb(143, 143, 143);stroke-width:1;fill:none;}#chatgpt-mermaid-\_r_75s\_ .stateGroup .composit{fill:transparent;border-bottom:1px;}#chatgpt-mermaid-\_r_75s\_ .stateGroup .alt-composit{fill:#e0e0e0;border-bottom:1px;}#chatgpt-mermaid-\_r_75s\_ .state-note{stroke:rgb(107, 198, 127);fill:rgb(243, 243, 243);}#chatgpt-mermaid-\_r_75s\_ .state-note text{fill:rgb(13, 13, 13);stroke:none;font-size:10px;}#chatgpt-mermaid-\_r_75s\_ .stateLabel .box{stroke:none;stroke-width:0;fill:rgb(222, 234, 251);opacity:0.5;}#chatgpt-mermaid-\_r_75s\_ .edgeLabel .label rect{fill:rgb(222, 234, 251);opacity:0.5;}#chatgpt-mermaid-\_r_75s\_ .edgeLabel{background-color:rgb(252, 252, 252);text-align:center;}#chatgpt-mermaid-\_r_75s\_ .edgeLabel p{background-color:rgb(252, 252, 252);}#chatgpt-mermaid-\_r_75s\_ .edgeLabel rect{opacity:0.5;background-color:rgb(252, 252, 252);fill:rgb(252, 252, 252);}#chatgpt-mermaid-\_r_75s\_ .edgeLabel .label text{fill:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_75s\_ .label div .edgeLabel{color:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_75s\_ .stateLabel text{fill:rgb(13, 13, 13);font-size:10px;font-weight:bold;}#chatgpt-mermaid-\_r_75s\_ .node circle.state-start{fill:rgb(143, 143, 143);stroke:rgb(143, 143, 143);}#chatgpt-mermaid-\_r_75s\_ .node .fork-join{fill:rgb(143, 143, 143);stroke:rgb(143, 143, 143);}#chatgpt-mermaid-\_r_75s\_ .node circle.state-end{fill:rgb(83, 154, 248);stroke:transparent;stroke-width:1.5;}#chatgpt-mermaid-\_r_75s\_ .end-state-inner{fill:transparent;stroke-width:1.5;}#chatgpt-mermaid-\_r_75s\_ .node rect{fill:rgb(222, 234, 251);stroke:rgb(83, 154, 248);stroke-width:1px;}#chatgpt-mermaid-\_r_75s\_ .node polygon{fill:rgb(222, 234, 251);stroke:rgb(83, 154, 248);stroke-width:1px;}#chatgpt-mermaid-\_r_75s\_ [id$="-barbEnd"]{fill:rgb(143, 143, 143);}#chatgpt-mermaid-\_r_75s\_ .statediagram-cluster rect{fill:rgb(222, 234, 251);stroke:rgb(83, 154, 248);stroke-width:1px;}#chatgpt-mermaid-\_r_75s\_ .cluster-label,#chatgpt-mermaid-\_r_75s\_ .nodeLabel{color:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_75s\_ .statediagram-cluster rect.outer{rx:5px;ry:5px;}#chatgpt-mermaid-\_r_75s\_ .statediagram-state .divider{stroke:rgb(83, 154, 248);}#chatgpt-mermaid-\_r_75s\_ .statediagram-state .title-state{rx:5px;ry:5px;}#chatgpt-mermaid-\_r_75s\_ .statediagram-cluster.statediagram-cluster .inner{fill:transparent;}#chatgpt-mermaid-\_r_75s\_ .statediagram-cluster.statediagram-cluster-alt .inner{fill:rgb(243, 243, 243);}#chatgpt-mermaid-\_r_75s\_ .statediagram-cluster .inner{rx:0;ry:0;}#chatgpt-mermaid-\_r_75s\_ .statediagram-state rect.basic{rx:5px;ry:5px;}#chatgpt-mermaid-\_r_75s\_ .statediagram-state rect.divider{stroke-dasharray:10,10;fill:rgb(243, 243, 243);}#chatgpt-mermaid-\_r_75s\_ .note-edge{stroke-dasharray:5;}#chatgpt-mermaid-\_r_75s\_ .statediagram-note rect{fill:rgb(243, 243, 243);stroke:rgb(107, 198, 127);stroke-width:1px;rx:0;ry:0;}#chatgpt-mermaid-\_r_75s\_ .statediagram-note rect{fill:rgb(243, 243, 243);stroke:rgb(107, 198, 127);stroke-width:1px;rx:0;ry:0;}#chatgpt-mermaid-\_r_75s\_ .statediagram-note text{fill:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_75s\_ .statediagram-note .nodeLabel{color:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_75s\_ .statediagram .edgeLabel{color:red;}#chatgpt-mermaid-\_r_75s\_ [id$="-dependencyStart"],#chatgpt-mermaid-\_r_75s\_ [id$="-dependencyEnd"]{fill:rgb(143, 143, 143);stroke:rgb(143, 143, 143);stroke-width:1;}#chatgpt-mermaid-\_r_75s\_ .statediagramTitleText{text-anchor:middle;font-size:18px;fill:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_75s\_ [data-look="neo"].statediagram-cluster rect{fill:rgb(222, 234, 251);stroke:url(#chatgpt-mermaid-\_r_75s\_-gradient);stroke-width:1;}#chatgpt-mermaid-\_r_75s\_ [data-look="neo"].statediagram-cluster rect.outer{rx:5px;ry:5px;filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-\_r_75s\_ .node .neo-node{stroke:rgb(83, 154, 248);}#chatgpt-mermaid-\_r_75s\_ [data-look="neo"].node rect,#chatgpt-mermaid-\_r_75s\_ [data-look="neo"].cluster rect,#chatgpt-mermaid-\_r_75s\_ [data-look="neo"].node polygon{stroke:url(#chatgpt-mermaid-\_r_75s\_-gradient);filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-\_r_75s\_ [data-look="neo"].swimlane.cluster rect{filter:none;}#chatgpt-mermaid-\_r_75s\_ [data-look="neo"].node path{stroke:url(#chatgpt-mermaid-\_r_75s\_-gradient);stroke-width:1px;}#chatgpt-mermaid-\_r_75s\_ [data-look="neo"].node .outer-path{filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-\_r_75s\_ [data-look="neo"].node .neo-line path{stroke:rgb(83, 154, 248);filter:none;}#chatgpt-mermaid-\_r_75s\_ [data-look="neo"].node circle{stroke:url(#chatgpt-mermaid-\_r_75s\_-gradient);filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-\_r_75s\_ [data-look="neo"].node circle .state-start{fill:#000000;}#chatgpt-mermaid-\_r_75s\_ [data-look="neo"].icon-shape .icon{fill:url(#chatgpt-mermaid-\_r_75s\_-gradient);filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-\_r_75s\_ [data-look="neo"].icon-shape .icon-neo path{stroke:url(#chatgpt-mermaid-\_r_75s\_-gradient);filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-\_r_75s\_ :root{--mermaid-font-family:-apple-system-body,ui-sans-serif,-apple-system,system-ui,"Segoe UI",Helvetica,"Apple Color Emoji",Arial,sans-serif,"Segoe UI Emoji","Segoe UI Symbol";}PRIVATEPUBLIC_VIEWREUSE_ALLOWEDREMIX_ALLOWEDLICENSEDHIDDENREVOKEDEXPIRED

### **22.4 授权记录**

授权记录至少包含：

- 资产 ID。
- 资产版本。
- 授权主体。
- 使用主体。
- 授权类型。
- 授权范围。
- 是否允许商业使用。
- 是否允许二次创作。
- 是否允许下载原始素材。
- 授权开始时间。
- 授权结束时间。
- 撤销时间。
- 交易记录。
- 协议版本。

### **22.5 删除与撤销的区别**

| 操作       | 结果                 |
| -------- | ------------------ |
| 用户删除原始衣物 | 原始衣橱不再展示，进入删除流程    |
| 用户删除数字资产 | 不再允许新增穿戴，历史作品按快照处理 |
| 用户隐藏公开作品 | 停止公开展示             |
| 用户撤销免费复用 | 停止新的复用申请           |
| 用户撤销商业授权 | 按授权协议处理已有授权和交易     |
| 平台因侵权下架  | 停止展示和新增复用，保留必要审计记录 |

### **22.6 社区 Feed**

**[PRD 产品需求]**

Feed 分类：

- 推荐。
- 关注。
- 最新。
- 主题活动。
- 创作者。
- 角色展示。

推荐排序可以考虑：

- 发布时间。
- 用户兴趣。
- 互动质量。
- 内容质量。
- 主题相关性。
- 用户屏蔽和不感兴趣行为。

不得仅按点赞量排序，避免刷量和低质内容挤占推荐。

### **22.7 举报与治理**

举报类型：

- 违规内容。
- 色情或不适宜内容。
- 侵权。
- 冒充创作者。
- 盗用资产。
- 垃圾内容。
- 骚扰。
- 诈骗。
- 其他。

处理状态：

\#chatgpt-mermaid-\_r_763\_{font-family:-apple-system-body,ui-sans-serif,-apple-system,system-ui,"Segoe UI",Helvetica,"Apple Color Emoji",Arial,sans-serif,"Segoe UI Emoji","Segoe UI Symbol";font-size:16px;fill:rgb(13, 13, 13);}@keyframes edge-animation-frame{from{stroke-dashoffset:0;}}@keyframes dash{to{stroke-dashoffset:0;}}#chatgpt-mermaid-\_r_763\_ .edge-animation-slow{stroke-dasharray:9,5!important;stroke-dashoffset:900;animation:dash 50s linear infinite;stroke-linecap:round;}#chatgpt-mermaid-\_r_763\_ .edge-animation-fast{stroke-dasharray:9,5!important;stroke-dashoffset:900;animation:dash 20s linear infinite;stroke-linecap:round;}#chatgpt-mermaid-\_r_763\_ .error-icon{fill:rgb(243, 243, 243);}#chatgpt-mermaid-\_r_763\_ .error-text{fill:rgb(13, 13, 13);stroke:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_763\_ .edge-thickness-normal{stroke-width:1px;}#chatgpt-mermaid-\_r_763\_ .edge-thickness-thick{stroke-width:3.5px;}#chatgpt-mermaid-\_r_763\_ .edge-pattern-solid{stroke-dasharray:0;}#chatgpt-mermaid-\_r_763\_ .edge-thickness-invisible{stroke-width:0;fill:none;}#chatgpt-mermaid-\_r_763\_ .edge-pattern-dashed{stroke-dasharray:3;}#chatgpt-mermaid-\_r_763\_ .edge-pattern-dotted{stroke-dasharray:2;}#chatgpt-mermaid-\_r_763\_ .marker{fill:rgb(143, 143, 143);stroke:rgb(143, 143, 143);}#chatgpt-mermaid-\_r_763\_ .marker.cross{stroke:rgb(143, 143, 143);}#chatgpt-mermaid-\_r_763\_ svg{font-family:-apple-system-body,ui-sans-serif,-apple-system,system-ui,"Segoe UI",Helvetica,"Apple Color Emoji",Arial,sans-serif,"Segoe UI Emoji","Segoe UI Symbol";font-size:16px;}#chatgpt-mermaid-\_r_763\_ p{margin:0;}#chatgpt-mermaid-\_r_763\_ defs [id$="-barbEnd"]{fill:rgb(143, 143, 143);stroke:rgb(143, 143, 143);}#chatgpt-mermaid-\_r_763\_ g.stateGroup text{fill:rgb(83, 154, 248);stroke:none;font-size:10px;}#chatgpt-mermaid-\_r_763\_ g.stateGroup text{fill:rgb(13, 13, 13);stroke:none;font-size:10px;}#chatgpt-mermaid-\_r_763\_ g.stateGroup .state-title{font-weight:bolder;fill:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_763\_ g.stateGroup rect{fill:rgb(222, 234, 251);stroke:rgb(83, 154, 248);}#chatgpt-mermaid-\_r_763\_ g.stateGroup line{stroke:rgb(143, 143, 143);stroke-width:1;}#chatgpt-mermaid-\_r_763\_ .transition{stroke:rgb(143, 143, 143);stroke-width:1;fill:none;}#chatgpt-mermaid-\_r_763\_ .stateGroup .composit{fill:transparent;border-bottom:1px;}#chatgpt-mermaid-\_r_763\_ .stateGroup .alt-composit{fill:#e0e0e0;border-bottom:1px;}#chatgpt-mermaid-\_r_763\_ .state-note{stroke:rgb(107, 198, 127);fill:rgb(243, 243, 243);}#chatgpt-mermaid-\_r_763\_ .state-note text{fill:rgb(13, 13, 13);stroke:none;font-size:10px;}#chatgpt-mermaid-\_r_763\_ .stateLabel .box{stroke:none;stroke-width:0;fill:rgb(222, 234, 251);opacity:0.5;}#chatgpt-mermaid-\_r_763\_ .edgeLabel .label rect{fill:rgb(222, 234, 251);opacity:0.5;}#chatgpt-mermaid-\_r_763\_ .edgeLabel{background-color:rgb(252, 252, 252);text-align:center;}#chatgpt-mermaid-\_r_763\_ .edgeLabel p{background-color:rgb(252, 252, 252);}#chatgpt-mermaid-\_r_763\_ .edgeLabel rect{opacity:0.5;background-color:rgb(252, 252, 252);fill:rgb(252, 252, 252);}#chatgpt-mermaid-\_r_763\_ .edgeLabel .label text{fill:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_763\_ .label div .edgeLabel{color:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_763\_ .stateLabel text{fill:rgb(13, 13, 13);font-size:10px;font-weight:bold;}#chatgpt-mermaid-\_r_763\_ .node circle.state-start{fill:rgb(143, 143, 143);stroke:rgb(143, 143, 143);}#chatgpt-mermaid-\_r_763\_ .node .fork-join{fill:rgb(143, 143, 143);stroke:rgb(143, 143, 143);}#chatgpt-mermaid-\_r_763\_ .node circle.state-end{fill:rgb(83, 154, 248);stroke:transparent;stroke-width:1.5;}#chatgpt-mermaid-\_r_763\_ .end-state-inner{fill:transparent;stroke-width:1.5;}#chatgpt-mermaid-\_r_763\_ .node rect{fill:rgb(222, 234, 251);stroke:rgb(83, 154, 248);stroke-width:1px;}#chatgpt-mermaid-\_r_763\_ .node polygon{fill:rgb(222, 234, 251);stroke:rgb(83, 154, 248);stroke-width:1px;}#chatgpt-mermaid-\_r_763\_ [id$="-barbEnd"]{fill:rgb(143, 143, 143);}#chatgpt-mermaid-\_r_763\_ .statediagram-cluster rect{fill:rgb(222, 234, 251);stroke:rgb(83, 154, 248);stroke-width:1px;}#chatgpt-mermaid-\_r_763\_ .cluster-label,#chatgpt-mermaid-\_r_763\_ .nodeLabel{color:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_763\_ .statediagram-cluster rect.outer{rx:5px;ry:5px;}#chatgpt-mermaid-\_r_763\_ .statediagram-state .divider{stroke:rgb(83, 154, 248);}#chatgpt-mermaid-\_r_763\_ .statediagram-state .title-state{rx:5px;ry:5px;}#chatgpt-mermaid-\_r_763\_ .statediagram-cluster.statediagram-cluster .inner{fill:transparent;}#chatgpt-mermaid-\_r_763\_ .statediagram-cluster.statediagram-cluster-alt .inner{fill:rgb(243, 243, 243);}#chatgpt-mermaid-\_r_763\_ .statediagram-cluster .inner{rx:0;ry:0;}#chatgpt-mermaid-\_r_763\_ .statediagram-state rect.basic{rx:5px;ry:5px;}#chatgpt-mermaid-\_r_763\_ .statediagram-state rect.divider{stroke-dasharray:10,10;fill:rgb(243, 243, 243);}#chatgpt-mermaid-\_r_763\_ .note-edge{stroke-dasharray:5;}#chatgpt-mermaid-\_r_763\_ .statediagram-note rect{fill:rgb(243, 243, 243);stroke:rgb(107, 198, 127);stroke-width:1px;rx:0;ry:0;}#chatgpt-mermaid-\_r_763\_ .statediagram-note rect{fill:rgb(243, 243, 243);stroke:rgb(107, 198, 127);stroke-width:1px;rx:0;ry:0;}#chatgpt-mermaid-\_r_763\_ .statediagram-note text{fill:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_763\_ .statediagram-note .nodeLabel{color:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_763\_ .statediagram .edgeLabel{color:red;}#chatgpt-mermaid-\_r_763\_ [id$="-dependencyStart"],#chatgpt-mermaid-\_r_763\_ [id$="-dependencyEnd"]{fill:rgb(143, 143, 143);stroke:rgb(143, 143, 143);stroke-width:1;}#chatgpt-mermaid-\_r_763\_ .statediagramTitleText{text-anchor:middle;font-size:18px;fill:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_763\_ [data-look="neo"].statediagram-cluster rect{fill:rgb(222, 234, 251);stroke:url(#chatgpt-mermaid-\_r_763\_-gradient);stroke-width:1;}#chatgpt-mermaid-\_r_763\_ [data-look="neo"].statediagram-cluster rect.outer{rx:5px;ry:5px;filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-\_r_763\_ .node .neo-node{stroke:rgb(83, 154, 248);}#chatgpt-mermaid-\_r_763\_ [data-look="neo"].node rect,#chatgpt-mermaid-\_r_763\_ [data-look="neo"].cluster rect,#chatgpt-mermaid-\_r_763\_ [data-look="neo"].node polygon{stroke:url(#chatgpt-mermaid-\_r_763\_-gradient);filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-\_r_763\_ [data-look="neo"].swimlane.cluster rect{filter:none;}#chatgpt-mermaid-\_r_763\_ [data-look="neo"].node path{stroke:url(#chatgpt-mermaid-\_r_763\_-gradient);stroke-width:1px;}#chatgpt-mermaid-\_r_763\_ [data-look="neo"].node .outer-path{filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-\_r_763\_ [data-look="neo"].node .neo-line path{stroke:rgb(83, 154, 248);filter:none;}#chatgpt-mermaid-\_r_763\_ [data-look="neo"].node circle{stroke:url(#chatgpt-mermaid-\_r_763\_-gradient);filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-\_r_763\_ [data-look="neo"].node circle .state-start{fill:#000000;}#chatgpt-mermaid-\_r_763\_ [data-look="neo"].icon-shape .icon{fill:url(#chatgpt-mermaid-\_r_763\_-gradient);filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-\_r_763\_ [data-look="neo"].icon-shape .icon-neo path{stroke:url(#chatgpt-mermaid-\_r_763\_-gradient);filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-\_r_763\_ :root{--mermaid-font-family:-apple-system-body,ui-sans-serif,-apple-system,system-ui,"Segoe UI",Helvetica,"Apple Color Emoji",Arial,sans-serif,"Segoe UI Emoji","Segoe UI Symbol";}SUBMITTEDPENDING_REVIEWREVIEWINGCONFIRMEDREJECTEDCONTENT_HIDDENAPPEALINGRESTOREDREMOVED

平台必须保留举报理由、处理人、处理时间、证据引用和申诉结果。不能只提供一个举报按钮而没有后续治理闭环。

## **二十三、AI 服务与推荐系统技术规格**

### **23.1 AI 能力拆分**

| 能力     | 输入         | 输出    | 是否异步  |
| ------ | ---------- | ----- | ----- |
| 衣物分类   | 图片         | 分类、标签 | 可异步   |
| 图像质量检测 | 图片         | 质量评分  | 同步/异步 |
| 主体分割   | 图片         | Mask  | 异步    |
| 颜色识别   | 图片         | 颜色属性  | 同步    |
| 材质推测   | 图片         | 材质候选  | 同步    |
| 服装素材生成 | 图片、Mask、参数 | 贴图/资产 | 异步    |
| 锚点预测   | 服装素材       | 锚点位置  | 异步    |
| 搭配推荐   | 衣橱、角色、需求   | 资产组合  | 异步    |
| 生成解释   | 搭配方案       | 推荐理由  | 同步/异步 |
| 用户偏好更新 | 用户行为       | 偏好数据  | 异步    |

### **23.2 模型服务路由**

AI 服务不应将所有任务都交给同一个模型。

建议按照任务类型路由：

- 文件质量检测：轻量视觉模型或传统图像算法。
- 衣物分类：专用分类模型或视觉模型。
- 主体分割：分割模型。
- 颜色提取：图像处理算法与视觉模型组合。
- 材质推测：视觉模型，输出候选及置信度。
- 自然语言需求理解：LLM。
- 搭配候选筛选：规则引擎。
- 搭配排序：规则评分与模型排序组合。
- 生成式素材处理：图像生成模型。
- 生成结果质量检测：视觉质量模型 + 人工抽检。

路由策略需要支持：

1. 模型供应商配置化。
2. 模型版本记录。
3. 超时切换。
4. 限流处理。
5. 成本统计。
6. 输出格式验证。
7. 灰度模型实验。
8. 模型下线和回滚。

### **23.3 AI 任务通用数据结构**

```
{
  "taskId": "TASK_001",
  "taskType": "GARMENT_GENERATION",
  "status": "RUNNING",
  "userId": "USER_001",
  "inputRefs": ["MEDIA_001"],
  "model": {
    "provider": "configured_provider",
    "modelId": "configured_model",
    "version": "1.0"
  },
  "progress": {
    "stage": "SEGMENTATION",
    "percent": 35
  },
  "retryCount": 0,
  "maxRetries": 3,
  "createdAt": "2026-11-13T10:00:00Z"
}
```

### **23.4 任务队列**

任务建议分队列：

- `image-security`
- `image-moderation`
- `image-recognition`
- `image-segmentation`
- `garment-generation`
- `garment-fitting`
- `outfit-recommendation`
- `outfit-render`
- `content-moderation`

不同任务采用不同超时和重试策略。

| 任务    | 超时策略  | 重试策略      |
| ----- | ----- | --------- |
| 图片审核  | 短超时   | 有限退避重试    |
| 分类识别  | 中等超时  | 有限重试      |
| 图片分割  | 中等超时  | 失败重试      |
| 服装生成  | 较长超时  | 检查任务状态后重试 |
| 角色渲染  | 客户端超时 | 本地恢复      |
| AI 搭配 | 中等超时  | 幂等重试      |

### **23.5 AI 失败处理**

所有任务必须区分：

- 用户取消。
- 输入不合法。
- 内容审核拒绝。
- 供应商超时。
- 模型服务限流。
- 模型服务异常。
- 输出格式错误。
- 质量检查失败。
- 资源存储失败。
- 数据库保存失败。

不能将这些全部显示为“生成失败”。

### **23.6 AI 输出结构校验**

LLM 返回结果必须通过 JSON Schema 校验。

```
{
  "type": "object",
  "required": ["recommendations"],
  "properties": {
    "recommendations": {
      "type": "array",
      "items": {
        "type": "object",
        "required": ["items", "reason"],
        "properties": {
          "items": {
            "type": "array",
            "items": {
              "type": "object",
              "required": ["garmentAssetId", "slot"],
              "properties": {
                "garmentAssetId": {"type": "string"},
                "slot": {"type": "string"}
              }
            }
          },
          "reason": {"type": "string"}
        }
      }
    }
  }
}
```

Schema 校验通过也不代表资产有效，仍需执行数据库存在性、用户权限、授权状态、部位兼容性和穿搭冲突校验。

## **二十四、完整异常场景与边界条件**

### **24.1 用户与账号**

| ID          | 场景        | 预期处理             |
| ----------- | --------- | ---------------- |
| EX-USER-001 | 注册时网络中断   | 不产生半完成账号；允许重试    |
| EX-USER-002 | 邮箱重复注册    | 返回明确错误           |
| EX-USER-003 | 登录态过期     | 保存未提交编辑状态，要求重新登录 |
| EX-USER-004 | 用户被禁用     | 阻止写操作，说明账号状态     |
| EX-USER-005 | 用户删除账号    | 进入账号删除与关联资产处理流程  |
| EX-USER-006 | 用户多设备同时操作 | 使用版本号避免覆盖        |
| EX-USER-007 | 用户切换账号    | 清理前一账号的本地私有缓存    |
| EX-USER-008 | 用户修改昵称    | 不影响资产所有权         |

### **24.2 衣物上传**

| ID        | 场景           | 预期处理          |
| --------- | ------------ | ------------- |
| EX-UP-001 | 文件格式不支持      | 拒绝上传          |
| EX-UP-002 | 文件损坏         | 拒绝并提示重新选择     |
| EX-UP-003 | 文件过大         | 前后端双重限制       |
| EX-UP-004 | 图片分辨率过低      | 提示补拍          |
| EX-UP-005 | 图片模糊         | 质量检测失败        |
| EX-UP-006 | 衣物被遮挡        | 提示重新拍摄或人工处理   |
| EX-UP-007 | 背景和衣服颜色相近    | 提示更换背景        |
| EX-UP-008 | 同一衣物重复上传     | 提示重复，不重复扣费    |
| EX-UP-009 | 用户上传中取消      | 取消任务并清理临时文件   |
| EX-UP-010 | 上传成功但数据库写入失败 | 补偿清理或恢复任务     |
| EX-UP-011 | 数据库成功但对象存储失败 | 不得标记上传成功      |
| EX-UP-012 | 审核服务超时       | 阻断后续模型处理      |
| EX-UP-013 | 审核服务返回未知状态   | 进入待复核         |
| EX-UP-014 | 用户删除审核中的图片   | 删除任务优先级高于普通回调 |
| EX-UP-015 | 图片含二维码       | 不自动访问外部链接     |
| EX-UP-016 | 图片含个人信息      | 提示用户遮挡并按策略处理  |

### **24.3 衣物识别与素材生成**

| ID        | 场景           | 预期处理           |
| --------- | ------------ | -------------- |
| EX-AI-001 | 连衣裙识别为上装     | 用户可修改，保留修正记录   |
| EX-AI-002 | 一张图片包含多件衣物   | 提示选择目标物体或分别创建  |
| EX-AI-003 | 衣物颜色识别错误     | 用户可手动调整        |
| EX-AI-004 | 材质无法识别       | 标记未知，不编造       |
| EX-AI-005 | 识别模型无响应      | 有限重试，允许手动录入    |
| EX-AI-006 | 分割边缘残缺       | 允许人工修正或重新处理    |
| EX-AI-007 | 衣物图案被 AI 改写  | 质量检查失败，保留原始图案  |
| EX-AI-008 | 背面生成与真实衣服不一致 | 标记为估算视图        |
| EX-AI-009 | 生成任务超时       | 显示可恢复任务状态      |
| EX-AI-010 | 生成服务限流       | 排队或稍后重试        |
| EX-AI-011 | 生成结果为空       | 不创建 READY 资产   |
| EX-AI-012 | 生成结果格式损坏     | 拒绝入库           |
| EX-AI-013 | 生成完成但保存失败    | 任务补偿，避免重复扣费    |
| EX-AI-014 | 生成结果被用户拒绝    | 保留原始衣物，允许重新生成  |
| EX-AI-015 | 用户编辑时任务完成    | 通过版本号避免覆盖编辑    |
| EX-AI-016 | 多次点击生成       | 同一幂等键只产生一个有效任务 |

### **24.4 角色系统**

| ID        | 场景               | 预期处理          |
| --------- | ---------------- | ------------- |
| EX-AV-001 | 创建角色时退出          | 未保存配置不生成正式角色  |
| EX-AV-002 | 角色模型加载失败         | 显示默认占位预览并允许重试 |
| EX-AV-003 | 身材参数越界           | 服务端拒绝或规范化     |
| EX-AV-004 | 多个滑块同时变化         | 使用节流/合并更新     |
| EX-AV-005 | 用户未保存就切换角色       | 弹出保存、放弃或取消    |
| EX-AV-006 | 角色删除但穿搭仍引用       | 按引用策略处理       |
| EX-AV-007 | Morph Target 不存在 | 禁用对应控制项       |
| EX-AV-008 | 角色模型版本更新         | 兼容迁移，不丢失外观    |
| EX-AV-009 | 渲染设备不支持          | 降级展示          |
| EX-AV-010 | 角色参数保存失败         | 保留本地编辑状态      |

### **24.5 换装系统**

| ID        | 场景          | 预期处理          |
| --------- | ----------- | ------------- |
| EX-DR-001 | 服装资产不存在     | 不加载并提示        |
| EX-DR-002 | 服装已被删除      | 历史穿搭显示快照或缺失提示 |
| EX-DR-003 | 服装无锚点       | 禁止正式穿戴        |
| EX-DR-004 | 服装不适配角色     | 提示不兼容或允许有限调整  |
| EX-DR-005 | 同槽位添加两件服装   | 默认替换并允许撤销     |
| EX-DR-006 | 外套遮挡内搭      | 按遮挡规则显示       |
| EX-DR-007 | 帽子与发型冲突     | 自动调整或提示       |
| EX-DR-008 | 饰品位置悬浮      | 自动吸附或允许手动调整   |
| EX-DR-009 | 用户将服装拖出可视区域 | 限制边界或提供重置     |
| EX-DR-010 | 渲染过程中切换角色   | 取消旧任务，加载新上下文  |
| EX-DR-011 | 服装贴图加载失败    | 显示资源异常状态      |
| EX-DR-012 | 多件服装同时加载    | 分批加载，避免卡顿     |
| EX-DR-013 | 用户连续撤销/重做   | 使用操作历史        |
| EX-DR-014 | 穿搭保存时网络中断   | 保留本地草稿        |
| EX-DR-015 | 同一穿搭多设备修改   | 使用版本号解决冲突     |

### **24.6 AI 搭配**

| ID         | 场景            | 预期处理           |
| ---------- | ------------- | -------------- |
| EX-REC-001 | 用户衣橱为空        | 引导添加衣物         |
| EX-REC-002 | 没有满足条件的服装     | 明确告知，无虚构推荐     |
| EX-REC-003 | 用户要求不存在的衣物    | 说明缺少该类资产       |
| EX-REC-004 | LLM 返回非法资产 ID | 服务端校验并拒绝       |
| EX-REC-005 | LLM 输出格式错误    | 重新生成或降级        |
| EX-REC-006 | 推荐结果违反互斥规则    | 规则引擎过滤         |
| EX-REC-007 | 推荐结果使用无授权资产   | 拒绝应用           |
| EX-REC-008 | 天气接口不可用       | 允许不依赖天气的推荐     |
| EX-REC-009 | 用户中途取消        | 取消可取消任务        |
| EX-REC-010 | 推荐任务超时        | 保留任务状态并允许重试    |
| EX-REC-011 | 用户拒绝推荐        | 记录反馈，不强制更新长期画像 |
| EX-REC-012 | 用户切换角色        | 重新按当前角色生成推荐    |

### **24.7 分享与社区**

| ID        | 场景        | 预期处理          |
| --------- | --------- | ------------- |
| EX-SH-001 | 用户公开私有衣物  | 明确提示公开范围      |
| EX-SH-002 | 作品公开但资产私有 | 只允许展示快照       |
| EX-SH-003 | 用户撤销复用授权  | 停止新增复用        |
| EX-SH-004 | 作者删除原始资产  | 历史作品按授权和快照处理  |
| EX-SH-005 | 作品被举报     | 进入审核队列        |
| EX-SH-006 | 用户恶意刷赞    | 风控限制          |
| EX-SH-007 | 评论包含违规内容  | 审核和隐藏         |
| EX-SH-008 | 用户被拉黑     | 双向互动按规则限制     |
| EX-SH-009 | 创作者账号被封禁  | 停止新增交易和授权     |
| EX-SH-010 | 用户复用无效资产  | 拒绝复用          |
| EX-SH-011 | 授权记录缺失    | 默认不允许复用       |
| EX-SH-012 | 作品发布审核失败  | 保持草稿，不进入 Feed |

## **二十五、测试计划与验收标准**

### **25.1 测试层级**

| 测试层级    | 测试对象              | 责任角色   |
| ------- | ----------------- | ------ |
| 单元测试    | 分类规则、参数校验、授权计算    | 开发     |
| 集成测试    | API、数据库、对象存储、任务队列 | 开发/测试  |
| AI 质量测试 | 分类、分割、生成、推荐       | AI/算法  |
| 渲染测试    | 角色、锚点、图层、遮挡       | 3D/客户端 |
| 端到端测试   | 上传到穿搭保存完整链路       | QA     |
| 安全测试    | 越权、文件伪装、审核绕过      | 安全/QA  |
| 性能测试    | 渲染、上传、任务并发        | QA/运维  |
| 兼容性测试   | 不同设备、系统、屏幕尺寸      | QA     |
| 用户验收测试  | 核心体验和可用性          | 产品/业务  |

### **25.2 核心端到端测试用例**

| Case ID | 测试步骤          | 预期结果              | 优先级 |
| ------- | ------------- | ----------------- | --- |
| E2E-001 | 注册账号并创建角色     | 角色创建成功            | P0  |
| E2E-002 | 上传合法上衣照片      | 上传进入处理流程          | P0  |
| E2E-003 | 上传非图片文件伪装 JPG | 被拒绝               | P0  |
| E2E-004 | 上传审核未通过图片     | 不进入识别和生成          | P0  |
| E2E-005 | 图片质量合格并完成识别   | 用户确认页正确展示         | P0  |
| E2E-006 | 修改 AI 分类后保存   | 用户确认结果生效          | P0  |
| E2E-007 | 生成服装数字资产      | 资产生成成功并有 Manifest | P0  |
| E2E-008 | 将服装穿到角色上      | 角色正确展示服装          | P0  |
| E2E-009 | 调整角色身材        | 服装按规则重新适配         | P0  |
| E2E-010 | 保存穿搭并退出重进     | 穿搭状态正确恢复          | P0  |
| E2E-011 | AI 根据衣橱推荐三套方案 | 仅使用真实资产           | P0  |
| E2E-012 | AI 推荐应用到角色    | 正确完成渲染            | P0  |
| E2E-013 | 发布公开穿搭作品      | 公开作品可浏览           | P1  |
| E2E-014 | 作品仅展示不允许复用    | 其他用户不能添加资产        | P0  |
| E2E-015 | 允许免费复用        | 其他用户按授权复用         | P1  |
| E2E-016 | 用户撤销授权        | 新复用被阻止            | P0  |
| E2E-017 | 用户删除衣物        | 按规则处理历史穿搭         | P0  |
| E2E-018 | AI 服务超时       | 有明确状态和重试          | P0  |
| E2E-019 | 对象存储失败        | 不出现假成功状态          | P0  |
| E2E-020 | 用户尝试读取他人私有资产  | 服务端拒绝             | P0  |

### **25.3 AI 质量验收**

建议建立独立的标准测试数据集。

测试数据至少覆盖：

- 不同服装类别。
- 不同拍摄角度。
- 不同背景。
- 不同光照。
- 不同颜色。
- 不同材质。
- 复杂图案。
- 透明材质。
- 多件衣物重叠。
- 衣物部分遮挡。
- 低分辨率。
- 高分辨率。
- 复杂边缘。

建议分为训练/调优数据、验证数据和独立测试数据，避免同一图片同时参与调优和最终验收。

| 能力 | 指标                        | 验收方式      |
| -- | ------------------------- | --------- |
| 分类 | Top-1 Accuracy / Macro-F1 | 人工标注集     |
| 分割 | IoU / Dice                | 标注 Mask   |
| 颜色 | 主色准确率                     | 人工标注      |
| 材质 | 分类准确率                     | 人工标注      |
| 锚点 | 平均定位误差                    | 标注锚点      |
| 生成 | 纹理保真、轮廓保真                 | 人工评审 + 指标 |
| 适配 | 穿模率、悬浮率                   | 标准角色测试    |
| 推荐 | 采纳率、保存率                   | 线上行为      |

上线门槛不应只看模型内部评分，应结合人工抽样验收。

### **25.4 角色与服装视觉验收**

建立标准组合矩阵：

| 角色体型 | 上装 | 下装 | 连衣裙 | 外套 | 饰品 |
| ---- | -- | -- | --- | -- | -- |
| 纤细型  | 必测 | 必测 | 必测  | 必测 | 必测 |
| 标准型  | 必测 | 必测 | 必测  | 必测 | 必测 |
| 丰满型  | 必测 | 必测 | 必测  | 必测 | 必测 |
| 娇小型  | 必测 | 必测 | 必测  | 必测 | 必测 |
| 高挑型  | 必测 | 必测 | 必测  | 必测 | 必测 |

每个组合至少验证：

- 正面。
- 左侧。
- 右侧。
- 轻微旋转。
- 角色身材变化。
- 服装缩放。
- 服装移动。
- 多件叠穿。
- 保存和恢复。

### **25.5 测试追踪矩阵**

每一项需求必须能追踪到：

- 页面 ID。
- API。
- 数据表。
- 测试用例。
- 缺陷记录。
- 验收结论。

### **25.6 上线门槛**

以下任意一项未满足，不得将对应功能标记为可上线：

- 私有资产存在跨用户读取漏洞。
- 上传审核能够被绕过。
- 未审核图片进入生成模型。
- AI 能够使用不存在或无权使用的资产。
- 资产授权失效后仍可新增复用。
- 删除用户数据后，相关资源长期残留且无处理记录。
- 角色和服装渲染会导致客户端持续崩溃。
- 任务失败后可能重复扣费。
- 数据库和对象存储状态不一致且没有补偿机制。
- 核心 E2E P0 用例未通过。

## **二十六、非功能需求与系统质量标准**

### **26.1 性能**

| 指标         | 建议目标            |
| ---------- | --------------- |
| 常规 API P95 | 小于 500ms，外部依赖除外 |
| 列表分页       | 常规场景 1 秒内       |
| 上传反馈       | 立即展示上传状态        |
| 角色初始展示     | 3—5 秒目标         |
| 已缓存角色切换    | 1 秒目标           |
| 换装操作响应     | 100ms 级交互目标     |
| 图片识别       | 以实际模型压测设定 SLA   |
| 素材生成       | 异步执行，不阻塞主界面     |
| AI 搭配      | 支持任务状态与超时恢复     |

### **26.2 可用性**

- 网络中断后允许恢复。
- 异步任务不依赖页面一直打开。
- 客户端关闭后任务仍可继续或进入可恢复状态。
- 服务端重启后任务状态可恢复。
- 任务重复回调不产生重复资产。
- 失败任务不会长期停留在处理中。
- 重要操作提供撤销或恢复机制。

### **26.3 安全**

- 所有私有资源默认鉴权。
- 对象存储不开放任意公共写入。
- 文件上传执行服务端验证。
- API 执行资源级权限检查。
- 管理员操作必须审计。
- AI 服务凭证只保存在服务端。
- 用户上传文件采用随机对象名。
- 防止路径穿越和文件伪装。
- 限制图片尺寸和解码资源。
- 审核和生成任务之间有状态门禁。
- 重要接口有频率限制。

### **26.4 隐私**

- 身材和现实身体数据默认私有。
- 不强制用户填写现实三围。
- 用户可删除衣物、角色、作品和账号。
- 公开作品不自动公开原始衣物图片。
- 不默认把用户资产用于模型训练。
- 用户可查看授权状态。
- 用户可以撤销非必要授权。
- 数据删除流程覆盖缓存、对象存储和搜索索引。

### **26.5 兼容性**

重点测试：

- iOS 不同系统版本。
- Android 不同系统版本。
- 不同屏幕比例。
- 高刷新率与普通刷新率。
- 低内存设备。
- WebGL 能力差异。
- 网络质量差异。
- 前后台切换。
- 长时间渲染。
- 多次角色切换。

### **26.6 可观测性**

必须有：

- API 日志。
- AI 任务日志。
- 上传任务日志。
- 审核事件日志。
- 角色渲染错误日志。
- 资源加载失败日志。
- 资产授权审计日志。
- 关键业务埋点。
- 错误告警。
- 成本监控。

日志不得包含用户密码、AccessKey、完整签名 URL、非必要个人信息或未脱敏的私密内容。

## **二十七、后台管理与运营系统**

### **27.1 后台模块**

| 模块      | 功能            |
| ------- | ------------- |
| 用户管理    | 用户查询、账号状态、封禁  |
| 角色管理    | 角色查询、违规角色处理   |
| 衣物资产管理  | 查看资产状态、处理失败资产 |
| 上传任务管理  | 上传状态、异常任务     |
| AI 任务管理 | 模型任务、重试、失败原因  |
| 内容审核    | 作品审核、举报、申诉    |
| 资产审核    | 服装素材和版权审核     |
| 授权管理    | 授权状态、撤销、交易记录  |
| 会员管理    | 会员权益、额度、订阅状态  |
| 活动管理    | 主题挑战、活动素材     |
| 数据分析    | 上传、生成、穿搭、分享指标 |
| 系统配置    | 模型、阈值、任务配置    |

### **27.2 后台权限**

建议 RBAC：

- `SUPER_ADMIN`
- `OPS_ADMIN`
- `CONTENT_REVIEWER`
- `ASSET_REVIEWER`
- `CUSTOMER_SUPPORT`
- `DATA_ANALYST`

不同角色只能查看和操作职责范围内的数据。

### **27.3 人工复核工作台**

需要支持：

- 待复核任务列表。
- 图片预览。
- AI 识别结果。
- 风险标签。
- 资产生成结果。
- 通过。
- 拒绝。
- 要求重新处理。
- 复核理由。
- 操作历史。

所有人工复核结果必须记录操作者、时间和理由。

### **27.4 任务管理**

后台应能查看：

- 当前排队任务数。
- 运行中任务数。
- 失败任务数。
- 超时任务数。
- 平均执行时间。
- 供应商异常。
- 重试次数。
- 任务成本。

管理员不能通过后台任意修改任务状态绕过审核和资产校验。

## **二十八、商业化与权益系统研发规格**

### **28.1 商业化原则**

沿用原始产品规划的商业模式，不改变免费版、会员订阅、虚拟服饰商城、创作者市场、角色装扮包、AI 高级服务、品牌合作和电商导购的方向。

V1.0 重点把会员、额度和交易所需的数据结构提前设计好，不要求首期全部上线。

### **28.2 会员权益模型**

建议采用配置化权益，而不是在代码中写死会员等级。

| 权益     | 免费用户   | 会员用户 | 高级会员（预留） |
| ------ | ------ | ---- | -------- |
| 基础衣橱   | 基础额度   | 扩展额度 | 更高额度     |
| 角色数量   | 限量     | 更多角色 | 更多角色     |
| 基础换装   | 支持     | 支持   | 支持       |
| AI 搭配  | 每日有限次数 | 更高额度 | 更高额度     |
| 服装素材生成 | 有限额度   | 更多额度 | 更高额度     |
| 高级角色定制 | 基础功能   | 高级功能 | 完整功能     |
| 穿搭记录   | 支持     | 支持   | 支持       |
| 分享模板   | 基础模板   | 高级模板 | 高级模板     |
| 高清渲染   | 基础规格   | 高规格  | 更高规格     |

具体数量、价格、额度需要通过成本测算和用户实验确定，本 PRD 不提前虚构商业指标。

### **28.3 权益数据结构**

建议新增：

- `membership_plans`
- `user_subscriptions`
- `membership_entitlements`
- `usage_quotas`
- `usage_records`
- `billing_orders`
- `refund_records`

额度记录示例：

```
{
  "userId": "USER_001",
  "entitlement": "GARMENT_GENERATION",
  "period": "2026-11",
  "quota": 30,
  "used": 8,
  "reserved": 1,
  "remaining": 21
}
```

### **28.4 额度扣减规则**

1. 用户发起任务时先检查可用额度。
2. 创建任务成功后预占额度。
3. 任务成功后正式扣减。
4. 任务失败且符合退款规则时释放预占额度。
5. 用户主动取消时按任务实际阶段执行规则。
6. 同一个幂等任务不能重复扣减。
7. 退款、补偿和人工调整必须有审计记录。

### **28.5 商业化异常**

| 场景          | 处理                   |
| ----------- | -------------------- |
| 会员到期        | 按规则限制新增权益，不删除历史资产    |
| 订阅支付成功但回调失败 | 支付对账和补偿              |
| 重复支付回调      | 幂等处理                 |
| 退款          | 回收未使用权益，历史已消耗服务按协议处理 |
| 生成失败        | 按规则退还额度              |
| 用户取消订阅      | 权益持续到有效期结束或按渠道规则处理   |
| 会员升级        | 按差价或剩余周期规则计算         |
| 会员降级        | 不删除超出额度的已有资产，限制新增操作  |

## **二十九、版本规划与研发排期拆分**

### **29.1 版本关系**

保留 V0.1、V1.0、V1.5、V2.0 规划，并补充每阶段的研发交付物和验收条件。

| 阶段        | 目标        | 主要交付                        |
| --------- | --------- | --------------------------- |
| V0.1 技术验证 | 证明技术路线可行  | 角色 Demo、衣物数字化 Demo、换装 Demo  |
| V1.0 MVP  | 核心产品可用    | 个人衣橱、角色、上传、2.5D 资产、换装、AI 搭配 |
| V1.5 社区生态 | 用户创作和内容流动 | Feed、关注、分享、授权、主题活动          |
| V2.0 资产经济 | 创作者和商业生态  | 商城、交易、原创工具、品牌合作             |

### **29.2 V0.1 PoC 必须完成的验证**

**PoC-A：角色系统**

- 导入一个基础角色模型。
- 支持至少一组脸部参数。
- 支持至少一组身材参数。
- 支持角色保存与恢复。
- 支持基础骨骼和挂载点。

**PoC-B：服装资产**

- 上传真实衣物照片。
- 完成主体分割。
- 生成透明背景素材。
- 生成 Manifest。
- 支持上装、下装、鞋子、饰品等基本分类。

**PoC-C：换装引擎**

- 角色穿戴至少四种类型服装。
- 支持多个饰品叠加。
- 支持调整位置、缩放和层级。
- 支持保存和恢复。
- 验证至少三种身材下的适配效果。

**PoC-D：AI 搭配**

- 从真实衣橱读取候选资产。
- 根据场景生成搭配方案。
- 校验资产 ID。
- 在渲染引擎中实际执行换装。
- 保存用户反馈。

### **29.3 V1.0 研发任务拆分**

| 研发模块  | 主要工作              | 优先级 |
| ----- | ----------------- | --- |
| 账号系统  | 登录、注册、个人资料、鉴权     | P0  |
| 角色系统  | 角色创建、外观、身材配置      | P0  |
| 衣橱系统  | 分类、搜索、详情、编辑       | P0  |
| 上传服务  | 文件上传、安全检查、存储      | P0  |
| 审核服务  | 图片审核、人工复核         | P0  |
| AI 识别 | 分类、颜色、标签、置信度      | P0  |
| 素材生产  | 分割、贴图、资产 Manifest | P0  |
| 换装引擎  | 锚点、图层、适配、渲染       | P0  |
| 穿搭系统  | 保存、历史、恢复          | P0  |
| AI 搭配 | 需求理解、规则过滤、推荐      | P0  |
| 分享系统  | 作品展示、私有和公开权限      | P1  |
| 社区    | Feed、点赞、收藏、评论     | P1  |
| 商业化   | 会员、额度、订阅          | P1  |
| 创作者市场 | 交易、授权、结算          | P2  |

### **29.4 研发依赖关系**

\#chatgpt-mermaid-\_r_76p\_{font-family:-apple-system-body,ui-sans-serif,-apple-system,system-ui,"Segoe UI",Helvetica,"Apple Color Emoji",Arial,sans-serif,"Segoe UI Emoji","Segoe UI Symbol";font-size:16px;fill:rgb(13, 13, 13);}@keyframes edge-animation-frame{from{stroke-dashoffset:0;}}@keyframes dash{to{stroke-dashoffset:0;}}#chatgpt-mermaid-\_r_76p\_ .edge-animation-slow{stroke-dasharray:9,5!important;stroke-dashoffset:900;animation:dash 50s linear infinite;stroke-linecap:round;}#chatgpt-mermaid-\_r_76p\_ .edge-animation-fast{stroke-dasharray:9,5!important;stroke-dashoffset:900;animation:dash 20s linear infinite;stroke-linecap:round;}#chatgpt-mermaid-\_r_76p\_ .error-icon{fill:rgb(243, 243, 243);}#chatgpt-mermaid-\_r_76p\_ .error-text{fill:rgb(13, 13, 13);stroke:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_76p\_ .edge-thickness-normal{stroke-width:1px;}#chatgpt-mermaid-\_r_76p\_ .edge-thickness-thick{stroke-width:3.5px;}#chatgpt-mermaid-\_r_76p\_ .edge-pattern-solid{stroke-dasharray:0;}#chatgpt-mermaid-\_r_76p\_ .edge-thickness-invisible{stroke-width:0;fill:none;}#chatgpt-mermaid-\_r_76p\_ .edge-pattern-dashed{stroke-dasharray:3;}#chatgpt-mermaid-\_r_76p\_ .edge-pattern-dotted{stroke-dasharray:2;}#chatgpt-mermaid-\_r_76p\_ .marker{fill:rgb(143, 143, 143);stroke:rgb(143, 143, 143);}#chatgpt-mermaid-\_r_76p\_ .marker.cross{stroke:rgb(143, 143, 143);}#chatgpt-mermaid-\_r_76p\_ svg{font-family:-apple-system-body,ui-sans-serif,-apple-system,system-ui,"Segoe UI",Helvetica,"Apple Color Emoji",Arial,sans-serif,"Segoe UI Emoji","Segoe UI Symbol";font-size:16px;}#chatgpt-mermaid-\_r_76p\_ p{margin:0;}#chatgpt-mermaid-\_r_76p\_ .label{font-family:-apple-system-body,ui-sans-serif,-apple-system,system-ui,"Segoe UI",Helvetica,"Apple Color Emoji",Arial,sans-serif,"Segoe UI Emoji","Segoe UI Symbol";color:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_76p\_ .cluster-label text{fill:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_76p\_ .cluster-label span{color:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_76p\_ .cluster-label span p{background-color:transparent;}#chatgpt-mermaid-\_r_76p\_ .label text,#chatgpt-mermaid-\_r_76p\_ span{fill:rgb(13, 13, 13);color:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_76p\_ .node rect,#chatgpt-mermaid-\_r_76p\_ .node circle,#chatgpt-mermaid-\_r_76p\_ .node ellipse,#chatgpt-mermaid-\_r_76p\_ .node polygon,#chatgpt-mermaid-\_r_76p\_ .node path{fill:rgb(222, 234, 251);stroke:rgb(83, 154, 248);stroke-width:1px;}#chatgpt-mermaid-\_r_76p\_ .rough-node .label text,#chatgpt-mermaid-\_r_76p\_ .node .label text,#chatgpt-mermaid-\_r_76p\_ .image-shape .label,#chatgpt-mermaid-\_r_76p\_ .icon-shape .label{text-anchor:middle;}#chatgpt-mermaid-\_r_76p\_ .node .katex path{fill:#000;stroke:#000;stroke-width:1px;}#chatgpt-mermaid-\_r_76p\_ .rough-node .label,#chatgpt-mermaid-\_r_76p\_ .node .label,#chatgpt-mermaid-\_r_76p\_ .image-shape .label,#chatgpt-mermaid-\_r_76p\_ .icon-shape .label{text-align:center;}#chatgpt-mermaid-\_r_76p\_ .node.clickable{cursor:pointer;}#chatgpt-mermaid-\_r_76p\_ .root .anchor path{fill:rgb(143, 143, 143)!important;stroke-width:0;stroke:rgb(143, 143, 143);}#chatgpt-mermaid-\_r_76p\_ .arrowheadPath{fill:rgb(143, 143, 143);}#chatgpt-mermaid-\_r_76p\_ .edgePath .path{stroke:rgb(143, 143, 143);stroke-width:1px;}#chatgpt-mermaid-\_r_76p\_ .flowchart-link{stroke:rgb(143, 143, 143);fill:none;}#chatgpt-mermaid-\_r_76p\_ .edgeLabel{background-color:rgb(252, 252, 252);text-align:center;}#chatgpt-mermaid-\_r_76p\_ .edgeLabel p{background-color:rgb(252, 252, 252);}#chatgpt-mermaid-\_r_76p\_ .edgeLabel rect{opacity:0.5;background-color:rgb(252, 252, 252);fill:rgb(252, 252, 252);}#chatgpt-mermaid-\_r_76p\_ .labelBkg{background-color:rgba(252, 252, 252, 0.5);}#chatgpt-mermaid-\_r_76p\_ .cluster rect{fill:rgb(243, 243, 243);stroke:rgba(0, 0, 0, 0.1);stroke-width:1px;}#chatgpt-mermaid-\_r_76p\_ .cluster text{fill:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_76p\_ .cluster span{color:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_76p\_ div.mermaidTooltip{position:absolute;text-align:center;max-width:200px;padding:2px;font-family:-apple-system-body,ui-sans-serif,-apple-system,system-ui,"Segoe UI",Helvetica,"Apple Color Emoji",Arial,sans-serif,"Segoe UI Emoji","Segoe UI Symbol";font-size:12px;background:rgb(243, 243, 243);border:1px solid rgba(0, 0, 0, 0.1);border-radius:2px;pointer-events:none;z-index:100;}#chatgpt-mermaid-\_r_76p\_ .flowchartTitleText{text-anchor:middle;font-size:18px;fill:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_76p\_ rect.text{fill:none;stroke-width:0;}#chatgpt-mermaid-\_r_76p\_ .icon-shape,#chatgpt-mermaid-\_r_76p\_ .image-shape{background-color:rgb(252, 252, 252);text-align:center;}#chatgpt-mermaid-\_r_76p\_ .icon-shape p,#chatgpt-mermaid-\_r_76p\_ .image-shape p{background-color:rgb(252, 252, 252);padding:2px;}#chatgpt-mermaid-\_r_76p\_ .icon-shape .label rect,#chatgpt-mermaid-\_r_76p\_ .image-shape .label rect{opacity:0.5;background-color:rgb(252, 252, 252);fill:rgb(252, 252, 252);}#chatgpt-mermaid-\_r_76p\_ .label-icon{display:inline-block;height:1em;overflow:visible;vertical-align:-0.125em;}#chatgpt-mermaid-\_r_76p\_ .node .label-icon path{fill:currentColor;stroke:revert;stroke-width:revert;}#chatgpt-mermaid-\_r_76p\_ .node .neo-node{stroke:rgb(83, 154, 248);}#chatgpt-mermaid-\_r_76p\_ [data-look="neo"].node rect,#chatgpt-mermaid-\_r_76p\_ [data-look="neo"].cluster rect,#chatgpt-mermaid-\_r_76p\_ [data-look="neo"].node polygon{stroke:url(#chatgpt-mermaid-\_r_76p\_-gradient);filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-\_r_76p\_ [data-look="neo"].swimlane.cluster rect{filter:none;}#chatgpt-mermaid-\_r_76p\_ [data-look="neo"].node path{stroke:url(#chatgpt-mermaid-\_r_76p\_-gradient);stroke-width:1px;}#chatgpt-mermaid-\_r_76p\_ [data-look="neo"].node .outer-path{filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-\_r_76p\_ [data-look="neo"].node .neo-line path{stroke:rgb(83, 154, 248);filter:none;}#chatgpt-mermaid-\_r_76p\_ [data-look="neo"].node circle{stroke:url(#chatgpt-mermaid-\_r_76p\_-gradient);filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-\_r_76p\_ [data-look="neo"].node circle .state-start{fill:#000000;}#chatgpt-mermaid-\_r_76p\_ [data-look="neo"].icon-shape .icon{fill:url(#chatgpt-mermaid-\_r_76p\_-gradient);filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-\_r_76p\_ [data-look="neo"].icon-shape .icon-neo path{stroke:url(#chatgpt-mermaid-\_r_76p\_-gradient);filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-\_r_76p\_ .node text{font-size:14px;font-weight:600;letter-spacing:normal;fill:rgb(0, 79, 153);}#chatgpt-mermaid-\_r_76p\_ .edgeLabels text{font-size:13px;font-weight:600;letter-spacing:-0.08px;fill:rgb(0, 79, 153);}#chatgpt-mermaid-\_r_76p\_ .node tspan[font-weight="normal"],#chatgpt-mermaid-\_r_76p\_ .edgeLabels tspan[font-weight="normal"]{font-weight:600;}#chatgpt-mermaid-\_r_76p\_ .edgeLabel .label rect{opacity:1;rx:13px;ry:13px;fill:rgb(245, 250, 255);stroke:rgb(206, 219, 229);stroke-width:1px;}#chatgpt-mermaid-\_r_76p\_ .node rect,#chatgpt-mermaid-\_r_76p\_ .node circle,#chatgpt-mermaid-\_r_76p\_ .node ellipse,#chatgpt-mermaid-\_r_76p\_ .node polygon,#chatgpt-mermaid-\_r_76p\_ .node path{fill:rgb(229, 243, 255);stroke:rgba(0, 0, 0, 0.1);stroke-width:1px;}#chatgpt-mermaid-\_r_76p\_ .node rect{rx:16px;ry:16px;}#chatgpt-mermaid-\_r_76p\_ .mermaid-decision .label-container{fill:rgb(245, 250, 255);stroke:rgb(206, 219, 229);stroke-dasharray:2,2;}#chatgpt-mermaid-\_r_76p\_ .edgePaths .flowchart-link{stroke:rgb(143, 143, 143);stroke-width:1px;stroke-linecap:round;stroke-linejoin:round;}#chatgpt-mermaid-\_r_76p\_ .marker{fill:rgb(143, 143, 143);stroke:rgb(143, 143, 143);}#chatgpt-mermaid-\_r_76p\_ :root{--mermaid-font-family:-apple-system-body,ui-sans-serif,-apple-system,system-ui,"Segoe UI",Helvetica,"Apple Color Emoji",Arial,sans-serif,"Segoe UI Emoji","Segoe UI Symbol";}需求冻结与视觉规范数据模型与 API 契约账号、权限与资产基础服务衣物上传和存储审核、识别与分割服装资产 Manifest角色模型与 Morph 系统角色渲染模块服装锚点与适配换装引擎穿搭保存与恢复AI 搭配执行分享与社区灰度、监控与上线

### **29.5 研发排期建议**

建议以研发工作包和验收里程碑管理，不在技术 PoC 未完成前强行承诺固定工期。

| 里程碑        | 工作内容         | 退出条件        |
| ---------- | ------------ | ----------- |
| M0 需求冻结    | 产品范围、交互、数据契约 | P0 需求确认     |
| M1 技术 PoC  | 角色、服装、渲染验证   | 核心技术可运行     |
| M2 基础服务    | 账号、角色、衣橱、上传  | 核心 API 可用   |
| M3 AI 资产生产 | 审核、识别、分割、生成  | 衣物可转化为资产    |
| M4 换装闭环    | 锚点、图层、适配、保存  | 真实衣物可穿到角色身上 |
| M5 AI 搭配   | 推荐、规则校验、渲染   | AI 可执行搭配    |
| M6 质量验收    | 安全、性能、兼容性    | P0 用例通过     |
| M7 MVP 发布  | 灰度、监控、回滚     | 满足上线门槛      |

## **三十、产品指标、埋点与数据分析规格**

### **30.1 北极星指标**

**每周有效穿搭创作用户数（Weekly Active Outfit Creators）**

定义：一周内至少完成一次有效穿搭，并保存、分享或记录穿搭的去重用户数。

有效穿搭定义：

- 至少有一个有效角色。
- 至少有一件有效服装资产。
- 穿搭保存成功。
- 不是系统自动创建的空记录。
- 不属于异常刷量或测试账号。

### **30.2 漏斗指标**

核心业务漏斗：

\#chatgpt-mermaid-\_r_770\_{font-family:-apple-system-body,ui-sans-serif,-apple-system,system-ui,"Segoe UI",Helvetica,"Apple Color Emoji",Arial,sans-serif,"Segoe UI Emoji","Segoe UI Symbol";font-size:16px;fill:rgb(13, 13, 13);}@keyframes edge-animation-frame{from{stroke-dashoffset:0;}}@keyframes dash{to{stroke-dashoffset:0;}}#chatgpt-mermaid-\_r_770\_ .edge-animation-slow{stroke-dasharray:9,5!important;stroke-dashoffset:900;animation:dash 50s linear infinite;stroke-linecap:round;}#chatgpt-mermaid-\_r_770\_ .edge-animation-fast{stroke-dasharray:9,5!important;stroke-dashoffset:900;animation:dash 20s linear infinite;stroke-linecap:round;}#chatgpt-mermaid-\_r_770\_ .error-icon{fill:rgb(243, 243, 243);}#chatgpt-mermaid-\_r_770\_ .error-text{fill:rgb(13, 13, 13);stroke:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_770\_ .edge-thickness-normal{stroke-width:1px;}#chatgpt-mermaid-\_r_770\_ .edge-thickness-thick{stroke-width:3.5px;}#chatgpt-mermaid-\_r_770\_ .edge-pattern-solid{stroke-dasharray:0;}#chatgpt-mermaid-\_r_770\_ .edge-thickness-invisible{stroke-width:0;fill:none;}#chatgpt-mermaid-\_r_770\_ .edge-pattern-dashed{stroke-dasharray:3;}#chatgpt-mermaid-\_r_770\_ .edge-pattern-dotted{stroke-dasharray:2;}#chatgpt-mermaid-\_r_770\_ .marker{fill:rgb(143, 143, 143);stroke:rgb(143, 143, 143);}#chatgpt-mermaid-\_r_770\_ .marker.cross{stroke:rgb(143, 143, 143);}#chatgpt-mermaid-\_r_770\_ svg{font-family:-apple-system-body,ui-sans-serif,-apple-system,system-ui,"Segoe UI",Helvetica,"Apple Color Emoji",Arial,sans-serif,"Segoe UI Emoji","Segoe UI Symbol";font-size:16px;}#chatgpt-mermaid-\_r_770\_ p{margin:0;}#chatgpt-mermaid-\_r_770\_ .label{font-family:-apple-system-body,ui-sans-serif,-apple-system,system-ui,"Segoe UI",Helvetica,"Apple Color Emoji",Arial,sans-serif,"Segoe UI Emoji","Segoe UI Symbol";color:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_770\_ .cluster-label text{fill:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_770\_ .cluster-label span{color:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_770\_ .cluster-label span p{background-color:transparent;}#chatgpt-mermaid-\_r_770\_ .label text,#chatgpt-mermaid-\_r_770\_ span{fill:rgb(13, 13, 13);color:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_770\_ .node rect,#chatgpt-mermaid-\_r_770\_ .node circle,#chatgpt-mermaid-\_r_770\_ .node ellipse,#chatgpt-mermaid-\_r_770\_ .node polygon,#chatgpt-mermaid-\_r_770\_ .node path{fill:rgb(222, 234, 251);stroke:rgb(83, 154, 248);stroke-width:1px;}#chatgpt-mermaid-\_r_770\_ .rough-node .label text,#chatgpt-mermaid-\_r_770\_ .node .label text,#chatgpt-mermaid-\_r_770\_ .image-shape .label,#chatgpt-mermaid-\_r_770\_ .icon-shape .label{text-anchor:middle;}#chatgpt-mermaid-\_r_770\_ .node .katex path{fill:#000;stroke:#000;stroke-width:1px;}#chatgpt-mermaid-\_r_770\_ .rough-node .label,#chatgpt-mermaid-\_r_770\_ .node .label,#chatgpt-mermaid-\_r_770\_ .image-shape .label,#chatgpt-mermaid-\_r_770\_ .icon-shape .label{text-align:center;}#chatgpt-mermaid-\_r_770\_ .node.clickable{cursor:pointer;}#chatgpt-mermaid-\_r_770\_ .root .anchor path{fill:rgb(143, 143, 143)!important;stroke-width:0;stroke:rgb(143, 143, 143);}#chatgpt-mermaid-\_r_770\_ .arrowheadPath{fill:rgb(143, 143, 143);}#chatgpt-mermaid-\_r_770\_ .edgePath .path{stroke:rgb(143, 143, 143);stroke-width:1px;}#chatgpt-mermaid-\_r_770\_ .flowchart-link{stroke:rgb(143, 143, 143);fill:none;}#chatgpt-mermaid-\_r_770\_ .edgeLabel{background-color:rgb(252, 252, 252);text-align:center;}#chatgpt-mermaid-\_r_770\_ .edgeLabel p{background-color:rgb(252, 252, 252);}#chatgpt-mermaid-\_r_770\_ .edgeLabel rect{opacity:0.5;background-color:rgb(252, 252, 252);fill:rgb(252, 252, 252);}#chatgpt-mermaid-\_r_770\_ .labelBkg{background-color:rgba(252, 252, 252, 0.5);}#chatgpt-mermaid-\_r_770\_ .cluster rect{fill:rgb(243, 243, 243);stroke:rgba(0, 0, 0, 0.1);stroke-width:1px;}#chatgpt-mermaid-\_r_770\_ .cluster text{fill:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_770\_ .cluster span{color:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_770\_ div.mermaidTooltip{position:absolute;text-align:center;max-width:200px;padding:2px;font-family:-apple-system-body,ui-sans-serif,-apple-system,system-ui,"Segoe UI",Helvetica,"Apple Color Emoji",Arial,sans-serif,"Segoe UI Emoji","Segoe UI Symbol";font-size:12px;background:rgb(243, 243, 243);border:1px solid rgba(0, 0, 0, 0.1);border-radius:2px;pointer-events:none;z-index:100;}#chatgpt-mermaid-\_r_770\_ .flowchartTitleText{text-anchor:middle;font-size:18px;fill:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_770\_ rect.text{fill:none;stroke-width:0;}#chatgpt-mermaid-\_r_770\_ .icon-shape,#chatgpt-mermaid-\_r_770\_ .image-shape{background-color:rgb(252, 252, 252);text-align:center;}#chatgpt-mermaid-\_r_770\_ .icon-shape p,#chatgpt-mermaid-\_r_770\_ .image-shape p{background-color:rgb(252, 252, 252);padding:2px;}#chatgpt-mermaid-\_r_770\_ .icon-shape .label rect,#chatgpt-mermaid-\_r_770\_ .image-shape .label rect{opacity:0.5;background-color:rgb(252, 252, 252);fill:rgb(252, 252, 252);}#chatgpt-mermaid-\_r_770\_ .label-icon{display:inline-block;height:1em;overflow:visible;vertical-align:-0.125em;}#chatgpt-mermaid-\_r_770\_ .node .label-icon path{fill:currentColor;stroke:revert;stroke-width:revert;}#chatgpt-mermaid-\_r_770\_ .node .neo-node{stroke:rgb(83, 154, 248);}#chatgpt-mermaid-\_r_770\_ [data-look="neo"].node rect,#chatgpt-mermaid-\_r_770\_ [data-look="neo"].cluster rect,#chatgpt-mermaid-\_r_770\_ [data-look="neo"].node polygon{stroke:url(#chatgpt-mermaid-\_r_770\_-gradient);filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-\_r_770\_ [data-look="neo"].swimlane.cluster rect{filter:none;}#chatgpt-mermaid-\_r_770\_ [data-look="neo"].node path{stroke:url(#chatgpt-mermaid-\_r_770\_-gradient);stroke-width:1px;}#chatgpt-mermaid-\_r_770\_ [data-look="neo"].node .outer-path{filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-\_r_770\_ [data-look="neo"].node .neo-line path{stroke:rgb(83, 154, 248);filter:none;}#chatgpt-mermaid-\_r_770\_ [data-look="neo"].node circle{stroke:url(#chatgpt-mermaid-\_r_770\_-gradient);filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-\_r_770\_ [data-look="neo"].node circle .state-start{fill:#000000;}#chatgpt-mermaid-\_r_770\_ [data-look="neo"].icon-shape .icon{fill:url(#chatgpt-mermaid-\_r_770\_-gradient);filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-\_r_770\_ [data-look="neo"].icon-shape .icon-neo path{stroke:url(#chatgpt-mermaid-\_r_770\_-gradient);filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-\_r_770\_ .node text{font-size:14px;font-weight:600;letter-spacing:normal;fill:rgb(0, 79, 153);}#chatgpt-mermaid-\_r_770\_ .edgeLabels text{font-size:13px;font-weight:600;letter-spacing:-0.08px;fill:rgb(0, 79, 153);}#chatgpt-mermaid-\_r_770\_ .node tspan[font-weight="normal"],#chatgpt-mermaid-\_r_770\_ .edgeLabels tspan[font-weight="normal"]{font-weight:600;}#chatgpt-mermaid-\_r_770\_ .edgeLabel .label rect{opacity:1;rx:13px;ry:13px;fill:rgb(245, 250, 255);stroke:rgb(206, 219, 229);stroke-width:1px;}#chatgpt-mermaid-\_r_770\_ .node rect,#chatgpt-mermaid-\_r_770\_ .node circle,#chatgpt-mermaid-\_r_770\_ .node ellipse,#chatgpt-mermaid-\_r_770\_ .node polygon,#chatgpt-mermaid-\_r_770\_ .node path{fill:rgb(229, 243, 255);stroke:rgba(0, 0, 0, 0.1);stroke-width:1px;}#chatgpt-mermaid-\_r_770\_ .node rect{rx:16px;ry:16px;}#chatgpt-mermaid-\_r_770\_ .mermaid-decision .label-container{fill:rgb(245, 250, 255);stroke:rgb(206, 219, 229);stroke-dasharray:2,2;}#chatgpt-mermaid-\_r_770\_ .edgePaths .flowchart-link{stroke:rgb(143, 143, 143);stroke-width:1px;stroke-linecap:round;stroke-linejoin:round;}#chatgpt-mermaid-\_r_770\_ .marker{fill:rgb(143, 143, 143);stroke:rgb(143, 143, 143);}#chatgpt-mermaid-\_r_770\_ :root{--mermaid-font-family:-apple-system-body,ui-sans-serif,-apple-system,system-ui,"Segoe UI",Helvetica,"Apple Color Emoji",Arial,sans-serif,"Segoe UI Emoji","Segoe UI Symbol";}进入上传上传完成审核通过识别确认资产生成首次穿搭保存穿搭分享作品

以上仅描述漏斗结构，不代表现有真实数据或业务预测。

建议拆解：

\\[ 上传完成率 = \frac{上传完成用户}{进入上传用户} \\]

\\[ 审核通过率 = \frac{审核通过数量}{提交审核数量} \\]

\\[ 资产生成成功率 = \frac{生成成功资产}{发起生成任务} \\]

\\[ 首次穿搭完成率 = \frac{完成首次穿搭用户}{注册用户} \\]

\\[ AI推荐采纳率 = \frac{被应用的推荐方案}{有效推荐方案} \\]

### **30.3 埋点事件**

| 事件名                             | 触发时机   | 关键属性    |
| ------------------------------- | ------ | ------- |
| `user_registered`               | 注册成功   | 渠道、时间   |
| `avatar_create_started`         | 开始创建角色 | 模板 ID   |
| `avatar_created`                | 创建成功   | 模型、风格   |
| `avatar_body_changed`           | 身材参数变化 | 参数类型    |
| `wardrobe_upload_started`       | 开始上传   | 上传方式    |
| `wardrobe_upload_completed`     | 上传完成   | 图片大小、格式 |
| `wardrobe_upload_failed`        | 上传失败   | 错误码     |
| `garment_moderation_completed`  | 审核完成   | 状态、耗时   |
| `garment_recognition_completed` | 识别完成   | 类别、置信度  |
| `garment_asset_generated`       | 资产生成成功 | 资产类型、耗时 |
| `garment_asset_corrected`       | 用户修正资产 | 修改字段    |
| `garment_asset_rejected`        | 用户拒绝素材 | 原因      |
| `outfit_item_equipped`          | 穿戴服装   | 资产类别    |
| `outfit_item_removed`           | 脱下服装   | 资产类别    |
| `outfit_saved`                  | 保存穿搭   | 角色 ID   |
| `outfit_restored`               | 恢复历史穿搭 | 版本      |
| `ai_recommendation_requested`   | 发起搭配   | 场景、风格   |
| `ai_recommendation_completed`   | 推荐完成   | 方案数量    |
| `ai_recommendation_applied`     | 应用推荐   | 方案 ID   |
| `ai_recommendation_rejected`    | 拒绝推荐   | 原因      |
| `outfit_shared`                 | 分享作品   | 分享类型    |
| `shared_asset_reused`           | 复用资产   | 授权类型    |
| `asset_license_changed`         | 修改授权   | 原状态、新状态 |

### **30.4 数据分析维度**

- 用户来源。
- 新老用户。
- 免费/会员用户。
- 角色数量。
- 衣物数量。
- 衣物类别。
- 上传方式。
- AI 模型版本。
- 生成任务状态。
- 设备型号。
- 系统版本。
- 网络质量。
- 作品类型。
- 授权类型。

### **30.5 AI 成本指标**

必须单独跟踪：

- 每次衣物识别成本。
- 每次图像分割成本。
- 每次服装素材生成成本。
- 每次 AI 搭配成本。
- 每个有效用户的 AI 成本。
- 每套有效穿搭的 AI 成本。
- 失败任务成本。
- 重试成本。
- 缓存命中率。

避免只看 API 单价，而忽略重试、失败、人工复核、对象存储和渲染成本。

## **三十一、风险管理与决策清单**

### **31.1 技术风险**

| 风险          | 影响        | 应对                   |
| ----------- | --------- | -------------------- |
| 真实衣物分割质量不足  | 无法形成可用资产  | 先建立标准拍摄和分割 PoC       |
| AI 改变衣物图案   | 资产失真      | 原图纹理优先、生成质量校验        |
| 2.5D 资产适配困难 | 换装效果差     | 分品类处理，不承诺全自动         |
| 身材形变导致穿模    | 角色体验差     | Morph Target 与服装适配规则 |
| 角色模型资源过大    | 移动端卡顿     | 资源压缩和分级加载            |
| 服装遮挡复杂      | 视觉错误      | 图层、Mask、深度规则         |
| AI 推荐幻觉     | 不存在的服装被推荐 | 候选集检索和资产 ID 校验       |
| 模型供应商不稳定    | 任务失败      | 模型路由和降级策略            |
| 资产版本升级破坏历史  | 历史作品异常    | 版本引用和快照机制            |

### **31.2 产品风险**

| 风险         | 影响         | 应对           |
| ---------- | ---------- | ------------ |
| 上传门槛太高     | 新用户流失      | 拍摄引导和快速入库    |
| 角色编辑复杂     | 用户无法完成创建   | 模板优先、渐进式编辑   |
| 衣物识别需要频繁修正 | 用户失去信任     | 置信度分层和手动纠正   |
| 真实衣橱价值不足   | 使用频率低      | AI 场景推荐和穿搭记录 |
| 角色情感价值不足   | 用户缺少持续打开动力 | 角色成长和展示内容    |
| 社区冷启动困难    | 内容不足       | 官方主题和示例内容    |
| 商业化过早      | 影响体验       | 先验证核心使用价值    |
| 免费生成成本过高   | 毛利恶化       | 额度、缓存、任务去重   |

### **31.3 法律与版权风险**

- 用户上传服装照片不意味着用户拥有服装图案的商业版权。
- 品牌 Logo、动漫形象、设计师作品需要版权和商标规则。
- 公开展示和商业复用必须分开授权。
- 用户删除素材后需要处理已授权资产。
- 用户生成内容需要举报、下架、申诉机制。
- 对未成年人使用场景建立适当保护措施。
- 对 AI 生成内容的标识义务进行法务评估。
- 用户上传图片、身材数据和角色信息应按隐私规则处理。
- 对第三方模型、审核服务和对象存储的数据处理边界进行审查。

### **31.4 立项前需要确认的决策**

| 决策编号  | 问题       | 推荐方向              | 决策责任  |
| ----- | -------- | ----------------- | ----- |
| D-001 | 角色风格     | 可爱卡通/二次元 3D       | 产品+美术 |
| D-002 | 首期角色模型   | 单基础模型，多形变配置       | 3D 技术 |
| D-003 | 服装生成     | 2D/2.5D 优先        | AI+3D |
| D-004 | 首期服装类别   | 上装、下装、连衣裙、鞋、饰品    | 产品    |
| D-005 | 首期渲染     | Three.js 独立模块 PoC | 客户端   |
| D-006 | AI 识别供应商 | 先做模型效果对比          | AI 技术 |
| D-007 | 图片审核     | 服务端审核门禁           | 后端+安全 |
| D-008 | 数据存储     | 关系型数据库+对象存储       | 后端    |
| D-009 | 资产授权     | 展示、复用、商业使用分离      | 产品+法务 |
| D-010 | 会员策略     | 先测算成本再定价          | 产品    |
| D-011 | 角色数量限制   | 配置化权益             | 产品    |
| D-012 | 真实身材数据   | 完全可选、默认私有         | 产品+法务 |

## **三十二、最终交付物清单**

项目不能以“页面已经画完”作为完成标准。每个模块都需要明确的交付件。

| 模块    | 必须交付物                         |
| ----- | ----------------------------- |
| 产品    | PRD、页面清单、交互原型、业务规则            |
| UI/UX | 页面设计、组件规范、空状态、错误状态            |
| 角色系统  | 模型规范、骨骼规范、Morph 参数、资源清单       |
| 服装系统  | 资产 Manifest、锚点表、图层规则、适配规范     |
| AI    | 模型选型报告、Prompt/Schema、评测集、成本报告 |
| 后端    | ERD、数据字典、API 契约、任务状态机         |
| 客户端   | 渲染模块、资源加载、交互实现                |
| 安全    | 上传安全、审核规则、权限测试                |
| 测试    | 测试计划、测试用例、执行报告、缺陷清单           |
| 运维    | 部署方案、监控、告警、备份、回滚              |
| 运营    | 内容审核规则、活动配置、会员权益配置            |

### **32.1 交付目录建议**

```
AI-Digital-Wardrobe/
│
├── README.md
├── PRD-V1.0.md
│
├── product/
│   ├── product-positioning.md
│   ├── competitor-analysis.md
│   ├── page-inventory.md
│   ├── interaction-spec.md
│   ├── business-rules.md
│   └── roadmap.md
│
├── architecture/
│   ├── system-architecture.md
│   ├── data-model.md
│   ├── api-contract.md
│   ├── ai-workflow.md
│   └── security-architecture.md
│
├── character-system/
│   ├── character-architecture.md
│   ├── body-morph-spec.md
│   ├── model-standard.md
│   └── rendering-spec.md
│
├── garment-system/
│   ├── garment-asset-spec.md
│   ├── anchor-spec.md
│   ├── layer-occlusion-spec.md
│   ├── fitting-spec.md
│   └── manifest-schema.json
│
├── community/
│   ├── sharing-spec.md
│   ├── license-spec.md
│   └── moderation-spec.md
│
├── testing/
│   ├── test-plan.md
│   ├── test-cases.md
│   ├── acceptance-criteria.md
│   └── traceability-matrix.md
│
└── assets/
    ├── original-reference/
    ├── product-diagrams/
    ├── character-diagrams/
    ├── garment-diagrams/
    └── ui-wireframes/
```

## **三十三、给管理层的完整立项汇报结论**

### **33.1 这不是一个单点 AI 工具**

产品的核心价值是将四种能力组合起来：

**现实衣橱**

解决衣物管理、搭配和利用率问题。

**虚拟角色**

提供角色身份、外观定制和情感价值。

**AI 穿搭**

理解用户需求，真正调用衣橱资产完成搭配。

**UGC 与数字资产生态**

让作品、服装、角色和授权形成内容流动。

### **33.2 产品真正需要验证的核心假设**

| 核心假设         | 验证方式         | 如果失败           |
| ------------ | ------------ | -------------- |
| 用户愿意上传真实衣物   | 上传转化率、完成时间   | 优化拍摄和入库流程      |
| AI 能稳定识别衣物   | 分类准确率、用户修正率  | 缩小支持品类         |
| 真实衣物能转成可穿戴资产 | 素材生成成功率、人工验收 | 采用半自动生产        |
| 角色能承载服装展示    | 角色适配、视觉质量    | 优先固定视角 2D/2.5D |
| 用户愿意持续搭配     | WAOC、周活跃创作用户 | 强化场景和记录        |
| AI 推荐确实有用    | 推荐采纳率、保存率    | 先规则推荐再升级模型     |
| 用户愿意分享内容     | 分享率、复用率      | 强化作品展示和模板      |
| 资产可以形成商业价值   | 授权、交易和付费意愿   | 延后市场化          |

### **33.3 首期最重要的 Demo**

建议给管理层展示一条完整、可操作的垂直链路，而不是分别展示几个孤立页面。

Demo 必须是真实链路：

- 不是把衣服图片直接贴到角色图片上就算完成。
- 必须有真实的衣物资产记录。
- 必须有角色配置。
- 必须有服装锚点和图层信息。
- 必须有穿搭保存记录。
- AI 必须引用实际衣橱资产。
- 分享必须有权限控制。

这条链路跑通后，才能证明产品的核心差异化成立。

# **第三部分：品牌命名、视觉定位与 UI/UX 设计规范**

## **三十四、品牌命名与产品品牌体系**

### **34.1 命名原则**

本产品不是单纯的衣物管理工具，也不是传统的女性向换装游戏。品牌名称需要同时容纳以下内容：

- 真实衣橱：用户自己的衣服、鞋包、配饰。
- 虚拟角色：可以创建、编辑、养成的数字形象。
- 时尚创作：穿搭、服装设计、角色造型。
- AI 能力：智能识别、搭配推荐、生成和辅助创作。
- 社区生态：用户作品、创作者、分享和数字资产。

因此，名称不能过于工具化，也不能过于幼态。

参考《奇迹暖暖》《闪耀暖暖》的女性向命名逻辑，可以借鉴它们的**意象化、情绪化、易记忆和世界观延展能力**；参考《燕云十六声》《第五人格》的命名方式，则要让品牌具有独立辨识度，而不是直接描述功能。

命名规则：

1. 中文名优先四至五个字。
2. 读音顺畅，避免生僻字和难以输入的字。
3. 具有服饰、光影、织物、星空、梦境、时光等意象。
4. 不直接包含“AI”“衣橱”“换装”等工具关键词。
5. 英文名应当可以独立成为品牌，不要求逐字翻译中文。
6. 应支持未来扩展到虚拟服装、角色、创作者和数字资产。
7. 正式定名前需要检查商标、域名、应用商店重名及近似名称。

### **34.2 中文与英文品牌候选**

# **衣间星河**

综合首选

# **VESTORIA**

![PANDORA'S BOX: Visual story via photography and styling :: Behance](https://images.openai.com/static-rsc-4/1ug5nh55Jg2ElIKf8Z48rVNjtn4TZm1frzvZCKTvoTR0lO--wJ_s4AQve9ec7R8jSbZ7q4laOsgFV_ZL7VdJjcwlqRCzvZ554AiHdvEGv4rzCkCwMy68kyKL2YW0r2iHJvnOJ5Vt3ANID3sKAXNwfa2exNQsZlbXelcyBHyxB5k?purpose=inline)

![behance.net](https://www.behance.net/gallery/188099531/PANDORAS-BOX-Visual-story-via-photography-and-styling?utm_source=chatgpt.com)

**品牌意象：** 衣橱中的每一件衣服，都能延伸出一个新的自己。

“衣间”对应真实衣橱，“星河”对应虚拟角色、创意表达和时尚社区。能够同时承载现实衣物管理和虚拟世界观。

英文名是品牌创意构词，Vest 联想到服饰，Story 联想到个人故事。适合长期发展为综合时尚产品。

# **云裳拾光**

# **LUMIWARD**

![Soft Ivory White Lifestyle Stock Images | Minimal Luxury Neutral Aesthetic Collection — AI Aesthetic STUDIO](https://images.openai.com/static-rsc-4/KuXr883MTEFM8l3_X4OInr2TYLgIDOJ5Q6bu1HSZx9sRN3Yrr4x_xnLqtPPlW94_HpboZsIcaqMYPsYzkwLyXGuPitmuBSKK05JPiK5i5p052muBCZtxeldPGv9_PJUJ_i5dAvPzANFHn0zOC9yhNufboNsOuVa1M_u43IymiOI?purpose=inline)

![ai-aesthetic-studio.com](https://www.ai-aesthetic-studio.com/ai-aesthetic-studio-shop/p/ai-aesthetic-white-ivory-lifestyle-stock-images?utm_source=chatgpt.com)

**品牌意象：** 收藏每一刻的美。

“云裳”有服饰意象，“拾光”有记录、收藏和回忆的感觉。女性化程度较高，适合衣橱记录、穿搭日记和个人风格成长。

# **绮梦衣境**

# **MIRRORIA**

![妖精の仕立て屋 | chichi-pui（ちちぷい）AIイラスト専用の投稿＆生成サイト](https://images.openai.com/static-rsc-4/GMWTKbz9bt6iCCM07qSJ0lOCQCU9H3H5makZjCpsV-8sx2UgLOpIOT9bIeibrPPrL6CgPweAEsyvv6UxqMe_l7-4TOsqH8c4jUrsd4d8j_sIwQJsWpfYLvMpPLlRJ0gAEgJGzAa26rEsT-k1yXis0RWx-Lb4TfaGdAmZkvryRLo?purpose=inline)

![chichi-pui.com](https://www.chichi-pui.com/posts/f132fa9c-6fae-46ad-808f-8809561dca36/?utm_source=chatgpt.com)

**品牌意象：** 进入自己的时尚幻想世界。

“绮梦”强调幻想与审美，“衣境”强调服装构建的个人世界。更偏游戏化、虚拟角色、换装和创作社区，世界观空间比较大。

# **织光来信**

# **LUMELLE**

![Overhead view of fresh pink shrub roses with peach-colored silk ribbon with text space and notebook. Inspiration concept](https://images.openai.com/static-rsc-4/_Z8HPirxOdA87zhq1JQ7_JqK6Vwj9pKj8z4M6b-0w2MBGkXbmekNmkM9_tccLWBl0F7oIEXbSMQjh3O5kmHDqrIGpqSHbKT_bDBUzHRWg_wz_vByRqkbDArqBC5Tr6XwoXTkZTumNVJFLNQk_h-GFVTHkyIKwrY2tzZt35RDJcsRMg7l1sikGKUH4SIPRqYh?purpose=inline)

**品牌意象：** 用穿搭写下自己的故事。

更偏文艺、独立设计师和生活方式品牌。适合强调用户表达、穿搭分享、搭配灵感和社区内容，而不是传统换装游戏。

# **衣序流光**

# **AUREVIA**

![Brand Styling for Image Consultants: How Ashley Elevated Her Visual Brand Without Starting Over — Rene Kauder](https://images.openai.com/static-rsc-4/p1QlYveRGPeixdRPNPokTUGt4KfygJl_hNI3Lo9E1UlNgk9x4HVgFZ7I7KEgLLrdsJkUB0w_0bJ-1dqvqhMRriuxcGMBM65OWleg0fA30rIOF9mjez6RID4bY4i8e0vqkhGBAE1roSl5PzXSUwL7-8PjCQjnbh20vHk4of6NjKo?purpose=inline)

![savvyandstyle.com](https://www.savvyandstyle.com/blog/brand-styling-for-image-consultants-ashley-schafer?utm_source=chatgpt.com)

**品牌意象：** 让日常穿搭成为一种秩序与美学。

“衣序”有衣橱整理、风格体系和搭配逻辑，“流光”增加精致感。更成熟、更时装编辑部化，适合将 AI 穿搭作为核心卖点。

# **星衣漫游**

# **STELLWEAR**

![《閃耀暖暖》主題活動「墟空中的星芒」復刻 評選賽商城上新「弗雷迪的航線」《シャイニングニキ》 - 巴哈姆特](https://images.openai.com/static-rsc-4/OtG-Qb68POh2A2jgGky3uYLAxsv-SRP2N2nA9QXBTOpJlHYVPbEsjEfpVpQ1zEgd9ek0WeE5kFCQU5evmf1XDT-tdWM6GK7WlEyKmxj7HdDQ7Hogn9_kFtwEQpZ2d2JeKEoXmyzoyVS6dceiortuGDCt3MZiJD8dZZfhE3ACb9Q?purpose=inline)

![gnn.gamer.com.tw](https://gnn.gamer.com.tw/detail.php?sn=259611\&utm_source=chatgpt.com)

**品牌意象：** 在不同风格之间自由探索。

“星衣”有虚拟服装和数字时尚的感觉，“漫游”适合角色探索、主题穿搭、社区活动和未来虚拟空间。

### **34.3 命名横向比较**

| 中文名  | 女性化 | 时尚感 | 游戏世界观 | 工具属性兼容 | 长期品牌延展 |
| ---- | --- | --- | ----- | ------ | ------ |
| 衣间星河 | 高   | 高   | 高     | 高      | 高      |
| 云裳拾光 | 很高  | 中高  | 中高    | 高      | 高      |
| 绮梦衣境 | 很高  | 高   | 很高    | 中      | 高      |
| 织光来信 | 高   | 很高  | 中     | 高      | 高      |
| 衣序流光 | 中高  | 很高  | 中     | 很高     | 高      |
| 星衣漫游 | 高   | 中高  | 很高    | 中高     | 高      |

**推荐结论：**

- 综合时尚产品：衣间星河。
- 温柔、精致、偏女性生活方式：云裳拾光。
- 更接近女性向换装游戏：绮梦衣境。
- 强调真实衣橱与时尚社区：衣序流光。

### **34.4 品牌名称使用规范**

以「衣间星河 VESTORIA」为示例，建立完整品牌表达：

A PERSONAL FASHION UNIVERSE

# **衣间星河**

# **VESTORIA**

## 你的数字衣橱，也是你的时尚世界。

YOUR STYLE, YOUR UNIVERSE

**产品正式名称：** 衣间星河

**英文品牌：** VESTORIA

**产品副标题：** AI 数字衣橱 · 虚拟穿搭 · 时尚创作社区

**品牌主张：** 每一件衣服，都是另一个自己的开始。

品牌文案的其他备选：

- 每一种风格，都值得被珍藏。
- 穿上自己的想象。
- 让衣橱成为自己的世界。
- 现实有衣橱，想象有星河。
- 让每一个角色，都拥有自己的风格。

### **34.5 品牌资产交付**

设计团队需要交付：

1. 中文标准字。
2. 英文标准字。
3. 中英文组合 Logo。
4. 横版 Logo。
5. 竖版 Logo。
6. 图形标志。
7. App 图标。
8. 深色背景版本。
9. 浅色背景版本。
10. 单色版本。
11. 最小显示尺寸。
12. 安全留白区域。
13. 禁止变形、拉伸和错误配色示例。
14. 启动页品牌动画。
15. 社区作品水印模板。

## **三十五、UI 总体视觉定位**

### **35.1 视觉风格定义**

本产品 UI 采用：

# **轻奢时尚杂志 × 女性向幻想游戏 × 数字衣橱**

它要有时尚品牌的高级感，也要保留女性向游戏的精致、装饰性和情绪价值。

用户打开产品时，应该觉得自己进入了一本可以互动的时尚杂志，而不是一个在管理衣服的 Excel，也不是普通服装电商商城。

![Reve 2.0 AI Image Generator — Free 4K Text to Image | SoraVideo](https://images.openai.com/static-rsc-4/9X_NTvb5r03jpNiA2OGMYeMiqqZJJ--hkI_RfawOKZhx0JPk6x15nmDpQUridLoOssQlJltQbIHFy3FJRfo4axTJWDRUS3ICrDTPutV9fzsBxIm6TTmUM0BGXNacbFjEM6X89VkCPoVgVh1HVf0lCMx9sWKcq0SlelwM37SXPcI?purpose=inline)

**时尚杂志编辑感**

用于首页、发现页、主题专题、品牌内容。

![闪耀暖暖国服怎么进不去 炸服的解决方法_闪耀暖暖_九游手机游戏](https://images.openai.com/static-rsc-4/TkEDPEZ6ggrxBpYxCVou_a7FFgeu97yd0PTUa_J55zshkMoApypdUHsiCXHXVFazcx3PfI2yreTzs5aw_lhqwCNTEyMJ4zgHrtj4rgj3GsVeLq8V06Rs-H7i-DMPSSxeOuHLmmkvjYcm2wn4l55hyIKAOllaSZDhGFbRAsG19J4?purpose=inline)

**女性向换装游戏质感**

用于角色、试穿、服装展示、套装收藏。

![Cult Gaia App Design | A Sculptural, Emotionally-Driven Mobile Experience | ToyFight](https://images.openai.com/static-rsc-4/DFYVK2oAQNDdhuN0mZQk7fY0OXeKOpc8qGrYghL0kaOkXUXNpU-rbf21JH7FJZUqwIy4WT-BHdSlPt2Hwy4jz5xmvSfcL--Rc3usaknDzDJvrxVP2s_QrsUqAlY7atPjo_lPR31sgB4o8hytpKtb5lz8xVCHicqlVA6BQNtkaak?purpose=inline)

**现代时尚 App**

用于真实衣橱、服装管理、筛选、搜索。

![Krea](https://images.openai.com/static-rsc-4/RFL1b4ZCbNTajz_pPRv3kCFRgDy6avkwhD_sfVwQRGQ8D9sP7c36lagGIdY_BdgBqM-TP_o-eV-08FvrxBhts-5yIazjEWR62YigBY7dqykv7qeLIzYySenre5ICFXE-KxH17-Ux_oHeBJ8svK8iJqjoUUgnY_F9zr-3zdG4KcM?purpose=inline)

**梦幻数字空间**

用于角色工作室、主题活动、AI 生成结果。

四种视觉语言必须有主次关系，不能每个页面各做各的。

**统一底层设计系统：时尚杂志负责排版，游戏负责情绪，工具负责效率。**

### **35.2 视觉定位的主次关系**

| 视觉来源     | 权重定位    | 负责的体验             |
| -------- | ------- | ----------------- |
| 时尚杂志     | 主视觉语言   | 排版、留白、摄影、专题、字体    |
| 女性向游戏    | 情绪与展示语言 | 角色、换装、服装收藏、成就     |
| 现代工具 App | 功能交互语言  | 上传、筛选、编辑、管理、搜索    |
| 数字幻想空间   | 局部氛围语言  | AI、角色工坊、主题活动、虚拟资产 |

不允许把所有页面都做成游戏界面，也不允许把所有页面都做成工具表格。

## **三十六、品牌色彩系统与 Design Token**

### **36.1 品牌基础色**

主色不能是大面积荧光粉，也不建议使用常见 AI 产品的蓝紫渐变。

建议使用低饱和暖色作为底色，以莓果色作为品牌识别色，香槟金作为高级装饰色。

**品牌基础色**

**珍珠白**

\#F7F3EF页面背景

**雾粉灰**

\#E8DDE2柔和区块

**莓果酒红**

\#75485F品牌主色

**香槟金**

\#D6B98C高级装饰

**灰紫**

\#B9B0C8AI 与数字内容

**墨灰**

\#333039正文与标题

**功能色**

**成功色** #729B83

任务完成、审核通过、保存成功

**提醒色** #C58A70

待确认、风险提示、操作提醒

**错误色** #B75D68

上传失败、操作失败、审核拒绝

**AI 状态色** #8C83A7

AI 处理中、智能推荐、生成任务

### **36.2 色彩使用比例**

- 70% 使用珍珠白、暖白、浅灰等中性背景。
- 20% 使用雾粉灰、浅紫等辅助色。
- 10% 使用莓果色、香槟金等强调色。

使用约束：

1. 金色只用于收藏等级、稀有装饰、活动标识，不得大面积铺满。
2. 不允许每个模块随意使用一套不同的主色。
3. 服装本身是视觉主体，界面颜色必须给服装让位，不能抢服装的颜色。
4. 不能把粉色当成所有女性用户的默认偏好。
5. 深色服装、浅色服装和高饱和服装都必须在界面中清晰呈现。
6. 文字和背景必须保持足够对比度。
7. 状态不能只通过颜色区分，必须同时配合图标或文字。

### **36.3 字体与排版**

| 使用场景   | 字体建议                                  | 规则       |
| ------ | ------------------------------------- | -------- |
| 中文品牌标题 | 思源宋体 / Noto Serif SC                  | 体现优雅与编辑感 |
| 页面主标题  | 思源黑体 / Noto Sans SC                   | 清晰、克制    |
| 正文     | 思源黑体 / Noto Sans SC                   | 保证长时间阅读  |
| 英文标题   | Cormorant Garamond / Playfair Display | 时装杂志气质   |
| 英文正文   | Inter                                 | 现代、清晰    |
| 数字与统计  | Inter / DIN                           | 统一数字宽度   |

字体尺寸建议：

| 层级      | 字号      | 使用场景        |
| ------- | ------- | ----------- |
| Display | 32–40px | 首页品牌视觉、专题标题 |
| H1      | 24–28px | 页面主标题       |
| H2      | 20–22px | 模块标题        |
| H3      | 16–18px | 卡片标题        |
| Body    | 14–16px | 正文、说明       |
| Caption | 12–13px | 标签、辅助信息     |
| Micro   | 10–11px | 仅用于非关键信息    |

移动端正文不低于 14px，关键操作、服装名称、状态信息不能依赖极小字体展示。

### **36.4 间距与布局 Token**

建议使用 4px 基础间距单位：

| Token      | 数值   | 用途      |
| ---------- | ---- | ------- |
| spacing-1  | 4px  | 图标与文字间距 |
| spacing-2  | 8px  | 小型控件内部  |
| spacing-3  | 12px | 标签、紧凑卡片 |
| spacing-4  | 16px | 常规内容间距  |
| spacing-5  | 20px | 模块内部    |
| spacing-6  | 24px | 页面区块间距  |
| spacing-8  | 32px | 大区块分隔   |
| spacing-10 | 40px | 重点视觉留白  |
| spacing-12 | 48px | 页面主视觉间距 |

### **36.5 圆角与阴影**

| 组件     | 圆角建议    |
| ------ | ------- |
| 小型标签   | 6–8px   |
| 输入框    | 10–12px |
| 按钮     | 12–16px |
| 普通卡片   | 14–18px |
| 大型内容卡片 | 18–24px |
| 弹窗     | 20–24px |
| 角色展示容器 | 20–28px |

阴影规范：

- 默认卡片尽量不使用明显阴影。
- 浮层、弹窗使用柔和阴影。
- 选中态优先使用边框和背景变化。
- 不允许每个组件都使用阴影。
- 不允许厚重拟物浮雕效果。

## **三十七、UI 组件与交互规范**

### **37.1 按钮**

**PRIMARY BUTTON**

**开始搭配**

**SECONDARY BUTTON**

**选择衣物**

**TEXT BUTTON**

**查看全部**

规范：

- 主按钮：莓果酒红底、白字。
- 次按钮：白底、浅描边、深色字。
- 文字按钮：不使用厚重背景。
- 主按钮圆角 12–16px。
- 点击状态必须有反馈。
- 加载状态禁止重复提交。
- 禁用状态必须有明确视觉区别。
- 破坏性操作使用独立警示样式。
- 主要操作与次要操作不能使用同等视觉权重。

### **37.2 服装卡片**

![How to Choose Effortless Luxury Outfits          – Dusha + Amai](https://images.openai.com/static-rsc-4/FQqhs-3Ruwe1Uvf0kx31kORycSij2C0Jjuzgavitp7zYPV7SrnkqLelQqIgF7o58kG2PkVouKaYamVD87cdmH-DzeJp5FdPXPLhc8bYOdG9tLzDMZBgzw6LC-WIJpfk7enCphSO-O7b2QWeDDhGoEgNGuUDvnSjEwNbIyzcX7Zc?purpose=inline)

![dushaamai.com](https://dushaamai.com/blogs/news/how-to-choose-outfits-that-look-effortless-but-premium?utm_source=chatgpt.com)

规范：

- 图片比例优先 3:4 或 4:5。
- 图片背景干净，服装主体完整。
- 服装名称、分类、颜色等信息分层展示。
- 收藏、编辑、试穿等操作不覆盖服装主体。
- 不要把所有信息都堆在卡片上。
- 原始图片和抠图素材要有明确区分。
- 资产生成状态要明确展示。
- 不允许把失败或待确认资产显示成已完成状态。

### **37.3 标签与筛选**

**穿搭灵感**

通勤

简约

春季

已选：甜美

根据你的衣橱生成搭配建议

规范：

- 默认使用浅底、低饱和标签。
- 当前选中状态用品牌色。
- 标签必须能区分分类、风格、状态。
- 标签不应像游戏装备稀有度一样五颜六色。
- 多选标签需要显示已选数量或选中状态。
- 筛选条件支持清空和恢复默认。
- 筛选结果为空时必须提供调整条件的入口。

### **37.4 图标规范**

- 优先使用线性图标，统一 1.5–1.8px 描边。
- 线条圆润，避免硬朗的工业风图标。
- 主要功能图标使用统一图标库，不允许同一页面混合三种风格。
- 角色、衣服、配饰等专属图标可以使用原创插画。
- 收藏、点赞、穿搭、分享等高频操作必须保持语义一致。
- 不允许仅凭颜色区别图标功能。
- 图标触控区域应大于图形本身，避免误触。

### **37.5 装饰元素**

允许使用：

- 细线、珍珠、丝带、花瓣、星光。
- 杂志式页码、英文小标题、日期标记。
- 柔和渐变、轻微颗粒纹理、局部玻璃质感。
- 服装设计稿、手绘注释、材质细节。
- 轻量金属质感与局部压纹。

禁止：

- 大面积蝴蝶结、爱心、闪光特效。
- 所有按钮都使用渐变和阴影。
- 每个卡片都带装饰边框。
- 过度使用拟物金属、塑料高光和厚重浮雕。
- 把页面做成廉价的粉色购物商城。
- 装饰图案遮挡服装主体。
- 使用无实际意义的装饰按钮。

### **37.6 动效规范**

| 动作    | 建议反馈         | 时间        |
| ----- | ------------ | --------- |
| 页面切换  | 淡入 + 轻微位移    | 180–240ms |
| 卡片选中  | 轻微缩放 + 边框变化  | 120–180ms |
| 收藏    | 图标填充 + 轻反馈   | 180–250ms |
| 服装穿戴  | 服装层切换 + 轻微过渡 | 200–350ms |
| AI 生成 | 过程状态 + 阶段提示  | 按任务实际进度   |
| 成就解锁  | 轻量粒子 / 光效    | 500–800ms |

动效应服务于操作反馈和情绪价值，不能影响操作效率。AI 生成不得用一个无限旋转的圆圈假装任务正在推进。

## **三十八、六大模块的视觉差异规范**

虽然整款产品使用统一设计系统，但六个业务模块不能完全长得一样。

| 模块    | 视觉方向        | 页面核心           |
| ----- | ----------- | -------------- |
| 数字衣橱  | 极简时尚管理      | 服装图片、分类、筛选     |
| 角色工坊  | 梦幻创作空间      | 角色展示、身体参数、外观编辑 |
| AI 穿搭 | 时尚造型工作室     | 搭配方案、推荐理由、对比   |
| 换装系统  | 女性向游戏视觉     | 角色全身、服装层、试穿    |
| 作品社区  | 时尚杂志 / 社交平台 | 图片内容、穿搭故事、互动   |
| 数字资产  | 精品收藏馆       | 稀有度、收藏、授权、交易   |

### **38.1 数字衣橱：功能效率优先**

视觉重点：

- 服装本身的图片。
- 清晰的分类导航。
- 便捷的筛选和搜索。
- 服装属性和使用状态。
- 原始照片与数字资产状态。

禁止过多装饰、复杂动画和过度游戏化。

### **38.2 角色工坊：创作氛围优先**

视觉重点：

- 角色预览占据主要画面。
- 捏脸和身材调整控件明确。
- 角色编辑分阶段组织。
- 预设模板提供快速创建。
- 高级参数逐步展开。

不应将所有参数堆成一个长表单。

### **38.3 AI 穿搭：方案表达优先**

视觉重点：

- 多套方案并列比较。
- 每件服装来源明确。
- 推荐理由简短可读。
- 支持替换单品。
- 能够一键应用到角色。
- 能够保存和反馈。

AI 页面不能只有聊天气泡，必须把搭配结果作为主要视觉内容。

### **38.4 换装系统：角色展示优先**

视觉重点：

- 中央角色全身展示。
- 服装选择区。
- 服装分类。
- 角色旋转和姿势。
- 服装调整面板。
- 保存和拍照入口。

### **38.5 作品社区：内容消费优先**

视觉重点：

- 图片内容。
- 角色造型。
- 作者身份。
- 风格标签。
- 互动操作。
- 授权信息。

社区不能做成纯粹的商品货架，也不能把授权按钮塞进作品主视觉。

### **38.6 数字资产：收藏与权益优先**

视觉重点：

- 资产封面。
- 创作者信息。
- 资产稀有度或系列信息。
- 使用范围。
- 授权状态。
- 版本信息。

数字资产的“稀有度”必须来自真实业务规则，不能为了营造价值而虚构稀有等级。

## **三十九、核心页面视觉与线框结构**

以下线框用于规定页面区域、信息优先级和交互结构，不等同于最终高保真稿。设计团队必须在此基础上补充具体尺寸、图片、状态和交互。

### **39.1 首页 HOME-001**

![AI-Powered Personal Styling | Digital Wardrobe | UI/UX :: Behance](https://images.openai.com/static-rsc-4/PrtiTimxrb4HOjOJIJCkMS3lJ4dG47YNsP3PyqpT4qUE8YiDUJTS8Fqdij_B9YqmfNo-NLNLCfNnbL_sfuglfy20W84q_5Xkg24v_wv5dFUWuJfwdogUf36uBz_TlIzg19imOKBfZ9vrwEqvPln0ONqA9L4PhUD8gStcD9cRD3g?purpose=inline)

![behance.net](https://www.behance.net/gallery/232986325/AI-Powered-Personal-Styling-Digital-Wardrobe-UIUX?utm_source=chatgpt.com)

页面结构：

```
┌─────────────────────────────┐
│ VESTORIA          消息 头像  │
├─────────────────────────────┤
│                             │
│       当前虚拟角色展示       │
│      角色切换 / 角色主页     │
│                             │
├─────────────────────────────┤
│ 今日穿搭灵感                 │
│ 天气 / 场景 / 推荐理由       │
│ [查看搭配] [换一套]          │
├─────────────────────────────┤
│ 快捷入口                     │
│ 添加衣物 / AI 搭配 / 换装    │
├─────────────────────────────┤
│ 我的角色                     │
│ 角色卡片横向滚动             │
├─────────────────────────────┤
│ 穿搭灵感                     │
│ 双列瀑布流                   │
├─────────────────────────────┤
│ 首页 衣橱 换装 发现 我的     │
└─────────────────────────────┘
```

页面要求：

1. 首页视觉中心必须是角色或当日穿搭，而不是功能按钮。
2. 今日推荐必须能说明使用了哪些衣物。
3. 用户衣橱为空时，不得伪造“你的衣橱推荐”。
4. 快捷入口必须保持稳定。
5. 社区内容不能覆盖个人核心功能入口。
6. 首页推荐内容支持后台配置和排序。
7. 首次打开需要提供新手引导，但不能阻塞用户浏览。

### **39.2 数字衣橱 WARD-001**

![Case Study: AI Wardrobe Stylist by Renson Gerald on Dribbble](https://images.openai.com/static-rsc-4/1OCJwsaDkWushs3dCpss4JAZuhDhvPFLhJCmdhLvAH03zOhBrrdWzwA8TAQze5VrV8u9EZjTf464j51k06xqGREE3v1qucgNampWG2guAeGEovaKptG43MAx1Fqtg2c5sN5DtYgH3KAqMSQc-GYFwmGULz5qbYsC2Mp_8gkuAew?purpose=inline)

![dribbble.com](https://dribbble.com/shots/26825082-Case-Study-AI-Wardrobe-Stylist?utm_source=chatgpt.com)

```
┌─────────────────────────────┐
│ 我的衣橱                搜索 │
├─────────────────────────────┤
│ 全部  上装  下装  连衣裙  ... │
├─────────────────────────────┤
│ 筛选  排序  网格/列表         │
├──────────────┬──────────────┤
│              │              │
│    衣物图     │    衣物图     │
│    名称       │    名称       │
│    分类/颜色   │    分类/颜色   │
│              │              │
├──────────────┼──────────────┤
│              │              │
│    衣物图     │    衣物图     │
│    名称       │    名称       │
│    分类/颜色   │    分类/颜色   │
├──────────────┴──────────────┤
│                    ＋ 添加衣物│
└─────────────────────────────┘
```

页面要求：

- 默认以图片网格展示。
- 支持按服装类别筛选。
- 支持颜色、季节、风格、场景等组合筛选。
- 支持网格和列表视图切换。
- 支持按添加时间、使用频率和最近穿搭排序。
- 支持多选批量操作，但批量删除必须二次确认。
- 识别中、待确认、生成中、失败、可穿戴等状态要有区分。
- 服装卡片不展示过多属性，详细信息放到详情页。

### **39.3 衣物详情 WARD-002**

![FITS ME | AI 衣柜管理 & 穿搭助手](https://images.openai.com/static-rsc-4/X8BI1ttR8lwrJ1TEq-nTwxH-DZhnr5iqauvIiLyA-gQ6EOwVgNxTRoBcc_ehOu257hFO2TOKKTXQdjgPFj_6G7n4_aAkEjchIx50rmfNdh4SRqoeo9ts0wQLCYnzB7DiarZnYwEklAQW-IqM96XbVl10bbx2xHochOGnsfeUjVc?purpose=inline)

![fitsme.studio](https://www.fitsme.studio/zh?utm_source=chatgpt.com)

页面区域：

1. 服装原图和数字素材预览。
2. 衣物名称。
3. 分类和子分类。
4. 主色、辅助色。
5. 材质和季节。
6. 风格与场景。
7. 尺码和版型。
8. 资产生成状态。
9. 穿搭历史。
10. 隐私和授权。
11. 编辑、重新识别、重新生成、删除。

### **39.4 上传引导 WARD-004**

![Closet App Projects :: Photos, videos, logos, illustrations and branding :: Behance](https://images.openai.com/static-rsc-4/wygDPS6cwGmQtVG5GpEMB4gmBr5V9DyrsMp8Q093IsN4D0J4oPH3fTZn3q1WwzwUh3eOo1_HpsqaOHJhlyhFE6smVnwRBnVXV5LjFj8v8m7LjJkMrCKHgCWLeOcapdkv2VDyebkDdpxbEqrdVsIlPkQfVJXSM4QkeYeNU222kI0?purpose=inline)

![behance.net](https://www.behance.net/search/projects/closet%20app?utm_source=chatgpt.com)

```
┌─────────────────────────────┐
│ 返回       添加一件新衣物     │
├─────────────────────────────┤
│                             │
│        拍摄区域              │
│     ┌─────────────────┐     │
│     │                 │     │
│     │   衣物轮廓提示    │     │
│     │                 │     │
│     └─────────────────┘     │
│                             │
│  光线正常 / 衣物完整 / 清晰   │
├─────────────────────────────┤
│ 正面拍摄为必需，背面可选      │
│                             │
│ [拍摄]       [从相册选择]     │
└─────────────────────────────┘
```

拍摄引导要求：

- 必须告诉用户如何摆放衣服。
- 实时显示模糊、过暗、遮挡等提示。
- 不应把拍摄规范写成冗长说明。
- 拍摄失败应能重新拍摄。
- 支持取消。
- 支持预览后确认上传。
- 未获得相机权限时提供权限说明和相册入口。

### **39.5 角色工坊 AVATAR-001～005**

![3D着せ替えコーデRPG『シャイニングニキ』5周年イベント開催！期間限定のUR・SSRコーデパーツが無料でたくさん入手できるチャンス！ - ゲームウィズ](https://images.openai.com/static-rsc-4/3ksiifunSjqQxaNnNegwsbafT-chV8WVlIhWRA72cv9c-HDhw0h5_Z6f5pjV9n1Kr9IsOeUpZ9g6P7OSFO2c9UJzo1PIgBYQ0KgxqzWYU88rMVlIv7bBrIEiI1nfnX-YdYPkoxLdNTaJ57HXos-Y1251XmW3GoF4Ac_ONqBY59Y?purpose=inline)

![gamewith.jp](https://gamewith.jp/gamedb/10580/articles/55065?utm_source=chatgpt.com)

```
┌─────────────────────────────┐
│ 角色工坊            保存角色 │
├─────────────────────────────┤
│                             │
│                             │
│        角色全身预览          │
│                             │
│       旋转 / 缩放 / 姿势      │
│                             │
├─────────────────────────────┤
│ 外观  脸型  发型  身材  妆容  │
├─────────────────────────────┤
│ 当前分类的选项列表           │
│ 预设卡片 / 颜色 / 参数滑块    │
├─────────────────────────────┤
│ 重置          取消      保存 │
└─────────────────────────────┘
```

角色工坊要求：

- 角色预览必须占据页面主要面积。
- 角色参数采用分组，不允许全部展开。
- 角色参数修改后实时预览。
- 角色编辑支持撤销和恢复。
- 保存失败必须保留当前编辑状态。
- 退出时检查是否存在未保存修改。
- 身材参数和真实身体数据分离。
- 角色模板与实际模型资源必须建立映射。

### **39.6 换装系统 DRESS-001**

![Anime Fashion Princess Dressup for Android - Download the APK from Uptodown](https://images.openai.com/static-rsc-4/g13VXmh7LLDLY0pBcWpVQTAogJo5qViKzz9pVyXuIkmqlzSIdNGAzuZbBibEVFRsz-w0zbtlSSpFgFGjedL9KvtGNWUYW86VDYDu7W-l9Phnk6KuQ3FQNadeFJ-t3q5MV0uadcB5kDLjC34IiyT6uDQYNEthdFc3fX2puzyOTQY?purpose=inline)

![anime-fashion-princess-dressup.en.uptodown.com](https://anime-fashion-princess-dressup.en.uptodown.com/android?utm_source=chatgpt.com)

```
┌─────────────────────────────┐
│ 返回     我的角色      保存  │
├─────────────────────────────┤
│                             │
│                             │
│        全身角色展示          │
│                             │
│     旋转 / 姿势 / 镜头       │
│                             │
├─────────────────────────────┤
│ 上装 下装 连衣裙 外套 鞋 饰品 │
├─────────────────────────────┤
│ 服装缩略图横向选择列表        │
├─────────────────────────────┤
│ AI搭配  随机  调整  拍照      │
└─────────────────────────────┘
```

换装页面要求：

- 角色必须始终是视觉中心。
- 服装列表不能遮挡主要角色区域。
- 分类切换不能丢失当前穿搭状态。
- 穿戴操作必须有即时反馈。
- 同槽位冲突要有明确替换提示。
- 支持撤销、重做和恢复默认。
- 服装资源加载失败不能清空整套穿搭。
- 保存时必须保存资产版本和变换配置。

### **39.7 AI 穿搭 AI-001～002**

![Subhana – AI-Powered Wardrobe & Outfit Generator by Miawmiaw on Dribbble](https://images.openai.com/static-rsc-4/Z5LvVwWjGefqo8qaCJuO4MNoIXGF1w04otNbRdoiZVJdc63fWNLD0lHPEHprUKraggAvM53DH8kPvHkUfC1L_O5Cc95JK1uPdAi7wKXmLvG0ERckkqFkuYqrHIaMk1EAr_k4usgkSNbvMpOTqWpVO8MAq9lI_nLq4MODOQfpfJw?purpose=inline)

![dribbble.com](https://dribbble.com/shots/26875575-Subhana-AI-Powered-Wardrobe-Outfit-Generator?utm_source=chatgpt.com)

```
┌─────────────────────────────┐
│ AI 穿搭助手                 │
├─────────────────────────────┤
│ 你今天准备去哪里？           │
│ [通勤] [约会] [旅行] [聚会]  │
│                             │
│ 想要什么风格？               │
│ [甜美] [简约] [复古] [优雅]  │
│                             │
│ 使用哪些衣服？               │
│ [全部衣橱] [指定衣物]         │
│                             │
│ 其他要求：                   │
│ 不要高跟鞋、不要太正式……     │
├─────────────────────────────┤
│ [生成穿搭方案]               │
├─────────────────────────────┤
│ 方案 1 / 方案 2 / 方案 3     │
│ 角色效果 + 服装来源 + 理由    │
│ [试穿] [替换] [保存]         │
└─────────────────────────────┘
```

AI 结果必须可执行：

- 显示实际衣物资产。
- 显示搭配理由。
- 显示缺少的品类。
- 显示替代单品。
- 支持单件替换。
- 支持重新生成。
- 支持反馈不喜欢的原因。
- 支持一键应用到当前角色。
- 支持保存成穿搭方案。

### **39.8 社区 COMMUNITY-001**

![Fashion Social App | Style Sharing Platform | Outfit Inspiration by ByteTown for ByteTown Agency on Dribbble](https://images.openai.com/static-rsc-4/_ff7QCX2_rguz3D7gTSUrTCGY8p57VKjpqqiV2yhFGOgUhI0I1Y3uM1qff-4CIoWaXjCshthihqAc7zFiUyvuMpuQI8Mo7gcHW32qWe6Z_Fx31415vbpQsGuGAmJnp4xEgmMSNVLXqnHQ1L4C4SPgZhE_7y8G8gD-F29PHKDW1w?purpose=inline)

![dribbble.com](https://dribbble.com/shots/26694513-Fashion-Social-App-Style-Sharing-Platform-Outfit-Inspiration?utm_source=chatgpt.com)

页面要求：

- 推荐、关注、最新、主题等内容分类。
- 图片瀑布流。
- 作者信息。
- 作品标题和风格标签。
- 点赞、收藏、评论。
- 作品详情页。
- 资产授权信息。
- 复用入口。
- 举报和屏蔽入口。

### **39.9 个人中心 PROFILE-001**

![Trevi - Fashion Reimagined](https://images.openai.com/static-rsc-4/u-ibCjeN62rLxmpBr0NlTV4We72lWJVEYRYD-k97KjO3jwp_fiOvVBghbPvCaS_yx0R0Qj0Vxbh9e69MOONVDY3TT2W7PwRPpk9sM5ZhETLD0mj5JTDhXZeMrHKFB-N68V6eV7_SMQaTuqPIEjLDx4m4QtEjtzmwpTwotDNoFzs?purpose=inline)

![gettrevi.ai](https://gettrevi.ai/?utm_source=chatgpt.com)

页面结构：

- 用户头像、昵称、个人简介。
- 我的角色。
- 我的衣橱。
- 我的穿搭作品。
- 我的收藏。
- 我的数字资产。
- 会员权益。
- 订单与额度。
- 隐私、授权和账户设置。

## **四十、响应式布局、折叠屏与多端适配**

### **40.1 移动端优先原则**

产品首期以移动端为主要使用场景，但角色工坊和服装编辑器需要考虑更大的屏幕空间。

建议采用：

- 手机：单列内容布局。
- 大屏手机：适当增加卡片列数。
- 平板：主内容 + 侧边栏。
- 折叠屏展开态：角色展示区和服装面板并排。
- Web 管理后台：桌面端优先。

### **40.2 断点建议**

以下为设计建议，最终由实际设备和客户端框架验证。

| 布局       | 参考宽度       | 布局要求        |
| -------- | ---------- | ----------- |
| Compact  | 小于 600px   | 单列、底部导航     |
| Medium   | 600–839px  | 双列卡片、侧边筛选可选 |
| Expanded | 840–1199px | 主内容 + 辅助面板  |
| Large    | 1200px 以上  | 多栏布局、桌面式工作区 |

### **40.3 折叠屏特别要求**

折叠屏不能只依赖系统自动拉伸页面。

必须区分：

**折叠态**

- 按普通手机单列布局。
- 角色展示和服装列表纵向排列。
- 底部导航保持正常使用。
- 不得将内容强行压缩到狭窄区域。

**展开态**

- 角色展示区占据主要空间。
- 服装选择区可以位于侧边。
- 属性编辑面板可以独立展开。
- 换装时支持更大预览区域。
- AI 方案可以并列对比。
- 支持双栏或三栏内容布局。

**状态连续性**

- 折叠和展开不能丢失当前角色。
- 不能清空未保存的穿搭。
- 页面切换不能重置 AI 任务。
- 滑块、筛选和编辑状态需要保留。
- 需要处理窗口尺寸变化引起的渲染视口更新。

### **40.4 平板与 Web**

平板端：

- 角色工坊适合双栏。
- 衣橱适合更多列的图片网格。
- AI 方案可以横向比较。
- 社区使用更宽的瀑布流。

Web 端：

- 不要求首期完整复制移动端所有交互。
- 管理后台应提供完整桌面布局。
- 创作者工具后续可以优先考虑 Web。
- 3D 角色渲染需要验证 WebGL 性能和浏览器兼容性。

## **四十一、图片、美术与视觉资产规范**

### **41.1 图片资产分类**

| 资产类型    | 用途           | 格式建议           |
| ------- | ------------ | -------------- |
| 品牌主视觉   | 启动页、专题页      | WebP / PNG     |
| 角色模型    | 3D 角色展示      | GLB / VRM      |
| 角色缩略图   | 列表和头像        | WebP           |
| 原始衣物图   | 用户原始上传       | 原图存储 + 处理副本    |
| 透明服装素材  | 2D 换装        | PNG / WebP     |
| 服装贴图    | 2.5D / 3D 服装 | WebP / KTX2 等  |
| 服装 Mask | 遮罩和分割        | PNG            |
| 社区作品    | 用户分享         | WebP / JPEG    |
| 活动插画    | 主题活动         | WebP / PNG     |
| 背景场景    | 角色拍照         | WebP / 3D 场景资源 |
| UI 图标   | 功能和装饰        | SVG / 图标字体     |

### **41.2 图片比例**

| 图片类型 | 推荐比例       | 用途           |
| ---- | ---------- | ------------ |
| 服装单品 | 3:4        | 衣橱卡片         |
| 服装详情 | 4:5        | 单品展示         |
| 角色全身 | 3:4 / 2:3  | 角色卡片         |
| 角色头像 | 1:1        | 头像和列表        |
| 穿搭作品 | 4:5        | 社区主内容        |
| 横版专题 | 16:9       | 活动与首页 Banner |
| 商品细节 | 1:1        | 材质和配饰细节      |
| 角色拍照 | 3:4 / 9:16 | 分享图片         |

### **41.3 角色美术规范**

角色需要建立统一的美术风格规范：

- 头身比例统一。
- 面部风格统一。
- 眼睛材质统一。
- 肤色范围统一。
- 发型模型规范统一。
- 骨骼和挂载点统一。
- 不同角色风格可扩展，但基础模型体系必须兼容。
- 角色全身展示不能被 UI 裁切。
- 角色默认姿势要能展示服装轮廓。
- 角色拍照动作和普通换装姿势需要区分。

建议首期建立三类风格方向：

![A series of smiling and cute baby chibi dolls with the theme of painting are cre - SeaArt AI](https://images.openai.com/static-rsc-4/ij_MIfzDAJqWgWExCifIXScqRB1kmUefXdi4WrNYKmSbp9xMjCf8hAXTKRIMgcqeNqlW36FYx-xmdl0awN97K7-MkeoKYU7-V6k2lfH_DjGaH6YJShTeeLUV2e9jiTfdWr593txoRhnaeW5qsE9AlpKXg0O4exmWATUR8k7gR2Q?purpose=inline)

**甜美可爱系**

圆润、柔和、轻幻想

![【VRC / VRM 対応3Dモデル】柘榴 -Zakuro- ver1.03 - yoyogi mori - BOOTH](https://images.openai.com/static-rsc-4/N5e7oaG3MQxZGpmmguFa2SCOGP2A4w_UzcOxKCfeqf-gYD7eOUt6UdGNbKUaDUE29DrE2paxP2GWs-o95oIp_nSOCG-WTnB0XynTQjt7tNEcIxTKpOdCdtaG8ZQtT8jjfymzsk7JXNPtcAwCcCRxi2Qqk5P_3PGMUfOAv4RGs_0?purpose=inline)

**精致时装系**

比例修长、服装展示优先

![「ナナセ・ノワール」専用【3D衣装モデル】Rosalieru（ロザリエル） - Noah’sArk【α】 - BOOTH](https://images.openai.com/static-rsc-4/VPyWrDnVaSCZzmXWHcYjj3wXi3MGFJjhRqPXJ0HxX7MXi3g41ZpBUS1lPrb3OeSGk6DMJAn8wrz1dkin2PlbhE_2NN0RmDR4YAa_SKkcy5lPZgTDT3izD4806hIeAq4TTizi29ORGscswbZZ8IKZ8fJre24jQr19Otyogo0kmiU?purpose=inline)

**幻想个性系**

适合主题服装与创作

### **41.4 服装美术规范**

服装素材必须区分：

- 真实服装照片。
- AI 抠图素材。
- AI 补全素材。
- 适配后的虚拟服装。
- 原创虚拟服装。
- 官方授权服装。

禁止：

- 将 AI 生成背面当作真实背面。
- 擅自改变用户上传服装的明显图案。
- 擅自添加品牌 Logo。
- 将用户私有衣物作为公开素材。
- 用一张正面图伪装成完整 3D 服装。
- 将不同资产版本混合使用。

### **41.5 UI 图片使用规则**

- 所有关键功能页面必须使用真实产品素材或高保真占位素材。
- 不允许以空白灰色方块代替需要展示的角色或服装主体。
- 不允许用不相关的时尚照片冒充实际功能效果。
- 图片素材必须有来源和授权记录。
- 原始 V0.1 文档已有的图片引用应保留在原对应章节，不应因为增加新图而移除。
- 新增参考图片必须服务于具体设计说明。
- 最终设计交付需要替换为项目自有或授权使用的图片素材。

## **四十二、UI 状态、异常状态与可访问性规范**

### **42.1 每个页面必须设计的状态**

| 状态               | 说明    | UI 要求     |
| ---------------- | ----- | --------- |
| Default          | 默认状态  | 正常展示      |
| Loading          | 加载中   | 骨架屏或明确进度  |
| Empty            | 无内容   | 说明原因和下一步  |
| Error            | 请求失败  | 说明问题并提供重试 |
| Disabled         | 不可操作  | 明确禁用原因    |
| Selected         | 已选中   | 清晰选中态     |
| Processing       | 任务处理中 | 展示当前阶段    |
| Success          | 操作成功  | 轻量反馈      |
| PermissionDenied | 权限不足  | 说明权限原因    |
| Offline          | 网络不可用 | 提供恢复入口    |

### **42.2 空状态**

必须覆盖：

- 新用户没有衣物。
- 用户没有创建角色。
- 角色没有穿搭。
- 用户没有收藏。
- 社区没有内容。
- 搜索没有结果。
- 用户没有数字资产。
- 用户没有历史记录。

空状态必须包括：

1. 当前状态说明。
2. 为什么会出现。
3. 用户可以做什么。
4. 一个主要操作入口。
5. 必要时提供次要入口。

### **42.3 错误状态**

错误文案不能只写“系统错误”。

例如：

| 错误场景   | 不合格文案 | 合格文案方向            |
| ------ | ----- | ----------------- |
| 上传失败   | 上传失败  | 图片没有完整上传，请检查网络后重试 |
| 图片模糊   | 识别失败  | 图片较模糊，建议重新拍摄      |
| 审核拒绝   | 操作失败  | 该图片未通过内容审核，无法继续处理 |
| 识别超时   | 系统异常  | 识别服务暂时没有响应，可以稍后重试 |
| 资产生成失败 | 生成失败  | 服装素材生成未完成，原始衣物已保留 |
| 无权复用   | 操作失败  | 该创作者未开放此素材的复用权限   |
| 网络断开   | 网络错误  | 网络连接中断，当前编辑内容已暂存  |

### **42.4 可访问性**

- 文本与背景达到可读对比度。
- 关键操作不能只通过颜色区分。
- 重要控件提供明确文字标签。
- 触控区域满足移动端可操作要求。
- 支持系统字体放大。
- 动效支持减少动态效果设置。
- 不应使用过小字体承载核心信息。
- 角色和服装图片应提供适当的替代描述。
- 错误提示不能只使用短暂 Toast。

## **四十三、设计评审与研发验收流程**

### **43.1 UI 设计交付物**

设计团队必须交付：

1. 品牌 Logo、英文 Logo、应用图标。
2. 品牌色彩和字体规范。
3. Design Token。
4. 基础组件库。
5. 首页完整高保真设计。
6. 六大业务模块全页面设计。
7. 弹窗、抽屉、底部操作栏设计。
8. 空状态、加载状态、错误状态。
9. 上传、识别、生成、审核等完整状态设计。
10. 角色和服装展示的独立视觉规范。
11. 交互原型与页面跳转图。
12. 手机、平板、折叠屏适配规范。
13. 角色模型视觉规范。
14. 服装素材规范。
15. 社区内容卡片规范。
16. 活动和专题视觉规范。
17. 图标和插画资产。
18. 动效说明和交付文件。

### **43.2 设计评审流程**

\#chatgpt-mermaid-\_r_7dt\_{font-family:-apple-system-body,ui-sans-serif,-apple-system,system-ui,"Segoe UI",Helvetica,"Apple Color Emoji",Arial,sans-serif,"Segoe UI Emoji","Segoe UI Symbol";font-size:16px;fill:rgb(13, 13, 13);}@keyframes edge-animation-frame{from{stroke-dashoffset:0;}}@keyframes dash{to{stroke-dashoffset:0;}}#chatgpt-mermaid-\_r_7dt\_ .edge-animation-slow{stroke-dasharray:9,5!important;stroke-dashoffset:900;animation:dash 50s linear infinite;stroke-linecap:round;}#chatgpt-mermaid-\_r_7dt\_ .edge-animation-fast{stroke-dasharray:9,5!important;stroke-dashoffset:900;animation:dash 20s linear infinite;stroke-linecap:round;}#chatgpt-mermaid-\_r_7dt\_ .error-icon{fill:rgb(243, 243, 243);}#chatgpt-mermaid-\_r_7dt\_ .error-text{fill:rgb(13, 13, 13);stroke:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_7dt\_ .edge-thickness-normal{stroke-width:1px;}#chatgpt-mermaid-\_r_7dt\_ .edge-thickness-thick{stroke-width:3.5px;}#chatgpt-mermaid-\_r_7dt\_ .edge-pattern-solid{stroke-dasharray:0;}#chatgpt-mermaid-\_r_7dt\_ .edge-thickness-invisible{stroke-width:0;fill:none;}#chatgpt-mermaid-\_r_7dt\_ .edge-pattern-dashed{stroke-dasharray:3;}#chatgpt-mermaid-\_r_7dt\_ .edge-pattern-dotted{stroke-dasharray:2;}#chatgpt-mermaid-\_r_7dt\_ .marker{fill:rgb(143, 143, 143);stroke:rgb(143, 143, 143);}#chatgpt-mermaid-\_r_7dt\_ .marker.cross{stroke:rgb(143, 143, 143);}#chatgpt-mermaid-\_r_7dt\_ svg{font-family:-apple-system-body,ui-sans-serif,-apple-system,system-ui,"Segoe UI",Helvetica,"Apple Color Emoji",Arial,sans-serif,"Segoe UI Emoji","Segoe UI Symbol";font-size:16px;}#chatgpt-mermaid-\_r_7dt\_ p{margin:0;}#chatgpt-mermaid-\_r_7dt\_ .label{font-family:-apple-system-body,ui-sans-serif,-apple-system,system-ui,"Segoe UI",Helvetica,"Apple Color Emoji",Arial,sans-serif,"Segoe UI Emoji","Segoe UI Symbol";color:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_7dt\_ .cluster-label text{fill:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_7dt\_ .cluster-label span{color:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_7dt\_ .cluster-label span p{background-color:transparent;}#chatgpt-mermaid-\_r_7dt\_ .label text,#chatgpt-mermaid-\_r_7dt\_ span{fill:rgb(13, 13, 13);color:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_7dt\_ .node rect,#chatgpt-mermaid-\_r_7dt\_ .node circle,#chatgpt-mermaid-\_r_7dt\_ .node ellipse,#chatgpt-mermaid-\_r_7dt\_ .node polygon,#chatgpt-mermaid-\_r_7dt\_ .node path{fill:rgb(222, 234, 251);stroke:rgb(83, 154, 248);stroke-width:1px;}#chatgpt-mermaid-\_r_7dt\_ .rough-node .label text,#chatgpt-mermaid-\_r_7dt\_ .node .label text,#chatgpt-mermaid-\_r_7dt\_ .image-shape .label,#chatgpt-mermaid-\_r_7dt\_ .icon-shape .label{text-anchor:middle;}#chatgpt-mermaid-\_r_7dt\_ .node .katex path{fill:#000;stroke:#000;stroke-width:1px;}#chatgpt-mermaid-\_r_7dt\_ .rough-node .label,#chatgpt-mermaid-\_r_7dt\_ .node .label,#chatgpt-mermaid-\_r_7dt\_ .image-shape .label,#chatgpt-mermaid-\_r_7dt\_ .icon-shape .label{text-align:center;}#chatgpt-mermaid-\_r_7dt\_ .node.clickable{cursor:pointer;}#chatgpt-mermaid-\_r_7dt\_ .root .anchor path{fill:rgb(143, 143, 143)!important;stroke-width:0;stroke:rgb(143, 143, 143);}#chatgpt-mermaid-\_r_7dt\_ .arrowheadPath{fill:rgb(143, 143, 143);}#chatgpt-mermaid-\_r_7dt\_ .edgePath .path{stroke:rgb(143, 143, 143);stroke-width:1px;}#chatgpt-mermaid-\_r_7dt\_ .flowchart-link{stroke:rgb(143, 143, 143);fill:none;}#chatgpt-mermaid-\_r_7dt\_ .edgeLabel{background-color:rgb(252, 252, 252);text-align:center;}#chatgpt-mermaid-\_r_7dt\_ .edgeLabel p{background-color:rgb(252, 252, 252);}#chatgpt-mermaid-\_r_7dt\_ .edgeLabel rect{opacity:0.5;background-color:rgb(252, 252, 252);fill:rgb(252, 252, 252);}#chatgpt-mermaid-\_r_7dt\_ .labelBkg{background-color:rgba(252, 252, 252, 0.5);}#chatgpt-mermaid-\_r_7dt\_ .cluster rect{fill:rgb(243, 243, 243);stroke:rgba(0, 0, 0, 0.1);stroke-width:1px;}#chatgpt-mermaid-\_r_7dt\_ .cluster text{fill:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_7dt\_ .cluster span{color:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_7dt\_ div.mermaidTooltip{position:absolute;text-align:center;max-width:200px;padding:2px;font-family:-apple-system-body,ui-sans-serif,-apple-system,system-ui,"Segoe UI",Helvetica,"Apple Color Emoji",Arial,sans-serif,"Segoe UI Emoji","Segoe UI Symbol";font-size:12px;background:rgb(243, 243, 243);border:1px solid rgba(0, 0, 0, 0.1);border-radius:2px;pointer-events:none;z-index:100;}#chatgpt-mermaid-\_r_7dt\_ .flowchartTitleText{text-anchor:middle;font-size:18px;fill:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_7dt\_ rect.text{fill:none;stroke-width:0;}#chatgpt-mermaid-\_r_7dt\_ .icon-shape,#chatgpt-mermaid-\_r_7dt\_ .image-shape{background-color:rgb(252, 252, 252);text-align:center;}#chatgpt-mermaid-\_r_7dt\_ .icon-shape p,#chatgpt-mermaid-\_r_7dt\_ .image-shape p{background-color:rgb(252, 252, 252);padding:2px;}#chatgpt-mermaid-\_r_7dt\_ .icon-shape .label rect,#chatgpt-mermaid-\_r_7dt\_ .image-shape .label rect{opacity:0.5;background-color:rgb(252, 252, 252);fill:rgb(252, 252, 252);}#chatgpt-mermaid-\_r_7dt\_ .label-icon{display:inline-block;height:1em;overflow:visible;vertical-align:-0.125em;}#chatgpt-mermaid-\_r_7dt\_ .node .label-icon path{fill:currentColor;stroke:revert;stroke-width:revert;}#chatgpt-mermaid-\_r_7dt\_ .node .neo-node{stroke:rgb(83, 154, 248);}#chatgpt-mermaid-\_r_7dt\_ [data-look="neo"].node rect,#chatgpt-mermaid-\_r_7dt\_ [data-look="neo"].cluster rect,#chatgpt-mermaid-\_r_7dt\_ [data-look="neo"].node polygon{stroke:url(#chatgpt-mermaid-\_r_7dt\_-gradient);filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-\_r_7dt\_ [data-look="neo"].swimlane.cluster rect{filter:none;}#chatgpt-mermaid-\_r_7dt\_ [data-look="neo"].node path{stroke:url(#chatgpt-mermaid-\_r_7dt\_-gradient);stroke-width:1px;}#chatgpt-mermaid-\_r_7dt\_ [data-look="neo"].node .outer-path{filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-\_r_7dt\_ [data-look="neo"].node .neo-line path{stroke:rgb(83, 154, 248);filter:none;}#chatgpt-mermaid-\_r_7dt\_ [data-look="neo"].node circle{stroke:url(#chatgpt-mermaid-\_r_7dt\_-gradient);filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-\_r_7dt\_ [data-look="neo"].node circle .state-start{fill:#000000;}#chatgpt-mermaid-\_r_7dt\_ [data-look="neo"].icon-shape .icon{fill:url(#chatgpt-mermaid-\_r_7dt\_-gradient);filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-\_r_7dt\_ [data-look="neo"].icon-shape .icon-neo path{stroke:url(#chatgpt-mermaid-\_r_7dt\_-gradient);filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-\_r_7dt\_ .node text{font-size:14px;font-weight:600;letter-spacing:normal;fill:rgb(0, 79, 153);}#chatgpt-mermaid-\_r_7dt\_ .edgeLabels text{font-size:13px;font-weight:600;letter-spacing:-0.08px;fill:rgb(0, 79, 153);}#chatgpt-mermaid-\_r_7dt\_ .node tspan[font-weight="normal"],#chatgpt-mermaid-\_r_7dt\_ .edgeLabels tspan[font-weight="normal"]{font-weight:600;}#chatgpt-mermaid-\_r_7dt\_ .edgeLabel .label rect{opacity:1;rx:13px;ry:13px;fill:rgb(245, 250, 255);stroke:rgb(206, 219, 229);stroke-width:1px;}#chatgpt-mermaid-\_r_7dt\_ .node rect,#chatgpt-mermaid-\_r_7dt\_ .node circle,#chatgpt-mermaid-\_r_7dt\_ .node ellipse,#chatgpt-mermaid-\_r_7dt\_ .node polygon,#chatgpt-mermaid-\_r_7dt\_ .node path{fill:rgb(229, 243, 255);stroke:rgba(0, 0, 0, 0.1);stroke-width:1px;}#chatgpt-mermaid-\_r_7dt\_ .node rect{rx:16px;ry:16px;}#chatgpt-mermaid-\_r_7dt\_ .mermaid-decision .label-container{fill:rgb(245, 250, 255);stroke:rgb(206, 219, 229);stroke-dasharray:2,2;}#chatgpt-mermaid-\_r_7dt\_ .edgePaths .flowchart-link{stroke:rgb(143, 143, 143);stroke-width:1px;stroke-linecap:round;stroke-linejoin:round;}#chatgpt-mermaid-\_r_7dt\_ .marker{fill:rgb(143, 143, 143);stroke:rgb(143, 143, 143);}#chatgpt-mermaid-\_r_7dt\_ :root{--mermaid-font-family:-apple-system-body,ui-sans-serif,-apple-system,system-ui,"Segoe UI",Helvetica,"Apple Color Emoji",Arial,sans-serif,"Segoe UI Emoji","Segoe UI Symbol";}产品需求确认低保真线框产品评审高保真视觉设计设计系统与组件检查交互原型评审开发技术评审设计交付与标注开发实现设计走查缺陷修复最终验收

### **43.3 UI 验收标准**

| 编号     | 规范     | 验收标准                   |
| ------ | ------ | ---------------------- |
| UI-001 | 统一色彩系统 | 全部页面使用同一套 Design Token |
| UI-002 | 统一字体层级 | 标题、正文、辅助信息层级一致         |
| UI-003 | 统一圆角体系 | 按钮、卡片、弹窗使用统一圆角规范       |
| UI-004 | 图片比例规范 | 服装、角色、社区内容分别规定比例       |
| UI-005 | 统一图标风格 | 不混用不同描边和填充体系           |
| UI-006 | 组件状态完整 | 默认、选中、禁用、加载、错误状态齐全     |
| UI-007 | 空状态完整  | 新用户无衣物、无角色、无作品均有引导     |
| UI-008 | 异常状态完整 | 上传失败、生成失败、网络错误有恢复入口    |
| UI-009 | 动效统一   | 过渡时间、缓动、反馈规范统一         |
| UI-010 | 无障碍    | 文字对比度、触控区域、文字缩放符合要求    |
| UI-011 | 多尺寸适配  | 手机、平板、折叠屏布局有明确规则       |
| UI-012 | 性能约束   | 图片懒加载、缩略图、列表虚拟化        |
| UI-013 | 主题一致性  | 各业务模块保持品牌统一，不能各自独立设计   |
| UI-014 | 内容真实性  | 真实照片、AI 生成和虚拟资产明确区分    |

### **43.4 设计验收必须实际检查**

- 页面是否符合产品信息架构。
- 所有按钮是否有实际行为。
- 是否存在只有视觉、没有功能的控件。
- 是否设计完整异常状态。
- 是否出现内容遮挡和点击区域冲突。
- 是否保留用户编辑状态。
- 是否正确展示资产状态。
- 是否明确区分真实图片与 AI 生成图片。
- 是否在不同屏幕尺寸下保持主要操作可用。
- 是否满足角色与服装的展示比例。
- 是否存在不必要的动画导致操作延迟。
- 是否出现颜色、字体、图标和间距不统一。

## **四十四、原始内容保留与版本合并说明**

本 V1.0 的合并结构应包含以下全部内容：

| 原始章节          | 保留内容                           | V1.0 补充方向          |
| ------------- | ------------------------------ | ------------------ |
| 一、产品定位        | 个人数字衣橱、AI 穿搭、虚拟角色养成、UGC 时尚社区   | 用户场景、产品边界、价值飞轮     |
| 二、竞品参考与产品机制   | 奇迹暖暖、燕云十六声、ZEPETO、Acloset      | 机制拆解和差异化分析         |
| 三、核心产品结构      | 六大模块、首页、数字衣橱、角色工坊、身材系统、换装工坊    | 页面规格、模块依赖          |
| 四、衣物上传        | 上传入口、拍摄规范、审核、识别、2.5D 生成        | 安全校验、质量门禁、任务状态     |
| 五、AI 穿搭助手     | 主动推荐、聊天搭配、自动换装、上下文与推荐机制        | 模型路由、Schema、候选资产校验 |
| 六、分享与社区       | 分享对象、授权体系、社区页面                 | 授权状态机、举报、申诉        |
| 七、角色和服装素材技术选型 | CharacterStudio、VRM、Three.js 等 | PoC、兼容性和许可核查       |
| 八、商业模式        | 会员、商城、创作者市场、虚拟资产经济             | 额度、计费、订单和退款        |
| 九、版本规划        | V0.1、V1.0、V1.5、V2.0            | 研发工作包和里程碑          |
| 十、产品指标        | 北极星指标、业务指标、埋点                  | 指标口径和成本分析          |
| 十一、边界条件与风险    | 上传、识别、生成、授权、删除、成本              | 完整异常用例和验收          |
| 十二、最终产品形态     | 我的世界、我的衣橱、换装工坊、时尚社区            | 信息架构和 UI 线框        |
| 十三、立项结论       | 现实价值、情感价值、生态价值                 | 核心假设验证             |
| 十四、立项后工作      | 产品、角色、服装、换装、数据、AI、审核           | 具体交付物和评审流程         |

### **44.1 原始视觉素材保留规则**

原始 V0.1 文档中的视觉参考图片，必须保留在对应章节原有位置：

- 竞品章节的《奇迹暖暖》《燕云十六声》、ZEPETO、Acloset 图片。
- 数字衣橱分类中的上装、下装、连衣裙、外套、鞋靴、包袋、首饰、发饰图片。
- 角色工坊中的角色与捏脸参考图片。
- 身材系统中的不同体型参考图片。
- 换装工坊的游戏交互参考图片。
- 衣物上传与拍摄参考图片。
- 2.5D 素材生成参考图片。
- AI 穿搭参考图片。
- 分享社区参考图片。
- 角色技术选型参考图片。
- 产品最终形态的四个空间参考图片。

新增图片只能补充，不能替换原始图片。原图引用地址、对应说明和上下文均应保留。

### **44.2 本版本需要研发评审后才能冻结的事项**

下面这些内容是 V1.0 设计建议，不应该在未做 PoC 前当成已经验证的事实：

1. CharacterStudio 对目标角色风格、模型编辑和移动端性能的实际支持程度。
2. VRM/GLB 的最终资源标准，以及是否需要自定义扩展。
3. Flutter 与 Three.js 渲染模块之间采用 WebView、独立原生渲染层还是其他集成方案。
4. SAM2、MediaPipe 或商业分割服务的最终选型。
5. 各类服装的 2.5D 生成质量和适配上限。
6. 不同体型之间的服装兼容范围。
7. 是否支持真实背面生成以及如何展示 AI 推测信息。
8. 会员额度、订阅价格和单次生成成本。
9. 图片审核服务商、API 版本、地域、价格和服务 SLA。
10. 对象存储、数据库、任务队列和部署架构的最终选型。
11. 首期角色模型的美术风格和资源授权。
12. 真实衣物转化为虚拟服装的人工修正比例。
13. 不同设备上的 3D 渲染性能。
14. 服装遮挡和不同体型适配的可实现范围。
15. 品牌中文名、英文名、商标和域名的最终确定。

## **四十五、最终版本结论与研发执行要求**

这份 V1.0 文档的目标，是把原始产品构想推进到可以进行产品评审、技术评估、UI 设计、研发拆分和测试验收的层级。

核心需要交付四类能力：

**第一类：产品体验**

- 完整的数字衣橱。
- 可创建和编辑的虚拟角色。
- 真实衣物到数字服装资产的生产流程。
- 角色换装和穿搭保存。
- AI 方案推荐和执行。
- 作品分享与社区。

**第二类：技术系统**

- 用户与权限系统。
- 衣物资产数据库。
- 角色模型、骨骼和 Morph 系统。
- 服装资产 Manifest、锚点、图层和适配系统。
- AI 识别、分割、生成和推荐服务。
- 异步任务、审核状态和失败恢复。
- 授权、版本和资产溯源。

**第三类：研发与测试**

- 页面交互规格。
- ERD 和数据字典。
- API 契约。
- 状态机。
- 异常场景。
- P0/P1 测试用例。
- 非功能需求。
- 上线阻断条件。
- 研发里程碑。

**第四类：品牌与视觉**

- 中英文品牌名称。
- Logo 和应用图标。
- 统一色彩、字体和 Design Token。
- 六大模块视觉规范。
- 首页、衣橱、角色工坊、换装、AI、社区高保真设计。
- 手机、平板、折叠屏适配。
- 角色和服装美术规范。
- 完整空状态、异常状态和动效规范。

### **45.1 最终推荐的产品定位**

# **衣间星河**

# **VESTORIA**

![Wall Rentals | Explore Our Stunning Options — Flora Blossa](https://images.openai.com/static-rsc-4/Xo_On3_J0zYWPHfTTgT_EnxvzuVcb0iPMOZ3ReYjJaa1oKBxFM_AscUo-4a9CqWvZg3a6D9Ao-IK1vOJ6TYnI3gcx6U7RXwYIGna82L5DHaF8sHib2El81wpLJr3pbxyLoLqVfuITJJE63UlTnY-NPyy-hmON4iLkCoUmO2Tnag?purpose=inline)

![florablossa.com](https://www.florablossa.com/wall-rentals?utm_source=chatgpt.com)

## **你的数字衣橱，也是你的时尚世界。**

YOUR STYLE, YOUR UNIVERSE

**核心体验**

- 现实：管理自己的衣服，理解自己的穿衣风格。
- 智能：AI 根据衣橱、场景和偏好提供穿搭建议。
- 虚拟：创建自己的数字形象，进行试穿与创作。
- 社交：分享作品、发现灵感、参与时尚社区。
- 资产：沉淀个人服装素材、原创设计和可授权数字内容。

### **45.2 首期研发优先级**

1. 先验证角色模型和服装资产能否真正兼容。
2. 再打通衣物上传、审核、识别、分割、资产生成。
3. 完成角色换装、服装调整和穿搭保存。
4. 完成 AI 从真实衣橱中选择服装并执行搭配。
5. 完成基础分享、隐私、审核和内容治理。
6. 最后再扩展社区增长、会员商业化和创作者市场。

**不要先做大量没有真实资产支撑的 UI 页面，也不要把“AI 能生成一张穿搭图片”当成核心链路完成。** 真正需要验证的是：用户的真实衣物能否稳定变成数字资产，数字资产能否在角色上正确穿戴，AI 能否调用这些真实资产完成搭配，并且整个过程可以保存、恢复、分享和追溯。

**版本说明：** 上述正文已经把产品原始规划的业务范围、V1.0 研发规格、独立角色与服装技术方案，以及品牌和 UI 设计规范整合到同一套章节结构中。需要特别说明的是，当前聊天正文中的原始第一至十四章是按原始内容重组扩写的完整业务基线，并非逐字复制原始文件的 1306 行；原文件中每一条原始图片 URL 也尚未逐条复录到这里。因此，不能把这份聊天稿误称为“原文件逐字无损合并版”。如果按你要求的严格无删减标准验收，必须再逐段对照原始文件，将原始图链和文字逐项核对后才能确认。
