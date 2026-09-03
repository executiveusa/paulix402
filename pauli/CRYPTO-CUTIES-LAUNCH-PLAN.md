# Crypto Cuties / Sovereign Payments Launch Plan

## Tonight — public proof surface

### Slice 0 — Baseline and branch safety
- Preserve x402 upstream code untouched where possible.
- Product additions live under `pauli/`.
- All launch work happens on `feat/crypto-cuties-sovereign-launch` until reviewed.

### Slice 1 — Landing shell
Build `pauli/apps/web` as a config-driven Next.js/TypeScript application.

Required routes:
- `/` — Crypto Cuties launch page
- `/pay` — payment request / checkout shell
- `/receipt/[id]` — normalized receipt view
- `/docs` — product explanation and open-source links
- `/brands/max-pay` — Max Pay preview using the same components

### Slice 2 — Crypto Cuties visual system
Direction: editorial nightlife + premium finance + cinematic technology.
Avoid generic neon Web3 gradients, meme-coin aesthetics, dating-site UX, investment hype and fake trading dashboards.

Hero:
- eyebrow: `CRYPTO CUTIES PRESENTS`
- headline: `MONEY FOR HUMANS AND MACHINES.`
- support: `A public experiment in payment sovereignty. Open source. Multi-rail. Verify everything.`
- primary CTA: `Watch the $1 proof`
- secondary CTA: `Explore the code`
- tertiary CTA: `Launch your own`

The AI characters are a media/editorial layer. Character visuals must be clearly synthetic and adult-coded. No character endorses or solicits purchase of a token.

### Slice 3 — Story sections
1. **The old way** — bank/processor dependency visual.
2. **The new way** — payment router: human, wallet, agent, merchant.
3. **One core, many rails** — x402, USDC, Lightning, XRPL, Creem, conventional adapters.
4. **Human Pay / Machine Pay** — side-by-side demonstration.
5. **Black Swan Mode** — rail failure visualization showing graceful fallback.
6. **Max Pay pilot** — first white-label customer proof.
7. **Open source** — architecture, self-hosting thesis and repository CTA.
8. **Verify Everything** — sources, receipts, status and claims ledger.

### Slice 4 — White-label renderer
Brand selected by host or environment variable:
- `BRAND_ID=crypto-cuties`
- `BRAND_ID=pauli-pay`
- `BRAND_ID=max-pay`

No duplicated pages. Theme/copy/rail policy come from brand configuration.

### Slice 5 — Payment core v0
Implement interfaces only before chain-specific code:
- `PaymentRequest`
- `PaymentQuote`
- `PaymentResult`
- `PaymentAdapter`
- `PaymentVerifier`
- `Receipt`

The application never grants access from a frontend callback alone. Payment must be verified server-side/onchain or through a trusted adapter before a receipt is marked settled.

### Slice 6 — First real rail
USDC testnet payment:
1. create request
2. display amount/recipient/network
3. user signs in their own wallet
4. backend verifies transaction
5. idempotency/replay check
6. store normalized ledger event
7. issue receipt

Only after testnet passes do a deliberately small mainnet proof.

### Slice 7 — x402 machine payment
Create one paid demo endpoint, e.g. `/api/proof`.
- first call returns HTTP 402 payment requirements
- agent/client signs payment
- facilitator/self-facilitator verifies/settles
- successful call returns HTTP 200 plus settlement receipt

### Slice 8 — Max Pay pilot
Use `max-pay.json` without modifying payment-core code.
Proof:
- Max Pay can create a payment request
- receive a small real payment
- generate the same normalized receipt
- disable one rail without affecting others

### Slice 9 — Deployment
Preferred production topology:
- public web: deployable to Max Digital Media infrastructure and standard preview providers
- payment verifier/router: sovereign VPS/Coolify/Docker
- database: Postgres/Supabase-compatible
- secrets: server-side environment/secret store only
- wallets: customer-controlled; no treasury private keys in app containers

### Slice 10 — Public launch proof
The public launch is not `we built a payment company`.
The public launch claim is exactly what is proven:
1. Crypto Cuties landing is live.
2. Code is public.
3. One $1-equivalent payment is independently verifiable.
4. One $0.01 x402 machine payment is independently verifiable.
5. Max Pay renders from the same core/config model.

## 30-day rollout

### Week 1 — Reveal + proof
- landing
- $1 proof
- x402 proof
- source + architecture page

### Week 2 — Max Pay
- payment links
- receipts
- team payment pilot
- collect friction/fee evidence

### Week 3 — second/third rails
- Lightning/BTCPay
- XRPL/RLUSD or other selected adapter
- routing UI

### Week 4 — open-source install
- Docker/Coolify deployment
- example tenant
- external install test
- security/threat review
- publish first verified case study

## Commercial offer
`Sovereign Payment Audit -> Sovereign Launch -> Managed Operations`

Sell implementation and operations; keep the protocol/core open.

## Stop conditions
Do not add another rail until the first rail has a verified transaction, receipt, replay protection and rollback path.
Do not create client forks for branding.
Do not add custody as a shortcut.
Do not market speculative token returns.
Do not claim bank independence when a configured adapter still depends on a bank or custodian.
