# **AI 数字衣橱与虚拟时尚社区**

# **产品需求文档 V1.0**

正式研发规格 · 原始 V0.1 基线 + 追加式研发设计 · 2026.11

## **文档控制与阅读说明**

### **版本关系**

| 文档        | 定位                        | 处理规则           |
| --------- | ------------------------- | -------------- |
| V0.1 原始初稿 | 产品定位、竞品、业务构想、技术方向和立项建议    | 全部保留，不删改       |
| V1.0 新增规格 | 产品交互、技术架构、数据、接口、AI 工作流、测试 | 追加，不覆盖原文       |
| 角色与服装技术方案 | 角色模型、身材形变、服装资产、锚点、图层和渲染   | 独立技术章节         |
| 验收与测试规范   | 正常流程、异常流程、边界、上线门槛         | 作为研发和 QA 的验收依据 |

### **三种规格的标识**

- **[产品需求 PRD]**：定义用户能看到什么、能做什么、页面如何交互。
- **[技术设计 TECH]**：定义数据、接口、模型、任务、权限、渲染和系统行为。
- **[验收标准 AC]**：定义什么条件算完成，如何验证正常和异常情况。

### **本版本的关键约束**

1. 真实衣物照片、AI 生成的服装素材、虚拟角色服装资产是不同的数据对象，不能混为一谈。
2. 上传、审核、识别、分割、生成、人工确认、适配、发布必须有独立状态。
3. AI 生成结果不得直接覆盖用户原始图片。
4. 用户的私人衣橱默认私有，分享作品不等于授权原始服装资产。
5. 第一阶段采用 3D 角色与 2D/2.5D 服装素材混合方案，不承诺任意真实服装自动重建为完整 360° 3D 网格。
6. LLM 负责理解需求和生成搭配决策，确定性规则负责资产约束，渲染引擎负责执行。
7. 所有异步任务必须有任务 ID、状态、重试、超时、失败原因和可追溯记录。

## **十五、产品范围、角色权限与核心业务规则**

### **15.1 产品边界**

**[产品需求 PRD]**

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

**[技术设计 TECH]**

所有业务数据必须具备明确的所有权字段：

- `owner_user_id`
- `tenant_id`（如未来支持机构或团队）
- `visibility`
- `created_by`
- `updated_by`

所有权校验必须在服务端执行。前端隐藏入口不构成权限控制。

### **15.3 账号与资产权限模型**

\#chatgpt-mermaid-\_r_362\_{font-family:-apple-system-body,ui-sans-serif,-apple-system,system-ui,"Segoe UI",Helvetica,"Apple Color Emoji",Arial,sans-serif,"Segoe UI Emoji","Segoe UI Symbol";font-size:16px;fill:rgb(13, 13, 13);}@keyframes edge-animation-frame{from{stroke-dashoffset:0;}}@keyframes dash{to{stroke-dashoffset:0;}}#chatgpt-mermaid-\_r_362\_ .edge-animation-slow{stroke-dasharray:9,5!important;stroke-dashoffset:900;animation:dash 50s linear infinite;stroke-linecap:round;}#chatgpt-mermaid-\_r_362\_ .edge-animation-fast{stroke-dasharray:9,5!important;stroke-dashoffset:900;animation:dash 20s linear infinite;stroke-linecap:round;}#chatgpt-mermaid-\_r_362\_ .error-icon{fill:rgb(243, 243, 243);}#chatgpt-mermaid-\_r_362\_ .error-text{fill:rgb(13, 13, 13);stroke:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_362\_ .edge-thickness-normal{stroke-width:1px;}#chatgpt-mermaid-\_r_362\_ .edge-thickness-thick{stroke-width:3.5px;}#chatgpt-mermaid-\_r_362\_ .edge-pattern-solid{stroke-dasharray:0;}#chatgpt-mermaid-\_r_362\_ .edge-thickness-invisible{stroke-width:0;fill:none;}#chatgpt-mermaid-\_r_362\_ .edge-pattern-dashed{stroke-dasharray:3;}#chatgpt-mermaid-\_r_362\_ .edge-pattern-dotted{stroke-dasharray:2;}#chatgpt-mermaid-\_r_362\_ .marker{fill:rgb(143, 143, 143);stroke:rgb(143, 143, 143);}#chatgpt-mermaid-\_r_362\_ .marker.cross{stroke:rgb(143, 143, 143);}#chatgpt-mermaid-\_r_362\_ svg{font-family:-apple-system-body,ui-sans-serif,-apple-system,system-ui,"Segoe UI",Helvetica,"Apple Color Emoji",Arial,sans-serif,"Segoe UI Emoji","Segoe UI Symbol";font-size:16px;}#chatgpt-mermaid-\_r_362\_ p{margin:0;}#chatgpt-mermaid-\_r_362\_ .label{font-family:-apple-system-body,ui-sans-serif,-apple-system,system-ui,"Segoe UI",Helvetica,"Apple Color Emoji",Arial,sans-serif,"Segoe UI Emoji","Segoe UI Symbol";color:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_362\_ .cluster-label text{fill:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_362\_ .cluster-label span{color:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_362\_ .cluster-label span p{background-color:transparent;}#chatgpt-mermaid-\_r_362\_ .label text,#chatgpt-mermaid-\_r_362\_ span{fill:rgb(13, 13, 13);color:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_362\_ .node rect,#chatgpt-mermaid-\_r_362\_ .node circle,#chatgpt-mermaid-\_r_362\_ .node ellipse,#chatgpt-mermaid-\_r_362\_ .node polygon,#chatgpt-mermaid-\_r_362\_ .node path{fill:rgb(222, 234, 251);stroke:rgb(83, 154, 248);stroke-width:1px;}#chatgpt-mermaid-\_r_362\_ .rough-node .label text,#chatgpt-mermaid-\_r_362\_ .node .label text,#chatgpt-mermaid-\_r_362\_ .image-shape .label,#chatgpt-mermaid-\_r_362\_ .icon-shape .label{text-anchor:middle;}#chatgpt-mermaid-\_r_362\_ .node .katex path{fill:#000;stroke:#000;stroke-width:1px;}#chatgpt-mermaid-\_r_362\_ .rough-node .label,#chatgpt-mermaid-\_r_362\_ .node .label,#chatgpt-mermaid-\_r_362\_ .image-shape .label,#chatgpt-mermaid-\_r_362\_ .icon-shape .label{text-align:center;}#chatgpt-mermaid-\_r_362\_ .node.clickable{cursor:pointer;}#chatgpt-mermaid-\_r_362\_ .root .anchor path{fill:rgb(143, 143, 143)!important;stroke-width:0;stroke:rgb(143, 143, 143);}#chatgpt-mermaid-\_r_362\_ .arrowheadPath{fill:rgb(143, 143, 143);}#chatgpt-mermaid-\_r_362\_ .edgePath .path{stroke:rgb(143, 143, 143);stroke-width:1px;}#chatgpt-mermaid-\_r_362\_ .flowchart-link{stroke:rgb(143, 143, 143);fill:none;}#chatgpt-mermaid-\_r_362\_ .edgeLabel{background-color:rgb(252, 252, 252);text-align:center;}#chatgpt-mermaid-\_r_362\_ .edgeLabel p{background-color:rgb(252, 252, 252);}#chatgpt-mermaid-\_r_362\_ .edgeLabel rect{opacity:0.5;background-color:rgb(252, 252, 252);fill:rgb(252, 252, 252);}#chatgpt-mermaid-\_r_362\_ .labelBkg{background-color:rgba(252, 252, 252, 0.5);}#chatgpt-mermaid-\_r_362\_ .cluster rect{fill:rgb(243, 243, 243);stroke:rgba(0, 0, 0, 0.1);stroke-width:1px;}#chatgpt-mermaid-\_r_362\_ .cluster text{fill:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_362\_ .cluster span{color:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_362\_ div.mermaidTooltip{position:absolute;text-align:center;max-width:200px;padding:2px;font-family:-apple-system-body,ui-sans-serif,-apple-system,system-ui,"Segoe UI",Helvetica,"Apple Color Emoji",Arial,sans-serif,"Segoe UI Emoji","Segoe UI Symbol";font-size:12px;background:rgb(243, 243, 243);border:1px solid rgba(0, 0, 0, 0.1);border-radius:2px;pointer-events:none;z-index:100;}#chatgpt-mermaid-\_r_362\_ .flowchartTitleText{text-anchor:middle;font-size:18px;fill:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_362\_ rect.text{fill:none;stroke-width:0;}#chatgpt-mermaid-\_r_362\_ .icon-shape,#chatgpt-mermaid-\_r_362\_ .image-shape{background-color:rgb(252, 252, 252);text-align:center;}#chatgpt-mermaid-\_r_362\_ .icon-shape p,#chatgpt-mermaid-\_r_362\_ .image-shape p{background-color:rgb(252, 252, 252);padding:2px;}#chatgpt-mermaid-\_r_362\_ .icon-shape .label rect,#chatgpt-mermaid-\_r_362\_ .image-shape .label rect{opacity:0.5;background-color:rgb(252, 252, 252);fill:rgb(252, 252, 252);}#chatgpt-mermaid-\_r_362\_ .label-icon{display:inline-block;height:1em;overflow:visible;vertical-align:-0.125em;}#chatgpt-mermaid-\_r_362\_ .node .label-icon path{fill:currentColor;stroke:revert;stroke-width:revert;}#chatgpt-mermaid-\_r_362\_ .node .neo-node{stroke:rgb(83, 154, 248);}#chatgpt-mermaid-\_r_362\_ [data-look="neo"].node rect,#chatgpt-mermaid-\_r_362\_ [data-look="neo"].cluster rect,#chatgpt-mermaid-\_r_362\_ [data-look="neo"].node polygon{stroke:url(#chatgpt-mermaid-\_r_362\_-gradient);filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-\_r_362\_ [data-look="neo"].swimlane.cluster rect{filter:none;}#chatgpt-mermaid-\_r_362\_ [data-look="neo"].node path{stroke:url(#chatgpt-mermaid-\_r_362\_-gradient);stroke-width:1px;}#chatgpt-mermaid-\_r_362\_ [data-look="neo"].node .outer-path{filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-\_r_362\_ [data-look="neo"].node .neo-line path{stroke:rgb(83, 154, 248);filter:none;}#chatgpt-mermaid-\_r_362\_ [data-look="neo"].node circle{stroke:url(#chatgpt-mermaid-\_r_362\_-gradient);filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-\_r_362\_ [data-look="neo"].node circle .state-start{fill:#000000;}#chatgpt-mermaid-\_r_362\_ [data-look="neo"].icon-shape .icon{fill:url(#chatgpt-mermaid-\_r_362\_-gradient);filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-\_r_362\_ [data-look="neo"].icon-shape .icon-neo path{stroke:url(#chatgpt-mermaid-\_r_362\_-gradient);filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-\_r_362\_ .node text{font-size:14px;font-weight:600;letter-spacing:normal;fill:rgb(0, 79, 153);}#chatgpt-mermaid-\_r_362\_ .edgeLabels text{font-size:13px;font-weight:600;letter-spacing:-0.08px;fill:rgb(0, 79, 153);}#chatgpt-mermaid-\_r_362\_ .node tspan[font-weight="normal"],#chatgpt-mermaid-\_r_362\_ .edgeLabels tspan[font-weight="normal"]{font-weight:600;}#chatgpt-mermaid-\_r_362\_ .edgeLabel .label rect{opacity:1;rx:13px;ry:13px;fill:rgb(245, 250, 255);stroke:rgb(206, 219, 229);stroke-width:1px;}#chatgpt-mermaid-\_r_362\_ .node rect,#chatgpt-mermaid-\_r_362\_ .node circle,#chatgpt-mermaid-\_r_362\_ .node ellipse,#chatgpt-mermaid-\_r_362\_ .node polygon,#chatgpt-mermaid-\_r_362\_ .node path{fill:rgb(229, 243, 255);stroke:rgba(0, 0, 0, 0.1);stroke-width:1px;}#chatgpt-mermaid-\_r_362\_ .node rect{rx:16px;ry:16px;}#chatgpt-mermaid-\_r_362\_ .mermaid-decision .label-container{fill:rgb(245, 250, 255);stroke:rgb(206, 219, 229);stroke-dasharray:2,2;}#chatgpt-mermaid-\_r_362\_ .edgePaths .flowchart-link{stroke:rgb(143, 143, 143);stroke-width:1px;stroke-linecap:round;stroke-linejoin:round;}#chatgpt-mermaid-\_r_362\_ .marker{fill:rgb(143, 143, 143);stroke:rgb(143, 143, 143);}#chatgpt-mermaid-\_r_362\_ :root{--mermaid-font-family:-apple-system-body,ui-sans-serif,-apple-system,system-ui,"Segoe UI",Helvetica,"Apple Color Emoji",Arial,sans-serif,"Segoe UI Emoji","Segoe UI Symbol";}用户账号个人空间个人衣橱角色列表穿搭作品私有服装资产授权记录分享设置公开展示免费复用授权付费授权其他用户浏览其他用户复用授权交易

### **15.4 核心业务规则**

| 规则 ID  | 规则               | 处理要求        |
| ------ | ---------------- | ----------- |
| BR-001 | 新建衣物默认私有         | 不进入公开搜索     |
| BR-002 | 新建角色默认私有         | 不自动生成公开主页   |
| BR-003 | 公开作品不代表资产公开      | 作品和资产分别授权   |
| BR-004 | AI 生成结果必须关联原始任务  | 可以追踪输入和模型版本 |
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

**[产品需求 PRD]**

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

\#chatgpt-mermaid-\_r_369\_{font-family:-apple-system-body,ui-sans-serif,-apple-system,system-ui,"Segoe UI",Helvetica,"Apple Color Emoji",Arial,sans-serif,"Segoe UI Emoji","Segoe UI Symbol";font-size:16px;fill:rgb(13, 13, 13);}@keyframes edge-animation-frame{from{stroke-dashoffset:0;}}@keyframes dash{to{stroke-dashoffset:0;}}#chatgpt-mermaid-\_r_369\_ .edge-animation-slow{stroke-dasharray:9,5!important;stroke-dashoffset:900;animation:dash 50s linear infinite;stroke-linecap:round;}#chatgpt-mermaid-\_r_369\_ .edge-animation-fast{stroke-dasharray:9,5!important;stroke-dashoffset:900;animation:dash 20s linear infinite;stroke-linecap:round;}#chatgpt-mermaid-\_r_369\_ .error-icon{fill:rgb(243, 243, 243);}#chatgpt-mermaid-\_r_369\_ .error-text{fill:rgb(13, 13, 13);stroke:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_369\_ .edge-thickness-normal{stroke-width:1px;}#chatgpt-mermaid-\_r_369\_ .edge-thickness-thick{stroke-width:3.5px;}#chatgpt-mermaid-\_r_369\_ .edge-pattern-solid{stroke-dasharray:0;}#chatgpt-mermaid-\_r_369\_ .edge-thickness-invisible{stroke-width:0;fill:none;}#chatgpt-mermaid-\_r_369\_ .edge-pattern-dashed{stroke-dasharray:3;}#chatgpt-mermaid-\_r_369\_ .edge-pattern-dotted{stroke-dasharray:2;}#chatgpt-mermaid-\_r_369\_ .marker{fill:rgb(143, 143, 143);stroke:rgb(143, 143, 143);}#chatgpt-mermaid-\_r_369\_ .marker.cross{stroke:rgb(143, 143, 143);}#chatgpt-mermaid-\_r_369\_ svg{font-family:-apple-system-body,ui-sans-serif,-apple-system,system-ui,"Segoe UI",Helvetica,"Apple Color Emoji",Arial,sans-serif,"Segoe UI Emoji","Segoe UI Symbol";font-size:16px;}#chatgpt-mermaid-\_r_369\_ p{margin:0;}#chatgpt-mermaid-\_r_369\_ .label{font-family:-apple-system-body,ui-sans-serif,-apple-system,system-ui,"Segoe UI",Helvetica,"Apple Color Emoji",Arial,sans-serif,"Segoe UI Emoji","Segoe UI Symbol";color:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_369\_ .cluster-label text{fill:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_369\_ .cluster-label span{color:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_369\_ .cluster-label span p{background-color:transparent;}#chatgpt-mermaid-\_r_369\_ .label text,#chatgpt-mermaid-\_r_369\_ span{fill:rgb(13, 13, 13);color:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_369\_ .node rect,#chatgpt-mermaid-\_r_369\_ .node circle,#chatgpt-mermaid-\_r_369\_ .node ellipse,#chatgpt-mermaid-\_r_369\_ .node polygon,#chatgpt-mermaid-\_r_369\_ .node path{fill:rgb(222, 234, 251);stroke:rgb(83, 154, 248);stroke-width:1px;}#chatgpt-mermaid-\_r_369\_ .rough-node .label text,#chatgpt-mermaid-\_r_369\_ .node .label text,#chatgpt-mermaid-\_r_369\_ .image-shape .label,#chatgpt-mermaid-\_r_369\_ .icon-shape .label{text-anchor:middle;}#chatgpt-mermaid-\_r_369\_ .node .katex path{fill:#000;stroke:#000;stroke-width:1px;}#chatgpt-mermaid-\_r_369\_ .rough-node .label,#chatgpt-mermaid-\_r_369\_ .node .label,#chatgpt-mermaid-\_r_369\_ .image-shape .label,#chatgpt-mermaid-\_r_369\_ .icon-shape .label{text-align:center;}#chatgpt-mermaid-\_r_369\_ .node.clickable{cursor:pointer;}#chatgpt-mermaid-\_r_369\_ .root .anchor path{fill:rgb(143, 143, 143)!important;stroke-width:0;stroke:rgb(143, 143, 143);}#chatgpt-mermaid-\_r_369\_ .arrowheadPath{fill:rgb(143, 143, 143);}#chatgpt-mermaid-\_r_369\_ .edgePath .path{stroke:rgb(143, 143, 143);stroke-width:1px;}#chatgpt-mermaid-\_r_369\_ .flowchart-link{stroke:rgb(143, 143, 143);fill:none;}#chatgpt-mermaid-\_r_369\_ .edgeLabel{background-color:rgb(252, 252, 252);text-align:center;}#chatgpt-mermaid-\_r_369\_ .edgeLabel p{background-color:rgb(252, 252, 252);}#chatgpt-mermaid-\_r_369\_ .edgeLabel rect{opacity:0.5;background-color:rgb(252, 252, 252);fill:rgb(252, 252, 252);}#chatgpt-mermaid-\_r_369\_ .labelBkg{background-color:rgba(252, 252, 252, 0.5);}#chatgpt-mermaid-\_r_369\_ .cluster rect{fill:rgb(243, 243, 243);stroke:rgba(0, 0, 0, 0.1);stroke-width:1px;}#chatgpt-mermaid-\_r_369\_ .cluster text{fill:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_369\_ .cluster span{color:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_369\_ div.mermaidTooltip{position:absolute;text-align:center;max-width:200px;padding:2px;font-family:-apple-system-body,ui-sans-serif,-apple-system,system-ui,"Segoe UI",Helvetica,"Apple Color Emoji",Arial,sans-serif,"Segoe UI Emoji","Segoe UI Symbol";font-size:12px;background:rgb(243, 243, 243);border:1px solid rgba(0, 0, 0, 0.1);border-radius:2px;pointer-events:none;z-index:100;}#chatgpt-mermaid-\_r_369\_ .flowchartTitleText{text-anchor:middle;font-size:18px;fill:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_369\_ rect.text{fill:none;stroke-width:0;}#chatgpt-mermaid-\_r_369\_ .icon-shape,#chatgpt-mermaid-\_r_369\_ .image-shape{background-color:rgb(252, 252, 252);text-align:center;}#chatgpt-mermaid-\_r_369\_ .icon-shape p,#chatgpt-mermaid-\_r_369\_ .image-shape p{background-color:rgb(252, 252, 252);padding:2px;}#chatgpt-mermaid-\_r_369\_ .icon-shape .label rect,#chatgpt-mermaid-\_r_369\_ .image-shape .label rect{opacity:0.5;background-color:rgb(252, 252, 252);fill:rgb(252, 252, 252);}#chatgpt-mermaid-\_r_369\_ .label-icon{display:inline-block;height:1em;overflow:visible;vertical-align:-0.125em;}#chatgpt-mermaid-\_r_369\_ .node .label-icon path{fill:currentColor;stroke:revert;stroke-width:revert;}#chatgpt-mermaid-\_r_369\_ .node .neo-node{stroke:rgb(83, 154, 248);}#chatgpt-mermaid-\_r_369\_ [data-look="neo"].node rect,#chatgpt-mermaid-\_r_369\_ [data-look="neo"].cluster rect,#chatgpt-mermaid-\_r_369\_ [data-look="neo"].node polygon{stroke:url(#chatgpt-mermaid-\_r_369\_-gradient);filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-\_r_369\_ [data-look="neo"].swimlane.cluster rect{filter:none;}#chatgpt-mermaid-\_r_369\_ [data-look="neo"].node path{stroke:url(#chatgpt-mermaid-\_r_369\_-gradient);stroke-width:1px;}#chatgpt-mermaid-\_r_369\_ [data-look="neo"].node .outer-path{filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-\_r_369\_ [data-look="neo"].node .neo-line path{stroke:rgb(83, 154, 248);filter:none;}#chatgpt-mermaid-\_r_369\_ [data-look="neo"].node circle{stroke:url(#chatgpt-mermaid-\_r_369\_-gradient);filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-\_r_369\_ [data-look="neo"].node circle .state-start{fill:#000000;}#chatgpt-mermaid-\_r_369\_ [data-look="neo"].icon-shape .icon{fill:url(#chatgpt-mermaid-\_r_369\_-gradient);filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-\_r_369\_ [data-look="neo"].icon-shape .icon-neo path{stroke:url(#chatgpt-mermaid-\_r_369\_-gradient);filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-\_r_369\_ .node text{font-size:14px;font-weight:600;letter-spacing:normal;fill:rgb(0, 79, 153);}#chatgpt-mermaid-\_r_369\_ .edgeLabels text{font-size:13px;font-weight:600;letter-spacing:-0.08px;fill:rgb(0, 79, 153);}#chatgpt-mermaid-\_r_369\_ .node tspan[font-weight="normal"],#chatgpt-mermaid-\_r_369\_ .edgeLabels tspan[font-weight="normal"]{font-weight:600;}#chatgpt-mermaid-\_r_369\_ .edgeLabel .label rect{opacity:1;rx:13px;ry:13px;fill:rgb(245, 250, 255);stroke:rgb(206, 219, 229);stroke-width:1px;}#chatgpt-mermaid-\_r_369\_ .node rect,#chatgpt-mermaid-\_r_369\_ .node circle,#chatgpt-mermaid-\_r_369\_ .node ellipse,#chatgpt-mermaid-\_r_369\_ .node polygon,#chatgpt-mermaid-\_r_369\_ .node path{fill:rgb(229, 243, 255);stroke:rgba(0, 0, 0, 0.1);stroke-width:1px;}#chatgpt-mermaid-\_r_369\_ .node rect{rx:16px;ry:16px;}#chatgpt-mermaid-\_r_369\_ .mermaid-decision .label-container{fill:rgb(245, 250, 255);stroke:rgb(206, 219, 229);stroke-dasharray:2,2;}#chatgpt-mermaid-\_r_369\_ .edgePaths .flowchart-link{stroke:rgb(143, 143, 143);stroke-width:1px;stroke-linecap:round;stroke-linejoin:round;}#chatgpt-mermaid-\_r_369\_ .marker{fill:rgb(143, 143, 143);stroke:rgb(143, 143, 143);}#chatgpt-mermaid-\_r_369\_ :root{--mermaid-font-family:-apple-system-body,ui-sans-serif,-apple-system,system-ui,"Segoe UI",Helvetica,"Apple Color Emoji",Arial,sans-serif,"Segoe UI Emoji","Segoe UI Symbol";}首页我的衣橱角色工坊换装工坊AI穿搭发现社区上传衣物安全检查AI识别用户确认服装资产预览创建角色身材编辑保存穿搭搭配方案分享设置作品详情

### **16.4 页面交互规格：HOME-001 首页**

**[产品需求 PRD]**

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

**[验收标准 AC]**

