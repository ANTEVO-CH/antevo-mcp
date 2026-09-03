# Security

## Reporting

Email **contact@antevo.ch**. Please include what you did, what you expected and what
happened. We will confirm receipt and keep you updated until it is closed.

Do not open a public issue for a suspected vulnerability.

## What these servers do

All three are **read-only**. No tool exposed on the public Executive and Trademark servers,
or on the aggregated Wealth connector, can create, modify or delete anything.

**Executive** and **Trademark** serve published editorial and public-register data. They
carry no personal data and need no account.

**Wealth** serves one signed-in customer their own household's records, over OAuth 2.1 with
PKCE. Discovery is deliberately open — `initialize`, `tools/list` and `ping` answer without
a token, so the tool surface can be inspected before anyone signs in. Everything that
reaches data requires a token: any `tools/call`, resource read or prompt read answers `401`
with the RFC 9728 `WWW-Authenticate` challenge that begins the authorization flow.

## Scope

This repository contains connection metadata only. A vulnerability in the Antevo services
these files point at is in scope for the address above; the files here describe endpoints
and cannot themselves execute anything.
