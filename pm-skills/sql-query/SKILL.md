# SQL Query - SQL数据查询

---

## Description

用SQL自助取数，不依赖数据团队也能快速获取数据。

**解决的实际问题：**
- 找数据团队排期要等一周
- 需求描述不清，返工多次
- 临时想看个数，等不及

---

## When to Use

**强制触发条件（任一满足）：**
- 明确说"查一下数据"、"跑个SQL"
- 需要快速验证假设（<1小时）
- 数据团队排期紧张
- 高频取数需求（每周/每日）

**不适用场景：**
- 复杂分析（涉及多表关联>5个）
- 大数据量（>1000万条）
- 生产环境直接查询（用只读库）

---

## Pre-conditions

**必须提供：**
- 表结构说明
- 查询目标
- 时间范围

---

## Workflow

### Phase 1: 理解表结构

```markdown
## 核心表说明

### user表
| 字段 | 类型 | 说明 |
|------|------|------|
| user_id | BIGINT | 用户ID |
| register_time | DATETIME | 注册时间 |
| channel | VARCHAR | 注册渠道 |
| platform | VARCHAR | iOS/Android |

### event表
| 字段 | 类型 | 说明 |
|------|------|------|
| event_id | BIGINT | 事件ID |
| user_id | BIGINT | 用户ID |
| event_name | VARCHAR | 事件名 |
| event_time | DATETIME | 事件时间 |
| params | JSON | 事件参数 |
```

### Phase 2: 编写查询

```markdown
## 常用查询模板

### 1. 每日新增用户
```sql
SELECT 
    DATE(register_time) as dt,
    COUNT(DISTINCT user_id) as new_users
FROM user
WHERE register_time >= '2026-01-01'
GROUP BY dt
ORDER BY dt DESC;
```

### 2. 次日留存
```sql
WITH new_users AS (
    SELECT user_id, DATE(register_time) as register_date
    FROM user
    WHERE register_time >= DATE_SUB(CURRENT_DATE, INTERVAL 30 DAY)
),
next_day_active AS (
    SELECT DISTINCT user_id, DATE(event_time) as active_date
    FROM event
    WHERE event_name = 'app_launch'
)
SELECT 
    n.register_date,
    COUNT(DISTINCT n.user_id) as new_users,
    COUNT(DISTINCT a.user_id) as d2_active,
    ROUND(COUNT(DISTINCT a.user_id) * 100.0 / COUNT(DISTINCT n.user_id), 2) as d2_retention
FROM new_users n
LEFT JOIN next_day_active a 
    ON n.user_id = a.user_id 
    AND a.active_date = DATE_ADD(n.register_date, INTERVAL 1 DAY)
GROUP BY n.register_date
ORDER BY n.register_date DESC;
```

### 3. 功能使用统计
```sql
SELECT 
    event_name,
    COUNT(*) as total_count,
    COUNT(DISTINCT user_id) as unique_users,
    ROUND(COUNT(*) * 1.0 / COUNT(DISTINCT user_id), 2) as avg_per_user
FROM event
WHERE event_time >= DATE_SUB(CURRENT_DATE, INTERVAL 7 DAY)
GROUP BY event_name
ORDER BY total_count DESC;
```

### 4. 用户分群
```sql
-- 按活跃度分群
SELECT 
    CASE 
        WHEN launch_days >= 20 THEN '高活跃'
        WHEN launch_days >= 10 THEN '中活跃'
        WHEN launch_days >= 1 THEN '低活跃'
        ELSE '流失'
    END as user_group,
    COUNT(DISTINCT user_id) as user_count
FROM (
    SELECT 
        user_id,
        COUNT(DISTINCT DATE(event_time)) as launch_days
    FROM event
    WHERE event_name = 'app_launch'
        AND event_time >= DATE_SUB(CURRENT_DATE, INTERVAL 30 DAY)
    GROUP BY user_id
) t
GROUP BY user_group;
```

### 5. 漏斗查询
```sql
WITH funnel AS (
    SELECT 
        DATE(event_time) as dt,
        COUNT(DISTINCT CASE WHEN event_name = 'page_home' THEN user_id END) as step1,
        COUNT(DISTINCT CASE WHEN event_name = 'btn_click' THEN user_id END) as step2,
        COUNT(DISTINCT CASE WHEN event_name = 'order_submit' THEN user_id END) as step3
    FROM event
    WHERE event_time >= DATE_SUB(CURRENT_DATE, INTERVAL 7 DAY)
    GROUP BY dt
)
SELECT 
    dt,
    step1,
    step2,
    ROUND(step2 * 100.0 / step1, 2) as step1_2_rate,
    step3,
    ROUND(step3 * 100.0 / step2, 2) as step2_3_rate
FROM funnel
ORDER BY dt DESC;
```
```

### Phase 3: 优化与验证

```markdown
## SQL优化原则

1. **避免SELECT ***
   - 只选需要的字段
   
2. **WHERE条件加索引字段**
   - event_time, user_id 通常有索引
   
3. **大数据量分批查询**
   - 按天分多次查，再汇总
   
4. **先EXPLAIN看执行计划**
   - 确认是否走索引

## 验证清单
- [ ] 结果数量级合理
- [ ] 抽样验证几条数据
- [ ] 和之前同类查询对比
```

---

## Output

```markdown
# 数据查询结果

## 查询目的
[说明]

## SQL语句
```sql
[代码]
```

## 查询结果
| 日期 | 新增用户 | 次日留存 |
|------|---------|---------|
| 2026-04-01 | 100 | 40% |

## 结论
[数据洞察]
```

---

## Quality Gates

- [ ] SQL有注释说明
- [ ] 时间范围明确
- [ ] 结果抽样验证
- [ ] 执行时间<10秒

---

## Version

- v1.0.0 | 2026-04-08
