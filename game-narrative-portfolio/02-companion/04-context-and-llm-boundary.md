# Dialogue Context & LLM Boundary

## Context Assembly
System/Safety → Character Canon → World State → Relationship → Scene → Relevant Confirmed Memories → Recent Conversation → User Query。

## LLM 可以
- 自然语言表达
- 在已确认上下文中变化措辞
- 提议 Candidate

## LLM 不可以
- 直接改 Canon
- 直接 Commit World Event
- 凭空建立人物关系
- 凭空创造已发生行程/持有物
- 把未确认 Candidate 当事实

新事实输出必须进入 `proposed_fact`，经规则/产品逻辑确认后才能持久化。
