# Narrative Data Schema

## Event
```yaml
event_id: C03_MEM_UMBRELLA_01
version: 1
chapter: C03
type: memory
trigger:
  type: area_object
  id: rooftop_memory_zone
preconditions: []
sequence: []
writes: []
interrupt_policy: lock_input
reentry_policy: no_replay
save_policy: persist_stage
owner: narrative
status: implemented
```

## Dialogue
```yaml
line_id: C03_DLG_ROOFTOP_044
event_id: C03_MEM_UMBRELLA_01
speaker: daughter
condition: relationship_arc >= 2
emotion: restrained
loc_key: dlg.c03.044
```

命名：`[CHAPTER]_[TYPE]_[SUBJECT]_[INDEX]`。  
禁止 `event1 / new_dialogue / final_final_2`。
