# 📊 Customer Support Operations & SLA Optimization

---

## 🚨 Executive Summary

Customer support operations are often assumed to struggle due to high demand.  
This analysis challenges that assumption.

Using **200K+ support tickets**, this project uncovers a critical insight:

> **The problem is not demand — it is execution**

Despite stable ticket volume, the system consistently underperforms due to:

- Low resolution output  
- Delayed response times  
- Poor SLA adherence  

The result is **systematic backlog growth and service inefficiency**.

---

## 🎯 Business Problem

Organizations lack visibility into how demand, resolution capacity, and agent behavior interact.

This creates key risks:

- Growing backlog  
- SLA violations  
- Poor customer experience  
- Inefficient resource utilization  

### Key Questions Answered

- Is demand increasing or stable?  
- Are we keeping up with incoming tickets?  
- What drives SLA breaches?  
- Where do delays occur in the lifecycle?  
- How do agents perform under workload?  

---

## 🧠 Key Insight

> Support operations are not constrained by demand  
> They are constrained by **agent execution and response behavior**

---

## 🧱 Dataset

| Attribute | Description |
|----------|------------|
| Records | 200,000+ tickets |
| Time Range | 3 years |
| Structure | Operational support dataset |
| Key Fields | status, priority, category, timestamps, SLA |

---

## 🛠️ Tech Stack

| Layer | Tools |
|------|------|
| Data Processing | Python (pandas, numpy) |
| Analysis | SQL |
| Visualization | Power BI |
| Forecasting | ARIMA |

---

## ⚙️ Workflow


Raw Data → Cleaning → Feature Engineering → SQL Analysis → Power BI → Insights


---

## 🔧 Feature Engineering

### Time Features Created

- Year  
- Month  
- Weekday  
- Year-Month  

### SLA Thresholds

| Priority | SLA Threshold |
|---------|--------------|
| Urgent | 6 hrs |
| High | 8 hrs |
| Medium | 24 hrs |
| Low | 48 hrs |

---

# 📈 Analysis & Insights

---

## 📊 Demand is Stable

- Daily volume: **160–220 tickets**  
- Monthly: **~5K tickets**  
- Yearly: **~66K tickets**

**Insight:**  
Demand is predictable and not the source of operational issues.

---

## ⚠️ Resolution Output is Low

- Agents resolve only **~50% of assigned tickets**  
- Remaining tickets accumulate into backlog  

**Insight:**  
Backlog is driven by **low resolution capacity**, not demand spikes.

---

## ⛔ SLA Compliance is Poor

- No agent exceeds **30% SLA compliance**  
- Failures occur across all categories  

**Insight:**  
This is **system-wide underperformance**

---

## ⏱️ Response and Resolution Delays

| Metric | Value |
|------|------|
| Avg First Response | ~31–33 hrs |
| Avg Resolution Time | ~120 hrs |

**Insight:**  
Delays directly cause SLA breaches and backlog growth.

---

## 📂 Category Concentration

- Few categories dominate ticket volume  

**Insight:**  
Fixing top categories reduces workload significantly.

---

## 👤 Agent Performance Issues

- Agents resolve **60–80 tickets/month regardless of workload**  
- Output does not scale with assigned tickets  

**Insight:**  
Indicates lack of accountability and performance benchmarks.

---

# 📊 Dashboards

---

## 🖥️ Operational Dashboard

**Purpose:** Monitor overall system performance  

**Includes:**

- Ticket volume trends  
- SLA compliance  
- Demand vs resolution  
- Backlog tracking  
- Top categories  

---

## 👤 Agent Performance Dashboard

**Purpose:** Evaluate individual agent efficiency  

**Includes:**

- Agent performance metrics  
- SLA compliance by category  
- Resolution and response trends  
- Workload vs efficiency  

---

# 🧮 Sample SQL

```sql
SELECT 
    DATE_TRUNC('month', ticket_created_date) AS month,
    COUNT(*) AS total_tickets
FROM tickets
GROUP BY month
ORDER BY month;
🐍 Sample Python
daily = data.groupby("ticket_created_date").size().reset_index(name="ticket_count")

daily["rolling_7"] = daily["ticket_count"].rolling(7).mean()

# 🧮 DAX Measures

These DAX measures were used to build the key KPIs for ticket demand, resolution performance, SLA compliance, and agent efficiency.

---

## Core Metrics

### Ticket Count
Counts total tickets in the current filter context.

```DAX
Ticket Count = COUNT('Joined_data (60)'[ticket_id])

unts tickets that are still unresolved.

Tickets Unresolved = 
CALCULATE(
    COUNTROWS('Joined_data (60)'),
    'Joined_data (60)'[status] IN {"Open", "In Progress", "Pending Customer"}
)

unts tickets that are still unresolved.

Tickets Unresolved = 
CALCULATE(
    COUNTROWS('Joined_data (60)'),
    'Joined_data (60)'[status] IN {"Open", "In Progress", "Pending Customer"}
)

SLA Compliance % =
VAR WithinSLA =
    CALCULATE(
        COUNTROWS('Joined_data (60)'),
        'Joined_data (60)'[sla_breached_recalc] = FALSE()
    )
RETURN
    DIVIDE(WithinSLA, COUNTROWS('Joined_data (60)'))

SLA Breach % =
VAR Breached =
    CALCULATE(
        COUNTROWS('Joined_data (60)'),
        'Joined_data (60)'[sla_breached_recalc] = TRUE()
    )
RETURN
    DIVIDE(Breached, COUNTROWS('Joined_data (60)'))

Performance Rank =
RANKX(
    ALL('Joined_data (60)'[agent_id]),
    [Performance Score],
    ,
    DESC
)


```

# 📌 Recommendations

---

## 1. Introduce Performance Benchmarks
- Define minimum resolution targets for each agent  
- Ensure output scales with assigned workload  

---

## 2. Enforce SLA-Based Prioritization
- Prioritize tickets approaching SLA breach  
- Reduce delays in first response  

---

## 3. Improve Agent Accountability
- Track performance at the individual agent level  
- Introduce standardized performance scoring  

---

## 4. Reduce Resolution Time
- Optimize internal workflows  
- Improve handling of high-complexity tickets  

---

## 5. Optimize Work Allocation
- Balance ticket distribution across agents  
- Monitor capacity versus workload  

---

## 6. Address High-Volume Categories
- Identify and reduce repeat issues  
- Improve upstream processes to limit ticket generation  

---

## 7. Implement Continuous Monitoring
- Use dashboards for real-time performance tracking  
- Enable proactive operational decision-making  

---

# 🧠 Final Conclusion

> The system is not overloaded  
> It is **underperforming**

Improving:

- Response time  
- Resolution efficiency  
- Accountability  

Will directly improve:

- SLA compliance  
- Backlog reduction  
- Customer experience  

---

# 💼 Portfolio Value

This project demonstrates:

- End-to-end analytics workflow  
- Strong business-focused thinking  
- Real operational problem solving  
- Dashboard storytelling  
- Senior-level analytical insights  

---



**David Asikpo**  
Business Intelligence Analyst  
