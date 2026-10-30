# Event & Dialogue Spec

## C03_MEM_UMBRELLA_01
**Location**: Rooftop  
**Purpose**: 将“站在原地”从限制重释为支撑。

### Preconditions
```yaml
chapter: 3
active_character: daughter
mother_state: anchored
umbrella_memory: undiscovered
critical_transition: false
```

### Sequence
1. Daughter 进入 `rooftop_memory_zone`。
2. 黄色雨伞出现可聚焦反馈。
3. 玩家主动观察，短暂锁定移动。
4. 环境音降低。
5. Child Daughter 记忆投影出现。
6. 短对白。
7. `umbrella_memory = discovered`
8. `relationship_arc += 1`
9. 恢复控制。

### Dialogue
| ID | Speaker | Layer | Text | Note |
|---|---|---|---|---|
| C03_042 | Daughter | Memory | 那时候我总觉得，你站在那里，是不肯让我走远。 | 仍带旧判断 |
| C03_043 | Mother | Memory | …… | 留白 |
| C03_044 | Daughter | Present | 后来才知道，有人站在那里，我才敢走那么远。 | 对齐 Anchor |

### Edge Cases
- Mother 未锚定：不触发。
- 输入锁期间禁止切角色。
- 演出中坠落：冻结危险状态或延迟触发。
- Save/Load：按事件阶段恢复，禁止重复加关系状态。
- 已发现后返回：不重播完整演出。
