# Clearwater

**Neutral DeFi Risk Intelligence Aggregator**

Clearwater is an open source web application that aggregates DeFi risk intelligence from every major feed into a single neutral view, presenting each rating verbatim, producing no synthesis or composite scoring of its own.

---

## What It Does

DeFi risk intelligence has matured significantly. BlockAnalitica covers collateral risk. DeFiScan publishes decentralization and upgrade risk assessments. Pharos tracks dependency and oracle exposure. Credora models counterparty credit risk. Each is valuable. None talks to the others.

Clearwater is the aggregation layer. One page per protocol. One row per feed provider. Every rating shown exactly as the provider published it, with a direct link to the source. No Clearwater risk score. No weighting. No opinion.

The right model is oracle diversity: no single feed should be canonical, and the aggregation is the value.

---

## Scope

**At launch:** Top 20 Ethereum mainnet DeFi protocols by TVL, fully populated across all available risk feeds.

**Seed protocol list:**

| # | Protocol | Category |
|---|----------|----------|
| 1 | Lido | Liquid Staking |
| 2 | Aave V3 / V4 | Lending |
| 3 | EigenLayer | Restaking |
| 4 | Uniswap V3 | DEX |
| 5 | Maker / Sky | CDP / Stablecoin |
| 6 | Compound V3 | Lending |
| 7 | Curve Finance | DEX / Stablecoin |
| 8 | Pendle | Yield Trading |
| 9 | Rocket Pool | Liquid Staking |
| 10 | Spark Protocol | Lending |
| 11 | GMX V2 | Perpetuals |
| 12 | Euler Finance | Lending |
| 13 | Morpho | Lending |
| 14 | Balancer V3 | DEX |
| 15 | Chainlink | Oracle |
| 16 | Circle CCTP | Bridge / Stablecoin |
| 17 | dYdX | Perpetuals |
| 18 | Frax Finance | Stablecoin |
| 19 | Yearn Finance | Yield Aggregator |
| 20 | Convex Finance | Yield / Governance |

Final list confirmed against DefiLlama at the time of launch delivery. Protocols that exit the top 20 before launch are documented and substituted.

---

## Feed Providers

Clearwater integrates every major DeFi risk intelligence feed:

| Provider | Integration | Notes |
|----------|-------------|-------|
| BlockAnalitica | Automated | REST API |
| DeFiScan | Automated | Public GitHub data |
| Pharos | Automated / Manual | API access in progress |
| Credora | Manual initially | Documented update process |
| CuratorWatch | Automated | Open data model |
| DeFiPunk'd | Manual initially | Community maintained |

Providers without public APIs are populated manually and flagged with a **"Manual-last updated [date]"** indicator. The community correctable data layer means anyone can submit a pull request to update a manual entry with a source citation.

---

## What Clearwater Does Not Do

To be explicit, these constraints are codified in the project charter and are not subject to modification:

- **No composite scoring.** Clearwater does not produce a Clearwater Risk Score.
- **No weighting.** Clearwater does not rank one feed provider's rating above another's.
- **No interpolation.** Clearwater does not estimate ratings for protocols a feed provider has not covered. Coverage gaps are shown as gaps.
- **No promotional arrangements.** Clearwater does not accept sponsorship, listing fees, or commercial arrangements from protocols or feed providers.
- **No opinion.** Clearwater shows what each feed says and lets the user decide what it means.

---

## The Data Layer

Every protocol's feed data is stored as a versioned JSON file in this repository, following a documented open schema. This means:

- Any community member can submit a pull request to update a feed rating with a source citation
- Coverage gaps are visible in the repository, not hidden from view
- Any project can consume the data layer directly without going through the Clearwater interface
- The schema is stable and versioned

The data layer is the primary mechanism for keeping manual feed data accurate between our own update cycles. It is not an optional community engagement. It is the architecture.

---

## Interface Design

Clearwater follows the legibility standard of L2Beat, Walletbeat, and DeFiScan: data dense, no marketing language, no dark patterns. Each protocol page shows:

- Protocol name, category, current TVL (sourced from DefiLlama)
- One row per feed provider: provider name, rating or assessment (verbatim), date of last update, direct link to the source
- Coverage gaps shown explicitly
- A changelog showing when ratings changed and from what to what

There is no homepage leaderboard. There is no "safest protocol" ranking.

---

## Stack

- **Frontend:** Next.js 14 + TypeScript
- **Data layer:** Open JSON schema, versioned in this repository
- **TVL:** DefiLlama API, cached 15 minutes, displayed with timestamp
- **Governance data:** On-chain sources (Tally, Boardroom, Snapshot) where available
- **Hosting:** Vercel - clearwater.fouriers.xyz

---

## Who Builds This

Clearwater is built and stewarded by [Fourier](https://fouriers.xyz), an EVM gas optimization and research practice. Fourier has published independent analyses of eleven major Ethereum protocols, which includes Uniswap V3, Aave V4, GMX Synthetics, Lido, Euler, Compound & Circle CCTP, with every finding published publicly and no protocol sponsorship.

**Named steward:** Ram Manohar Suresh Chandra  
**Public presence:** [fouriers.xyz](https://fouriers.xyz) · [github.com/NthMOMENT](https://github.com/NthMOMENT) · [@0xfourier](https://x.com/0xfourier)

Published research: [github.com/NthMOMENT/Fourier.u](https://github.com/NthMOMENT/Fourier.u)

**Conflict disclosure:** Fourier has no commercial relationship with any listed protocol or feed provider. All prior protocol analyses were conducted independently and were not reviewed or approved by the protocols they cover. A full CONFLICTS.md will be committed to this repository before any code is written.

---

## Funding

Clearwater is being built under a grant application to the Ethereum Foundation's Ecosystem Support Program (RFP: Neutral DeFi Risk Intelligence Aggregator).

---

## Status

**Pre-development.** Grant application submitted June 2026. Development begins upon grant activation.

Milestone plan:
- **Weeks 1–4:** Project charter, data schema v1, feed integration architecture, provider outreach
- **Weeks 5–12:** Working application deployed, top 10 protocols fully populated, community data layer live
- **Weeks 13–20:** All 20 protocols fully populated, all feeds integrated, changelog live, full documentation

---

## License

MIT open source from day one.
