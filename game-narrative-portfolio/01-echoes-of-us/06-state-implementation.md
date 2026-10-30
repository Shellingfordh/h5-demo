# Narrative State & Implementation

```yaml
chapter_state:
  current_chapter: int
  checkpoint_id: string
character_state:
  active_character: mother|daughter
  mother_anchor: bool
  daughter_anchor: bool
  mother_fallen: bool
  daughter_fallen: bool
relationship_state:
  relationship_arc: int
  tether_interpretation: restriction|cooperation|support
memory_state:
  umbrella_memory: undiscovered|triggered|discovered
presentation_state:
  camera_mode: 2d|2_5d
  focus_mode: bool
  cutscene_lock: bool
```

## Event Contract 必须包含
unique ID / preconditions / trigger / sequence / persistent writes / interrupt / re-entry / save-load / QA。

## 跨职能边界
- Narrative：目的、条件、状态、台词、节奏。
- Level：Trigger Area、空间门控、Checkpoint。
- Gameplay：Switch、Anchor、Tether、Fall Recovery。
- Art/Audio/UI：物件、演出、环境音、字幕。
- QA：重复触发、错序、Save/Load、极端输入。
