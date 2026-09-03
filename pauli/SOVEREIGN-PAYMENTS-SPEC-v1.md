# Sovereign Payments — Product Specification v1

## Mode
Brownfield fork of `x402-foundation/x402`. Preserve upstream protocol compatibility. Product-specific code lives under `pauli/` to minimize merge conflicts with upstream.

## Outcome
Ship a reusable, white-label, non-custodial payment operating layer for humans, teams, SaaS products and AI agents. First branded proofs: Crypto Cuties public launch and Max Pay pilot.

## Core rule
One codebase. Many brands. No client-specific forks unless a technical constraint requires it.

## Product layers
1. **Protocol layer** — upstream x402 packages and specifications.
2. **Sovereign core** — normalized payment requests, routing, verification, receipts, ledger, policy and entitlement events.
3. **Adapters** — x402, USDC, BTC/Lightning, XRPL/XRP/RLUSD, Open Payments/Interledger, Creem, Stripe/Cash App and future rails.
4. **Brand shell** — config-driven checkout, landing, payment links and receipts.
5. **Deployment layer** — self-hosted Docker/Coolify first; optional Vercel/Netlify/Cloudflare frontends.

## Non-custodial default
The software coordinates and verifies payment; users and organizations control their own wallets and keys. The core must not require pooled custody or omnibus balances.

## Normalized contracts

### PaymentRequest
- id
- amount
- denomination
- recipient
- purpose
- acceptedRails[]
- expiresAt
- metadata

### PaymentQuote
- rail
- network
- asset
- receiveAmount
- estimatedFee
- estimatedSettlementTime
- paymentInstructions

### PaymentResult
- paymentId
- rail
- network
- asset
- amount
- status
- settlementReference
- timestamp
- receiptHash

## White-label contract
Each tenant is configuration, not a fork:
- `brand.name`
- `brand.logo`
- `brand.theme`
- `brand.copy`
- `brand.domain`
- `treasury.recipientAddresses`
- `rails.enabled`
- `rails.priority`
- `compliance.disclosures`
- `agentPolicy.dailyLimit`
- `agentPolicy.allowedRecipients`

Initial tenants:
- Crypto Cuties — public education + proof layer
- Pauli Pay — owner/studio deployment
- Max Pay — Max Digital Media pilot

## Landing page goal
Crypto Cuties is the public story, not an investment product.

Hero thesis:
**Money for humans and machines. Own your rails. Verify everything.**

Primary CTAs:
1. Watch the $1 proof
2. View the open-source code
3. Launch your own payment stack

Sections:
1. Hero / Crypto Cuties reveal
2. Why payment sovereignty matters
3. Live multi-rail payment visualization
4. Human Pay vs Machine Pay
5. Supported/roadmap rails
6. Max Pay first pilot
7. Black-swan resilience matrix
8. Open-source architecture
9. Education / Verify Everything
10. Call to deploy / contribute

## First vertical proof
`$1 USDC -> verify -> normalized ledger event -> receipt -> entitlement callback`

Acceptance criteria:
- receiver controls the destination wallet
- no private key stored in frontend
- payment independently verifiable onchain
- idempotent verification
- duplicate/replay protection
- failure state recorded
- receipt contains settlement reference
- testnet proof before mainnet
- rollback documented

## Second proof
`$0.01 x402 -> agent pays -> facilitator verifies/settles -> resource returns 200`

## Third proof
Max Pay white-label instance uses the exact same core and a different config file only.

## Initial rail priority
1. x402 + USDC
2. direct USDC payment links
3. Bitcoin Lightning / BTCPay
4. XRPL / XRP / RLUSD
5. Creem Merchant-of-Record adapter
6. Stripe/Cash App adapter
7. Open Payments / Interledger exploration

## Security boundaries
- no secrets committed
- no browser-held treasury keys
- wallet signing isolated from application server where possible
- agent wallets use capped allowances
- treasury uses separate custody
- adapters can be individually disabled
- upstream x402 patches remain mergeable
- audit log for every quote, verification and settlement

## Compliance boundary
This project is payment software and education, not a token sale, investment product, exchange or default custodian. Crypto Cuties content must not promise returns or recommend purchases as personalized investment advice. Jurisdiction-specific obligations remain deployment-dependent.

## Deployment model
- Core services: self-hosted VPS / Coolify / Docker
- Database: Postgres/Supabase-compatible schema
- Public landing: deployable to Netlify/Vercel/Cloudflare or same VPS
- RPC/facilitator providers: replaceable; self-host option documented

## 30-day commercial path
- Free: open-source core, SDK, docs, local Docker deployment
- Paid: Sovereign Payment Audit, white-label implementation, migration, custom adapter, managed deployment, monitoring/security support

## Proof before claims
Do not market a rail as production-ready until it has:
1. automated tests
2. threat review
3. real small-value transaction proof
4. rollback/disable procedure
5. independent verification

## Status
Architecture locked. Implementation not yet production-ready.
