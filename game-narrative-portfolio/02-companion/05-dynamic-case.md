# Dynamic Narrative Case｜旧书店

Day 1：NPC 提到旧书店；玩家表示兴趣。  
系统：形成 PREFERENCE + SHARED_HOOK。

Day 3（玩家离线）：Runtime 判断 NPC 有空、地点开放、hook 未解决；Commit `evt_bookstore_visit_001`。

Day 4：3D 房间桌面出现旧书。

- 玩家观察：触发 `OBJ_OLD_BOOK_001`，NPC 可自然关联 Day 1。
- 玩家忽略：不强迫 NPC 汇报；事件仍属于世界历史。

**体验目标**：不是“AI 记住关键词”，而是“我说过的话进入了另一个人的生活，并在几天后留下可观察痕迹”。
