# Git Workflow

## Branch
`main`：稳定、可演示；禁止 force push / delete。  
建议：
- `game/chapter-3`
- `feature/tether-anchor`
- `fix/tether-airborne-jitter`
- `narrative/chapter-3-rooftop`
- `dialogue/chapter-3-memory`
- `docs/narrative-pipeline`
- `art/memory-umbrella`
- `audio/rooftop-memory`

## Commit
```text
feat(narrative): add chapter 3 umbrella memory event
feat(dialogue): add rooftop mother-daughter conversation
feat(level): add warehouse dual-character gate
feat(state): persist umbrella memory discovery
fix(narrative): prevent memory event retrigger after reload
fix(tether): stabilize airborne state near equal height
docs(character): revise Mother relationship arc
refactor(state): separate memory state from checkpoint state
test(narrative): add save-load cases for C03 memory
```

## Narrative Change Rules
状态/条件变更必须同步 Event Spec、State Schema、QA。  
删除剧情必须检查 Trigger、Save、Localization Key、VO、Timeline 等引用。

## PR Template
```md
## What
## Why
## State Impact
## Cross-discipline Impact
- [ ] Level
- [ ] Gameplay
- [ ] UI
- [ ] Art
- [ ] Audio
- [ ] Localization
- [ ] Save Data
## Test
## Screenshots / Video
```
