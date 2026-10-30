# Level Narrative Spec

## Puzzle Grammar
### Heavy Object
Solver: Mother  
Meaning: 稳定与力量可以为别人创造路径。

### Low Passage
Solver: Daughter  
Meaning: 独立探索；但 Mother 的位置仍影响安全范围。

### Anchor
Meaning: “留下”是主动行为，而非停滞。

### Tethered Airborne
既有 Chapter 3 设计记录：W / ↑ 沿线移动。  
Meaning: 牵挂线第一次明确成为移动资源。

## Checkpoint Narrative
- 保留已完成 Memory State；
- 不重复关键情绪演出；
- 恢复到语义合理位置；
- 牵挂状态与角色状态一致。

## Known Technical Risks
- 同高度 W 输入抖动；
- 上方角色以另一角色为支撑时异常跳动/重置；
- fall-limit oscillation；
- 横向输入不应直接破坏 tethered airborne；
- `fallen` 应为稳定显式状态；
- Tab 切换不要擅自改变 anchor 继承关系。
