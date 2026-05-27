
# tokenomics-model
Config-driven tokenomics simulation engine. Models supply schedules, staking dynamics, demand trajectories, and price discovery from genesis through maturity. Produces structured PDF reports with scenario analysis, Monte Carlo distributions, and automated risk flags.

---

<img width="602" height="636" alt="token_test_mapes" src="https://github.com/user-attachments/assets/093cad8c-82bd-46c9-91df-d2df919e20fc" />
<img width="776" height="724" alt="token_test_scenario" src="https://github.com/user-attachments/assets/14343019-caa4-4852-819c-b08a678bd1ef" />

---

## Architecture

```
                          ┌──────────────────┐
                          │  Parameter Set    │
                          │  (JSON config)    │
                          └────────┬─────────┘
                                   │
                          ┌────────▼─────────┐
                          │  Schema Validate  │
                          │  + Invariants     │
                          └────────┬─────────┘
                                   │
                   ┌───────────────┼───────────────┐
                   │               │               │
          ┌────────▼──────┐ ┌─────▼──────┐ ┌──────▼───────┐
          │ Supply        │ │ Staking    │ │ Demand       │
          │ Dynamics      │ │ Behavior   │ │ Projection   │
          └────────┬──────┘ └─────┬──────┘ └──────┬───────┘
                   │               │               │
                   └───────────────┼───────────────┘
                                   │
                          ┌────────▼─────────┐
                          │  Price Discovery  │
                          │  (regime-aware)   │
                          └────────┬─────────┘
                                   │
                   ┌───────────────┼───────────────┐
                   │               │               │
          ┌────────▼──────┐ ┌─────▼──────┐ ┌──────▼───────┐
          │ Risk Flags    │ │ Treasury   │ │ Sensitivity   │
          │ Detection     │ │ Simulation │ │ Analysis      │
          └────────┬──────┘ └─────┬──────┘ └──────┬───────┘
                   │               │               │
                   └───────────────┼───────────────┘
                                   │
                          ┌────────▼─────────┐
                          │   Report Output   │
                          │      (PDF)        │
                          └──────────────────┘
```

---

## Capabilities

- **Supply Dynamics** - Multi-cohort vesting schedules and sell pressure modeling
- **Staking Behavior** - Staking ratio dynamics
- **Demand Projection** - KPI-based demand trajectories
- **Price Discovery** - Regime-aware pricing with market factor modulation
- **Risk Detection** - 6 automated risk flags
- **Treasury Simulation** - USD burn schedules with runway floor protection
- **Sensitivity Analysis** - Multi-scenario comparison, parameter sweeps, cliff shock simulation
- **Monte Carlo** - Probabilistic simulation across random parameter distributions
- **Dual-Token Architecture** - Isolated simulation of paired token economies
- **Back-Validation** - Historical data ingestion, MAPE-based accuracy scoring
- **Web GUI** - Local Flask interface for interactive configuration and execution

---

## Test Coverage
```
  Domain              Tests
  ──────              ─────
  Supply/Vesting      44
  Staking             31
  Demand              34
  Price (MV=PQ)       43
  Emissions           50
  Risk Flags          35
  Treasury            23
  Treasury Engine     13
  Scenarios           14
  Monte Carlo          6
  Conservation        26
  Circulation          9
  Determinism          9
  Edge Cases          11
  Config Validation   29
  Reports              4
  Dual-Token          12
  Sanity Checks        5
  ───────────────────────
  Total              398

All 398 tests passing.
```
---

## Tech Stack

- Python 3.12
- Pydantic
- NumPy / Pandas
- Matplotlib
- ReportLab
- Flask
- pytest

---

## Project Scope

- 49 historical tokens back-validated across major protocol archetypes, with active expansion in progress
- 19 test modules covering all engine components
- SQLite database for validation run history
- CLI toolchain for batch operations, DB management, and parameter derivation
- VSCode-debuggable pipeline with per-step timing instrumentation