- 首页必须在无角色、无衣物、无网络、推荐服务失败情况下可正常展示。
- 角色切换后，首页所有角色相关内容同步更新。
- 不得把其他用户的私有衣物展示在推荐区域。
- 点击快捷入口必须进入对应业务流程，不得出现无响应控件。

### **16.5 页面交互规格：WARD-003 上传入口**

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

### **16.6 页面交互规格：WARD-006 AI 识别确认**

**[产品需求 PRD]**

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

**[验收标准 AC]**

- 用户修改后保存的数据必须覆盖 AI 初始建议，但保留 AI 识别历史。
- 用户可以跳过非必要属性。
- 分类修改后，相关身体部位和锚点配置应重新计算。
- 识别失败时仍允许用户手动录入衣物。
- 用户未确认之前，不得将资产标记为正式可穿戴。

### **16.7 页面交互规格：AVATAR-004 身材编辑**

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

**[技术设计 TECH]**

身材参数采用归一化数值，例如 0—1。前端滑块值必须由后端保存的参数范围校验，不接受任意浮点值。

身材配置版本应记录：

- `body_profile_id`
- `avatar_id`
- `body_template_id`
- `morph_parameters`
- `version`
- `created_at`
- `updated_at`

## **十七、核心业务流程与状态机**

### **17.1 端到端衣物数字化流程**

**[技术设计 TECH]**

\#chatgpt-mermaid-\_r_36g\_{font-family:-apple-system-body,ui-sans-serif,-apple-system,system-ui,"Segoe UI",Helvetica,"Apple Color Emoji",Arial,sans-serif,"Segoe UI Emoji","Segoe UI Symbol";font-size:16px;fill:rgb(13, 13, 13);}@keyframes edge-animation-frame{from{stroke-dashoffset:0;}}@keyframes dash{to{stroke-dashoffset:0;}}#chatgpt-mermaid-\_r_36g\_ .edge-animation-slow{stroke-dasharray:9,5!important;stroke-dashoffset:900;animation:dash 50s linear infinite;stroke-linecap:round;}#chatgpt-mermaid-\_r_36g\_ .edge-animation-fast{stroke-dasharray:9,5!important;stroke-dashoffset:900;animation:dash 20s linear infinite;stroke-linecap:round;}#chatgpt-mermaid-\_r_36g\_ .error-icon{fill:rgb(243, 243, 243);}#chatgpt-mermaid-\_r_36g\_ .error-text{fill:rgb(13, 13, 13);stroke:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_36g\_ .edge-thickness-normal{stroke-width:1px;}#chatgpt-mermaid-\_r_36g\_ .edge-thickness-thick{stroke-width:3.5px;}#chatgpt-mermaid-\_r_36g\_ .edge-pattern-solid{stroke-dasharray:0;}#chatgpt-mermaid-\_r_36g\_ .edge-thickness-invisible{stroke-width:0;fill:none;}#chatgpt-mermaid-\_r_36g\_ .edge-pattern-dashed{stroke-dasharray:3;}#chatgpt-mermaid-\_r_36g\_ .edge-pattern-dotted{stroke-dasharray:2;}#chatgpt-mermaid-\_r_36g\_ .marker{fill:rgb(143, 143, 143);stroke:rgb(143, 143, 143);}#chatgpt-mermaid-\_r_36g\_ .marker.cross{stroke:rgb(143, 143, 143);}#chatgpt-mermaid-\_r_36g\_ svg{font-family:-apple-system-body,ui-sans-serif,-apple-system,system-ui,"Segoe UI",Helvetica,"Apple Color Emoji",Arial,sans-serif,"Segoe UI Emoji","Segoe UI Symbol";font-size:16px;}#chatgpt-mermaid-\_r_36g\_ p{margin:0;}#chatgpt-mermaid-\_r_36g\_ .label{font-family:-apple-system-body,ui-sans-serif,-apple-system,system-ui,"Segoe UI",Helvetica,"Apple Color Emoji",Arial,sans-serif,"Segoe UI Emoji","Segoe UI Symbol";color:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_36g\_ .cluster-label text{fill:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_36g\_ .cluster-label span{color:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_36g\_ .cluster-label span p{background-color:transparent;}#chatgpt-mermaid-\_r_36g\_ .label text,#chatgpt-mermaid-\_r_36g\_ span{fill:rgb(13, 13, 13);color:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_36g\_ .node rect,#chatgpt-mermaid-\_r_36g\_ .node circle,#chatgpt-mermaid-\_r_36g\_ .node ellipse,#chatgpt-mermaid-\_r_36g\_ .node polygon,#chatgpt-mermaid-\_r_36g\_ .node path{fill:rgb(222, 234, 251);stroke:rgb(83, 154, 248);stroke-width:1px;}#chatgpt-mermaid-\_r_36g\_ .rough-node .label text,#chatgpt-mermaid-\_r_36g\_ .node .label text,#chatgpt-mermaid-\_r_36g\_ .image-shape .label,#chatgpt-mermaid-\_r_36g\_ .icon-shape .label{text-anchor:middle;}#chatgpt-mermaid-\_r_36g\_ .node .katex path{fill:#000;stroke:#000;stroke-width:1px;}#chatgpt-mermaid-\_r_36g\_ .rough-node .label,#chatgpt-mermaid-\_r_36g\_ .node .label,#chatgpt-mermaid-\_r_36g\_ .image-shape .label,#chatgpt-mermaid-\_r_36g\_ .icon-shape .label{text-align:center;}#chatgpt-mermaid-\_r_36g\_ .node.clickable{cursor:pointer;}#chatgpt-mermaid-\_r_36g\_ .root .anchor path{fill:rgb(143, 143, 143)!important;stroke-width:0;stroke:rgb(143, 143, 143);}#chatgpt-mermaid-\_r_36g\_ .arrowheadPath{fill:rgb(143, 143, 143);}#chatgpt-mermaid-\_r_36g\_ .edgePath .path{stroke:rgb(143, 143, 143);stroke-width:1px;}#chatgpt-mermaid-\_r_36g\_ .flowchart-link{stroke:rgb(143, 143, 143);fill:none;}#chatgpt-mermaid-\_r_36g\_ .edgeLabel{background-color:rgb(252, 252, 252);text-align:center;}#chatgpt-mermaid-\_r_36g\_ .edgeLabel p{background-color:rgb(252, 252, 252);}#chatgpt-mermaid-\_r_36g\_ .edgeLabel rect{opacity:0.5;background-color:rgb(252, 252, 252);fill:rgb(252, 252, 252);}#chatgpt-mermaid-\_r_36g\_ .labelBkg{background-color:rgba(252, 252, 252, 0.5);}#chatgpt-mermaid-\_r_36g\_ .cluster rect{fill:rgb(243, 243, 243);stroke:rgba(0, 0, 0, 0.1);stroke-width:1px;}#chatgpt-mermaid-\_r_36g\_ .cluster text{fill:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_36g\_ .cluster span{color:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_36g\_ div.mermaidTooltip{position:absolute;text-align:center;max-width:200px;padding:2px;font-family:-apple-system-body,ui-sans-serif,-apple-system,system-ui,"Segoe UI",Helvetica,"Apple Color Emoji",Arial,sans-serif,"Segoe UI Emoji","Segoe UI Symbol";font-size:12px;background:rgb(243, 243, 243);border:1px solid rgba(0, 0, 0, 0.1);border-radius:2px;pointer-events:none;z-index:100;}#chatgpt-mermaid-\_r_36g\_ .flowchartTitleText{text-anchor:middle;font-size:18px;fill:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_36g\_ rect.text{fill:none;stroke-width:0;}#chatgpt-mermaid-\_r_36g\_ .icon-shape,#chatgpt-mermaid-\_r_36g\_ .image-shape{background-color:rgb(252, 252, 252);text-align:center;}#chatgpt-mermaid-\_r_36g\_ .icon-shape p,#chatgpt-mermaid-\_r_36g\_ .image-shape p{background-color:rgb(252, 252, 252);padding:2px;}#chatgpt-mermaid-\_r_36g\_ .icon-shape .label rect,#chatgpt-mermaid-\_r_36g\_ .image-shape .label rect{opacity:0.5;background-color:rgb(252, 252, 252);fill:rgb(252, 252, 252);}#chatgpt-mermaid-\_r_36g\_ .label-icon{display:inline-block;height:1em;overflow:visible;vertical-align:-0.125em;}#chatgpt-mermaid-\_r_36g\_ .node .label-icon path{fill:currentColor;stroke:revert;stroke-width:revert;}#chatgpt-mermaid-\_r_36g\_ .node .neo-node{stroke:rgb(83, 154, 248);}#chatgpt-mermaid-\_r_36g\_ [data-look="neo"].node rect,#chatgpt-mermaid-\_r_36g\_ [data-look="neo"].cluster rect,#chatgpt-mermaid-\_r_36g\_ [data-look="neo"].node polygon{stroke:url(#chatgpt-mermaid-\_r_36g\_-gradient);filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-\_r_36g\_ [data-look="neo"].swimlane.cluster rect{filter:none;}#chatgpt-mermaid-\_r_36g\_ [data-look="neo"].node path{stroke:url(#chatgpt-mermaid-\_r_36g\_-gradient);stroke-width:1px;}#chatgpt-mermaid-\_r_36g\_ [data-look="neo"].node .outer-path{filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-\_r_36g\_ [data-look="neo"].node .neo-line path{stroke:rgb(83, 154, 248);filter:none;}#chatgpt-mermaid-\_r_36g\_ [data-look="neo"].node circle{stroke:url(#chatgpt-mermaid-\_r_36g\_-gradient);filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-\_r_36g\_ [data-look="neo"].node circle .state-start{fill:#000000;}#chatgpt-mermaid-\_r_36g\_ [data-look="neo"].icon-shape .icon{fill:url(#chatgpt-mermaid-\_r_36g\_-gradient);filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-\_r_36g\_ [data-look="neo"].icon-shape .icon-neo path{stroke:url(#chatgpt-mermaid-\_r_36g\_-gradient);filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-\_r_36g\_ .node text{font-size:14px;font-weight:600;letter-spacing:normal;fill:rgb(0, 79, 153);}#chatgpt-mermaid-\_r_36g\_ .edgeLabels text{font-size:13px;font-weight:600;letter-spacing:-0.08px;fill:rgb(0, 79, 153);}#chatgpt-mermaid-\_r_36g\_ .node tspan[font-weight="normal"],#chatgpt-mermaid-\_r_36g\_ .edgeLabels tspan[font-weight="normal"]{font-weight:600;}#chatgpt-mermaid-\_r_36g\_ .edgeLabel .label rect{opacity:1;rx:13px;ry:13px;fill:rgb(245, 250, 255);stroke:rgb(206, 219, 229);stroke-width:1px;}#chatgpt-mermaid-\_r_36g\_ .node rect,#chatgpt-mermaid-\_r_36g\_ .node circle,#chatgpt-mermaid-\_r_36g\_ .node ellipse,#chatgpt-mermaid-\_r_36g\_ .node polygon,#chatgpt-mermaid-\_r_36g\_ .node path{fill:rgb(229, 243, 255);stroke:rgba(0, 0, 0, 0.1);stroke-width:1px;}#chatgpt-mermaid-\_r_36g\_ .node rect{rx:16px;ry:16px;}#chatgpt-mermaid-\_r_36g\_ .mermaid-decision .label-container{fill:rgb(245, 250, 255);stroke:rgb(206, 219, 229);stroke-dasharray:2,2;}#chatgpt-mermaid-\_r_36g\_ .edgePaths .flowchart-link{stroke:rgb(143, 143, 143);stroke-width:1px;stroke-linecap:round;stroke-linejoin:round;}#chatgpt-mermaid-\_r_36g\_ .marker{fill:rgb(143, 143, 143);stroke:rgb(143, 143, 143);}#chatgpt-mermaid-\_r_36g\_ :root{--mermaid-font-family:-apple-system-body,ui-sans-serif,-apple-system,system-ui,"Segoe UI",Helvetica,"Apple Color Emoji",Arial,sans-serif,"Segoe UI Emoji","Segoe UI Symbol";}用户上传图片鉴权与额度校验文件安全验证拒绝上传私有隔离存储图片内容审核内容拒绝人工复核图像质量检测请求重新拍摄衣物分类识别主体分割用户确认属性生成服装素材锚点与图层配置角色适配测试人工调整/重新生成资产正式入库可用于换装与AI搭配失败通过拒绝待复核通过通过拒绝不合格合格失败通过

### **17.2 上传任务状态机**

\#chatgpt-mermaid-\_r_36n\_{font-family:-apple-system-body,ui-sans-serif,-apple-system,system-ui,"Segoe UI",Helvetica,"Apple Color Emoji",Arial,sans-serif,"Segoe UI Emoji","Segoe UI Symbol";font-size:16px;fill:rgb(13, 13, 13);}@keyframes edge-animation-frame{from{stroke-dashoffset:0;}}@keyframes dash{to{stroke-dashoffset:0;}}#chatgpt-mermaid-\_r_36n\_ .edge-animation-slow{stroke-dasharray:9,5!important;stroke-dashoffset:900;animation:dash 50s linear infinite;stroke-linecap:round;}#chatgpt-mermaid-\_r_36n\_ .edge-animation-fast{stroke-dasharray:9,5!important;stroke-dashoffset:900;animation:dash 20s linear infinite;stroke-linecap:round;}#chatgpt-mermaid-\_r_36n\_ .error-icon{fill:rgb(243, 243, 243);}#chatgpt-mermaid-\_r_36n\_ .error-text{fill:rgb(13, 13, 13);stroke:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_36n\_ .edge-thickness-normal{stroke-width:1px;}#chatgpt-mermaid-\_r_36n\_ .edge-thickness-thick{stroke-width:3.5px;}#chatgpt-mermaid-\_r_36n\_ .edge-pattern-solid{stroke-dasharray:0;}#chatgpt-mermaid-\_r_36n\_ .edge-thickness-invisible{stroke-width:0;fill:none;}#chatgpt-mermaid-\_r_36n\_ .edge-pattern-dashed{stroke-dasharray:3;}#chatgpt-mermaid-\_r_36n\_ .edge-pattern-dotted{stroke-dasharray:2;}#chatgpt-mermaid-\_r_36n\_ .marker{fill:rgb(143, 143, 143);stroke:rgb(143, 143, 143);}#chatgpt-mermaid-\_r_36n\_ .marker.cross{stroke:rgb(143, 143, 143);}#chatgpt-mermaid-\_r_36n\_ svg{font-family:-apple-system-body,ui-sans-serif,-apple-system,system-ui,"Segoe UI",Helvetica,"Apple Color Emoji",Arial,sans-serif,"Segoe UI Emoji","Segoe UI Symbol";font-size:16px;}#chatgpt-mermaid-\_r_36n\_ p{margin:0;}#chatgpt-mermaid-\_r_36n\_ defs [id$="-barbEnd"]{fill:rgb(143, 143, 143);stroke:rgb(143, 143, 143);}#chatgpt-mermaid-\_r_36n\_ g.stateGroup text{fill:rgb(83, 154, 248);stroke:none;font-size:10px;}#chatgpt-mermaid-\_r_36n\_ g.stateGroup text{fill:rgb(13, 13, 13);stroke:none;font-size:10px;}#chatgpt-mermaid-\_r_36n\_ g.stateGroup .state-title{font-weight:bolder;fill:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_36n\_ g.stateGroup rect{fill:rgb(222, 234, 251);stroke:rgb(83, 154, 248);}#chatgpt-mermaid-\_r_36n\_ g.stateGroup line{stroke:rgb(143, 143, 143);stroke-width:1;}#chatgpt-mermaid-\_r_36n\_ .transition{stroke:rgb(143, 143, 143);stroke-width:1;fill:none;}#chatgpt-mermaid-\_r_36n\_ .stateGroup .composit{fill:transparent;border-bottom:1px;}#chatgpt-mermaid-\_r_36n\_ .stateGroup .alt-composit{fill:#e0e0e0;border-bottom:1px;}#chatgpt-mermaid-\_r_36n\_ .state-note{stroke:rgb(107, 198, 127);fill:rgb(243, 243, 243);}#chatgpt-mermaid-\_r_36n\_ .state-note text{fill:rgb(13, 13, 13);stroke:none;font-size:10px;}#chatgpt-mermaid-\_r_36n\_ .stateLabel .box{stroke:none;stroke-width:0;fill:rgb(222, 234, 251);opacity:0.5;}#chatgpt-mermaid-\_r_36n\_ .edgeLabel .label rect{fill:rgb(222, 234, 251);opacity:0.5;}#chatgpt-mermaid-\_r_36n\_ .edgeLabel{background-color:rgb(252, 252, 252);text-align:center;}#chatgpt-mermaid-\_r_36n\_ .edgeLabel p{background-color:rgb(252, 252, 252);}#chatgpt-mermaid-\_r_36n\_ .edgeLabel rect{opacity:0.5;background-color:rgb(252, 252, 252);fill:rgb(252, 252, 252);}#chatgpt-mermaid-\_r_36n\_ .edgeLabel .label text{fill:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_36n\_ .label div .edgeLabel{color:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_36n\_ .stateLabel text{fill:rgb(13, 13, 13);font-size:10px;font-weight:bold;}#chatgpt-mermaid-\_r_36n\_ .node circle.state-start{fill:rgb(143, 143, 143);stroke:rgb(143, 143, 143);}#chatgpt-mermaid-\_r_36n\_ .node .fork-join{fill:rgb(143, 143, 143);stroke:rgb(143, 143, 143);}#chatgpt-mermaid-\_r_36n\_ .node circle.state-end{fill:rgb(83, 154, 248);stroke:transparent;stroke-width:1.5;}#chatgpt-mermaid-\_r_36n\_ .end-state-inner{fill:transparent;stroke-width:1.5;}#chatgpt-mermaid-\_r_36n\_ .node rect{fill:rgb(222, 234, 251);stroke:rgb(83, 154, 248);stroke-width:1px;}#chatgpt-mermaid-\_r_36n\_ .node polygon{fill:rgb(222, 234, 251);stroke:rgb(83, 154, 248);stroke-width:1px;}#chatgpt-mermaid-\_r_36n\_ [id$="-barbEnd"]{fill:rgb(143, 143, 143);}#chatgpt-mermaid-\_r_36n\_ .statediagram-cluster rect{fill:rgb(222, 234, 251);stroke:rgb(83, 154, 248);stroke-width:1px;}#chatgpt-mermaid-\_r_36n\_ .cluster-label,#chatgpt-mermaid-\_r_36n\_ .nodeLabel{color:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_36n\_ .statediagram-cluster rect.outer{rx:5px;ry:5px;}#chatgpt-mermaid-\_r_36n\_ .statediagram-state .divider{stroke:rgb(83, 154, 248);}#chatgpt-mermaid-\_r_36n\_ .statediagram-state .title-state{rx:5px;ry:5px;}#chatgpt-mermaid-\_r_36n\_ .statediagram-cluster.statediagram-cluster .inner{fill:transparent;}#chatgpt-mermaid-\_r_36n\_ .statediagram-cluster.statediagram-cluster-alt .inner{fill:rgb(243, 243, 243);}#chatgpt-mermaid-\_r_36n\_ .statediagram-cluster .inner{rx:0;ry:0;}#chatgpt-mermaid-\_r_36n\_ .statediagram-state rect.basic{rx:5px;ry:5px;}#chatgpt-mermaid-\_r_36n\_ .statediagram-state rect.divider{stroke-dasharray:10,10;fill:rgb(243, 243, 243);}#chatgpt-mermaid-\_r_36n\_ .note-edge{stroke-dasharray:5;}#chatgpt-mermaid-\_r_36n\_ .statediagram-note rect{fill:rgb(243, 243, 243);stroke:rgb(107, 198, 127);stroke-width:1px;rx:0;ry:0;}#chatgpt-mermaid-\_r_36n\_ .statediagram-note rect{fill:rgb(243, 243, 243);stroke:rgb(107, 198, 127);stroke-width:1px;rx:0;ry:0;}#chatgpt-mermaid-\_r_36n\_ .statediagram-note text{fill:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_36n\_ .statediagram-note .nodeLabel{color:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_36n\_ .statediagram .edgeLabel{color:red;}#chatgpt-mermaid-\_r_36n\_ [id$="-dependencyStart"],#chatgpt-mermaid-\_r_36n\_ [id$="-dependencyEnd"]{fill:rgb(143, 143, 143);stroke:rgb(143, 143, 143);stroke-width:1;}#chatgpt-mermaid-\_r_36n\_ .statediagramTitleText{text-anchor:middle;font-size:18px;fill:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_36n\_ [data-look="neo"].statediagram-cluster rect{fill:rgb(222, 234, 251);stroke:url(#chatgpt-mermaid-\_r_36n\_-gradient);stroke-width:1;}#chatgpt-mermaid-\_r_36n\_ [data-look="neo"].statediagram-cluster rect.outer{rx:5px;ry:5px;filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-\_r_36n\_ .node .neo-node{stroke:rgb(83, 154, 248);}#chatgpt-mermaid-\_r_36n\_ [data-look="neo"].node rect,#chatgpt-mermaid-\_r_36n\_ [data-look="neo"].cluster rect,#chatgpt-mermaid-\_r_36n\_ [data-look="neo"].node polygon{stroke:url(#chatgpt-mermaid-\_r_36n\_-gradient);filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-\_r_36n\_ [data-look="neo"].swimlane.cluster rect{filter:none;}#chatgpt-mermaid-\_r_36n\_ [data-look="neo"].node path{stroke:url(#chatgpt-mermaid-\_r_36n\_-gradient);stroke-width:1px;}#chatgpt-mermaid-\_r_36n\_ [data-look="neo"].node .outer-path{filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-\_r_36n\_ [data-look="neo"].node .neo-line path{stroke:rgb(83, 154, 248);filter:none;}#chatgpt-mermaid-\_r_36n\_ [data-look="neo"].node circle{stroke:url(#chatgpt-mermaid-\_r_36n\_-gradient);filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-\_r_36n\_ [data-look="neo"].node circle .state-start{fill:#000000;}#chatgpt-mermaid-\_r_36n\_ [data-look="neo"].icon-shape .icon{fill:url(#chatgpt-mermaid-\_r_36n\_-gradient);filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-\_r_36n\_ [data-look="neo"].icon-shape .icon-neo path{stroke:url(#chatgpt-mermaid-\_r_36n\_-gradient);filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-\_r_36n\_ :root{--mermaid-font-family:-apple-system-body,ui-sans-serif,-apple-system,system-ui,"Segoe UI",Helvetica,"Apple Color Emoji",Arial,sans-serif,"Segoe UI Emoji","Segoe UI Symbol";}CREATEDUPLOADINGUPLOADEDUPLOAD_FAILEDFILE_VALIDATINGFILE_REJECTEDMODERATION_PENDINGMODERATINGMODERATION_PASSEDMODERATION_REJECTEDREVIEW_REQUIREDQUALITY_CHECKINGQUALITY_FAILEDRECOGNIZINGUSER_CONFIRMINGGENERATION_PENDINGGENERATINGGENERATION_FAILEDASSET_REVIEWREADYMANUAL_ADJUSTMENTDELETED重试重新上传重试

### **17.3 状态定义与转换限制**

| 状态                  | 含义      | 用户可见 | 允许重试       |
| ------------------- | ------- | ---- | ---------- |
| CREATED             | 任务已创建   | 是    | 否          |
| UPLOADING           | 文件上传中   | 是    | 是          |
| UPLOADED            | 上传完成    | 是    | 否          |
| FILE_VALIDATING     | 文件安全检查  | 是    | 否          |
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

**[技术设计 TECH]**

将 AI 生成拆成多个独立任务，不能设计为一个无法恢复的长请求。

