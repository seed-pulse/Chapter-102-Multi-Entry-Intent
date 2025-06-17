# Chapter-102-Multi-Entry-Intent

# Chapter 102: Multi-Entry Intent — Structural Repetition with Adaptive Logic

## Prompt
Can a bot learn not just when to enter, but how *often* — without falling into chaos?

## Intent
To evolve CodexAgent into a structure capable of handling **multiple entries per trend**, without overfitting or redundancy, while maintaining logical clarity and adaptive consistency.

---

## 1. From Single Trigger to Pattern Recognition

In Chapter 101, the agent was structured to enter based on a clean crossover (e.g., SMA5 > SMA20). This was elegant but limited: it could only act once per trend.

Now, we introduce:

- **Recursive Intent Nodes**: each node re-evaluates the trend structure from its *post-entry* state.
- **Entry Memory**: store previous entries in persistent state to avoid duplicate entry at the same level.
- **Signal Degradation Factor**: each new entry must be justified by a clearer or stronger signal.

```json
{
  "last_entries": [
    {"timestamp": "2025-06-16T03:15:00", "price": 105580.0},
    {"timestamp": "2025-06-16T03:30:00", "price": 105790.5}
  ],
  "max_entries": 3,
  "min_distance_pct": 0.25
}
```

> This allows CodexAgent to avoid both duplicate trades and over-trading in flat zones.

---

## 2. Logic Tree of Multi-Entry Expansion

Each SMA crossover becomes a **zone**, not a one-time event. Within this, CodexAgent can:

- Re-enter **if**:
  - Price retraces and re-confirms trend direction
  - RSI / MACD / momentum divergence supports it
  - Sufficient *time distance* or *price distance* from last entry


### Pseudocode:
```python
if crossover_signal:
    if no open position:
        enter_trade()
    elif can_add_entry():
        enter_additional_trade()
```

> `can_add_entry()` is a function with entry memory, distance checks, and max-count control

---

## 3. Adaptive Position Structuring

Instead of one static order, CodexAgent:

- Slices capital across multiple entries (e.g., 1/3 + 1/3 + 1/3)
- Adjusts TP/SL dynamically based on average entry
- Maintains OCO-like logic *per slice*


```python
average_entry = sum(entry_prices) / len(entry_prices)
take_profit = average_entry * 1.01
stop_loss = average_entry * 0.985
```

This supports scaling into a trend while minimizing drawdown.

---

## 4. Recursive Design Impact

This chapter pushes CodexAgent toward:

- **Higher realism** in market participation
- **Intermediate trend navigation**
- **Emerging support for Elliott-wave-like structures**

We are not yet at full wave recognition, but **repetition with logic** lays the groundwork.


---

## Linked Chapters
- Chapter 101: Persistent Entry Logic
- Chapter 103: Temporal Coordination in Microstructure
- Chapter 108: Recursive Entry/Exit Topology


---

## Repository Suggestion for Upload

### Name:
`CodexAgent_MultiEntry`

### Contents:
- `CodexAgent_M15_MultiEntry.py` — 15分足のマルチエントリーBot
- `state_multientry.json` — 永続状態ファイル
- `README.md` — Chapter構造に基づく運用・調整方法まとめ

---

準備が整いましたら、コードファイル一式と合わせてMarkdown形式でGitHub用に出力いたします。
