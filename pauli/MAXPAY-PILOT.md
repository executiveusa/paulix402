# MaxPay Internal Pilot

## Goal
Prove that MaxPay can coordinate real payments between the team without making any single processor the system of record.

## Pilot users
Internal team only until verification, receipt integrity, replay protection, and operational controls are proven.

## Rail A — USDC
First programmable proof.

Flow:
1. Create a small MaxPay payment request.
2. Display amount, recipient address, asset, network, expiration, and purpose.
3. Sender signs with their own wallet.
4. Server independently verifies recipient, amount, asset, network, confirmation state, and transaction hash.
5. Reject replay/duplicate settlement.
6. Normalize the transaction into the MaxPay ledger.
7. Issue a receipt.

Start on testnet where applicable. Mainnet proof must be deliberately small.

## Rail B — Cash App Business
U.S. convenience rail.

Use Cash App Business only for legitimate goods/services payments under Cash App's current Business Terms. It remains a Block-controlled/KYCed rail and must never be described as sovereign or censorship-resistant.

Pilot record:
- MaxPay request ID
- sender/reference supplied by operator
- gross amount
- Cash App fee if applicable
- net amount received
- timestamp
- manual/adapter verification status
- normalized MaxPay receipt

Do not represent Cash App settlement as onchain verification.

## Rail C — x402
Machine-payment proof after Rail A passes.

1. Agent requests paid resource.
2. Resource returns 402 requirements.
3. Agent pays under a hard spending policy.
4. Server/facilitator verifies and settles.
5. Resource returns result and MaxPay records the receipt.

## Acceptance criteria
- No private treasury key in browser or app container.
- A frontend redirect cannot mark a payment paid.
- Duplicate events cannot create duplicate payments.
- Failed/underpaid/wrong-recipient transactions remain unpaid.
- Every settled payment has a verifiable or explicitly documented settlement reference.
- Each rail can be disabled without disabling MaxPay.

## Public claim boundary
Until the criteria above pass, MaxPay is an invite-only payment infrastructure experiment—not a production payment processor.