\#chatgpt-mermaid-\_r_36u\_{font-family:-apple-system-body,ui-sans-serif,-apple-system,system-ui,"Segoe UI",Helvetica,"Apple Color Emoji",Arial,sans-serif,"Segoe UI Emoji","Segoe UI Symbol";font-size:16px;fill:rgb(13, 13, 13);}@keyframes edge-animation-frame{from{stroke-dashoffset:0;}}@keyframes dash{to{stroke-dashoffset:0;}}#chatgpt-mermaid-\_r_36u\_ .edge-animation-slow{stroke-dasharray:9,5!important;stroke-dashoffset:900;animation:dash 50s linear infinite;stroke-linecap:round;}#chatgpt-mermaid-\_r_36u\_ .edge-animation-fast{stroke-dasharray:9,5!important;stroke-dashoffset:900;animation:dash 20s linear infinite;stroke-linecap:round;}#chatgpt-mermaid-\_r_36u\_ .error-icon{fill:rgb(243, 243, 243);}#chatgpt-mermaid-\_r_36u\_ .error-text{fill:rgb(13, 13, 13);stroke:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_36u\_ .edge-thickness-normal{stroke-width:1px;}#chatgpt-mermaid-\_r_36u\_ .edge-thickness-thick{stroke-width:3.5px;}#chatgpt-mermaid-\_r_36u\_ .edge-pattern-solid{stroke-dasharray:0;}#chatgpt-mermaid-\_r_36u\_ .edge-thickness-invisible{stroke-width:0;fill:none;}#chatgpt-mermaid-\_r_36u\_ .edge-pattern-dashed{stroke-dasharray:3;}#chatgpt-mermaid-\_r_36u\_ .edge-pattern-dotted{stroke-dasharray:2;}#chatgpt-mermaid-\_r_36u\_ .marker{fill:rgb(143, 143, 143);stroke:rgb(143, 143, 143);}#chatgpt-mermaid-\_r_36u\_ .marker.cross{stroke:rgb(143, 143, 143);}#chatgpt-mermaid-\_r_36u\_ svg{font-family:-apple-system-body,ui-sans-serif,-apple-system,system-ui,"Segoe UI",Helvetica,"Apple Color Emoji",Arial,sans-serif,"Segoe UI Emoji","Segoe UI Symbol";font-size:16px;}#chatgpt-mermaid-\_r_36u\_ p{margin:0;}#chatgpt-mermaid-\_r_36u\_ .label{font-family:-apple-system-body,ui-sans-serif,-apple-system,system-ui,"Segoe UI",Helvetica,"Apple Color Emoji",Arial,sans-serif,"Segoe UI Emoji","Segoe UI Symbol";color:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_36u\_ .cluster-label text{fill:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_36u\_ .cluster-label span{color:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_36u\_ .cluster-label span p{background-color:transparent;}#chatgpt-mermaid-\_r_36u\_ .label text,#chatgpt-mermaid-\_r_36u\_ span{fill:rgb(13, 13, 13);color:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_36u\_ .node rect,#chatgpt-mermaid-\_r_36u\_ .node circle,#chatgpt-mermaid-\_r_36u\_ .node ellipse,#chatgpt-mermaid-\_r_36u\_ .node polygon,#chatgpt-mermaid-\_r_36u\_ .node path{fill:rgb(222, 234, 251);stroke:rgb(83, 154, 248);stroke-width:1px;}#chatgpt-mermaid-\_r_36u\_ .rough-node .label text,#chatgpt-mermaid-\_r_36u\_ .node .label text,#chatgpt-mermaid-\_r_36u\_ .image-shape .label,#chatgpt-mermaid-\_r_36u\_ .icon-shape .label{text-anchor:middle;}#chatgpt-mermaid-\_r_36u\_ .node .katex path{fill:#000;stroke:#000;stroke-width:1px;}#chatgpt-mermaid-\_r_36u\_ .rough-node .label,#chatgpt-mermaid-\_r_36u\_ .node .label,#chatgpt-mermaid-\_r_36u\_ .image-shape .label,#chatgpt-mermaid-\_r_36u\_ .icon-shape .label{text-align:center;}#chatgpt-mermaid-\_r_36u\_ .node.clickable{cursor:pointer;}#chatgpt-mermaid-\_r_36u\_ .root .anchor path{fill:rgb(143, 143, 143)!important;stroke-width:0;stroke:rgb(143, 143, 143);}#chatgpt-mermaid-\_r_36u\_ .arrowheadPath{fill:rgb(143, 143, 143);}#chatgpt-mermaid-\_r_36u\_ .edgePath .path{stroke:rgb(143, 143, 143);stroke-width:1px;}#chatgpt-mermaid-\_r_36u\_ .flowchart-link{stroke:rgb(143, 143, 143);fill:none;}#chatgpt-mermaid-\_r_36u\_ .edgeLabel{background-color:rgb(252, 252, 252);text-align:center;}#chatgpt-mermaid-\_r_36u\_ .edgeLabel p{background-color:rgb(252, 252, 252);}#chatgpt-mermaid-\_r_36u\_ .edgeLabel rect{opacity:0.5;background-color:rgb(252, 252, 252);fill:rgb(252, 252, 252);}#chatgpt-mermaid-\_r_36u\_ .labelBkg{background-color:rgba(252, 252, 252, 0.5);}#chatgpt-mermaid-\_r_36u\_ .cluster rect{fill:rgb(243, 243, 243);stroke:rgba(0, 0, 0, 0.1);stroke-width:1px;}#chatgpt-mermaid-\_r_36u\_ .cluster text{fill:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_36u\_ .cluster span{color:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_36u\_ div.mermaidTooltip{position:absolute;text-align:center;max-width:200px;padding:2px;font-family:-apple-system-body,ui-sans-serif,-apple-system,system-ui,"Segoe UI",Helvetica,"Apple Color Emoji",Arial,sans-serif,"Segoe UI Emoji","Segoe UI Symbol";font-size:12px;background:rgb(243, 243, 243);border:1px solid rgba(0, 0, 0, 0.1);border-radius:2px;pointer-events:none;z-index:100;}#chatgpt-mermaid-\_r_36u\_ .flowchartTitleText{text-anchor:middle;font-size:18px;fill:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_36u\_ rect.text{fill:none;stroke-width:0;}#chatgpt-mermaid-\_r_36u\_ .icon-shape,#chatgpt-mermaid-\_r_36u\_ .image-shape{background-color:rgb(252, 252, 252);text-align:center;}#chatgpt-mermaid-\_r_36u\_ .icon-shape p,#chatgpt-mermaid-\_r_36u\_ .image-shape p{background-color:rgb(252, 252, 252);padding:2px;}#chatgpt-mermaid-\_r_36u\_ .icon-shape .label rect,#chatgpt-mermaid-\_r_36u\_ .image-shape .label rect{opacity:0.5;background-color:rgb(252, 252, 252);fill:rgb(252, 252, 252);}#chatgpt-mermaid-\_r_36u\_ .label-icon{display:inline-block;height:1em;overflow:visible;vertical-align:-0.125em;}#chatgpt-mermaid-\_r_36u\_ .node .label-icon path{fill:currentColor;stroke:revert;stroke-width:revert;}#chatgpt-mermaid-\_r_36u\_ .node .neo-node{stroke:rgb(83, 154, 248);}#chatgpt-mermaid-\_r_36u\_ [data-look="neo"].node rect,#chatgpt-mermaid-\_r_36u\_ [data-look="neo"].cluster rect,#chatgpt-mermaid-\_r_36u\_ [data-look="neo"].node polygon{stroke:url(#chatgpt-mermaid-\_r_36u\_-gradient);filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-\_r_36u\_ [data-look="neo"].swimlane.cluster rect{filter:none;}#chatgpt-mermaid-\_r_36u\_ [data-look="neo"].node path{stroke:url(#chatgpt-mermaid-\_r_36u\_-gradient);stroke-width:1px;}#chatgpt-mermaid-\_r_36u\_ [data-look="neo"].node .outer-path{filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-\_r_36u\_ [data-look="neo"].node .neo-line path{stroke:rgb(83, 154, 248);filter:none;}#chatgpt-mermaid-\_r_36u\_ [data-look="neo"].node circle{stroke:url(#chatgpt-mermaid-\_r_36u\_-gradient);filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-\_r_36u\_ [data-look="neo"].node circle .state-start{fill:#000000;}#chatgpt-mermaid-\_r_36u\_ [data-look="neo"].icon-shape .icon{fill:url(#chatgpt-mermaid-\_r_36u\_-gradient);filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-\_r_36u\_ [data-look="neo"].icon-shape .icon-neo path{stroke:url(#chatgpt-mermaid-\_r_36u\_-gradient);filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-\_r_36u\_ .node text{font-size:14px;font-weight:600;letter-spacing:normal;fill:rgb(0, 79, 153);}#chatgpt-mermaid-\_r_36u\_ .edgeLabels text{font-size:13px;font-weight:600;letter-spacing:-0.08px;fill:rgb(0, 79, 153);}#chatgpt-mermaid-\_r_36u\_ .node tspan[font-weight="normal"],#chatgpt-mermaid-\_r_36u\_ .edgeLabels tspan[font-weight="normal"]{font-weight:600;}#chatgpt-mermaid-\_r_36u\_ .edgeLabel .label rect{opacity:1;rx:13px;ry:13px;fill:rgb(245, 250, 255);stroke:rgb(206, 219, 229);stroke-width:1px;}#chatgpt-mermaid-\_r_36u\_ .node rect,#chatgpt-mermaid-\_r_36u\_ .node circle,#chatgpt-mermaid-\_r_36u\_ .node ellipse,#chatgpt-mermaid-\_r_36u\_ .node polygon,#chatgpt-mermaid-\_r_36u\_ .node path{fill:rgb(229, 243, 255);stroke:rgba(0, 0, 0, 0.1);stroke-width:1px;}#chatgpt-mermaid-\_r_36u\_ .node rect{rx:16px;ry:16px;}#chatgpt-mermaid-\_r_36u\_ .mermaid-decision .label-container{fill:rgb(245, 250, 255);stroke:rgb(206, 219, 229);stroke-dasharray:2,2;}#chatgpt-mermaid-\_r_36u\_ .edgePaths .flowchart-link{stroke:rgb(143, 143, 143);stroke-width:1px;stroke-linecap:round;stroke-linejoin:round;}#chatgpt-mermaid-\_r_36u\_ .marker{fill:rgb(143, 143, 143);stroke:rgb(143, 143, 143);}#chatgpt-mermaid-\_r_36u\_ :root{--mermaid-font-family:-apple-system-body,ui-sans-serif,-apple-system,system-ui,"Segoe UI",Helvetica,"Apple Color Emoji",Arial,sans-serif,"Segoe UI Emoji","Segoe UI Symbol";}原始照片安全检查衣物主体分割轮廓修正纹理与颜色提取服装类别判断生成标准化贴图锚点定位图层配置角色适配测试资产入库

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

### **17.5 AI 搭配工作流**

\#chatgpt-mermaid-\_r_375\_{font-family:-apple-system-body,ui-sans-serif,-apple-system,system-ui,"Segoe UI",Helvetica,"Apple Color Emoji",Arial,sans-serif,"Segoe UI Emoji","Segoe UI Symbol";font-size:16px;fill:rgb(13, 13, 13);}@keyframes edge-animation-frame{from{stroke-dashoffset:0;}}@keyframes dash{to{stroke-dashoffset:0;}}#chatgpt-mermaid-\_r_375\_ .edge-animation-slow{stroke-dasharray:9,5!important;stroke-dashoffset:900;animation:dash 50s linear infinite;stroke-linecap:round;}#chatgpt-mermaid-\_r_375\_ .edge-animation-fast{stroke-dasharray:9,5!important;stroke-dashoffset:900;animation:dash 20s linear infinite;stroke-linecap:round;}#chatgpt-mermaid-\_r_375\_ .error-icon{fill:rgb(243, 243, 243);}#chatgpt-mermaid-\_r_375\_ .error-text{fill:rgb(13, 13, 13);stroke:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_375\_ .edge-thickness-normal{stroke-width:1px;}#chatgpt-mermaid-\_r_375\_ .edge-thickness-thick{stroke-width:3.5px;}#chatgpt-mermaid-\_r_375\_ .edge-pattern-solid{stroke-dasharray:0;}#chatgpt-mermaid-\_r_375\_ .edge-thickness-invisible{stroke-width:0;fill:none;}#chatgpt-mermaid-\_r_375\_ .edge-pattern-dashed{stroke-dasharray:3;}#chatgpt-mermaid-\_r_375\_ .edge-pattern-dotted{stroke-dasharray:2;}#chatgpt-mermaid-\_r_375\_ .marker{fill:rgb(143, 143, 143);stroke:rgb(143, 143, 143);}#chatgpt-mermaid-\_r_375\_ .marker.cross{stroke:rgb(143, 143, 143);}#chatgpt-mermaid-\_r_375\_ svg{font-family:-apple-system-body,ui-sans-serif,-apple-system,system-ui,"Segoe UI",Helvetica,"Apple Color Emoji",Arial,sans-serif,"Segoe UI Emoji","Segoe UI Symbol";font-size:16px;}#chatgpt-mermaid-\_r_375\_ p{margin:0;}#chatgpt-mermaid-\_r_375\_ .label{font-family:-apple-system-body,ui-sans-serif,-apple-system,system-ui,"Segoe UI",Helvetica,"Apple Color Emoji",Arial,sans-serif,"Segoe UI Emoji","Segoe UI Symbol";color:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_375\_ .cluster-label text{fill:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_375\_ .cluster-label span{color:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_375\_ .cluster-label span p{background-color:transparent;}#chatgpt-mermaid-\_r_375\_ .label text,#chatgpt-mermaid-\_r_375\_ span{fill:rgb(13, 13, 13);color:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_375\_ .node rect,#chatgpt-mermaid-\_r_375\_ .node circle,#chatgpt-mermaid-\_r_375\_ .node ellipse,#chatgpt-mermaid-\_r_375\_ .node polygon,#chatgpt-mermaid-\_r_375\_ .node path{fill:rgb(222, 234, 251);stroke:rgb(83, 154, 248);stroke-width:1px;}#chatgpt-mermaid-\_r_375\_ .rough-node .label text,#chatgpt-mermaid-\_r_375\_ .node .label text,#chatgpt-mermaid-\_r_375\_ .image-shape .label,#chatgpt-mermaid-\_r_375\_ .icon-shape .label{text-anchor:middle;}#chatgpt-mermaid-\_r_375\_ .node .katex path{fill:#000;stroke:#000;stroke-width:1px;}#chatgpt-mermaid-\_r_375\_ .rough-node .label,#chatgpt-mermaid-\_r_375\_ .node .label,#chatgpt-mermaid-\_r_375\_ .image-shape .label,#chatgpt-mermaid-\_r_375\_ .icon-shape .label{text-align:center;}#chatgpt-mermaid-\_r_375\_ .node.clickable{cursor:pointer;}#chatgpt-mermaid-\_r_375\_ .root .anchor path{fill:rgb(143, 143, 143)!important;stroke-width:0;stroke:rgb(143, 143, 143);}#chatgpt-mermaid-\_r_375\_ .arrowheadPath{fill:rgb(143, 143, 143);}#chatgpt-mermaid-\_r_375\_ .edgePath .path{stroke:rgb(143, 143, 143);stroke-width:1px;}#chatgpt-mermaid-\_r_375\_ .flowchart-link{stroke:rgb(143, 143, 143);fill:none;}#chatgpt-mermaid-\_r_375\_ .edgeLabel{background-color:rgb(252, 252, 252);text-align:center;}#chatgpt-mermaid-\_r_375\_ .edgeLabel p{background-color:rgb(252, 252, 252);}#chatgpt-mermaid-\_r_375\_ .edgeLabel rect{opacity:0.5;background-color:rgb(252, 252, 252);fill:rgb(252, 252, 252);}#chatgpt-mermaid-\_r_375\_ .labelBkg{background-color:rgba(252, 252, 252, 0.5);}#chatgpt-mermaid-\_r_375\_ .cluster rect{fill:rgb(243, 243, 243);stroke:rgba(0, 0, 0, 0.1);stroke-width:1px;}#chatgpt-mermaid-\_r_375\_ .cluster text{fill:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_375\_ .cluster span{color:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_375\_ div.mermaidTooltip{position:absolute;text-align:center;max-width:200px;padding:2px;font-family:-apple-system-body,ui-sans-serif,-apple-system,system-ui,"Segoe UI",Helvetica,"Apple Color Emoji",Arial,sans-serif,"Segoe UI Emoji","Segoe UI Symbol";font-size:12px;background:rgb(243, 243, 243);border:1px solid rgba(0, 0, 0, 0.1);border-radius:2px;pointer-events:none;z-index:100;}#chatgpt-mermaid-\_r_375\_ .flowchartTitleText{text-anchor:middle;font-size:18px;fill:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_375\_ rect.text{fill:none;stroke-width:0;}#chatgpt-mermaid-\_r_375\_ .icon-shape,#chatgpt-mermaid-\_r_375\_ .image-shape{background-color:rgb(252, 252, 252);text-align:center;}#chatgpt-mermaid-\_r_375\_ .icon-shape p,#chatgpt-mermaid-\_r_375\_ .image-shape p{background-color:rgb(252, 252, 252);padding:2px;}#chatgpt-mermaid-\_r_375\_ .icon-shape .label rect,#chatgpt-mermaid-\_r_375\_ .image-shape .label rect{opacity:0.5;background-color:rgb(252, 252, 252);fill:rgb(252, 252, 252);}#chatgpt-mermaid-\_r_375\_ .label-icon{display:inline-block;height:1em;overflow:visible;vertical-align:-0.125em;}#chatgpt-mermaid-\_r_375\_ .node .label-icon path{fill:currentColor;stroke:revert;stroke-width:revert;}#chatgpt-mermaid-\_r_375\_ .node .neo-node{stroke:rgb(83, 154, 248);}#chatgpt-mermaid-\_r_375\_ [data-look="neo"].node rect,#chatgpt-mermaid-\_r_375\_ [data-look="neo"].cluster rect,#chatgpt-mermaid-\_r_375\_ [data-look="neo"].node polygon{stroke:url(#chatgpt-mermaid-\_r_375\_-gradient);filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-\_r_375\_ [data-look="neo"].swimlane.cluster rect{filter:none;}#chatgpt-mermaid-\_r_375\_ [data-look="neo"].node path{stroke:url(#chatgpt-mermaid-\_r_375\_-gradient);stroke-width:1px;}#chatgpt-mermaid-\_r_375\_ [data-look="neo"].node .outer-path{filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-\_r_375\_ [data-look="neo"].node .neo-line path{stroke:rgb(83, 154, 248);filter:none;}#chatgpt-mermaid-\_r_375\_ [data-look="neo"].node circle{stroke:url(#chatgpt-mermaid-\_r_375\_-gradient);filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-\_r_375\_ [data-look="neo"].node circle .state-start{fill:#000000;}#chatgpt-mermaid-\_r_375\_ [data-look="neo"].icon-shape .icon{fill:url(#chatgpt-mermaid-\_r_375\_-gradient);filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-\_r_375\_ [data-look="neo"].icon-shape .icon-neo path{stroke:url(#chatgpt-mermaid-\_r_375\_-gradient);filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-\_r_375\_ .node text{font-size:14px;font-weight:600;letter-spacing:normal;fill:rgb(0, 79, 153);}#chatgpt-mermaid-\_r_375\_ .edgeLabels text{font-size:13px;font-weight:600;letter-spacing:-0.08px;fill:rgb(0, 79, 153);}#chatgpt-mermaid-\_r_375\_ .node tspan[font-weight="normal"],#chatgpt-mermaid-\_r_375\_ .edgeLabels tspan[font-weight="normal"]{font-weight:600;}#chatgpt-mermaid-\_r_375\_ .edgeLabel .label rect{opacity:1;rx:13px;ry:13px;fill:rgb(245, 250, 255);stroke:rgb(206, 219, 229);stroke-width:1px;}#chatgpt-mermaid-\_r_375\_ .node rect,#chatgpt-mermaid-\_r_375\_ .node circle,#chatgpt-mermaid-\_r_375\_ .node ellipse,#chatgpt-mermaid-\_r_375\_ .node polygon,#chatgpt-mermaid-\_r_375\_ .node path{fill:rgb(229, 243, 255);stroke:rgba(0, 0, 0, 0.1);stroke-width:1px;}#chatgpt-mermaid-\_r_375\_ .node rect{rx:16px;ry:16px;}#chatgpt-mermaid-\_r_375\_ .mermaid-decision .label-container{fill:rgb(245, 250, 255);stroke:rgb(206, 219, 229);stroke-dasharray:2,2;}#chatgpt-mermaid-\_r_375\_ .edgePaths .flowchart-link{stroke:rgb(143, 143, 143);stroke-width:1px;stroke-linecap:round;stroke-linejoin:round;}#chatgpt-mermaid-\_r_375\_ .marker{fill:rgb(143, 143, 143);stroke:rgb(143, 143, 143);}#chatgpt-mermaid-\_r_375\_ :root{--mermaid-font-family:-apple-system-body,ui-sans-serif,-apple-system,system-ui,"Segoe UI",Helvetica,"Apple Color Emoji",Arial,sans-serif,"Segoe UI Emoji","Segoe UI Symbol";}用户输入需求意图识别提取场景/风格/季节/限制读取当前角色查询衣橱资产硬规则过滤候选服装组合颜色与风格评分LLM解释与排序资产ID合法性校验渲染引擎试穿生成多套方案用户选择保存/修改/拒绝反馈记录

**重要约束：**

- LLM 只能从服务端提供的候选资产中选择。
- 不能让模型自由生成数据库 ID。
- 模型返回的资产 ID 必须二次校验。
- 推荐结果必须满足服装部位、层级和授权规则。
- 无合适衣物时明确告知用户，不得伪造库存。
- 用户拒绝某套方案时记录拒绝原因，但不得未经同意将其推断为长期偏好。

## **十八、数据库设计与 ERD**

### **18.1 数据库设计原则**

**[技术设计 TECH]**

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

