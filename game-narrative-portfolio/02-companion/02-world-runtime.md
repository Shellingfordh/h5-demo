# World Runtime

角色离线时按事件粒度推进，而非模拟每一分钟：

`last_seen → elapsed_time → routine → pending plans → unresolved hooks → event candidates → validation → commit → world update`

## Example
Day 1：角色提到城南旧书店。  
玩家表示兴趣 → 写入 shared hook。  
Day 3：Runtime 检查空闲时间、地点可达性和 hook。  
Event Generator 提议“去旧书店”。  
Validator 通过 → Commit。  
Day 4：房间出现 `old_book_on_desk=true`。  
玩家观察 → 对话检索 Day 1 共同记忆。

**旧书先存在于世界，再被对话解释；不是玩家问了以后 LLM 才临时编一本书。**
