# State / Event / Dialogue

```yaml
evidence:
  ledger_weight: false
  remake_mark: false
  verbal_order: false
  old_object: false
relationship:
  jingyi: 0
  craftsman: 0
risk:
  audit: 0
gold:
  accounted_weight: 10.0
  verified_weight: 8.7
```

## EVT_QG_021
前置：`ledger_weight=true`, `jingyi>=1`

选择：
1. 直接质问缺金 → jingyi -1。
2. 问是否改制 → 解锁 verbal_order hook。
3. 暂不追问 → 保关系、延迟证据。

### Dialogue
沈砚：账上写十两。复验只有八两七钱。  
静宜：所以你来问我，少的那一两三钱去了哪里。  
沈砚：这支簪一直由你经手。  
静宜：一直在内廷。

选 B：“你只说它没出去，没说它没被改过。”  
静宜：（停顿）你比我想的看得仔细。

设计：人物不是简单撒谎，而是只说局部真话。