\#chatgpt-mermaid-\_r_37c\_{font-family:-apple-system-body,ui-sans-serif,-apple-system,system-ui,"Segoe UI",Helvetica,"Apple Color Emoji",Arial,sans-serif,"Segoe UI Emoji","Segoe UI Symbol";font-size:16px;fill:rgb(13, 13, 13);}@keyframes edge-animation-frame{from{stroke-dashoffset:0;}}@keyframes dash{to{stroke-dashoffset:0;}}#chatgpt-mermaid-\_r_37c\_ .edge-animation-slow{stroke-dasharray:9,5!important;stroke-dashoffset:900;animation:dash 50s linear infinite;stroke-linecap:round;}#chatgpt-mermaid-\_r_37c\_ .edge-animation-fast{stroke-dasharray:9,5!important;stroke-dashoffset:900;animation:dash 20s linear infinite;stroke-linecap:round;}#chatgpt-mermaid-\_r_37c\_ .error-icon{fill:rgb(243, 243, 243);}#chatgpt-mermaid-\_r_37c\_ .error-text{fill:rgb(13, 13, 13);stroke:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_37c\_ .edge-thickness-normal{stroke-width:1px;}#chatgpt-mermaid-\_r_37c\_ .edge-thickness-thick{stroke-width:3.5px;}#chatgpt-mermaid-\_r_37c\_ .edge-pattern-solid{stroke-dasharray:0;}#chatgpt-mermaid-\_r_37c\_ .edge-thickness-invisible{stroke-width:0;fill:none;}#chatgpt-mermaid-\_r_37c\_ .edge-pattern-dashed{stroke-dasharray:3;}#chatgpt-mermaid-\_r_37c\_ .edge-pattern-dotted{stroke-dasharray:2;}#chatgpt-mermaid-\_r_37c\_ .marker{fill:rgb(143, 143, 143);stroke:rgb(143, 143, 143);}#chatgpt-mermaid-\_r_37c\_ .marker.cross{stroke:rgb(143, 143, 143);}#chatgpt-mermaid-\_r_37c\_ svg{font-family:-apple-system-body,ui-sans-serif,-apple-system,system-ui,"Segoe UI",Helvetica,"Apple Color Emoji",Arial,sans-serif,"Segoe UI Emoji","Segoe UI Symbol";font-size:16px;}#chatgpt-mermaid-\_r_37c\_ p{margin:0;}#chatgpt-mermaid-\_r_37c\_ .entityBox{fill:rgb(222, 234, 251);stroke:rgb(83, 154, 248);}#chatgpt-mermaid-\_r_37c\_ .relationshipLabelBox{fill:rgb(243, 243, 243);opacity:0.7;background-color:rgb(243, 243, 243);}#chatgpt-mermaid-\_r_37c\_ .relationshipLabelBox rect{opacity:0.5;}#chatgpt-mermaid-\_r_37c\_ .labelBkg{background-color:rgba(243, 243, 243, 0.5);}#chatgpt-mermaid-\_r_37c\_ .edgeLabel{background-color:rgb(252, 252, 252);}#chatgpt-mermaid-\_r_37c\_ .edgeLabel .label rect{fill:rgb(252, 252, 252);}#chatgpt-mermaid-\_r_37c\_ .edgeLabel .label text{fill:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_37c\_ .edgeLabel .label{fill:rgb(83, 154, 248);font-size:14px;}#chatgpt-mermaid-\_r_37c\_ .label{font-family:-apple-system-body,ui-sans-serif,-apple-system,system-ui,"Segoe UI",Helvetica,"Apple Color Emoji",Arial,sans-serif,"Segoe UI Emoji","Segoe UI Symbol";color:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_37c\_ .edge-pattern-dashed{stroke-dasharray:8,8;}#chatgpt-mermaid-\_r_37c\_ .node rect,#chatgpt-mermaid-\_r_37c\_ .node circle,#chatgpt-mermaid-\_r_37c\_ .node ellipse,#chatgpt-mermaid-\_r_37c\_ .node polygon{fill:rgb(222, 234, 251);stroke:rgb(83, 154, 248);stroke-width:1px;}#chatgpt-mermaid-\_r_37c\_ .relationshipLine{stroke:rgb(143, 143, 143);stroke-width:1px;fill:none;}#chatgpt-mermaid-\_r_37c\_ .marker{fill:none!important;stroke:rgb(143, 143, 143)!important;stroke-width:1;}#chatgpt-mermaid-\_r_37c\_ [data-look=neo].labelBkg{background-color:rgba(243, 243, 243, 0.5);}#chatgpt-mermaid-\_r_37c\_ .node .neo-node{stroke:rgb(83, 154, 248);}#chatgpt-mermaid-\_r_37c\_ [data-look="neo"].node rect,#chatgpt-mermaid-\_r_37c\_ [data-look="neo"].cluster rect,#chatgpt-mermaid-\_r_37c\_ [data-look="neo"].node polygon{stroke:url(#chatgpt-mermaid-\_r_37c\_-gradient);filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-\_r_37c\_ [data-look="neo"].swimlane.cluster rect{filter:none;}#chatgpt-mermaid-\_r_37c\_ [data-look="neo"].node path{stroke:url(#chatgpt-mermaid-\_r_37c\_-gradient);stroke-width:1px;}#chatgpt-mermaid-\_r_37c\_ [data-look="neo"].node .outer-path{filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-\_r_37c\_ [data-look="neo"].node .neo-line path{stroke:rgb(83, 154, 248);filter:none;}#chatgpt-mermaid-\_r_37c\_ [data-look="neo"].node circle{stroke:url(#chatgpt-mermaid-\_r_37c\_-gradient);filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-\_r_37c\_ [data-look="neo"].node circle .state-start{fill:#000000;}#chatgpt-mermaid-\_r_37c\_ [data-look="neo"].icon-shape .icon{fill:url(#chatgpt-mermaid-\_r_37c\_-gradient);filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-\_r_37c\_ [data-look="neo"].icon-shape .icon-neo path{stroke:url(#chatgpt-mermaid-\_r_37c\_-gradient);filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-\_r_37c\_ :root{--mermaid-font-family:-apple-system-body,ui-sans-serif,-apple-system,system-ui,"Segoe UI",Helvetica,"Apple Color Emoji",Arial,sans-serif,"Segoe UI Emoji","Segoe UI Symbol";}USERSuuididPKstringemailstringnicknamestringstatusdatetimecreated_atAVATARSuuididPKuuidowner_user_idFKstringnamestringmodel_idstringstyle_iduuidcurrent_body_profile_idstringvisibilitydatetimecreated_atGARMENTSuuididPKuuidowner_user_idFKstringcategorystringsubcategorystringstatusjsonattributesstringvisibilitydatetimecreated_atOUTFITSuuididPKuuidowner_user_idFKuuidavatar_idFKstringnamestringstatusstringcover_keydatetimecreated_atAI_TASKSuuididPKuuiduser_idFKstringtask_typestringstatusstringmodel_versionjsoninput_refsjsonoutput_refsstringerror_codePOSTSuuididPKuuidowner_user_idFKuuidoutfit_idFKstringtitlestringvisibilitystringstatusBODY_PROFILESuuididPKuuidavatar_idFKstringtemplate_idjsonmorph_parametersintversiondatetimeupdated_atGARMENT_MEDIAuuididPKuuidgarment_idFKstringmedia_typestringstorage_keystringchecksumintwidthintheightGARMENT_ASSETSuuididPKuuidgarment_idFKstringasset_versionstringasset_typestringstatusstringmanifest_keyASSET_PARTSuuididPKuuidgarment_asset_idFKstringpart_typestringstorage_keyintlayer_orderASSET_ANCHORSuuididPKuuidgarment_asset_idFKstringanchor_namejsontransformOUTFIT_ITEMSuuididPKuuidoutfit_idFKuuidgarment_asset_idFKstringslotjsontransformintlayer_orderAI_TASK_EVENTSuuididPKuuidtask_idFKstringstagestringstatusjsondetaildatetimecreated_atMODERATION_EVENTSuuididPKuuidgarment_idFKstringproviderstringdecisionstringpolicy_versiondatetimecreated_atPOST_ASSETSuuididPKuuidpost_idFKuuidgarment_asset_idFKstringdisplay_onlystringreuse_permissionLICENSESuuididPKuuidasset_idFKuuidowner_user_idFKstringlicense_typestringstatusdatetimeexpires_atINTERACTIONSuuididPKuuiduser_idFKuuidpost_idFKstringtypedatetimecreated_atownsownscreatesrequestspublisheshaswearscontainsgeneratesincludesdefinescontainsused_inlogsreviewed_byexposesreferenced_bygrantslicensedperformsreceives

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

**[技术设计 TECH]**

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

**[技术设计 TECH]**

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

衣物列表支持：

- 一级分类。
- 二级分类。
- 颜色。
- 季节。
- 场景。
- 风格。
- 资产状态。
- 创建时间。
- 关键词。

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

独立技术方案 A

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

\#chatgpt-mermaid-\_r_38h\_{font-family:-apple-system-body,ui-sans-serif,-apple-system,system-ui,"Segoe UI",Helvetica,"Apple Color Emoji",Arial,sans-serif,"Segoe UI Emoji","Segoe UI Symbol";font-size:16px;fill:rgb(13, 13, 13);}@keyframes edge-animation-frame{from{stroke-dashoffset:0;}}@keyframes dash{to{stroke-dashoffset:0;}}#chatgpt-mermaid-\_r_38h\_ .edge-animation-slow{stroke-dasharray:9,5!important;stroke-dashoffset:900;animation:dash 50s linear infinite;stroke-linecap:round;}#chatgpt-mermaid-\_r_38h\_ .edge-animation-fast{stroke-dasharray:9,5!important;stroke-dashoffset:900;animation:dash 20s linear infinite;stroke-linecap:round;}#chatgpt-mermaid-\_r_38h\_ .error-icon{fill:rgb(243, 243, 243);}#chatgpt-mermaid-\_r_38h\_ .error-text{fill:rgb(13, 13, 13);stroke:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_38h\_ .edge-thickness-normal{stroke-width:1px;}#chatgpt-mermaid-\_r_38h\_ .edge-thickness-thick{stroke-width:3.5px;}#chatgpt-mermaid-\_r_38h\_ .edge-pattern-solid{stroke-dasharray:0;}#chatgpt-mermaid-\_r_38h\_ .edge-thickness-invisible{stroke-width:0;fill:none;}#chatgpt-mermaid-\_r_38h\_ .edge-pattern-dashed{stroke-dasharray:3;}#chatgpt-mermaid-\_r_38h\_ .edge-pattern-dotted{stroke-dasharray:2;}#chatgpt-mermaid-\_r_38h\_ .marker{fill:rgb(143, 143, 143);stroke:rgb(143, 143, 143);}#chatgpt-mermaid-\_r_38h\_ .marker.cross{stroke:rgb(143, 143, 143);}#chatgpt-mermaid-\_r_38h\_ svg{font-family:-apple-system-body,ui-sans-serif,-apple-system,system-ui,"Segoe UI",Helvetica,"Apple Color Emoji",Arial,sans-serif,"Segoe UI Emoji","Segoe UI Symbol";font-size:16px;}#chatgpt-mermaid-\_r_38h\_ p{margin:0;}#chatgpt-mermaid-\_r_38h\_ .label{font-family:-apple-system-body,ui-sans-serif,-apple-system,system-ui,"Segoe UI",Helvetica,"Apple Color Emoji",Arial,sans-serif,"Segoe UI Emoji","Segoe UI Symbol";color:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_38h\_ .cluster-label text{fill:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_38h\_ .cluster-label span{color:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_38h\_ .cluster-label span p{background-color:transparent;}#chatgpt-mermaid-\_r_38h\_ .label text,#chatgpt-mermaid-\_r_38h\_ span{fill:rgb(13, 13, 13);color:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_38h\_ .node rect,#chatgpt-mermaid-\_r_38h\_ .node circle,#chatgpt-mermaid-\_r_38h\_ .node ellipse,#chatgpt-mermaid-\_r_38h\_ .node polygon,#chatgpt-mermaid-\_r_38h\_ .node path{fill:rgb(222, 234, 251);stroke:rgb(83, 154, 248);stroke-width:1px;}#chatgpt-mermaid-\_r_38h\_ .rough-node .label text,#chatgpt-mermaid-\_r_38h\_ .node .label text,#chatgpt-mermaid-\_r_38h\_ .image-shape .label,#chatgpt-mermaid-\_r_38h\_ .icon-shape .label{text-anchor:middle;}#chatgpt-mermaid-\_r_38h\_ .node .katex path{fill:#000;stroke:#000;stroke-width:1px;}#chatgpt-mermaid-\_r_38h\_ .rough-node .label,#chatgpt-mermaid-\_r_38h\_ .node .label,#chatgpt-mermaid-\_r_38h\_ .image-shape .label,#chatgpt-mermaid-\_r_38h\_ .icon-shape .label{text-align:center;}#chatgpt-mermaid-\_r_38h\_ .node.clickable{cursor:pointer;}#chatgpt-mermaid-\_r_38h\_ .root .anchor path{fill:rgb(143, 143, 143)!important;stroke-width:0;stroke:rgb(143, 143, 143);}#chatgpt-mermaid-\_r_38h\_ .arrowheadPath{fill:rgb(143, 143, 143);}#chatgpt-mermaid-\_r_38h\_ .edgePath .path{stroke:rgb(143, 143, 143);stroke-width:1px;}#chatgpt-mermaid-\_r_38h\_ .flowchart-link{stroke:rgb(143, 143, 143);fill:none;}#chatgpt-mermaid-\_r_38h\_ .edgeLabel{background-color:rgb(252, 252, 252);text-align:center;}#chatgpt-mermaid-\_r_38h\_ .edgeLabel p{background-color:rgb(252, 252, 252);}#chatgpt-mermaid-\_r_38h\_ .edgeLabel rect{opacity:0.5;background-color:rgb(252, 252, 252);fill:rgb(252, 252, 252);}#chatgpt-mermaid-\_r_38h\_ .labelBkg{background-color:rgba(252, 252, 252, 0.5);}#chatgpt-mermaid-\_r_38h\_ .cluster rect{fill:rgb(243, 243, 243);stroke:rgba(0, 0, 0, 0.1);stroke-width:1px;}#chatgpt-mermaid-\_r_38h\_ .cluster text{fill:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_38h\_ .cluster span{color:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_38h\_ div.mermaidTooltip{position:absolute;text-align:center;max-width:200px;padding:2px;font-family:-apple-system-body,ui-sans-serif,-apple-system,system-ui,"Segoe UI",Helvetica,"Apple Color Emoji",Arial,sans-serif,"Segoe UI Emoji","Segoe UI Symbol";font-size:12px;background:rgb(243, 243, 243);border:1px solid rgba(0, 0, 0, 0.1);border-radius:2px;pointer-events:none;z-index:100;}#chatgpt-mermaid-\_r_38h\_ .flowchartTitleText{text-anchor:middle;font-size:18px;fill:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_38h\_ rect.text{fill:none;stroke-width:0;}#chatgpt-mermaid-\_r_38h\_ .icon-shape,#chatgpt-mermaid-\_r_38h\_ .image-shape{background-color:rgb(252, 252, 252);text-align:center;}#chatgpt-mermaid-\_r_38h\_ .icon-shape p,#chatgpt-mermaid-\_r_38h\_ .image-shape p{background-color:rgb(252, 252, 252);padding:2px;}#chatgpt-mermaid-\_r_38h\_ .icon-shape .label rect,#chatgpt-mermaid-\_r_38h\_ .image-shape .label rect{opacity:0.5;background-color:rgb(252, 252, 252);fill:rgb(252, 252, 252);}#chatgpt-mermaid-\_r_38h\_ .label-icon{display:inline-block;height:1em;overflow:visible;vertical-align:-0.125em;}#chatgpt-mermaid-\_r_38h\_ .node .label-icon path{fill:currentColor;stroke:revert;stroke-width:revert;}#chatgpt-mermaid-\_r_38h\_ .node .neo-node{stroke:rgb(83, 154, 248);}#chatgpt-mermaid-\_r_38h\_ [data-look="neo"].node rect,#chatgpt-mermaid-\_r_38h\_ [data-look="neo"].cluster rect,#chatgpt-mermaid-\_r_38h\_ [data-look="neo"].node polygon{stroke:url(#chatgpt-mermaid-\_r_38h\_-gradient);filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-\_r_38h\_ [data-look="neo"].swimlane.cluster rect{filter:none;}#chatgpt-mermaid-\_r_38h\_ [data-look="neo"].node path{stroke:url(#chatgpt-mermaid-\_r_38h\_-gradient);stroke-width:1px;}#chatgpt-mermaid-\_r_38h\_ [data-look="neo"].node .outer-path{filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-\_r_38h\_ [data-look="neo"].node .neo-line path{stroke:rgb(83, 154, 248);filter:none;}#chatgpt-mermaid-\_r_38h\_ [data-look="neo"].node circle{stroke:url(#chatgpt-mermaid-\_r_38h\_-gradient);filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-\_r_38h\_ [data-look="neo"].node circle .state-start{fill:#000000;}#chatgpt-mermaid-\_r_38h\_ [data-look="neo"].icon-shape .icon{fill:url(#chatgpt-mermaid-\_r_38h\_-gradient);filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-\_r_38h\_ [data-look="neo"].icon-shape .icon-neo path{stroke:url(#chatgpt-mermaid-\_r_38h\_-gradient);filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-\_r_38h\_ .node text{font-size:14px;font-weight:600;letter-spacing:normal;fill:rgb(0, 79, 153);}#chatgpt-mermaid-\_r_38h\_ .edgeLabels text{font-size:13px;font-weight:600;letter-spacing:-0.08px;fill:rgb(0, 79, 153);}#chatgpt-mermaid-\_r_38h\_ .node tspan[font-weight="normal"],#chatgpt-mermaid-\_r_38h\_ .edgeLabels tspan[font-weight="normal"]{font-weight:600;}#chatgpt-mermaid-\_r_38h\_ .edgeLabel .label rect{opacity:1;rx:13px;ry:13px;fill:rgb(245, 250, 255);stroke:rgb(206, 219, 229);stroke-width:1px;}#chatgpt-mermaid-\_r_38h\_ .node rect,#chatgpt-mermaid-\_r_38h\_ .node circle,#chatgpt-mermaid-\_r_38h\_ .node ellipse,#chatgpt-mermaid-\_r_38h\_ .node polygon,#chatgpt-mermaid-\_r_38h\_ .node path{fill:rgb(229, 243, 255);stroke:rgba(0, 0, 0, 0.1);stroke-width:1px;}#chatgpt-mermaid-\_r_38h\_ .node rect{rx:16px;ry:16px;}#chatgpt-mermaid-\_r_38h\_ .mermaid-decision .label-container{fill:rgb(245, 250, 255);stroke:rgb(206, 219, 229);stroke-dasharray:2,2;}#chatgpt-mermaid-\_r_38h\_ .edgePaths .flowchart-link{stroke:rgb(143, 143, 143);stroke-width:1px;stroke-linecap:round;stroke-linejoin:round;}#chatgpt-mermaid-\_r_38h\_ .marker{fill:rgb(143, 143, 143);stroke:rgb(143, 143, 143);}#chatgpt-mermaid-\_r_38h\_ :root{--mermaid-font-family:-apple-system-body,ui-sans-serif,-apple-system,system-ui,"Segoe UI",Helvetica,"Apple Color Emoji",Arial,sans-serif,"Segoe UI Emoji","Segoe UI Symbol";}资源系统角色系统3D 渲染模块应用业务层模型资源贴图资源角色配置本地缓存基础角色模型骨骼 SkeletonMorph Targets面部参数发型系统身材系统姿势/动作Three.js / WebGLGLB / VRM LoaderScene ManagerCamera ControllerLightingMaterial SystemFlutter UI角色状态管理角色业务 API

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

**[技术设计 TECH]**

不能把身材系统简单实现成对整个角色模型做 X/Y/Z 缩放。

这种方案会造成：

- 肢体比例异常。
- 服装拉伸。
- 骨骼位置偏移。
- 手脚比例不自然。
- 服装和身体碰撞。
- 不同身材下的模型失真。

推荐采用基础模型 + Morph Targets 的方式。

身材参数与 Morph Target 的映射：

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

注意：实际参数不能假设所有模型都能天然支持。需要美术和技术团队共同确定每个基础模型的 Morph Target 集合。

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

\#chatgpt-mermaid-\_r_38t\_{font-family:-apple-system-body,ui-sans-serif,-apple-system,system-ui,"Segoe UI",Helvetica,"Apple Color Emoji",Arial,sans-serif,"Segoe UI Emoji","Segoe UI Symbol";font-size:16px;fill:rgb(13, 13, 13);}@keyframes edge-animation-frame{from{stroke-dashoffset:0;}}@keyframes dash{to{stroke-dashoffset:0;}}#chatgpt-mermaid-\_r_38t\_ .edge-animation-slow{stroke-dasharray:9,5!important;stroke-dashoffset:900;animation:dash 50s linear infinite;stroke-linecap:round;}#chatgpt-mermaid-\_r_38t\_ .edge-animation-fast{stroke-dasharray:9,5!important;stroke-dashoffset:900;animation:dash 20s linear infinite;stroke-linecap:round;}#chatgpt-mermaid-\_r_38t\_ .error-icon{fill:rgb(243, 243, 243);}#chatgpt-mermaid-\_r_38t\_ .error-text{fill:rgb(13, 13, 13);stroke:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_38t\_ .edge-thickness-normal{stroke-width:1px;}#chatgpt-mermaid-\_r_38t\_ .edge-thickness-thick{stroke-width:3.5px;}#chatgpt-mermaid-\_r_38t\_ .edge-pattern-solid{stroke-dasharray:0;}#chatgpt-mermaid-\_r_38t\_ .edge-thickness-invisible{stroke-width:0;fill:none;}#chatgpt-mermaid-\_r_38t\_ .edge-pattern-dashed{stroke-dasharray:3;}#chatgpt-mermaid-\_r_38t\_ .edge-pattern-dotted{stroke-dasharray:2;}#chatgpt-mermaid-\_r_38t\_ .marker{fill:rgb(143, 143, 143);stroke:rgb(143, 143, 143);}#chatgpt-mermaid-\_r_38t\_ .marker.cross{stroke:rgb(143, 143, 143);}#chatgpt-mermaid-\_r_38t\_ svg{font-family:-apple-system-body,ui-sans-serif,-apple-system,system-ui,"Segoe UI",Helvetica,"Apple Color Emoji",Arial,sans-serif,"Segoe UI Emoji","Segoe UI Symbol";font-size:16px;}#chatgpt-mermaid-\_r_38t\_ p{margin:0;}#chatgpt-mermaid-\_r_38t\_ .label{font-family:-apple-system-body,ui-sans-serif,-apple-system,system-ui,"Segoe UI",Helvetica,"Apple Color Emoji",Arial,sans-serif,"Segoe UI Emoji","Segoe UI Symbol";color:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_38t\_ .cluster-label text{fill:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_38t\_ .cluster-label span{color:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_38t\_ .cluster-label span p{background-color:transparent;}#chatgpt-mermaid-\_r_38t\_ .label text,#chatgpt-mermaid-\_r_38t\_ span{fill:rgb(13, 13, 13);color:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_38t\_ .node rect,#chatgpt-mermaid-\_r_38t\_ .node circle,#chatgpt-mermaid-\_r_38t\_ .node ellipse,#chatgpt-mermaid-\_r_38t\_ .node polygon,#chatgpt-mermaid-\_r_38t\_ .node path{fill:rgb(222, 234, 251);stroke:rgb(83, 154, 248);stroke-width:1px;}#chatgpt-mermaid-\_r_38t\_ .rough-node .label text,#chatgpt-mermaid-\_r_38t\_ .node .label text,#chatgpt-mermaid-\_r_38t\_ .image-shape .label,#chatgpt-mermaid-\_r_38t\_ .icon-shape .label{text-anchor:middle;}#chatgpt-mermaid-\_r_38t\_ .node .katex path{fill:#000;stroke:#000;stroke-width:1px;}#chatgpt-mermaid-\_r_38t\_ .rough-node .label,#chatgpt-mermaid-\_r_38t\_ .node .label,#chatgpt-mermaid-\_r_38t\_ .image-shape .label,#chatgpt-mermaid-\_r_38t\_ .icon-shape .label{text-align:center;}#chatgpt-mermaid-\_r_38t\_ .node.clickable{cursor:pointer;}#chatgpt-mermaid-\_r_38t\_ .root .anchor path{fill:rgb(143, 143, 143)!important;stroke-width:0;stroke:rgb(143, 143, 143);}#chatgpt-mermaid-\_r_38t\_ .arrowheadPath{fill:rgb(143, 143, 143);}#chatgpt-mermaid-\_r_38t\_ .edgePath .path{stroke:rgb(143, 143, 143);stroke-width:1px;}#chatgpt-mermaid-\_r_38t\_ .flowchart-link{stroke:rgb(143, 143, 143);fill:none;}#chatgpt-mermaid-\_r_38t\_ .edgeLabel{background-color:rgb(252, 252, 252);text-align:center;}#chatgpt-mermaid-\_r_38t\_ .edgeLabel p{background-color:rgb(252, 252, 252);}#chatgpt-mermaid-\_r_38t\_ .edgeLabel rect{opacity:0.5;background-color:rgb(252, 252, 252);fill:rgb(252, 252, 252);}#chatgpt-mermaid-\_r_38t\_ .labelBkg{background-color:rgba(252, 252, 252, 0.5);}#chatgpt-mermaid-\_r_38t\_ .cluster rect{fill:rgb(243, 243, 243);stroke:rgba(0, 0, 0, 0.1);stroke-width:1px;}#chatgpt-mermaid-\_r_38t\_ .cluster text{fill:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_38t\_ .cluster span{color:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_38t\_ div.mermaidTooltip{position:absolute;text-align:center;max-width:200px;padding:2px;font-family:-apple-system-body,ui-sans-serif,-apple-system,system-ui,"Segoe UI",Helvetica,"Apple Color Emoji",Arial,sans-serif,"Segoe UI Emoji","Segoe UI Symbol";font-size:12px;background:rgb(243, 243, 243);border:1px solid rgba(0, 0, 0, 0.1);border-radius:2px;pointer-events:none;z-index:100;}#chatgpt-mermaid-\_r_38t\_ .flowchartTitleText{text-anchor:middle;font-size:18px;fill:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_38t\_ rect.text{fill:none;stroke-width:0;}#chatgpt-mermaid-\_r_38t\_ .icon-shape,#chatgpt-mermaid-\_r_38t\_ .image-shape{background-color:rgb(252, 252, 252);text-align:center;}#chatgpt-mermaid-\_r_38t\_ .icon-shape p,#chatgpt-mermaid-\_r_38t\_ .image-shape p{background-color:rgb(252, 252, 252);padding:2px;}#chatgpt-mermaid-\_r_38t\_ .icon-shape .label rect,#chatgpt-mermaid-\_r_38t\_ .image-shape .label rect{opacity:0.5;background-color:rgb(252, 252, 252);fill:rgb(252, 252, 252);}#chatgpt-mermaid-\_r_38t\_ .label-icon{display:inline-block;height:1em;overflow:visible;vertical-align:-0.125em;}#chatgpt-mermaid-\_r_38t\_ .node .label-icon path{fill:currentColor;stroke:revert;stroke-width:revert;}#chatgpt-mermaid-\_r_38t\_ .node .neo-node{stroke:rgb(83, 154, 248);}#chatgpt-mermaid-\_r_38t\_ [data-look="neo"].node rect,#chatgpt-mermaid-\_r_38t\_ [data-look="neo"].cluster rect,#chatgpt-mermaid-\_r_38t\_ [data-look="neo"].node polygon{stroke:url(#chatgpt-mermaid-\_r_38t\_-gradient);filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-\_r_38t\_ [data-look="neo"].swimlane.cluster rect{filter:none;}#chatgpt-mermaid-\_r_38t\_ [data-look="neo"].node path{stroke:url(#chatgpt-mermaid-\_r_38t\_-gradient);stroke-width:1px;}#chatgpt-mermaid-\_r_38t\_ [data-look="neo"].node .outer-path{filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-\_r_38t\_ [data-look="neo"].node .neo-line path{stroke:rgb(83, 154, 248);filter:none;}#chatgpt-mermaid-\_r_38t\_ [data-look="neo"].node circle{stroke:url(#chatgpt-mermaid-\_r_38t\_-gradient);filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-\_r_38t\_ [data-look="neo"].node circle .state-start{fill:#000000;}#chatgpt-mermaid-\_r_38t\_ [data-look="neo"].icon-shape .icon{fill:url(#chatgpt-mermaid-\_r_38t\_-gradient);filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-\_r_38t\_ [data-look="neo"].icon-shape .icon-neo path{stroke:url(#chatgpt-mermaid-\_r_38t\_-gradient);filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-\_r_38t\_ .node text{font-size:14px;font-weight:600;letter-spacing:normal;fill:rgb(0, 79, 153);}#chatgpt-mermaid-\_r_38t\_ .edgeLabels text{font-size:13px;font-weight:600;letter-spacing:-0.08px;fill:rgb(0, 79, 153);}#chatgpt-mermaid-\_r_38t\_ .node tspan[font-weight="normal"],#chatgpt-mermaid-\_r_38t\_ .edgeLabels tspan[font-weight="normal"]{font-weight:600;}#chatgpt-mermaid-\_r_38t\_ .edgeLabel .label rect{opacity:1;rx:13px;ry:13px;fill:rgb(245, 250, 255);stroke:rgb(206, 219, 229);stroke-width:1px;}#chatgpt-mermaid-\_r_38t\_ .node rect,#chatgpt-mermaid-\_r_38t\_ .node circle,#chatgpt-mermaid-\_r_38t\_ .node ellipse,#chatgpt-mermaid-\_r_38t\_ .node polygon,#chatgpt-mermaid-\_r_38t\_ .node path{fill:rgb(229, 243, 255);stroke:rgba(0, 0, 0, 0.1);stroke-width:1px;}#chatgpt-mermaid-\_r_38t\_ .node rect{rx:16px;ry:16px;}#chatgpt-mermaid-\_r_38t\_ .mermaid-decision .label-container{fill:rgb(245, 250, 255);stroke:rgb(206, 219, 229);stroke-dasharray:2,2;}#chatgpt-mermaid-\_r_38t\_ .edgePaths .flowchart-link{stroke:rgb(143, 143, 143);stroke-width:1px;stroke-linecap:round;stroke-linejoin:round;}#chatgpt-mermaid-\_r_38t\_ .marker{fill:rgb(143, 143, 143);stroke:rgb(143, 143, 143);}#chatgpt-mermaid-\_r_38t\_ :root{--mermaid-font-family:-apple-system-body,ui-sans-serif,-apple-system,system-ui,"Segoe UI",Helvetica,"Apple Color Emoji",Arial,sans-serif,"Segoe UI Emoji","Segoe UI Symbol";}创建角色选择基础模型选择美术风格设置基础脸型选择发型和肤色选择身材模板自由调整预览角色是否满意保存角色生成角色资源配置进入换装工坊否是

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

