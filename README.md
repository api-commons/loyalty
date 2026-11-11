# Loyalty

The common loyalty vocabulary -- the members enrolled in a programme, the points they earn and spend, the rewards they redeem, the tiers they climb and the referrals they make -- distilled from the APIs that already exist. Part of [Schema Commons](https://github.com/api-commons/schema-commons),
published by the [API Commons](https://apicommons.org).

Built from the providers tagged Loyalty, Rewards, Loyalty & Incentives, Loyalty Programs, Customer Loyalty, Referral, Referral Marketing, Incentives in [APIs.io](https://apis.io) that
publish their own OpenAPI. Only harvested contracts count -- nothing API Evangelist
generated. Every number below is a count of providers.

## What the market already agrees on

<!-- commons:summary -->
| Concept | Expose it | Readable schema | Core properties (share) | Collection named |
| --- | ---: | ---: | --- | --- |
| member | 14 | 12 | id 58% | members 11, accounts 2, member 1 |
| reward | 11 | 10 | id 100%, created_at 90%, status 80%, type 70%, description 50%, name 50%, updated_at 50% | rewards 10, reward 3, offers 3, redemptions 3 |
| referral | 7 | 7 | id 57% | referrals 5, referral 3, advocates 1 |

Cohort: 77 providers with harvested OpenAPI, 17 crosswalks. Of the providers exposing a member: 43% create, 71% list, 50% fetch, 21% update, 7% delete. Generated 2026-11-10 by build.py.
<!-- /commons:summary -->

Shares are of the providers with a readable resource schema for that concept. The
extended tier and the long tail of every concept are in [profile.yml](profile.yml).

## What the measurement shows

- A reward agrees on name, type, status, description and dates: what can be redeemed is shared across loyalty platforms, card-linked offer networks and incentive tools.
- A member agrees only on an id: Square's loyalty accounts, Starbucks' star balances and Smile's customers each carry the points balance and the tier in their own shape.
- Points are a balance on the member far more often than a resource of their own, and tiers a field rather than a list (4 and 2 providers).

## Artifacts

- [openapi.yml](openapi.yml) -- OpenAPI 3.1 of the shared operations. No one serves it; it
  is the shape to map to. Lints clean against the
  [naming ruleset](https://github.com/api-commons/schema-commons/blob/main/ruleset/schema-commons-naming.yaml).
- [schema/](schema) -- JSON Schema 2020-12 per concept; each property carries
  `x-commons-tier`, `x-commons-share`, `x-commons-providers` and the spellings seen.
- [crosswalk/](crosswalk) -- one per provider, common name -> their name, with the harvested
  spec and operations each mapping was read from.
- [adopters.yml](adopters.yml) -- who exposes which concept, linked to their APIs.io page.
- [concepts.yml](concepts.yml) -- the only hand-written input: concepts, path segments and
  their qualifiers, aliases, reviewed exclusions, merged duplicates, and the decisions below.
- [census/](census) -- the cohort and the raw census the profile is built from.

## Decisions

These are calls, not measurements, recorded so they can be revisited as the method matures.

- A member covers loyalty accounts and profiles; a reward covers offers, perks, catalog items and redemptions.
- Points transactions and tiers are not published as concepts; they are recorded for the next re-measure.
- A referral covers advocates and referral codes.
- Gift cards are not a cohort tag: they are a stored-value payment instrument, not loyalty.
- Duplicates merged: Impact.

## Rebuild

```bash
../schema-commons/scripts/run.sh .
```

## License

Artifacts CC BY-NC-SA 4.0 ([LICENSE](LICENSE)); code Apache 2.0 ([LICENSE-CODE](LICENSE-CODE)).
