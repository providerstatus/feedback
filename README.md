# ProviderStatus — feedback

Public issue tracker for **[ProviderStatus by HostAtlas](https://providerstatus.dev)**,
the independent uptime monitor for the third-party providers your stack
depends on.

There is no code in this repository. It exists so that anyone can tell
us a number is wrong, ask for a provider to be added, or report a
problem with the text API — without needing an account anywhere but
GitHub.

> **Pre-launch — the pages are not up yet, but the measurement is real.**
> `providerstatus.dev` has no site behind it at the moment; the HTML is
> written and unpublished. What does run is the measurement: eight probe
> locations have been checking 113 endpoints since 31 August 2026, and
> `providerstatus.sh` serves those numbers as plain text today —
> `curl providerstatus.sh/stripe`. Every figure there is our own
> observation, so **if one looks wrong to you, that is exactly the report
> we want.** This notice used to say the numbers were placeholders. They
> stopped being placeholders when the probes started, and this sentence
> took six weeks to catch up.

---

## What to open an issue for

**A status looks wrong.** A provider marked down that is plainly fine, a
provider that is clearly broken and still shows green, an availability
figure that cannot be right. Tell us what you saw and roughly when, in
UTC — a rough timestamp makes the difference between "we can look it up"
and "we cannot". Raw per-location measurements are queryable for about
three months, so an old report is still checkable.

**A provider is missing.** We monitor what we depend on ourselves plus
what people ask for. Bring the public endpoint you want probed. If it is
unauthenticated and does not mind **one request a minute from each of
eight locations**, it usually lands quickly. A slower cadence is
available where a provider prefers one — three endpoints are on five
minutes today and one is on ten.

**The API or the docs are wrong.** A response shape that changed without
warning, a documented endpoint that behaves differently, an example that
does not run. `providerstatus.sh` is meant to be scriptable; if it
surprises you, that is a bug.

**The site itself is broken.** Rendering problems, unreadable contrast,
a page that fails on your browser or screen reader.

## What not to open an issue for

**Security vulnerabilities.** Do not post them here — a public issue
discloses the problem to everyone before it is fixed. Use
[private vulnerability reporting](https://github.com/providerstatus/feedback/security/advisories/new),
which is enabled on this repository and visible only to us. Details in
our [SECURITY.md](SECURITY.md) in this repository. (The
`security.txt` on `providerstatus.dev` is the same policy, and that host
serves nothing yet.)

**Outages at the providers themselves.** We measure Stripe, Hetzner,
Cloudflare and the rest from the outside; we do not operate them and
cannot fix them. If one of them is down, their own support is the
address. What *is* useful to us: "your page says X, their status page
says Y" — that discrepancy is exactly what we want to know about.

**HostAtlas product support.** ProviderStatus is free and public;
HostAtlas is the paid product it grew out of. For anything about your
own fleet, monitors or billing, go to [hostatlas.app](https://hostatlas.app).

---

## How we handle issues

We read everything. A wrong-status report gets checked against the raw
probe data first — if our measurement was wrong we say so in the thread
and fix the threshold or the endpoint. If the measurement was right and
the provider disagreed with it, we say that too, with both timestamps.

No SLA on responses. This is run by a small team alongside the paid
product.

## Related

Two of these are not published yet, and are marked so rather than left
to fail in your browser — see the notice at the top.

| | |
|---|---|
| Live status | [providerstatus.dev](https://providerstatus.dev) — *not published yet* |
| Text / JSON API | [providerstatus.sh](https://providerstatus.sh) — **live today** |
| Method in full | [providerstatus.dev/about](https://providerstatus.dev/about) — *not published yet* |
| The product | [hostatlas.app](https://hostatlas.app) · [github.com/hostatlas-app](https://github.com/hostatlas-app) |
| Open-source tools | [labs.hostatlas.app](https://labs.hostatlas.app) · [github.com/hostatlas-labs](https://github.com/hostatlas-labs) |

---

Copyright © 2026 **HostAtlas Technologies LLC**. All rights reserved.
ProviderStatus is not affiliated with, endorsed by or sponsored by any
monitored provider; their names are used solely to identify the services
being measured.