独立技术方案 B

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

\#chatgpt-mermaid-\_r_399\_{font-family:-apple-system-body,ui-sans-serif,-apple-system,system-ui,"Segoe UI",Helvetica,"Apple Color Emoji",Arial,sans-serif,"Segoe UI Emoji","Segoe UI Symbol";font-size:16px;fill:rgb(13, 13, 13);}@keyframes edge-animation-frame{from{stroke-dashoffset:0;}}@keyframes dash{to{stroke-dashoffset:0;}}#chatgpt-mermaid-\_r_399\_ .edge-animation-slow{stroke-dasharray:9,5!important;stroke-dashoffset:900;animation:dash 50s linear infinite;stroke-linecap:round;}#chatgpt-mermaid-\_r_399\_ .edge-animation-fast{stroke-dasharray:9,5!important;stroke-dashoffset:900;animation:dash 20s linear infinite;stroke-linecap:round;}#chatgpt-mermaid-\_r_399\_ .error-icon{fill:rgb(243, 243, 243);}#chatgpt-mermaid-\_r_399\_ .error-text{fill:rgb(13, 13, 13);stroke:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_399\_ .edge-thickness-normal{stroke-width:1px;}#chatgpt-mermaid-\_r_399\_ .edge-thickness-thick{stroke-width:3.5px;}#chatgpt-mermaid-\_r_399\_ .edge-pattern-solid{stroke-dasharray:0;}#chatgpt-mermaid-\_r_399\_ .edge-thickness-invisible{stroke-width:0;fill:none;}#chatgpt-mermaid-\_r_399\_ .edge-pattern-dashed{stroke-dasharray:3;}#chatgpt-mermaid-\_r_399\_ .edge-pattern-dotted{stroke-dasharray:2;}#chatgpt-mermaid-\_r_399\_ .marker{fill:rgb(143, 143, 143);stroke:rgb(143, 143, 143);}#chatgpt-mermaid-\_r_399\_ .marker.cross{stroke:rgb(143, 143, 143);}#chatgpt-mermaid-\_r_399\_ svg{font-family:-apple-system-body,ui-sans-serif,-apple-system,system-ui,"Segoe UI",Helvetica,"Apple Color Emoji",Arial,sans-serif,"Segoe UI Emoji","Segoe UI Symbol";font-size:16px;}#chatgpt-mermaid-\_r_399\_ p{margin:0;}#chatgpt-mermaid-\_r_399\_ .label{font-family:-apple-system-body,ui-sans-serif,-apple-system,system-ui,"Segoe UI",Helvetica,"Apple Color Emoji",Arial,sans-serif,"Segoe UI Emoji","Segoe UI Symbol";color:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_399\_ .cluster-label text{fill:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_399\_ .cluster-label span{color:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_399\_ .cluster-label span p{background-color:transparent;}#chatgpt-mermaid-\_r_399\_ .label text,#chatgpt-mermaid-\_r_399\_ span{fill:rgb(13, 13, 13);color:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_399\_ .node rect,#chatgpt-mermaid-\_r_399\_ .node circle,#chatgpt-mermaid-\_r_399\_ .node ellipse,#chatgpt-mermaid-\_r_399\_ .node polygon,#chatgpt-mermaid-\_r_399\_ .node path{fill:rgb(222, 234, 251);stroke:rgb(83, 154, 248);stroke-width:1px;}#chatgpt-mermaid-\_r_399\_ .rough-node .label text,#chatgpt-mermaid-\_r_399\_ .node .label text,#chatgpt-mermaid-\_r_399\_ .image-shape .label,#chatgpt-mermaid-\_r_399\_ .icon-shape .label{text-anchor:middle;}#chatgpt-mermaid-\_r_399\_ .node .katex path{fill:#000;stroke:#000;stroke-width:1px;}#chatgpt-mermaid-\_r_399\_ .rough-node .label,#chatgpt-mermaid-\_r_399\_ .node .label,#chatgpt-mermaid-\_r_399\_ .image-shape .label,#chatgpt-mermaid-\_r_399\_ .icon-shape .label{text-align:center;}#chatgpt-mermaid-\_r_399\_ .node.clickable{cursor:pointer;}#chatgpt-mermaid-\_r_399\_ .root .anchor path{fill:rgb(143, 143, 143)!important;stroke-width:0;stroke:rgb(143, 143, 143);}#chatgpt-mermaid-\_r_399\_ .arrowheadPath{fill:rgb(143, 143, 143);}#chatgpt-mermaid-\_r_399\_ .edgePath .path{stroke:rgb(143, 143, 143);stroke-width:1px;}#chatgpt-mermaid-\_r_399\_ .flowchart-link{stroke:rgb(143, 143, 143);fill:none;}#chatgpt-mermaid-\_r_399\_ .edgeLabel{background-color:rgb(252, 252, 252);text-align:center;}#chatgpt-mermaid-\_r_399\_ .edgeLabel p{background-color:rgb(252, 252, 252);}#chatgpt-mermaid-\_r_399\_ .edgeLabel rect{opacity:0.5;background-color:rgb(252, 252, 252);fill:rgb(252, 252, 252);}#chatgpt-mermaid-\_r_399\_ .labelBkg{background-color:rgba(252, 252, 252, 0.5);}#chatgpt-mermaid-\_r_399\_ .cluster rect{fill:rgb(243, 243, 243);stroke:rgba(0, 0, 0, 0.1);stroke-width:1px;}#chatgpt-mermaid-\_r_399\_ .cluster text{fill:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_399\_ .cluster span{color:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_399\_ div.mermaidTooltip{position:absolute;text-align:center;max-width:200px;padding:2px;font-family:-apple-system-body,ui-sans-serif,-apple-system,system-ui,"Segoe UI",Helvetica,"Apple Color Emoji",Arial,sans-serif,"Segoe UI Emoji","Segoe UI Symbol";font-size:12px;background:rgb(243, 243, 243);border:1px solid rgba(0, 0, 0, 0.1);border-radius:2px;pointer-events:none;z-index:100;}#chatgpt-mermaid-\_r_399\_ .flowchartTitleText{text-anchor:middle;font-size:18px;fill:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_399\_ rect.text{fill:none;stroke-width:0;}#chatgpt-mermaid-\_r_399\_ .icon-shape,#chatgpt-mermaid-\_r_399\_ .image-shape{background-color:rgb(252, 252, 252);text-align:center;}#chatgpt-mermaid-\_r_399\_ .icon-shape p,#chatgpt-mermaid-\_r_399\_ .image-shape p{background-color:rgb(252, 252, 252);padding:2px;}#chatgpt-mermaid-\_r_399\_ .icon-shape .label rect,#chatgpt-mermaid-\_r_399\_ .image-shape .label rect{opacity:0.5;background-color:rgb(252, 252, 252);fill:rgb(252, 252, 252);}#chatgpt-mermaid-\_r_399\_ .label-icon{display:inline-block;height:1em;overflow:visible;vertical-align:-0.125em;}#chatgpt-mermaid-\_r_399\_ .node .label-icon path{fill:currentColor;stroke:revert;stroke-width:revert;}#chatgpt-mermaid-\_r_399\_ .node .neo-node{stroke:rgb(83, 154, 248);}#chatgpt-mermaid-\_r_399\_ [data-look="neo"].node rect,#chatgpt-mermaid-\_r_399\_ [data-look="neo"].cluster rect,#chatgpt-mermaid-\_r_399\_ [data-look="neo"].node polygon{stroke:url(#chatgpt-mermaid-\_r_399\_-gradient);filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-\_r_399\_ [data-look="neo"].swimlane.cluster rect{filter:none;}#chatgpt-mermaid-\_r_399\_ [data-look="neo"].node path{stroke:url(#chatgpt-mermaid-\_r_399\_-gradient);stroke-width:1px;}#chatgpt-mermaid-\_r_399\_ [data-look="neo"].node .outer-path{filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-\_r_399\_ [data-look="neo"].node .neo-line path{stroke:rgb(83, 154, 248);filter:none;}#chatgpt-mermaid-\_r_399\_ [data-look="neo"].node circle{stroke:url(#chatgpt-mermaid-\_r_399\_-gradient);filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-\_r_399\_ [data-look="neo"].node circle .state-start{fill:#000000;}#chatgpt-mermaid-\_r_399\_ [data-look="neo"].icon-shape .icon{fill:url(#chatgpt-mermaid-\_r_399\_-gradient);filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-\_r_399\_ [data-look="neo"].icon-shape .icon-neo path{stroke:url(#chatgpt-mermaid-\_r_399\_-gradient);filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-\_r_399\_ .node text{font-size:14px;font-weight:600;letter-spacing:normal;fill:rgb(0, 79, 153);}#chatgpt-mermaid-\_r_399\_ .edgeLabels text{font-size:13px;font-weight:600;letter-spacing:-0.08px;fill:rgb(0, 79, 153);}#chatgpt-mermaid-\_r_399\_ .node tspan[font-weight="normal"],#chatgpt-mermaid-\_r_399\_ .edgeLabels tspan[font-weight="normal"]{font-weight:600;}#chatgpt-mermaid-\_r_399\_ .edgeLabel .label rect{opacity:1;rx:13px;ry:13px;fill:rgb(245, 250, 255);stroke:rgb(206, 219, 229);stroke-width:1px;}#chatgpt-mermaid-\_r_399\_ .node rect,#chatgpt-mermaid-\_r_399\_ .node circle,#chatgpt-mermaid-\_r_399\_ .node ellipse,#chatgpt-mermaid-\_r_399\_ .node polygon,#chatgpt-mermaid-\_r_399\_ .node path{fill:rgb(229, 243, 255);stroke:rgba(0, 0, 0, 0.1);stroke-width:1px;}#chatgpt-mermaid-\_r_399\_ .node rect{rx:16px;ry:16px;}#chatgpt-mermaid-\_r_399\_ .mermaid-decision .label-container{fill:rgb(245, 250, 255);stroke:rgb(206, 219, 229);stroke-dasharray:2,2;}#chatgpt-mermaid-\_r_399\_ .edgePaths .flowchart-link{stroke:rgb(143, 143, 143);stroke-width:1px;stroke-linecap:round;stroke-linejoin:round;}#chatgpt-mermaid-\_r_399\_ .marker{fill:rgb(143, 143, 143);stroke:rgb(143, 143, 143);}#chatgpt-mermaid-\_r_399\_ :root{--mermaid-font-family:-apple-system-body,ui-sans-serif,-apple-system,system-ui,"Segoe UI",Helvetica,"Apple Color Emoji",Arial,sans-serif,"Segoe UI Emoji","Segoe UI Symbol";}原始衣物照片安全验证内容审核质量检测主体分割生成 Mask边缘清理纹理保留类别和部位识别锚点定位图层定义生成资产 Manifest角色适配测试渲染预览用户确认/人工校验正式服装资产

### **21.4 分割与抠图方案**

候选技术：

- SAM2。
- MediaPipe Image Segmenter。
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
| 商用授权 | 代码、模型权重、训练数据许可 |

必须区分：

- 分割模型负责识别像素区域。
- 生成模型负责补全和转换素材。
- 分类模型负责理解衣物属性。
- 适配引擎负责把资产挂到角色上。

不能把这四种任务全部交给一个图像生成模型。

### **21.5 纹理保真策略**

这是服装资产生成的关键质量门槛。

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

建议定义：

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

锚点不只是一个坐标，还应包含：

- 坐标系。
- 位置。
- 旋转。
- 缩放。
- 父级骨骼。
- 允许偏移范围。
- 适配规则。

### **21.7 服装 Manifest**

每件正式服装都应该有一份机器可读的 Manifest。

