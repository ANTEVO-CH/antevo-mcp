# Antevo Companies

The public record on a Swiss company: register identity from the commercial
register (Zefix), the dated changes published in the gazette (SHAB), the group
structure and checks against official sanctions lists, each line with its source
and date. A company outside Switzerland that owns a Swiss one gets a thin file by
its LEI or ISIN.

**Signs you in over OAuth 2.1** with any Antevo account. Your assistant receives a
scoped token, never your password.

`https://api.antevo.ch/mcp/companies/mcp`

## What you can ask

- Find Sika AG and open its file.
- What has changed at this company since January?
- Who sits above this company in its group?
- Watch this company and tell me when something changes.

## What it will not do

It reads, with three exceptions: it starts or stops a watch when you ask, opening
a file uses your credits, and a deep file is written only after you agree to its
price. It never calls a company risky, suspicious or safe. **It supports a KYC
file; it is not a KYC, AML or sanctions-compliance screen.** SHAB lines are not
official publications; the authoritative text is on shab.ch.

Step by step: <https://antevo.ch/mcp/companies/>

## Install in Kiro

Powers → Add Custom Power → import from GitHub:
`https://github.com/ANTEVO-CH/antevo-mcp/tree/main/powers/antevo-companies`

Kiro asks you to sign in with your Antevo account the first time a tool runs.

## Privacy and support

- Privacy policy: <https://antevo.ch/policies/privacy-policy>
- Support: [contact@antevo.ch](mailto:contact@antevo.ch)
- Security reports: [SECURITY.md](../../SECURITY.md)

Full tool list and setup for other assistants: <https://antevo.ch/mcp>
