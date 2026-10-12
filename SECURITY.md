# Security policy

ProviderStatus measures third-party providers from the outside. There is no
account, no login and no customer data here — the worst thing an attacker
could do to this project is make it publish a wrong number about a company
that did nothing wrong. That is what this policy is for.

## Reporting

Use **GitHub private vulnerability reporting** on this repository:
<https://github.com/providerstatus/feedback/security/advisories/new>

The repository is public; the report is not. Only we can see it, and it stays
private until a fix ships. **Do not open a normal issue for a security
problem** — that discloses it to everyone before it is fixed.

We will acknowledge within a few days. There is no bounty; this is a free
service run by a small company, and we will say so rather than let you expect
one.

## Scope

| Surface | What runs there |
|---|---|
| `providerstatus.dev` | Static pages (Cloudflare Pages) **and** a Worker on six routes: `/api/v1/*` (public JSON), `/probe-sites`, `/probe-config` and `/sitemap-providers.xml` (public reads), `/ingest*` (shared-secret, probe hosts only) and `/admin/*` (bearer token) |
| `providerstatus.sh` | One Worker, read-only: the same data as plain text, JSON or Prometheus metrics |

Both are Cloudflare Workers over Cloudflare D1 and Analytics Engine. There is
no origin server, no container and no SSH surface belonging to this project
other than the probe hosts, which do not accept inbound connections for it.

**In scope, and the things we would most want to hear about:** anything that
lets a request write to the database or the ingest path without the shared
secret; anything that lets `/admin/*` run without the bearer token; a way to
make the public reads emit another host's internal probe hostname; and
anything that lets a third party influence a published figure about a named
provider.

**Out of scope:** the monitored providers themselves. We only send
unauthenticated `GET` requests to their public endpoints. Report problems in
their services to them, not to us. Also out of scope: missing security headers
with no demonstrated impact, volumetric denial of service, and reports whose
only content is a scanner's output.

**Please do not run automated scanners against the ingest endpoint.** It is
shared-secret authenticated and rate-sensitive — one accepted request per
probe per 20 seconds — and a scanner there costs real measurements. Tell us
what you suspect and we will reproduce it ourselves.

## What we publish afterwards

Corrections and incidents that affected published figures go into the public
changelog at <https://providerstatus.dev/changes>, including the ones that
make us look bad. If a vulnerability caused a wrong figure about a provider,
that provider is told directly as well.

---

Machine-readable version, kept in step with this file:
<https://providerstatus.dev/.well-known/security.txt>