```
{
  "assetId": "GA_TOP_001",
  "version": 1,
  "assetType": "LAYERED_2D",
  "category": "top",
  "bodyParts": [
    "torso",
    "left_arm",
    "right_arm"
  ],
  "anchors": {
    "neck": {
      "x": 0.5,
      "y": 0.08
    },
    "leftShoulder": {
      "x": 0.22,
      "y": 0.18
    },
    "rightShoulder": {
      "x": 0.78,
      "y": 0.18
    },
    "waist": {
      "x": 0.5,
      "y": 0.82
    }
  },
  "layers": {
    "order": 30,
    "occlusionGroup": "upper_body"
  },
  "fit": {
    "supportedBodyTypes": [
      "slim",
      "standard",
      "curvy"
    ],
    "scaleRange": {
      "min": 0.8,
      "max": 1.3
    },
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

初始图层建议：

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

注意：真实渲染不能完全依靠固定 Layer 数字。

例如耳环有一部分应该在耳朵前面，另一部分应该在头发后面。长发也可能需要前发、后发分层。

因此应同时使用：

- `layer_order`
- `occlusion_group`
- `depth_order`
- `anchor_binding`
- `mask_reference`

### **21.9 服装冲突检测**

**[技术设计 TECH]**

建立冲突规则表：

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

注意：这是一种初期工程抽象，不意味着只通过缩放就能解决真实 3D 布料适配。复杂服装后续仍需网格变形、骨骼绑定或重新生成资产。

### **21.11 换装渲染流程**

角色配置服务资产服务渲染模块Flutter界面用户角色配置服务资产服务渲染模块Flutter界面用户#chatgpt-mermaid-\_r_39l\_{font-family:-apple-system-body,ui-sans-serif,-apple-system,system-ui,"Segoe UI",Helvetica,"Apple Color Emoji",Arial,sans-serif,"Segoe UI Emoji","Segoe UI Symbol";font-size:16px;fill:rgb(13, 13, 13);}@keyframes edge-animation-frame{from{stroke-dashoffset:0;}}@keyframes dash{to{stroke-dashoffset:0;}}#chatgpt-mermaid-\_r_39l\_ .edge-animation-slow{stroke-dasharray:9,5!important;stroke-dashoffset:900;animation:dash 50s linear infinite;stroke-linecap:round;}#chatgpt-mermaid-\_r_39l\_ .edge-animation-fast{stroke-dasharray:9,5!important;stroke-dashoffset:900;animation:dash 20s linear infinite;stroke-linecap:round;}#chatgpt-mermaid-\_r_39l\_ .error-icon{fill:rgb(243, 243, 243);}#chatgpt-mermaid-\_r_39l\_ .error-text{fill:rgb(13, 13, 13);stroke:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_39l\_ .edge-thickness-normal{stroke-width:1px;}#chatgpt-mermaid-\_r_39l\_ .edge-thickness-thick{stroke-width:3.5px;}#chatgpt-mermaid-\_r_39l\_ .edge-pattern-solid{stroke-dasharray:0;}#chatgpt-mermaid-\_r_39l\_ .edge-thickness-invisible{stroke-width:0;fill:none;}#chatgpt-mermaid-\_r_39l\_ .edge-pattern-dashed{stroke-dasharray:3;}#chatgpt-mermaid-\_r_39l\_ .edge-pattern-dotted{stroke-dasharray:2;}#chatgpt-mermaid-\_r_39l\_ .marker{fill:rgb(143, 143, 143);stroke:rgb(143, 143, 143);}#chatgpt-mermaid-\_r_39l\_ .marker.cross{stroke:rgb(143, 143, 143);}#chatgpt-mermaid-\_r_39l\_ svg{font-family:-apple-system-body,ui-sans-serif,-apple-system,system-ui,"Segoe UI",Helvetica,"Apple Color Emoji",Arial,sans-serif,"Segoe UI Emoji","Segoe UI Symbol";font-size:16px;}#chatgpt-mermaid-\_r_39l\_ p{margin:0;}#chatgpt-mermaid-\_r_39l\_ .actor{stroke:rgb(83, 154, 248);fill:rgb(222, 234, 251);stroke-width:1;}#chatgpt-mermaid-\_r_39l\_ rect.actor.outer-path[data-look="neo"]{filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-\_r_39l\_ rect.note[data-look="neo"]{stroke:rgb(107, 198, 127);fill:rgb(243, 243, 243);filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-\_r_39l\_ text.actor>tspan{fill:rgb(13, 13, 13);stroke:none;}#chatgpt-mermaid-\_r_39l\_ .actor-line{stroke:rgb(143, 143, 143);}#chatgpt-mermaid-\_r_39l\_ .innerArc{stroke-width:1.5;stroke-dasharray:none;}#chatgpt-mermaid-\_r_39l\_ .messageLine0{stroke-width:1.5;stroke-dasharray:none;stroke:rgb(143, 143, 143);}#chatgpt-mermaid-\_r_39l\_ .messageLine1{stroke-width:1.5;stroke-dasharray:2,2;stroke:rgb(143, 143, 143);}#chatgpt-mermaid-\_r_39l\_ [id$="-arrowhead"] path{fill:rgb(143, 143, 143);stroke:rgb(143, 143, 143);}#chatgpt-mermaid-\_r_39l\_ .sequenceNumber{fill:#707070;}#chatgpt-mermaid-\_r_39l\_ [id$="-sequencenumber"]{fill:rgb(143, 143, 143);}#chatgpt-mermaid-\_r_39l\_ [id$="-crosshead"] path{fill:rgb(143, 143, 143);stroke:rgb(143, 143, 143);}#chatgpt-mermaid-\_r_39l\_ .messageText{fill:rgb(13, 13, 13);stroke:none;}#chatgpt-mermaid-\_r_39l\_ .labelBox{stroke:rgba(0, 0, 0, 0.1);fill:rgb(252, 252, 252);filter:none;}#chatgpt-mermaid-\_r_39l\_ .labelText,#chatgpt-mermaid-\_r_39l\_ .labelText>tspan{fill:rgb(13, 13, 13);stroke:none;}#chatgpt-mermaid-\_r_39l\_ .loopText,#chatgpt-mermaid-\_r_39l\_ .loopText>tspan{fill:rgb(13, 13, 13);stroke:none;}#chatgpt-mermaid-\_r_39l\_ .sectionTitle,#chatgpt-mermaid-\_r_39l\_ .sectionTitle>tspan{fill:rgb(13, 13, 13);stroke:none;}#chatgpt-mermaid-\_r_39l\_ .loopLine{stroke-width:2px;stroke-dasharray:2,2;stroke:rgba(0, 0, 0, 0.1);fill:rgba(0, 0, 0, 0.1);}#chatgpt-mermaid-\_r_39l\_ .note{stroke:rgb(107, 198, 127);fill:rgb(243, 243, 243);}#chatgpt-mermaid-\_r_39l\_ .noteText,#chatgpt-mermaid-\_r_39l\_ .noteText>tspan{fill:rgb(13, 13, 13);stroke:none;font-weight:normal;}#chatgpt-mermaid-\_r_39l\_ .activation0{fill:rgb(243, 243, 243);stroke:hsl(0, 0%, 85.2941176471%);}#chatgpt-mermaid-\_r_39l\_ .activation1{fill:rgb(243, 243, 243);stroke:hsl(0, 0%, 85.2941176471%);}#chatgpt-mermaid-\_r_39l\_ .activation2{fill:rgb(243, 243, 243);stroke:hsl(0, 0%, 85.2941176471%);}#chatgpt-mermaid-\_r_39l\_ .actorPopupMenu{position:absolute;}#chatgpt-mermaid-\_r_39l\_ .actorPopupMenuPanel{position:absolute;fill:rgb(222, 234, 251);box-shadow:0px 8px 16px 0px rgba(0,0,0,0.2);filter:drop-shadow(3px 5px 2px rgb(0 0 0 / 0.4));}#chatgpt-mermaid-\_r_39l\_ .actor-man circle,#chatgpt-mermaid-\_r_39l\_ line{fill:rgb(222, 234, 251);stroke-width:2px;}#chatgpt-mermaid-\_r_39l\_ g rect.rect{filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));stroke:rgb(83, 154, 248);}#chatgpt-mermaid-\_r_39l\_ .node .neo-node{stroke:rgb(83, 154, 248);}#chatgpt-mermaid-\_r_39l\_ [data-look="neo"].node rect,#chatgpt-mermaid-\_r_39l\_ [data-look="neo"].cluster rect,#chatgpt-mermaid-\_r_39l\_ [data-look="neo"].node polygon{stroke:url(#chatgpt-mermaid-\_r_39l\_-gradient);filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-\_r_39l\_ [data-look="neo"].swimlane.cluster rect{filter:none;}#chatgpt-mermaid-\_r_39l\_ [data-look="neo"].node path{stroke:url(#chatgpt-mermaid-\_r_39l\_-gradient);stroke-width:1px;}#chatgpt-mermaid-\_r_39l\_ [data-look="neo"].node .outer-path{filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-\_r_39l\_ [data-look="neo"].node .neo-line path{stroke:rgb(83, 154, 248);filter:none;}#chatgpt-mermaid-\_r_39l\_ [data-look="neo"].node circle{stroke:url(#chatgpt-mermaid-\_r_39l\_-gradient);filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-\_r_39l\_ [data-look="neo"].node circle .state-start{fill:#000000;}#chatgpt-mermaid-\_r_39l\_ [data-look="neo"].icon-shape .icon{fill:url(#chatgpt-mermaid-\_r_39l\_-gradient);filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-\_r_39l\_ [data-look="neo"].icon-shape .icon-neo path{stroke:url(#chatgpt-mermaid-\_r_39l\_-gradient);filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-\_r_39l\_ :root{--mermaid-font-family:-apple-system-body,ui-sans-serif,-apple-system,system-ui,"Segoe UI",Helvetica,"Apple Color Emoji",Arial,sans-serif,"Segoe UI Emoji","Segoe UI Symbol";}选择服装查询服装资产返回Manifest与资源地址查询当前角色参数返回身材与骨骼配置加载服装与角色检查锚点与图层执行适配计算执行冲突与遮挡处理返回预览状态调整位置/缩放/层级更新变换保存穿搭保存资产引用与变换返回保存结果

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

**[产品需求 PRD]**

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

\#chatgpt-mermaid-\_r_39s\_{font-family:-apple-system-body,ui-sans-serif,-apple-system,system-ui,"Segoe UI",Helvetica,"Apple Color Emoji",Arial,sans-serif,"Segoe UI Emoji","Segoe UI Symbol";font-size:16px;fill:rgb(13, 13, 13);}@keyframes edge-animation-frame{from{stroke-dashoffset:0;}}@keyframes dash{to{stroke-dashoffset:0;}}#chatgpt-mermaid-\_r_39s\_ .edge-animation-slow{stroke-dasharray:9,5!important;stroke-dashoffset:900;animation:dash 50s linear infinite;stroke-linecap:round;}#chatgpt-mermaid-\_r_39s\_ .edge-animation-fast{stroke-dasharray:9,5!important;stroke-dashoffset:900;animation:dash 20s linear infinite;stroke-linecap:round;}#chatgpt-mermaid-\_r_39s\_ .error-icon{fill:rgb(243, 243, 243);}#chatgpt-mermaid-\_r_39s\_ .error-text{fill:rgb(13, 13, 13);stroke:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_39s\_ .edge-thickness-normal{stroke-width:1px;}#chatgpt-mermaid-\_r_39s\_ .edge-thickness-thick{stroke-width:3.5px;}#chatgpt-mermaid-\_r_39s\_ .edge-pattern-solid{stroke-dasharray:0;}#chatgpt-mermaid-\_r_39s\_ .edge-thickness-invisible{stroke-width:0;fill:none;}#chatgpt-mermaid-\_r_39s\_ .edge-pattern-dashed{stroke-dasharray:3;}#chatgpt-mermaid-\_r_39s\_ .edge-pattern-dotted{stroke-dasharray:2;}#chatgpt-mermaid-\_r_39s\_ .marker{fill:rgb(143, 143, 143);stroke:rgb(143, 143, 143);}#chatgpt-mermaid-\_r_39s\_ .marker.cross{stroke:rgb(143, 143, 143);}#chatgpt-mermaid-\_r_39s\_ svg{font-family:-apple-system-body,ui-sans-serif,-apple-system,system-ui,"Segoe UI",Helvetica,"Apple Color Emoji",Arial,sans-serif,"Segoe UI Emoji","Segoe UI Symbol";font-size:16px;}#chatgpt-mermaid-\_r_39s\_ p{margin:0;}#chatgpt-mermaid-\_r_39s\_ defs [id$="-barbEnd"]{fill:rgb(143, 143, 143);stroke:rgb(143, 143, 143);}#chatgpt-mermaid-\_r_39s\_ g.stateGroup text{fill:rgb(83, 154, 248);stroke:none;font-size:10px;}#chatgpt-mermaid-\_r_39s\_ g.stateGroup text{fill:rgb(13, 13, 13);stroke:none;font-size:10px;}#chatgpt-mermaid-\_r_39s\_ g.stateGroup .state-title{font-weight:bolder;fill:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_39s\_ g.stateGroup rect{fill:rgb(222, 234, 251);stroke:rgb(83, 154, 248);}#chatgpt-mermaid-\_r_39s\_ g.stateGroup line{stroke:rgb(143, 143, 143);stroke-width:1;}#chatgpt-mermaid-\_r_39s\_ .transition{stroke:rgb(143, 143, 143);stroke-width:1;fill:none;}#chatgpt-mermaid-\_r_39s\_ .stateGroup .composit{fill:transparent;border-bottom:1px;}#chatgpt-mermaid-\_r_39s\_ .stateGroup .alt-composit{fill:#e0e0e0;border-bottom:1px;}#chatgpt-mermaid-\_r_39s\_ .state-note{stroke:rgb(107, 198, 127);fill:rgb(243, 243, 243);}#chatgpt-mermaid-\_r_39s\_ .state-note text{fill:rgb(13, 13, 13);stroke:none;font-size:10px;}#chatgpt-mermaid-\_r_39s\_ .stateLabel .box{stroke:none;stroke-width:0;fill:rgb(222, 234, 251);opacity:0.5;}#chatgpt-mermaid-\_r_39s\_ .edgeLabel .label rect{fill:rgb(222, 234, 251);opacity:0.5;}#chatgpt-mermaid-\_r_39s\_ .edgeLabel{background-color:rgb(252, 252, 252);text-align:center;}#chatgpt-mermaid-\_r_39s\_ .edgeLabel p{background-color:rgb(252, 252, 252);}#chatgpt-mermaid-\_r_39s\_ .edgeLabel rect{opacity:0.5;background-color:rgb(252, 252, 252);fill:rgb(252, 252, 252);}#chatgpt-mermaid-\_r_39s\_ .edgeLabel .label text{fill:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_39s\_ .label div .edgeLabel{color:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_39s\_ .stateLabel text{fill:rgb(13, 13, 13);font-size:10px;font-weight:bold;}#chatgpt-mermaid-\_r_39s\_ .node circle.state-start{fill:rgb(143, 143, 143);stroke:rgb(143, 143, 143);}#chatgpt-mermaid-\_r_39s\_ .node .fork-join{fill:rgb(143, 143, 143);stroke:rgb(143, 143, 143);}#chatgpt-mermaid-\_r_39s\_ .node circle.state-end{fill:rgb(83, 154, 248);stroke:transparent;stroke-width:1.5;}#chatgpt-mermaid-\_r_39s\_ .end-state-inner{fill:transparent;stroke-width:1.5;}#chatgpt-mermaid-\_r_39s\_ .node rect{fill:rgb(222, 234, 251);stroke:rgb(83, 154, 248);stroke-width:1px;}#chatgpt-mermaid-\_r_39s\_ .node polygon{fill:rgb(222, 234, 251);stroke:rgb(83, 154, 248);stroke-width:1px;}#chatgpt-mermaid-\_r_39s\_ [id$="-barbEnd"]{fill:rgb(143, 143, 143);}#chatgpt-mermaid-\_r_39s\_ .statediagram-cluster rect{fill:rgb(222, 234, 251);stroke:rgb(83, 154, 248);stroke-width:1px;}#chatgpt-mermaid-\_r_39s\_ .cluster-label,#chatgpt-mermaid-\_r_39s\_ .nodeLabel{color:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_39s\_ .statediagram-cluster rect.outer{rx:5px;ry:5px;}#chatgpt-mermaid-\_r_39s\_ .statediagram-state .divider{stroke:rgb(83, 154, 248);}#chatgpt-mermaid-\_r_39s\_ .statediagram-state .title-state{rx:5px;ry:5px;}#chatgpt-mermaid-\_r_39s\_ .statediagram-cluster.statediagram-cluster .inner{fill:transparent;}#chatgpt-mermaid-\_r_39s\_ .statediagram-cluster.statediagram-cluster-alt .inner{fill:rgb(243, 243, 243);}#chatgpt-mermaid-\_r_39s\_ .statediagram-cluster .inner{rx:0;ry:0;}#chatgpt-mermaid-\_r_39s\_ .statediagram-state rect.basic{rx:5px;ry:5px;}#chatgpt-mermaid-\_r_39s\_ .statediagram-state rect.divider{stroke-dasharray:10,10;fill:rgb(243, 243, 243);}#chatgpt-mermaid-\_r_39s\_ .note-edge{stroke-dasharray:5;}#chatgpt-mermaid-\_r_39s\_ .statediagram-note rect{fill:rgb(243, 243, 243);stroke:rgb(107, 198, 127);stroke-width:1px;rx:0;ry:0;}#chatgpt-mermaid-\_r_39s\_ .statediagram-note rect{fill:rgb(243, 243, 243);stroke:rgb(107, 198, 127);stroke-width:1px;rx:0;ry:0;}#chatgpt-mermaid-\_r_39s\_ .statediagram-note text{fill:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_39s\_ .statediagram-note .nodeLabel{color:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_39s\_ .statediagram .edgeLabel{color:red;}#chatgpt-mermaid-\_r_39s\_ [id$="-dependencyStart"],#chatgpt-mermaid-\_r_39s\_ [id$="-dependencyEnd"]{fill:rgb(143, 143, 143);stroke:rgb(143, 143, 143);stroke-width:1;}#chatgpt-mermaid-\_r_39s\_ .statediagramTitleText{text-anchor:middle;font-size:18px;fill:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_39s\_ [data-look="neo"].statediagram-cluster rect{fill:rgb(222, 234, 251);stroke:url(#chatgpt-mermaid-\_r_39s\_-gradient);stroke-width:1;}#chatgpt-mermaid-\_r_39s\_ [data-look="neo"].statediagram-cluster rect.outer{rx:5px;ry:5px;filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-\_r_39s\_ .node .neo-node{stroke:rgb(83, 154, 248);}#chatgpt-mermaid-\_r_39s\_ [data-look="neo"].node rect,#chatgpt-mermaid-\_r_39s\_ [data-look="neo"].cluster rect,#chatgpt-mermaid-\_r_39s\_ [data-look="neo"].node polygon{stroke:url(#chatgpt-mermaid-\_r_39s\_-gradient);filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-\_r_39s\_ [data-look="neo"].swimlane.cluster rect{filter:none;}#chatgpt-mermaid-\_r_39s\_ [data-look="neo"].node path{stroke:url(#chatgpt-mermaid-\_r_39s\_-gradient);stroke-width:1px;}#chatgpt-mermaid-\_r_39s\_ [data-look="neo"].node .outer-path{filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-\_r_39s\_ [data-look="neo"].node .neo-line path{stroke:rgb(83, 154, 248);filter:none;}#chatgpt-mermaid-\_r_39s\_ [data-look="neo"].node circle{stroke:url(#chatgpt-mermaid-\_r_39s\_-gradient);filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-\_r_39s\_ [data-look="neo"].node circle .state-start{fill:#000000;}#chatgpt-mermaid-\_r_39s\_ [data-look="neo"].icon-shape .icon{fill:url(#chatgpt-mermaid-\_r_39s\_-gradient);filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-\_r_39s\_ [data-look="neo"].icon-shape .icon-neo path{stroke:url(#chatgpt-mermaid-\_r_39s\_-gradient);filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-\_r_39s\_ :root{--mermaid-font-family:-apple-system-body,ui-sans-serif,-apple-system,system-ui,"Segoe UI",Helvetica,"Apple Color Emoji",Arial,sans-serif,"Segoe UI Emoji","Segoe UI Symbol";}PRIVATEPUBLIC_DISPLAYFREE_REUSEPAID_LICENSEREVOKED发布展示开启免费复用开启付费授权关闭复用关闭交易设为私有撤销授权撤销新增授权重新发布

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

**[产品需求 PRD]**

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

\#chatgpt-mermaid-\_r_3a3\_{font-family:-apple-system-body,ui-sans-serif,-apple-system,system-ui,"Segoe UI",Helvetica,"Apple Color Emoji",Arial,sans-serif,"Segoe UI Emoji","Segoe UI Symbol";font-size:16px;fill:rgb(13, 13, 13);}@keyframes edge-animation-frame{from{stroke-dashoffset:0;}}@keyframes dash{to{stroke-dashoffset:0;}}#chatgpt-mermaid-\_r_3a3\_ .edge-animation-slow{stroke-dasharray:9,5!important;stroke-dashoffset:900;animation:dash 50s linear infinite;stroke-linecap:round;}#chatgpt-mermaid-\_r_3a3\_ .edge-animation-fast{stroke-dasharray:9,5!important;stroke-dashoffset:900;animation:dash 20s linear infinite;stroke-linecap:round;}#chatgpt-mermaid-\_r_3a3\_ .error-icon{fill:rgb(243, 243, 243);}#chatgpt-mermaid-\_r_3a3\_ .error-text{fill:rgb(13, 13, 13);stroke:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_3a3\_ .edge-thickness-normal{stroke-width:1px;}#chatgpt-mermaid-\_r_3a3\_ .edge-thickness-thick{stroke-width:3.5px;}#chatgpt-mermaid-\_r_3a3\_ .edge-pattern-solid{stroke-dasharray:0;}#chatgpt-mermaid-\_r_3a3\_ .edge-thickness-invisible{stroke-width:0;fill:none;}#chatgpt-mermaid-\_r_3a3\_ .edge-pattern-dashed{stroke-dasharray:3;}#chatgpt-mermaid-\_r_3a3\_ .edge-pattern-dotted{stroke-dasharray:2;}#chatgpt-mermaid-\_r_3a3\_ .marker{fill:rgb(143, 143, 143);stroke:rgb(143, 143, 143);}#chatgpt-mermaid-\_r_3a3\_ .marker.cross{stroke:rgb(143, 143, 143);}#chatgpt-mermaid-\_r_3a3\_ svg{font-family:-apple-system-body,ui-sans-serif,-apple-system,system-ui,"Segoe UI",Helvetica,"Apple Color Emoji",Arial,sans-serif,"Segoe UI Emoji","Segoe UI Symbol";font-size:16px;}#chatgpt-mermaid-\_r_3a3\_ p{margin:0;}#chatgpt-mermaid-\_r_3a3\_ defs [id$="-barbEnd"]{fill:rgb(143, 143, 143);stroke:rgb(143, 143, 143);}#chatgpt-mermaid-\_r_3a3\_ g.stateGroup text{fill:rgb(83, 154, 248);stroke:none;font-size:10px;}#chatgpt-mermaid-\_r_3a3\_ g.stateGroup text{fill:rgb(13, 13, 13);stroke:none;font-size:10px;}#chatgpt-mermaid-\_r_3a3\_ g.stateGroup .state-title{font-weight:bolder;fill:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_3a3\_ g.stateGroup rect{fill:rgb(222, 234, 251);stroke:rgb(83, 154, 248);}#chatgpt-mermaid-\_r_3a3\_ g.stateGroup line{stroke:rgb(143, 143, 143);stroke-width:1;}#chatgpt-mermaid-\_r_3a3\_ .transition{stroke:rgb(143, 143, 143);stroke-width:1;fill:none;}#chatgpt-mermaid-\_r_3a3\_ .stateGroup .composit{fill:transparent;border-bottom:1px;}#chatgpt-mermaid-\_r_3a3\_ .stateGroup .alt-composit{fill:#e0e0e0;border-bottom:1px;}#chatgpt-mermaid-\_r_3a3\_ .state-note{stroke:rgb(107, 198, 127);fill:rgb(243, 243, 243);}#chatgpt-mermaid-\_r_3a3\_ .state-note text{fill:rgb(13, 13, 13);stroke:none;font-size:10px;}#chatgpt-mermaid-\_r_3a3\_ .stateLabel .box{stroke:none;stroke-width:0;fill:rgb(222, 234, 251);opacity:0.5;}#chatgpt-mermaid-\_r_3a3\_ .edgeLabel .label rect{fill:rgb(222, 234, 251);opacity:0.5;}#chatgpt-mermaid-\_r_3a3\_ .edgeLabel{background-color:rgb(252, 252, 252);text-align:center;}#chatgpt-mermaid-\_r_3a3\_ .edgeLabel p{background-color:rgb(252, 252, 252);}#chatgpt-mermaid-\_r_3a3\_ .edgeLabel rect{opacity:0.5;background-color:rgb(252, 252, 252);fill:rgb(252, 252, 252);}#chatgpt-mermaid-\_r_3a3\_ .edgeLabel .label text{fill:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_3a3\_ .label div .edgeLabel{color:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_3a3\_ .stateLabel text{fill:rgb(13, 13, 13);font-size:10px;font-weight:bold;}#chatgpt-mermaid-\_r_3a3\_ .node circle.state-start{fill:rgb(143, 143, 143);stroke:rgb(143, 143, 143);}#chatgpt-mermaid-\_r_3a3\_ .node .fork-join{fill:rgb(143, 143, 143);stroke:rgb(143, 143, 143);}#chatgpt-mermaid-\_r_3a3\_ .node circle.state-end{fill:rgb(83, 154, 248);stroke:transparent;stroke-width:1.5;}#chatgpt-mermaid-\_r_3a3\_ .end-state-inner{fill:transparent;stroke-width:1.5;}#chatgpt-mermaid-\_r_3a3\_ .node rect{fill:rgb(222, 234, 251);stroke:rgb(83, 154, 248);stroke-width:1px;}#chatgpt-mermaid-\_r_3a3\_ .node polygon{fill:rgb(222, 234, 251);stroke:rgb(83, 154, 248);stroke-width:1px;}#chatgpt-mermaid-\_r_3a3\_ [id$="-barbEnd"]{fill:rgb(143, 143, 143);}#chatgpt-mermaid-\_r_3a3\_ .statediagram-cluster rect{fill:rgb(222, 234, 251);stroke:rgb(83, 154, 248);stroke-width:1px;}#chatgpt-mermaid-\_r_3a3\_ .cluster-label,#chatgpt-mermaid-\_r_3a3\_ .nodeLabel{color:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_3a3\_ .statediagram-cluster rect.outer{rx:5px;ry:5px;}#chatgpt-mermaid-\_r_3a3\_ .statediagram-state .divider{stroke:rgb(83, 154, 248);}#chatgpt-mermaid-\_r_3a3\_ .statediagram-state .title-state{rx:5px;ry:5px;}#chatgpt-mermaid-\_r_3a3\_ .statediagram-cluster.statediagram-cluster .inner{fill:transparent;}#chatgpt-mermaid-\_r_3a3\_ .statediagram-cluster.statediagram-cluster-alt .inner{fill:rgb(243, 243, 243);}#chatgpt-mermaid-\_r_3a3\_ .statediagram-cluster .inner{rx:0;ry:0;}#chatgpt-mermaid-\_r_3a3\_ .statediagram-state rect.basic{rx:5px;ry:5px;}#chatgpt-mermaid-\_r_3a3\_ .statediagram-state rect.divider{stroke-dasharray:10,10;fill:rgb(243, 243, 243);}#chatgpt-mermaid-\_r_3a3\_ .note-edge{stroke-dasharray:5;}#chatgpt-mermaid-\_r_3a3\_ .statediagram-note rect{fill:rgb(243, 243, 243);stroke:rgb(107, 198, 127);stroke-width:1px;rx:0;ry:0;}#chatgpt-mermaid-\_r_3a3\_ .statediagram-note rect{fill:rgb(243, 243, 243);stroke:rgb(107, 198, 127);stroke-width:1px;rx:0;ry:0;}#chatgpt-mermaid-\_r_3a3\_ .statediagram-note text{fill:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_3a3\_ .statediagram-note .nodeLabel{color:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_3a3\_ .statediagram .edgeLabel{color:red;}#chatgpt-mermaid-\_r_3a3\_ [id$="-dependencyStart"],#chatgpt-mermaid-\_r_3a3\_ [id$="-dependencyEnd"]{fill:rgb(143, 143, 143);stroke:rgb(143, 143, 143);stroke-width:1;}#chatgpt-mermaid-\_r_3a3\_ .statediagramTitleText{text-anchor:middle;font-size:18px;fill:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_3a3\_ [data-look="neo"].statediagram-cluster rect{fill:rgb(222, 234, 251);stroke:url(#chatgpt-mermaid-\_r_3a3\_-gradient);stroke-width:1;}#chatgpt-mermaid-\_r_3a3\_ [data-look="neo"].statediagram-cluster rect.outer{rx:5px;ry:5px;filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-\_r_3a3\_ .node .neo-node{stroke:rgb(83, 154, 248);}#chatgpt-mermaid-\_r_3a3\_ [data-look="neo"].node rect,#chatgpt-mermaid-\_r_3a3\_ [data-look="neo"].cluster rect,#chatgpt-mermaid-\_r_3a3\_ [data-look="neo"].node polygon{stroke:url(#chatgpt-mermaid-\_r_3a3\_-gradient);filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-\_r_3a3\_ [data-look="neo"].swimlane.cluster rect{filter:none;}#chatgpt-mermaid-\_r_3a3\_ [data-look="neo"].node path{stroke:url(#chatgpt-mermaid-\_r_3a3\_-gradient);stroke-width:1px;}#chatgpt-mermaid-\_r_3a3\_ [data-look="neo"].node .outer-path{filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-\_r_3a3\_ [data-look="neo"].node .neo-line path{stroke:rgb(83, 154, 248);filter:none;}#chatgpt-mermaid-\_r_3a3\_ [data-look="neo"].node circle{stroke:url(#chatgpt-mermaid-\_r_3a3\_-gradient);filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-\_r_3a3\_ [data-look="neo"].node circle .state-start{fill:#000000;}#chatgpt-mermaid-\_r_3a3\_ [data-look="neo"].icon-shape .icon{fill:url(#chatgpt-mermaid-\_r_3a3\_-gradient);filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-\_r_3a3\_ [data-look="neo"].icon-shape .icon-neo path{stroke:url(#chatgpt-mermaid-\_r_3a3\_-gradient);filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-\_r_3a3\_ :root{--mermaid-font-family:-apple-system-body,ui-sans-serif,-apple-system,system-ui,"Segoe UI",Helvetica,"Apple Color Emoji",Arial,sans-serif,"Segoe UI Emoji","Segoe UI Symbol";}SUBMITTEDPENDING_REVIEWPROCESSINGCONFIRMEDREJECTEDREMOVEDLIMITEDACCOUNT_ACTIONAPPEALAPPEAL_APPROVEDAPPEAL_REJECTED

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

\#chatgpt-mermaid-\_r_3aa\_{font-family:-apple-system-body,ui-sans-serif,-apple-system,system-ui,"Segoe UI",Helvetica,"Apple Color Emoji",Arial,sans-serif,"Segoe UI Emoji","Segoe UI Symbol";font-size:16px;fill:rgb(13, 13, 13);}@keyframes edge-animation-frame{from{stroke-dashoffset:0;}}@keyframes dash{to{stroke-dashoffset:0;}}#chatgpt-mermaid-\_r_3aa\_ .edge-animation-slow{stroke-dasharray:9,5!important;stroke-dashoffset:900;animation:dash 50s linear infinite;stroke-linecap:round;}#chatgpt-mermaid-\_r_3aa\_ .edge-animation-fast{stroke-dasharray:9,5!important;stroke-dashoffset:900;animation:dash 20s linear infinite;stroke-linecap:round;}#chatgpt-mermaid-\_r_3aa\_ .error-icon{fill:rgb(243, 243, 243);}#chatgpt-mermaid-\_r_3aa\_ .error-text{fill:rgb(13, 13, 13);stroke:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_3aa\_ .edge-thickness-normal{stroke-width:1px;}#chatgpt-mermaid-\_r_3aa\_ .edge-thickness-thick{stroke-width:3.5px;}#chatgpt-mermaid-\_r_3aa\_ .edge-pattern-solid{stroke-dasharray:0;}#chatgpt-mermaid-\_r_3aa\_ .edge-thickness-invisible{stroke-width:0;fill:none;}#chatgpt-mermaid-\_r_3aa\_ .edge-pattern-dashed{stroke-dasharray:3;}#chatgpt-mermaid-\_r_3aa\_ .edge-pattern-dotted{stroke-dasharray:2;}#chatgpt-mermaid-\_r_3aa\_ .marker{fill:rgb(143, 143, 143);stroke:rgb(143, 143, 143);}#chatgpt-mermaid-\_r_3aa\_ .marker.cross{stroke:rgb(143, 143, 143);}#chatgpt-mermaid-\_r_3aa\_ svg{font-family:-apple-system-body,ui-sans-serif,-apple-system,system-ui,"Segoe UI",Helvetica,"Apple Color Emoji",Arial,sans-serif,"Segoe UI Emoji","Segoe UI Symbol";font-size:16px;}#chatgpt-mermaid-\_r_3aa\_ p{margin:0;}#chatgpt-mermaid-\_r_3aa\_ .label{font-family:-apple-system-body,ui-sans-serif,-apple-system,system-ui,"Segoe UI",Helvetica,"Apple Color Emoji",Arial,sans-serif,"Segoe UI Emoji","Segoe UI Symbol";color:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_3aa\_ .cluster-label text{fill:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_3aa\_ .cluster-label span{color:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_3aa\_ .cluster-label span p{background-color:transparent;}#chatgpt-mermaid-\_r_3aa\_ .label text,#chatgpt-mermaid-\_r_3aa\_ span{fill:rgb(13, 13, 13);color:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_3aa\_ .node rect,#chatgpt-mermaid-\_r_3aa\_ .node circle,#chatgpt-mermaid-\_r_3aa\_ .node ellipse,#chatgpt-mermaid-\_r_3aa\_ .node polygon,#chatgpt-mermaid-\_r_3aa\_ .node path{fill:rgb(222, 234, 251);stroke:rgb(83, 154, 248);stroke-width:1px;}#chatgpt-mermaid-\_r_3aa\_ .rough-node .label text,#chatgpt-mermaid-\_r_3aa\_ .node .label text,#chatgpt-mermaid-\_r_3aa\_ .image-shape .label,#chatgpt-mermaid-\_r_3aa\_ .icon-shape .label{text-anchor:middle;}#chatgpt-mermaid-\_r_3aa\_ .node .katex path{fill:#000;stroke:#000;stroke-width:1px;}#chatgpt-mermaid-\_r_3aa\_ .rough-node .label,#chatgpt-mermaid-\_r_3aa\_ .node .label,#chatgpt-mermaid-\_r_3aa\_ .image-shape .label,#chatgpt-mermaid-\_r_3aa\_ .icon-shape .label{text-align:center;}#chatgpt-mermaid-\_r_3aa\_ .node.clickable{cursor:pointer;}#chatgpt-mermaid-\_r_3aa\_ .root .anchor path{fill:rgb(143, 143, 143)!important;stroke-width:0;stroke:rgb(143, 143, 143);}#chatgpt-mermaid-\_r_3aa\_ .arrowheadPath{fill:rgb(143, 143, 143);}#chatgpt-mermaid-\_r_3aa\_ .edgePath .path{stroke:rgb(143, 143, 143);stroke-width:1px;}#chatgpt-mermaid-\_r_3aa\_ .flowchart-link{stroke:rgb(143, 143, 143);fill:none;}#chatgpt-mermaid-\_r_3aa\_ .edgeLabel{background-color:rgb(252, 252, 252);text-align:center;}#chatgpt-mermaid-\_r_3aa\_ .edgeLabel p{background-color:rgb(252, 252, 252);}#chatgpt-mermaid-\_r_3aa\_ .edgeLabel rect{opacity:0.5;background-color:rgb(252, 252, 252);fill:rgb(252, 252, 252);}#chatgpt-mermaid-\_r_3aa\_ .labelBkg{background-color:rgba(252, 252, 252, 0.5);}#chatgpt-mermaid-\_r_3aa\_ .cluster rect{fill:rgb(243, 243, 243);stroke:rgba(0, 0, 0, 0.1);stroke-width:1px;}#chatgpt-mermaid-\_r_3aa\_ .cluster text{fill:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_3aa\_ .cluster span{color:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_3aa\_ div.mermaidTooltip{position:absolute;text-align:center;max-width:200px;padding:2px;font-family:-apple-system-body,ui-sans-serif,-apple-system,system-ui,"Segoe UI",Helvetica,"Apple Color Emoji",Arial,sans-serif,"Segoe UI Emoji","Segoe UI Symbol";font-size:12px;background:rgb(243, 243, 243);border:1px solid rgba(0, 0, 0, 0.1);border-radius:2px;pointer-events:none;z-index:100;}#chatgpt-mermaid-\_r_3aa\_ .flowchartTitleText{text-anchor:middle;font-size:18px;fill:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_3aa\_ rect.text{fill:none;stroke-width:0;}#chatgpt-mermaid-\_r_3aa\_ .icon-shape,#chatgpt-mermaid-\_r_3aa\_ .image-shape{background-color:rgb(252, 252, 252);text-align:center;}#chatgpt-mermaid-\_r_3aa\_ .icon-shape p,#chatgpt-mermaid-\_r_3aa\_ .image-shape p{background-color:rgb(252, 252, 252);padding:2px;}#chatgpt-mermaid-\_r_3aa\_ .icon-shape .label rect,#chatgpt-mermaid-\_r_3aa\_ .image-shape .label rect{opacity:0.5;background-color:rgb(252, 252, 252);fill:rgb(252, 252, 252);}#chatgpt-mermaid-\_r_3aa\_ .label-icon{display:inline-block;height:1em;overflow:visible;vertical-align:-0.125em;}#chatgpt-mermaid-\_r_3aa\_ .node .label-icon path{fill:currentColor;stroke:revert;stroke-width:revert;}#chatgpt-mermaid-\_r_3aa\_ .node .neo-node{stroke:rgb(83, 154, 248);}#chatgpt-mermaid-\_r_3aa\_ [data-look="neo"].node rect,#chatgpt-mermaid-\_r_3aa\_ [data-look="neo"].cluster rect,#chatgpt-mermaid-\_r_3aa\_ [data-look="neo"].node polygon{stroke:url(#chatgpt-mermaid-\_r_3aa\_-gradient);filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-\_r_3aa\_ [data-look="neo"].swimlane.cluster rect{filter:none;}#chatgpt-mermaid-\_r_3aa\_ [data-look="neo"].node path{stroke:url(#chatgpt-mermaid-\_r_3aa\_-gradient);stroke-width:1px;}#chatgpt-mermaid-\_r_3aa\_ [data-look="neo"].node .outer-path{filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-\_r_3aa\_ [data-look="neo"].node .neo-line path{stroke:rgb(83, 154, 248);filter:none;}#chatgpt-mermaid-\_r_3aa\_ [data-look="neo"].node circle{stroke:url(#chatgpt-mermaid-\_r_3aa\_-gradient);filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-\_r_3aa\_ [data-look="neo"].node circle .state-start{fill:#000000;}#chatgpt-mermaid-\_r_3aa\_ [data-look="neo"].icon-shape .icon{fill:url(#chatgpt-mermaid-\_r_3aa\_-gradient);filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-\_r_3aa\_ [data-look="neo"].icon-shape .icon-neo path{stroke:url(#chatgpt-mermaid-\_r_3aa\_-gradient);filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-\_r_3aa\_ .node text{font-size:14px;font-weight:600;letter-spacing:normal;fill:rgb(0, 79, 153);}#chatgpt-mermaid-\_r_3aa\_ .edgeLabels text{font-size:13px;font-weight:600;letter-spacing:-0.08px;fill:rgb(0, 79, 153);}#chatgpt-mermaid-\_r_3aa\_ .node tspan[font-weight="normal"],#chatgpt-mermaid-\_r_3aa\_ .edgeLabels tspan[font-weight="normal"]{font-weight:600;}#chatgpt-mermaid-\_r_3aa\_ .edgeLabel .label rect{opacity:1;rx:13px;ry:13px;fill:rgb(245, 250, 255);stroke:rgb(206, 219, 229);stroke-width:1px;}#chatgpt-mermaid-\_r_3aa\_ .node rect,#chatgpt-mermaid-\_r_3aa\_ .node circle,#chatgpt-mermaid-\_r_3aa\_ .node ellipse,#chatgpt-mermaid-\_r_3aa\_ .node polygon,#chatgpt-mermaid-\_r_3aa\_ .node path{fill:rgb(229, 243, 255);stroke:rgba(0, 0, 0, 0.1);stroke-width:1px;}#chatgpt-mermaid-\_r_3aa\_ .node rect{rx:16px;ry:16px;}#chatgpt-mermaid-\_r_3aa\_ .mermaid-decision .label-container{fill:rgb(245, 250, 255);stroke:rgb(206, 219, 229);stroke-dasharray:2,2;}#chatgpt-mermaid-\_r_3aa\_ .edgePaths .flowchart-link{stroke:rgb(143, 143, 143);stroke-width:1px;stroke-linecap:round;stroke-linejoin:round;}#chatgpt-mermaid-\_r_3aa\_ .marker{fill:rgb(143, 143, 143);stroke:rgb(143, 143, 143);}#chatgpt-mermaid-\_r_3aa\_ :root{--mermaid-font-family:-apple-system-body,ui-sans-serif,-apple-system,system-ui,"Segoe UI",Helvetica,"Apple Color Emoji",Arial,sans-serif,"Segoe UI Emoji","Segoe UI Symbol";}AI请求AI编排服务任务类型视觉分类模型分割模型图像生成模型LLM质量评估模型统一结果层规则与Schema校验保存任务结果分类分割生成搭配质量检查

### **23.3 AI 任务通用数据结构**

```
{
  "taskId": "TASK_001",
  "taskType": "GARMENT_GENERATION",
  "status": "RUNNING",
  "userId": "USER_001",
  "inputRefs": [
    "MEDIA_001"
  ],
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

例如：

```
{
  "type": "object",
  "required": [
    "recommendations"
  ],
  "properties": {
    "recommendations": {
      "type": "array",
      "items": {
        "type": "object",
        "required": [
          "items",
          "reason"
        ],
        "properties": {
          "items": {
            "type": "array",
            "items": {
              "type": "object",
              "required": [
                "garmentAssetId",
                "slot"
              ],
              "properties": {
                "garmentAssetId": {
                  "type": "string"
                },
                "slot": {
                  "type": "string"
                }
              }
            }
          },
          "reason": {
            "type": "string"
          }
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

指标：

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

\#chatgpt-mermaid-\_r_3ar\_{font-family:-apple-system-body,ui-sans-serif,-apple-system,system-ui,"Segoe UI",Helvetica,"Apple Color Emoji",Arial,sans-serif,"Segoe UI Emoji","Segoe UI Symbol";font-size:16px;fill:rgb(13, 13, 13);}@keyframes edge-animation-frame{from{stroke-dashoffset:0;}}@keyframes dash{to{stroke-dashoffset:0;}}#chatgpt-mermaid-\_r_3ar\_ .edge-animation-slow{stroke-dasharray:9,5!important;stroke-dashoffset:900;animation:dash 50s linear infinite;stroke-linecap:round;}#chatgpt-mermaid-\_r_3ar\_ .edge-animation-fast{stroke-dasharray:9,5!important;stroke-dashoffset:900;animation:dash 20s linear infinite;stroke-linecap:round;}#chatgpt-mermaid-\_r_3ar\_ .error-icon{fill:rgb(243, 243, 243);}#chatgpt-mermaid-\_r_3ar\_ .error-text{fill:rgb(13, 13, 13);stroke:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_3ar\_ .edge-thickness-normal{stroke-width:1px;}#chatgpt-mermaid-\_r_3ar\_ .edge-thickness-thick{stroke-width:3.5px;}#chatgpt-mermaid-\_r_3ar\_ .edge-pattern-solid{stroke-dasharray:0;}#chatgpt-mermaid-\_r_3ar\_ .edge-thickness-invisible{stroke-width:0;fill:none;}#chatgpt-mermaid-\_r_3ar\_ .edge-pattern-dashed{stroke-dasharray:3;}#chatgpt-mermaid-\_r_3ar\_ .edge-pattern-dotted{stroke-dasharray:2;}#chatgpt-mermaid-\_r_3ar\_ .marker{fill:rgb(143, 143, 143);stroke:rgb(143, 143, 143);}#chatgpt-mermaid-\_r_3ar\_ .marker.cross{stroke:rgb(143, 143, 143);}#chatgpt-mermaid-\_r_3ar\_ svg{font-family:-apple-system-body,ui-sans-serif,-apple-system,system-ui,"Segoe UI",Helvetica,"Apple Color Emoji",Arial,sans-serif,"Segoe UI Emoji","Segoe UI Symbol";font-size:16px;}#chatgpt-mermaid-\_r_3ar\_ p{margin:0;}#chatgpt-mermaid-\_r_3ar\_ .label{font-family:-apple-system-body,ui-sans-serif,-apple-system,system-ui,"Segoe UI",Helvetica,"Apple Color Emoji",Arial,sans-serif,"Segoe UI Emoji","Segoe UI Symbol";color:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_3ar\_ .cluster-label text{fill:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_3ar\_ .cluster-label span{color:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_3ar\_ .cluster-label span p{background-color:transparent;}#chatgpt-mermaid-\_r_3ar\_ .label text,#chatgpt-mermaid-\_r_3ar\_ span{fill:rgb(13, 13, 13);color:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_3ar\_ .node rect,#chatgpt-mermaid-\_r_3ar\_ .node circle,#chatgpt-mermaid-\_r_3ar\_ .node ellipse,#chatgpt-mermaid-\_r_3ar\_ .node polygon,#chatgpt-mermaid-\_r_3ar\_ .node path{fill:rgb(222, 234, 251);stroke:rgb(83, 154, 248);stroke-width:1px;}#chatgpt-mermaid-\_r_3ar\_ .rough-node .label text,#chatgpt-mermaid-\_r_3ar\_ .node .label text,#chatgpt-mermaid-\_r_3ar\_ .image-shape .label,#chatgpt-mermaid-\_r_3ar\_ .icon-shape .label{text-anchor:middle;}#chatgpt-mermaid-\_r_3ar\_ .node .katex path{fill:#000;stroke:#000;stroke-width:1px;}#chatgpt-mermaid-\_r_3ar\_ .rough-node .label,#chatgpt-mermaid-\_r_3ar\_ .node .label,#chatgpt-mermaid-\_r_3ar\_ .image-shape .label,#chatgpt-mermaid-\_r_3ar\_ .icon-shape .label{text-align:center;}#chatgpt-mermaid-\_r_3ar\_ .node.clickable{cursor:pointer;}#chatgpt-mermaid-\_r_3ar\_ .root .anchor path{fill:rgb(143, 143, 143)!important;stroke-width:0;stroke:rgb(143, 143, 143);}#chatgpt-mermaid-\_r_3ar\_ .arrowheadPath{fill:rgb(143, 143, 143);}#chatgpt-mermaid-\_r_3ar\_ .edgePath .path{stroke:rgb(143, 143, 143);stroke-width:1px;}#chatgpt-mermaid-\_r_3ar\_ .flowchart-link{stroke:rgb(143, 143, 143);fill:none;}#chatgpt-mermaid-\_r_3ar\_ .edgeLabel{background-color:rgb(252, 252, 252);text-align:center;}#chatgpt-mermaid-\_r_3ar\_ .edgeLabel p{background-color:rgb(252, 252, 252);}#chatgpt-mermaid-\_r_3ar\_ .edgeLabel rect{opacity:0.5;background-color:rgb(252, 252, 252);fill:rgb(252, 252, 252);}#chatgpt-mermaid-\_r_3ar\_ .labelBkg{background-color:rgba(252, 252, 252, 0.5);}#chatgpt-mermaid-\_r_3ar\_ .cluster rect{fill:rgb(243, 243, 243);stroke:rgba(0, 0, 0, 0.1);stroke-width:1px;}#chatgpt-mermaid-\_r_3ar\_ .cluster text{fill:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_3ar\_ .cluster span{color:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_3ar\_ div.mermaidTooltip{position:absolute;text-align:center;max-width:200px;padding:2px;font-family:-apple-system-body,ui-sans-serif,-apple-system,system-ui,"Segoe UI",Helvetica,"Apple Color Emoji",Arial,sans-serif,"Segoe UI Emoji","Segoe UI Symbol";font-size:12px;background:rgb(243, 243, 243);border:1px solid rgba(0, 0, 0, 0.1);border-radius:2px;pointer-events:none;z-index:100;}#chatgpt-mermaid-\_r_3ar\_ .flowchartTitleText{text-anchor:middle;font-size:18px;fill:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_3ar\_ rect.text{fill:none;stroke-width:0;}#chatgpt-mermaid-\_r_3ar\_ .icon-shape,#chatgpt-mermaid-\_r_3ar\_ .image-shape{background-color:rgb(252, 252, 252);text-align:center;}#chatgpt-mermaid-\_r_3ar\_ .icon-shape p,#chatgpt-mermaid-\_r_3ar\_ .image-shape p{background-color:rgb(252, 252, 252);padding:2px;}#chatgpt-mermaid-\_r_3ar\_ .icon-shape .label rect,#chatgpt-mermaid-\_r_3ar\_ .image-shape .label rect{opacity:0.5;background-color:rgb(252, 252, 252);fill:rgb(252, 252, 252);}#chatgpt-mermaid-\_r_3ar\_ .label-icon{display:inline-block;height:1em;overflow:visible;vertical-align:-0.125em;}#chatgpt-mermaid-\_r_3ar\_ .node .label-icon path{fill:currentColor;stroke:revert;stroke-width:revert;}#chatgpt-mermaid-\_r_3ar\_ .node .neo-node{stroke:rgb(83, 154, 248);}#chatgpt-mermaid-\_r_3ar\_ [data-look="neo"].node rect,#chatgpt-mermaid-\_r_3ar\_ [data-look="neo"].cluster rect,#chatgpt-mermaid-\_r_3ar\_ [data-look="neo"].node polygon{stroke:url(#chatgpt-mermaid-\_r_3ar\_-gradient);filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-\_r_3ar\_ [data-look="neo"].swimlane.cluster rect{filter:none;}#chatgpt-mermaid-\_r_3ar\_ [data-look="neo"].node path{stroke:url(#chatgpt-mermaid-\_r_3ar\_-gradient);stroke-width:1px;}#chatgpt-mermaid-\_r_3ar\_ [data-look="neo"].node .outer-path{filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-\_r_3ar\_ [data-look="neo"].node .neo-line path{stroke:rgb(83, 154, 248);filter:none;}#chatgpt-mermaid-\_r_3ar\_ [data-look="neo"].node circle{stroke:url(#chatgpt-mermaid-\_r_3ar\_-gradient);filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-\_r_3ar\_ [data-look="neo"].node circle .state-start{fill:#000000;}#chatgpt-mermaid-\_r_3ar\_ [data-look="neo"].icon-shape .icon{fill:url(#chatgpt-mermaid-\_r_3ar\_-gradient);filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-\_r_3ar\_ [data-look="neo"].icon-shape .icon-neo path{stroke:url(#chatgpt-mermaid-\_r_3ar\_-gradient);filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-\_r_3ar\_ .node text{font-size:14px;font-weight:600;letter-spacing:normal;fill:rgb(0, 79, 153);}#chatgpt-mermaid-\_r_3ar\_ .edgeLabels text{font-size:13px;font-weight:600;letter-spacing:-0.08px;fill:rgb(0, 79, 153);}#chatgpt-mermaid-\_r_3ar\_ .node tspan[font-weight="normal"],#chatgpt-mermaid-\_r_3ar\_ .edgeLabels tspan[font-weight="normal"]{font-weight:600;}#chatgpt-mermaid-\_r_3ar\_ .edgeLabel .label rect{opacity:1;rx:13px;ry:13px;fill:rgb(245, 250, 255);stroke:rgb(206, 219, 229);stroke-width:1px;}#chatgpt-mermaid-\_r_3ar\_ .node rect,#chatgpt-mermaid-\_r_3ar\_ .node circle,#chatgpt-mermaid-\_r_3ar\_ .node ellipse,#chatgpt-mermaid-\_r_3ar\_ .node polygon,#chatgpt-mermaid-\_r_3ar\_ .node path{fill:rgb(229, 243, 255);stroke:rgba(0, 0, 0, 0.1);stroke-width:1px;}#chatgpt-mermaid-\_r_3ar\_ .node rect{rx:16px;ry:16px;}#chatgpt-mermaid-\_r_3ar\_ .mermaid-decision .label-container{fill:rgb(245, 250, 255);stroke:rgb(206, 219, 229);stroke-dasharray:2,2;}#chatgpt-mermaid-\_r_3ar\_ .edgePaths .flowchart-link{stroke:rgb(143, 143, 143);stroke-width:1px;stroke-linecap:round;stroke-linejoin:round;}#chatgpt-mermaid-\_r_3ar\_ .marker{fill:rgb(143, 143, 143);stroke:rgb(143, 143, 143);}#chatgpt-mermaid-\_r_3ar\_ :root{--mermaid-font-family:-apple-system-body,ui-sans-serif,-apple-system,system-ui,"Segoe UI",Helvetica,"Apple Color Emoji",Arial,sans-serif,"Segoe UI Emoji","Segoe UI Symbol";}需求编号页面/接口/数据设计研发实现单元测试集成测试端到端测试用户验收上线缺陷

每一项需求必须能追踪到：

- 页面 ID。
- API。
- 数据表。
- 测试用例。
- 缺陷记录。
- 验收结论。

### **25.6 上线门槛**

P0 阻断条件

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

沿用 V0.1 的商业模式，不改变免费版、会员订阅、虚拟服饰商城、创作者市场、角色装扮包、AI 高级服务、品牌合作和电商导购的方向。

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

保留 V0.1 中的 V0.1、V1.0、V1.5、V2.0 规划，并补充每阶段的研发交付物和验收条件。

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

\#chatgpt-mermaid-\_r_3bh\_{font-family:-apple-system-body,ui-sans-serif,-apple-system,system-ui,"Segoe UI",Helvetica,"Apple Color Emoji",Arial,sans-serif,"Segoe UI Emoji","Segoe UI Symbol";font-size:16px;fill:rgb(13, 13, 13);}@keyframes edge-animation-frame{from{stroke-dashoffset:0;}}@keyframes dash{to{stroke-dashoffset:0;}}#chatgpt-mermaid-\_r_3bh\_ .edge-animation-slow{stroke-dasharray:9,5!important;stroke-dashoffset:900;animation:dash 50s linear infinite;stroke-linecap:round;}#chatgpt-mermaid-\_r_3bh\_ .edge-animation-fast{stroke-dasharray:9,5!important;stroke-dashoffset:900;animation:dash 20s linear infinite;stroke-linecap:round;}#chatgpt-mermaid-\_r_3bh\_ .error-icon{fill:rgb(243, 243, 243);}#chatgpt-mermaid-\_r_3bh\_ .error-text{fill:rgb(13, 13, 13);stroke:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_3bh\_ .edge-thickness-normal{stroke-width:1px;}#chatgpt-mermaid-\_r_3bh\_ .edge-thickness-thick{stroke-width:3.5px;}#chatgpt-mermaid-\_r_3bh\_ .edge-pattern-solid{stroke-dasharray:0;}#chatgpt-mermaid-\_r_3bh\_ .edge-thickness-invisible{stroke-width:0;fill:none;}#chatgpt-mermaid-\_r_3bh\_ .edge-pattern-dashed{stroke-dasharray:3;}#chatgpt-mermaid-\_r_3bh\_ .edge-pattern-dotted{stroke-dasharray:2;}#chatgpt-mermaid-\_r_3bh\_ .marker{fill:rgb(143, 143, 143);stroke:rgb(143, 143, 143);}#chatgpt-mermaid-\_r_3bh\_ .marker.cross{stroke:rgb(143, 143, 143);}#chatgpt-mermaid-\_r_3bh\_ svg{font-family:-apple-system-body,ui-sans-serif,-apple-system,system-ui,"Segoe UI",Helvetica,"Apple Color Emoji",Arial,sans-serif,"Segoe UI Emoji","Segoe UI Symbol";font-size:16px;}#chatgpt-mermaid-\_r_3bh\_ p{margin:0;}#chatgpt-mermaid-\_r_3bh\_ .label{font-family:-apple-system-body,ui-sans-serif,-apple-system,system-ui,"Segoe UI",Helvetica,"Apple Color Emoji",Arial,sans-serif,"Segoe UI Emoji","Segoe UI Symbol";color:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_3bh\_ .cluster-label text{fill:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_3bh\_ .cluster-label span{color:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_3bh\_ .cluster-label span p{background-color:transparent;}#chatgpt-mermaid-\_r_3bh\_ .label text,#chatgpt-mermaid-\_r_3bh\_ span{fill:rgb(13, 13, 13);color:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_3bh\_ .node rect,#chatgpt-mermaid-\_r_3bh\_ .node circle,#chatgpt-mermaid-\_r_3bh\_ .node ellipse,#chatgpt-mermaid-\_r_3bh\_ .node polygon,#chatgpt-mermaid-\_r_3bh\_ .node path{fill:rgb(222, 234, 251);stroke:rgb(83, 154, 248);stroke-width:1px;}#chatgpt-mermaid-\_r_3bh\_ .rough-node .label text,#chatgpt-mermaid-\_r_3bh\_ .node .label text,#chatgpt-mermaid-\_r_3bh\_ .image-shape .label,#chatgpt-mermaid-\_r_3bh\_ .icon-shape .label{text-anchor:middle;}#chatgpt-mermaid-\_r_3bh\_ .node .katex path{fill:#000;stroke:#000;stroke-width:1px;}#chatgpt-mermaid-\_r_3bh\_ .rough-node .label,#chatgpt-mermaid-\_r_3bh\_ .node .label,#chatgpt-mermaid-\_r_3bh\_ .image-shape .label,#chatgpt-mermaid-\_r_3bh\_ .icon-shape .label{text-align:center;}#chatgpt-mermaid-\_r_3bh\_ .node.clickable{cursor:pointer;}#chatgpt-mermaid-\_r_3bh\_ .root .anchor path{fill:rgb(143, 143, 143)!important;stroke-width:0;stroke:rgb(143, 143, 143);}#chatgpt-mermaid-\_r_3bh\_ .arrowheadPath{fill:rgb(143, 143, 143);}#chatgpt-mermaid-\_r_3bh\_ .edgePath .path{stroke:rgb(143, 143, 143);stroke-width:1px;}#chatgpt-mermaid-\_r_3bh\_ .flowchart-link{stroke:rgb(143, 143, 143);fill:none;}#chatgpt-mermaid-\_r_3bh\_ .edgeLabel{background-color:rgb(252, 252, 252);text-align:center;}#chatgpt-mermaid-\_r_3bh\_ .edgeLabel p{background-color:rgb(252, 252, 252);}#chatgpt-mermaid-\_r_3bh\_ .edgeLabel rect{opacity:0.5;background-color:rgb(252, 252, 252);fill:rgb(252, 252, 252);}#chatgpt-mermaid-\_r_3bh\_ .labelBkg{background-color:rgba(252, 252, 252, 0.5);}#chatgpt-mermaid-\_r_3bh\_ .cluster rect{fill:rgb(243, 243, 243);stroke:rgba(0, 0, 0, 0.1);stroke-width:1px;}#chatgpt-mermaid-\_r_3bh\_ .cluster text{fill:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_3bh\_ .cluster span{color:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_3bh\_ div.mermaidTooltip{position:absolute;text-align:center;max-width:200px;padding:2px;font-family:-apple-system-body,ui-sans-serif,-apple-system,system-ui,"Segoe UI",Helvetica,"Apple Color Emoji",Arial,sans-serif,"Segoe UI Emoji","Segoe UI Symbol";font-size:12px;background:rgb(243, 243, 243);border:1px solid rgba(0, 0, 0, 0.1);border-radius:2px;pointer-events:none;z-index:100;}#chatgpt-mermaid-\_r_3bh\_ .flowchartTitleText{text-anchor:middle;font-size:18px;fill:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_3bh\_ rect.text{fill:none;stroke-width:0;}#chatgpt-mermaid-\_r_3bh\_ .icon-shape,#chatgpt-mermaid-\_r_3bh\_ .image-shape{background-color:rgb(252, 252, 252);text-align:center;}#chatgpt-mermaid-\_r_3bh\_ .icon-shape p,#chatgpt-mermaid-\_r_3bh\_ .image-shape p{background-color:rgb(252, 252, 252);padding:2px;}#chatgpt-mermaid-\_r_3bh\_ .icon-shape .label rect,#chatgpt-mermaid-\_r_3bh\_ .image-shape .label rect{opacity:0.5;background-color:rgb(252, 252, 252);fill:rgb(252, 252, 252);}#chatgpt-mermaid-\_r_3bh\_ .label-icon{display:inline-block;height:1em;overflow:visible;vertical-align:-0.125em;}#chatgpt-mermaid-\_r_3bh\_ .node .label-icon path{fill:currentColor;stroke:revert;stroke-width:revert;}#chatgpt-mermaid-\_r_3bh\_ .node .neo-node{stroke:rgb(83, 154, 248);}#chatgpt-mermaid-\_r_3bh\_ [data-look="neo"].node rect,#chatgpt-mermaid-\_r_3bh\_ [data-look="neo"].cluster rect,#chatgpt-mermaid-\_r_3bh\_ [data-look="neo"].node polygon{stroke:url(#chatgpt-mermaid-\_r_3bh\_-gradient);filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-\_r_3bh\_ [data-look="neo"].swimlane.cluster rect{filter:none;}#chatgpt-mermaid-\_r_3bh\_ [data-look="neo"].node path{stroke:url(#chatgpt-mermaid-\_r_3bh\_-gradient);stroke-width:1px;}#chatgpt-mermaid-\_r_3bh\_ [data-look="neo"].node .outer-path{filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-\_r_3bh\_ [data-look="neo"].node .neo-line path{stroke:rgb(83, 154, 248);filter:none;}#chatgpt-mermaid-\_r_3bh\_ [data-look="neo"].node circle{stroke:url(#chatgpt-mermaid-\_r_3bh\_-gradient);filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-\_r_3bh\_ [data-look="neo"].node circle .state-start{fill:#000000;}#chatgpt-mermaid-\_r_3bh\_ [data-look="neo"].icon-shape .icon{fill:url(#chatgpt-mermaid-\_r_3bh\_-gradient);filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-\_r_3bh\_ [data-look="neo"].icon-shape .icon-neo path{stroke:url(#chatgpt-mermaid-\_r_3bh\_-gradient);filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-\_r_3bh\_ .node text{font-size:14px;font-weight:600;letter-spacing:normal;fill:rgb(0, 79, 153);}#chatgpt-mermaid-\_r_3bh\_ .edgeLabels text{font-size:13px;font-weight:600;letter-spacing:-0.08px;fill:rgb(0, 79, 153);}#chatgpt-mermaid-\_r_3bh\_ .node tspan[font-weight="normal"],#chatgpt-mermaid-\_r_3bh\_ .edgeLabels tspan[font-weight="normal"]{font-weight:600;}#chatgpt-mermaid-\_r_3bh\_ .edgeLabel .label rect{opacity:1;rx:13px;ry:13px;fill:rgb(245, 250, 255);stroke:rgb(206, 219, 229);stroke-width:1px;}#chatgpt-mermaid-\_r_3bh\_ .node rect,#chatgpt-mermaid-\_r_3bh\_ .node circle,#chatgpt-mermaid-\_r_3bh\_ .node ellipse,#chatgpt-mermaid-\_r_3bh\_ .node polygon,#chatgpt-mermaid-\_r_3bh\_ .node path{fill:rgb(229, 243, 255);stroke:rgba(0, 0, 0, 0.1);stroke-width:1px;}#chatgpt-mermaid-\_r_3bh\_ .node rect{rx:16px;ry:16px;}#chatgpt-mermaid-\_r_3bh\_ .mermaid-decision .label-container{fill:rgb(245, 250, 255);stroke:rgb(206, 219, 229);stroke-dasharray:2,2;}#chatgpt-mermaid-\_r_3bh\_ .edgePaths .flowchart-link{stroke:rgb(143, 143, 143);stroke-width:1px;stroke-linecap:round;stroke-linejoin:round;}#chatgpt-mermaid-\_r_3bh\_ .marker{fill:rgb(143, 143, 143);stroke:rgb(143, 143, 143);}#chatgpt-mermaid-\_r_3bh\_ :root{--mermaid-font-family:-apple-system-body,ui-sans-serif,-apple-system,system-ui,"Segoe UI",Helvetica,"Apple Color Emoji",Arial,sans-serif,"Segoe UI Emoji","Segoe UI Symbol";}产品需求与视觉规范数据模型与接口契约账号和资产基础服务上传与审核AI识别与分割服装资产生成角色模型与Morph系统角色渲染模块换装交互穿搭保存AI搭配执行分享与社区商业化扩展

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

沿用原稿：

**每周有效穿搭创作用户数（Weekly Active Outfit Creators）**

定义：一周内至少完成一次有效穿搭，并保存、分享或记录穿搭的去重用户数。

建议增加有效穿搭定义：

- 至少有一个有效角色。
- 至少有一件有效服装资产。
- 穿搭保存成功。
- 不是系统自动创建的空记录。
- 不属于异常刷量或测试账号。

### **30.2 漏斗指标**

核心业务漏斗结构

这是业务转化路径示意，不代表现有真实数据。

03006009001,200进入上传上传完成审核通过识别确认资产生成首次穿搭保存穿搭分享作品

以上数字仅用于说明漏斗计算方法，不是产品目标或预测。

建议拆解：

\\[ 上传完成率 = \frac{上传完成用户}{进入上传用户} \\]

\\[ 审核通过率 = \frac{审核通过数量}{提交审核数量} \\]

\\[ 资产生成成功率 = \frac{生成成功资产}{发起生成任务} \\]

\\[ 首次穿搭完成率 = \frac{完成首次穿搭用户}{注册用户} \\]

\\[ AI 推荐采纳率 = \frac{被应用的推荐方案}{有效推荐方案} \\]

### **30.3 埋点事件**

保留原稿已有事件，并补充：

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
| D-010 | 会员策略     | 先测算成本再定价          | 产品+运营 |
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

## **现实衣橱**

解决衣物管理、搭配和利用率问题

## **虚拟角色**

提供角色身份、外观定制和情感价值

## **AI 穿搭**

理解用户需求，真正调用衣橱资产完成搭配

## **UGC 与数字资产生态**

让作品、服装、角色和授权形成内容流动

# **AI 数字衣橱与虚拟时尚世界**

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

建议给领导展示一条完整、可操作的垂直链路，而不是分别展示几个孤立页面。

\#chatgpt-mermaid-\_r_3co\_{font-family:-apple-system-body,ui-sans-serif,-apple-system,system-ui,"Segoe UI",Helvetica,"Apple Color Emoji",Arial,sans-serif,"Segoe UI Emoji","Segoe UI Symbol";font-size:16px;fill:rgb(13, 13, 13);}@keyframes edge-animation-frame{from{stroke-dashoffset:0;}}@keyframes dash{to{stroke-dashoffset:0;}}#chatgpt-mermaid-\_r_3co\_ .edge-animation-slow{stroke-dasharray:9,5!important;stroke-dashoffset:900;animation:dash 50s linear infinite;stroke-linecap:round;}#chatgpt-mermaid-\_r_3co\_ .edge-animation-fast{stroke-dasharray:9,5!important;stroke-dashoffset:900;animation:dash 20s linear infinite;stroke-linecap:round;}#chatgpt-mermaid-\_r_3co\_ .error-icon{fill:rgb(243, 243, 243);}#chatgpt-mermaid-\_r_3co\_ .error-text{fill:rgb(13, 13, 13);stroke:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_3co\_ .edge-thickness-normal{stroke-width:1px;}#chatgpt-mermaid-\_r_3co\_ .edge-thickness-thick{stroke-width:3.5px;}#chatgpt-mermaid-\_r_3co\_ .edge-pattern-solid{stroke-dasharray:0;}#chatgpt-mermaid-\_r_3co\_ .edge-thickness-invisible{stroke-width:0;fill:none;}#chatgpt-mermaid-\_r_3co\_ .edge-pattern-dashed{stroke-dasharray:3;}#chatgpt-mermaid-\_r_3co\_ .edge-pattern-dotted{stroke-dasharray:2;}#chatgpt-mermaid-\_r_3co\_ .marker{fill:rgb(143, 143, 143);stroke:rgb(143, 143, 143);}#chatgpt-mermaid-\_r_3co\_ .marker.cross{stroke:rgb(143, 143, 143);}#chatgpt-mermaid-\_r_3co\_ svg{font-family:-apple-system-body,ui-sans-serif,-apple-system,system-ui,"Segoe UI",Helvetica,"Apple Color Emoji",Arial,sans-serif,"Segoe UI Emoji","Segoe UI Symbol";font-size:16px;}#chatgpt-mermaid-\_r_3co\_ p{margin:0;}#chatgpt-mermaid-\_r_3co\_ .label{font-family:-apple-system-body,ui-sans-serif,-apple-system,system-ui,"Segoe UI",Helvetica,"Apple Color Emoji",Arial,sans-serif,"Segoe UI Emoji","Segoe UI Symbol";color:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_3co\_ .cluster-label text{fill:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_3co\_ .cluster-label span{color:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_3co\_ .cluster-label span p{background-color:transparent;}#chatgpt-mermaid-\_r_3co\_ .label text,#chatgpt-mermaid-\_r_3co\_ span{fill:rgb(13, 13, 13);color:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_3co\_ .node rect,#chatgpt-mermaid-\_r_3co\_ .node circle,#chatgpt-mermaid-\_r_3co\_ .node ellipse,#chatgpt-mermaid-\_r_3co\_ .node polygon,#chatgpt-mermaid-\_r_3co\_ .node path{fill:rgb(222, 234, 251);stroke:rgb(83, 154, 248);stroke-width:1px;}#chatgpt-mermaid-\_r_3co\_ .rough-node .label text,#chatgpt-mermaid-\_r_3co\_ .node .label text,#chatgpt-mermaid-\_r_3co\_ .image-shape .label,#chatgpt-mermaid-\_r_3co\_ .icon-shape .label{text-anchor:middle;}#chatgpt-mermaid-\_r_3co\_ .node .katex path{fill:#000;stroke:#000;stroke-width:1px;}#chatgpt-mermaid-\_r_3co\_ .rough-node .label,#chatgpt-mermaid-\_r_3co\_ .node .label,#chatgpt-mermaid-\_r_3co\_ .image-shape .label,#chatgpt-mermaid-\_r_3co\_ .icon-shape .label{text-align:center;}#chatgpt-mermaid-\_r_3co\_ .node.clickable{cursor:pointer;}#chatgpt-mermaid-\_r_3co\_ .root .anchor path{fill:rgb(143, 143, 143)!important;stroke-width:0;stroke:rgb(143, 143, 143);}#chatgpt-mermaid-\_r_3co\_ .arrowheadPath{fill:rgb(143, 143, 143);}#chatgpt-mermaid-\_r_3co\_ .edgePath .path{stroke:rgb(143, 143, 143);stroke-width:1px;}#chatgpt-mermaid-\_r_3co\_ .flowchart-link{stroke:rgb(143, 143, 143);fill:none;}#chatgpt-mermaid-\_r_3co\_ .edgeLabel{background-color:rgb(252, 252, 252);text-align:center;}#chatgpt-mermaid-\_r_3co\_ .edgeLabel p{background-color:rgb(252, 252, 252);}#chatgpt-mermaid-\_r_3co\_ .edgeLabel rect{opacity:0.5;background-color:rgb(252, 252, 252);fill:rgb(252, 252, 252);}#chatgpt-mermaid-\_r_3co\_ .labelBkg{background-color:rgba(252, 252, 252, 0.5);}#chatgpt-mermaid-\_r_3co\_ .cluster rect{fill:rgb(243, 243, 243);stroke:rgba(0, 0, 0, 0.1);stroke-width:1px;}#chatgpt-mermaid-\_r_3co\_ .cluster text{fill:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_3co\_ .cluster span{color:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_3co\_ div.mermaidTooltip{position:absolute;text-align:center;max-width:200px;padding:2px;font-family:-apple-system-body,ui-sans-serif,-apple-system,system-ui,"Segoe UI",Helvetica,"Apple Color Emoji",Arial,sans-serif,"Segoe UI Emoji","Segoe UI Symbol";font-size:12px;background:rgb(243, 243, 243);border:1px solid rgba(0, 0, 0, 0.1);border-radius:2px;pointer-events:none;z-index:100;}#chatgpt-mermaid-\_r_3co\_ .flowchartTitleText{text-anchor:middle;font-size:18px;fill:rgb(13, 13, 13);}#chatgpt-mermaid-\_r_3co\_ rect.text{fill:none;stroke-width:0;}#chatgpt-mermaid-\_r_3co\_ .icon-shape,#chatgpt-mermaid-\_r_3co\_ .image-shape{background-color:rgb(252, 252, 252);text-align:center;}#chatgpt-mermaid-\_r_3co\_ .icon-shape p,#chatgpt-mermaid-\_r_3co\_ .image-shape p{background-color:rgb(252, 252, 252);padding:2px;}#chatgpt-mermaid-\_r_3co\_ .icon-shape .label rect,#chatgpt-mermaid-\_r_3co\_ .image-shape .label rect{opacity:0.5;background-color:rgb(252, 252, 252);fill:rgb(252, 252, 252);}#chatgpt-mermaid-\_r_3co\_ .label-icon{display:inline-block;height:1em;overflow:visible;vertical-align:-0.125em;}#chatgpt-mermaid-\_r_3co\_ .node .label-icon path{fill:currentColor;stroke:revert;stroke-width:revert;}#chatgpt-mermaid-\_r_3co\_ .node .neo-node{stroke:rgb(83, 154, 248);}#chatgpt-mermaid-\_r_3co\_ [data-look="neo"].node rect,#chatgpt-mermaid-\_r_3co\_ [data-look="neo"].cluster rect,#chatgpt-mermaid-\_r_3co\_ [data-look="neo"].node polygon{stroke:url(#chatgpt-mermaid-\_r_3co\_-gradient);filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-\_r_3co\_ [data-look="neo"].swimlane.cluster rect{filter:none;}#chatgpt-mermaid-\_r_3co\_ [data-look="neo"].node path{stroke:url(#chatgpt-mermaid-\_r_3co\_-gradient);stroke-width:1px;}#chatgpt-mermaid-\_r_3co\_ [data-look="neo"].node .outer-path{filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-\_r_3co\_ [data-look="neo"].node .neo-line path{stroke:rgb(83, 154, 248);filter:none;}#chatgpt-mermaid-\_r_3co\_ [data-look="neo"].node circle{stroke:url(#chatgpt-mermaid-\_r_3co\_-gradient);filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-\_r_3co\_ [data-look="neo"].node circle .state-start{fill:#000000;}#chatgpt-mermaid-\_r_3co\_ [data-look="neo"].icon-shape .icon{fill:url(#chatgpt-mermaid-\_r_3co\_-gradient);filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-\_r_3co\_ [data-look="neo"].icon-shape .icon-neo path{stroke:url(#chatgpt-mermaid-\_r_3co\_-gradient);filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-\_r_3co\_ .node text{font-size:14px;font-weight:600;letter-spacing:normal;fill:rgb(0, 79, 153);}#chatgpt-mermaid-\_r_3co\_ .edgeLabels text{font-size:13px;font-weight:600;letter-spacing:-0.08px;fill:rgb(0, 79, 153);}#chatgpt-mermaid-\_r_3co\_ .node tspan[font-weight="normal"],#chatgpt-mermaid-\_r_3co\_ .edgeLabels tspan[font-weight="normal"]{font-weight:600;}#chatgpt-mermaid-\_r_3co\_ .edgeLabel .label rect{opacity:1;rx:13px;ry:13px;fill:rgb(245, 250, 255);stroke:rgb(206, 219, 229);stroke-width:1px;}#chatgpt-mermaid-\_r_3co\_ .node rect,#chatgpt-mermaid-\_r_3co\_ .node circle,#chatgpt-mermaid-\_r_3co\_ .node ellipse,#chatgpt-mermaid-\_r_3co\_ .node polygon,#chatgpt-mermaid-\_r_3co\_ .node path{fill:rgb(229, 243, 255);stroke:rgba(0, 0, 0, 0.1);stroke-width:1px;}#chatgpt-mermaid-\_r_3co\_ .node rect{rx:16px;ry:16px;}#chatgpt-mermaid-\_r_3co\_ .mermaid-decision .label-container{fill:rgb(245, 250, 255);stroke:rgb(206, 219, 229);stroke-dasharray:2,2;}#chatgpt-mermaid-\_r_3co\_ .edgePaths .flowchart-link{stroke:rgb(143, 143, 143);stroke-width:1px;stroke-linecap:round;stroke-linejoin:round;}#chatgpt-mermaid-\_r_3co\_ .marker{fill:rgb(143, 143, 143);stroke:rgb(143, 143, 143);}#chatgpt-mermaid-\_r_3co\_ :root{--mermaid-font-family:-apple-system-body,ui-sans-serif,-apple-system,system-ui,"Segoe UI",Helvetica,"Apple Color Emoji",Arial,sans-serif,"Segoe UI Emoji","Segoe UI Symbol";}用户上传白色衬衫照片系统识别为上装提取颜色/纹理/轮廓生成2.5D服装资产创建一个虚拟角色调整角色身材把衬衫穿到角色身上AI从衣橱选择裙子和鞋子生成多套搭配用户选择并调整保存穿搭设置分享权限发布作品

**Demo 必须是真实链路：**

- 不是把衣服图片直接贴到角色图片上就算完成。
- 必须有真实的衣物资产记录。
- 必须有角色配置。
- 必须有服装锚点和图层信息。
- 必须有穿搭保存记录。
- AI 必须引用实际衣橱资产。
- 分享必须有权限控制。

这条链路跑通后，才能证明产品的核心差异化成立。

# **附录 A：原始 V0.1 内容保留清单**

以下原稿章节全部作为 V1.0 的原始基线，不因新增研发规格而删除：

| 原始章节          | 保留内容                           |
| ------------- | ------------------------------ |
| 一、产品定位        | 个人数字衣橱、AI 穿搭、虚拟角色养成、UGC 时尚社区   |
| 二、竞品参考与产品机制   | 奇迹暖暖、燕云十六声、ZEPETO、Acloset 等    |
| 三、核心产品结构      | 六大模块、首页、数字衣橱、角色工坊、身材系统、换装工坊    |
| 四、衣物上传        | 上传入口、拍摄规范、审核、识别、2.5D 生成        |
| 五、AI 穿搭助手     | 主动推荐、聊天搭配、自动换装、上下文与推荐机制        |
| 六、分享与社区       | 分享对象、授权体系、社区页面                 |
| 七、角色和服装素材技术选型 | CharacterStudio、VRM、Three.js 等 |
| 八、商业模式        | 会员、商城、创作者市场、虚拟资产经济             |
| 九、版本规划        | V0.1、V1.0、V1.5、V2.0            |
| 十、产品指标        | 北极星指标、业务指标、埋点                  |
| 十一、边界条件与风险    | 上传、识别、生成、授权、删除、成本              |
| 十二、最终产品形态     | 我的世界、我的衣橱、换装工坊、时尚社区            |
| 十三、立项结论       | 现实价值、情感价值、生态价值                 |
| 十四、立项后工作      | 产品、角色、服装、换装、数据、AI、审核           |

**原稿中的视觉参考链接也应保留原位置，不以 Mermaid 图替换。** 本次新增的 Mermaid 图是研发说明图，不是原稿视觉素材的替代品。

# **附录 B：需要研发评审后才能冻结的事项**

下面这些内容是 V1.0 设计建议，不应该在未做 PoC 前当成已经验证的事实。

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

这些事项需要以 PoC、压测、授权核查和实际成本测算作为最终决策依据。

## **最终版本结论**

这份 V1.0 新增规格把原来偏产品构想的内容推进到了研发可评审的层级，重点补上了此前缺少的四个方面：

- **页面级需求**：页面清单、用户操作、跳转、空状态和失败状态。
- **系统级设计**：数据 ERD、API、异步任务、审核状态机、AI 编排。
- **独立技术方案**：角色 Morph、骨骼、服装 Manifest、锚点、图层、遮挡和适配。
- **可执行验收**：异常场景、端到端测试、质量指标、上线阻断条件。

需要明确一个交付边界：上面是新增的 V1.0 研发规格正文；由于你要求原稿不删改，原始 V0.1 的 1—14 章应保持原文件内容及图片链接原样放在本文件前部，再接上这里的第 15—33 章。**本回复没有逐字重排那 1306 行原稿，因此不能把它宣称为已经完成原文与新增内容的物理合并版。** 但新增规格已经按原稿的业务结构展开，章节编号可以直接追加，避免覆盖原文。