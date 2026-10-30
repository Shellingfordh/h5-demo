# Environmental Storytelling / Event / QA

## 偏室甲
第一眼：大量闪亮器物 → “藏宝室”。  
细看：摆放过整齐、尘层断裂、器物磨损年代不一致、墙角二次封砌。  
重解释：这是后期布置的价值陷阱。

## Event Table
| ID | Trigger | Decision | Effect |
|---|---|---|---|
| TR_A01 | 金箔残片 | 收集/忽略 | clue_gold_leaf |
| TR_B04 | 检查地面 | 深挖/离开 | clue_dust_break |
| TR_C07 | 重量机关失败 | 重试/查资料 | risk +1 |
| TR_D10 | 主室金契 | 带走/记录/放弃 | ending axis |
| TR_E12 | 队友要求撤离 | 同意/继续 | team_trust |

## QA
- [ ] 线索依赖无死锁
- [ ] 忽略非关键线索仍可通关
- [ ] 关键结论至少两个独立证据
- [ ] 错误解谜有后果但不软锁
- [ ] Backtracking 状态一致
- [ ] 拿走物件后环境同步
- [ ] Ending 条件可追溯
