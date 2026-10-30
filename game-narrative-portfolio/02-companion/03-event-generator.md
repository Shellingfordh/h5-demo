# Event Generator

```yaml
event_id: evt_bookstore_visit_001
actor: npc_a
location: south_city_bookstore
source_hooks: [bookstore_interest]
requirements:
  npc_free_time: true
  location_available: true
conflicts: [sick, out_of_city]
effects:
  inventory_add: old_book_001
  old_book_on_desk: true
  hooks_add: [discuss_old_book]
```

流程：
1. 读取 Canon + World State。
2. 找 Narrative Hook。
3. 生成 Candidate。
4. Validator 排冲突。
5. 按角色一致性、重复度、关系价值、成本评分。
6. Commit 一个或零个。
7. 写状态。
8. LLM 负责自然表达。

Anti-Repetition：cooldown、地点/人物 motif 计数、近期事件去重；禁止连续靠“突然生病/下雨/想起你”制造戏剧。
