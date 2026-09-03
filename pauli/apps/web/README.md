# MaxPay launch shell

A dependency-free static launch page for the first MaxPay invite-only beta.

## Purpose

This is intentionally a small marketing/proof surface, not the payment core. It translates the highest-value x402 ideas into plain language and directs interested operators into the Field Notes and invite list.

## Routes

- `/` — MaxPay invite-only landing page
- `/blog/` — first Field Note covering x402, exact, upto, batch settlement, session access and sovereignty
- `/thanks/` — invite confirmation + blog handoff

## Invite form

The form uses Netlify Forms markup:

- form name: `maxpay-invite`
- method: `POST`
- success path: `/thanks/`

For a non-Netlify host, replace the form action/handler with the selected backend without changing the page design.

## Deploy

Fast path on Netlify:

1. Create a site from `executiveusa/paulix402`.
2. Set base directory to `pauli/apps/web`.
3. No build command.
4. Publish directory: `.`
5. Verify the `maxpay-invite` form appears in Netlify Forms before sharing the link.

## Proof before public claim

This page may say MaxPay is being built or explored. It must not claim live payment rails until the corresponding payment test has independent settlement evidence, replay protection and receipt generation.
