# Pharmacy Process Improvement

A process-mining case study on retail pharmacy prescription fulfillment — mapping where delays actually form, and what closes the gap between a prescription being "filled" and a customer walking out with it.

Built as a single-page static site, with the underlying analysis done in [Disco](https://fluxicon.com/disco/).

## The question

A prescription moves through only a few steps — submitted, insurance verified, filled, ready for pickup, picked up. Each individual step takes minutes. So why does the whole thing so often take hours?

## Approach

- Modeled **200 synthetic prescriptions** moving through the fulfillment flow over a simulated month
- Built in real-world dynamics: a single shared pharmacist resource, insurance-type branching (private, Medicare, Medicaid, self-pay), prior authorizations, rejections, and **queueing** — cases waiting for a busy pharmacist rather than being processed the instant they arrive
- Mined the resulting event log in Disco to surface the process map, path variants, and per-step timing

## Key findings

- The **48-minute median delay** after prior-authorization approval is the single sharpest bottleneck in the process
- The worst-case path — insurance rejected, doctor contacted, claim resubmitted — runs to a **2-hour** median
- **35% of prescriptions** hit real queue wait for the pharmacist, concentrated at predictable peak hours (late morning, early afternoon, and evening pickup rush)
- The delay isn't in any single task — it's in how much work funnels through one shared resource

## Recommendations

1. **Auto-validate insurance** for returning customers to remove an entire branch from the flow (reduces variability)
2. **Route routine approval logging off the pharmacist** to a trained tech, reserving pharmacist time for clinical exceptions (reduces queueing at the bottleneck)
3. **Real-time queue visibility** so an invisible wait becomes a predictable one, cutting wasted trips and repeat calls

## Built with

- **Disco** — process mining and event-log analysis
- **HTML / CSS / JavaScript** — single-page static site, no build step
- Deployed via Netlify

## Context

Created for MSIS 503 (Operations Management / Business Analytics) as a process-improvement case study connecting a real-world workflow to course concepts: bottleneck analysis, queueing, variability (Ca/Cs), and process mining.

*Data is synthetic; fill-time and arrival-rate assumptions are grounded in published pharmacy benchmarks. Individual case records are fabricated for analysis.*
