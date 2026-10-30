# Long-term Memory Design

## Types
FACT / PREFERENCE / EMOTIONAL / SHARED_EVENT / RELATIONSHIP

## Memory Object
```json
{
  "memory_id":"mem_001",
  "owner":"npc_a",
  "participants":["npc_a","player"],
  "type":"SHARED_EVENT",
  "summary":"玩家对城南旧书店表现兴趣",
  "source_event":"chat_1042",
  "confidence":0.92,
  "emotional_weight":0.45,
  "relationship_weight":0.61,
  "status":"confirmed",
  "narrative_hooks":["bookstore_visit"]
}
```

## Pipeline
Raw Conversation → Candidate Extraction → Type → Conflict Check → Importance → Confirmation → Persistent Write。

## Retrieval
`semantic relevance × recency × emotional weight × relationship weight × confidence`

新记忆与旧事实冲突时不静默覆盖，使用 supersedes / disputed。
