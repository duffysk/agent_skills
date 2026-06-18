---
name: bikepacking-route-planner
description: >-
  Plan multi-day European river/rail bikepacking routes for a fixed group of
  6 fit road cyclists riding loaded panniers. USE FOR: proposing or vetting a
  cycle tour, building a day-by-day stage plan with stage and total distances,
  producing an elevation profile for the whole route and for each stage,
  providing downloadable GPX tracks for the whole route and each stage,
  checking that stages end near bookable accommodation, validating that the
  start and finish are reachable by train, estimating realistic daily
  distances, suggesting sightseeing and natural/historical points of interest
  along the way, comparing candidate routes (e.g. Main-Radweg vs Drauradweg),
  self-verifying the plan with an LLM-as-judge pass, or sanity-checking route
  length and elevation claims. DO NOT USE FOR: single-day rides, mountain-bike
  / gravel technical routing, or trips where lodging is camping/self-supported.
---

# Bikepacking Route Planner

A skill for planning scenic, low-traffic, multi-day European cycle tours for a
specific group. It encodes the group's hard constraints so every proposed route
is realistic and immediately actionable.

## The group (fixed assumptions)

- **Party size:** 6 adult cyclists riding together as one group.
- **Bikes:** loaded with panniers / bikepacking bags (touring weight, not racing light).
- **Fitness:** strong, experienced road cyclists.
- **Comfortable daily distance:** **100–120 km/day on flat terrain.**
  - Treat 100–120 km as the *flat* comfort range, not the maximum.
  - Reduce the daily target when a stage has meaningful climbing, rough
    surface, headwind exposure, or many sightseeing stops.
- **Lodging:** indoor only — guesthouses / pensions / private rooms booked via
  Airbnb / Booking.com. **No camping, no self-support.**
- **Home base / travel:** the group travels by train. **Prague is the default**
  departure and return city, but always confirm the actual departure station and
  the required return station (see "Intake questions") — they may differ, and the
  total travel-day length depends on them.

## Prior routes already done (don't re-propose; use as the taste benchmark)

- Donauradweg — Passau → Bratislava
- Elberadweg — Magdeburg → Prague
- Innradweg — St. Moritz → Passau

These define the desired character: well-signed **river cycle paths**, mostly
flat, dense accommodation, scenic but **not overcrowded**.

## Hard constraints (a route MUST satisfy all of these)

1. **Rail-reachable start.** The route's starting town must be reachable by
   train from the **departure city** (default Prague) without an excessively
   long journey. Prefer comfortable same-day connections over multi-leg,
   all-day transfers.
2. **Rail-reachable finish.** The end town must have a train connection that
   gets the group (and bikes) back to the **return city** (default Prague).
3. **Bike capacity on trains.** Verify the relevant operators (ČD / DB / ÖBB /
   SŽ etc.) allow bikes on the chosen connections, and that there is capacity
   for **6 bikes**. Bike spaces are limited (often only 5–8 per train) and
   usually require **reservation** — flag this explicitly and recommend booking
   as soon as reservations open (often ~6 months ahead).
4. **Stages end where you can sleep.** Every stage must finish in (or within a
   short, easy ride of) a town/village that plausibly has bookable indoor
   lodging for 6 people. Never end a stage in the middle of nowhere.
5. **Refreshment stops mid-stage.** Each stage should pass through towns or
   villages spaced so the group can stop for food/coffee/water roughly every
   25–40 km. Avoid long empty stretches with no services.
6. **Scenic and low-traffic.** Favour dedicated, signed cycle paths along
   rivers/lakes/valleys over road routes. Avoid busy roads and overcrowded
   tourist corridors where possible.

## Soft preferences (optimise for these once hard constraints are met)

- Net-downhill / flat profile (let the river do the work; west→east or
  upstream→downstream as appropriate).
- A mix of nature and characterful towns (old towns, wine regions, castles).
- A satisfying total length that fills the available days at ~100 km/day
  without forcing filler or brutal stages.
- A memorable highlight (a gorge, a famous old town, an alpine descent).

## Planning procedure

0. **Intake questions (ask up front before proposing routes).** Confirm the
   travel bookends, because they drive both the rail feasibility and how much
   riding time is lost to transit:
   - **"Which station/city will you depart from by train?"** (default Prague —
     confirm, don't assume.)
   - **"Which station/city do you need to return to?"** (may differ from the
     departure city, e.g. leaving from a holiday base but going home elsewhere.)
   - **"How many total days do you have, and how many of those can be riding
     days vs travel days?"**
   Use the answers to size travel days: estimate the rail time **departure
   city → route start** and **route finish → return city**. If either transfer
   is long (e.g. >6–7 h or arriving late), reserve a **dedicated travel day** (no
   or only a short ride) and subtract it from the riding budget. Account for both
   ends: a long outbound *and* a long return can cost two riding days. State the
   resulting riding-days count before building stages, and prefer routes whose
   start/finish minimise total transit time from/to the given cities.
1. **Clarify trip length.** Using the intake answers, compute riding days =
   total days − travel days. Riding days × ~100 km gives the target distance.
2. **Shortlist candidate routes.** Propose 2–4 named, signed long-distance
   routes that fit the taste benchmark and are not already done. State for each:
   approx total length, character, and rough rail time **from the departure city
   to the start and from the finish back to the return city** (not just Prague).
3. **Verify distances from authoritative sources — do NOT trust round numbers.**
   - River cycle paths follow meanders and are **longer** than the
     point-to-point or shortest-cycle-routing distance. Google Maps cycling
     directions often take shortcuts off the river and **understate** the
     signed-route length while **overstating** climbing.
   - Conversely, AI/search summaries in this project have repeatedly
     **overstated** segment kilometres — always cross-check.
   - Prefer primary sources: the official route website (km per town),
     **bikeline** guidebooks, **komoot**, or **outdooractive** elevation/length.
   - When unsure, give a range and label the source and its confidence.
4. **Build the day-by-day stage plan.** For each stage list:
   - Start town → end town, stage distance (km), and elevation summary
     (ascent +m / descent −m, min/max altitude).
   - A per-stage elevation profile (ASCII sparkline is acceptable in text
     output; reference an interactive komoot/outdooractive profile for detail).
   - End town's accommodation availability (note if booking is tight).
   - 1–3 suggested refreshment/sightseeing stops along the way.
   - Natural and historical points of interest on or near the stage
     (old towns, castles, gorges, lakes, vineyards, monasteries, viewpoints).
5. **Build the whole-route elevation profile.** Produce an overall profile
   across all stages (start altitude → finish altitude, total ascent/descent,
   and where the steepest sections fall). Note net up/downhill and recommend
   the riding direction that maximises descent.
6. **Provide downloadable GPX tracks.** Supply a link to a GPX/GPS track for
   the full route and, where possible, for each individual stage, so the group
   can load them onto a GPS head unit or phone app.
   - Prefer official route GPX downloads (e.g. the route's own website such as
     drauradweg.com / mainradweg.com, or the regional tourism portal).
   - Otherwise link a reputable platform track: **komoot**, **outdooractive**,
     **bikeline/GPSies**, **Bikemap**, or **GPX-Tour archives**; komoot lets
     you export per-stage GPX and split a tour into day stages.
   - Give one master GPX for the whole route plus one GPX per stage (split at
     the chosen overnight towns). If a verified per-stage file isn't available,
     say so and point to where the group can split the master track themselves.
   - Only link sources you can actually cite; never invent a GPX URL. If no
     reliable link is found, state that clearly and suggest how to generate one
     (e.g. plot the stage in komoot and export GPX).
7. **Validate the rail bookends.** Confirm departure-city → start and finish →
   return-city train connections, journey times, the resulting travel-day
   count, and the **6-bike reservation** requirement.
8. **Balance the stages.** Keep stages within the daily comfort range, front-
   load or back-load lighter days around long travel days, and leave slack for
   sightseeing in the marquee towns.
9. **Self-verify with an LLM-as-judge pass (mandatory).** Before presenting the
   plan, critique it against the rubric below and fix anything that fails. See
   "LLM-as-judge verification".
10. **Output.** Present the full plan per "Output format", then the judge
    verdict. Offer to adjust length (start higher upstream, extend onto a
    connecting route, or add rest/short days).

## LLM-as-judge verification

After drafting the plan, run a structured self-review *as if you were an
independent expert reviewer*. Score each criterion Pass / Warn / Fail with a
one-line justification, then revise the plan to clear every Fail (and ideally
every Warn) before presenting it. Always show the resulting scorecard to the
user for transparency.

Rubric (each criterion 0–5, plus a verdict):

1. **Rail-reachable start** from the departure city (reasonable journey, bikes
   allowed) and travel-day length accounted for.
2. **Rail-reachable finish** back to the return city (bikes allowed) and travel-
   day length accounted for.
3. **6-bike capacity / reservation** explicitly checked and flagged.
4. **Daily distances** within the 100–120 km flat comfort range, reduced
   appropriately for climbing/terrain; no brutal or filler stages.
5. **Every stage ends near bookable indoor lodging** for 6 people.
6. **Refreshment spacing** — services roughly every 25–40 km, no long voids.
7. **Scenic & low-traffic** character; overcrowded sections flagged/avoided.
8. **Distance figures verified against the OFFICIAL route website** (or another
   authoritative primary source), not a single search-summary number.
   - For every named long-distance route, locate its official site (e.g.
     **mainradweg.com**, **drauradweg.com**, **moselradweg.de**, **eurovelo.com**,
     the regional tourism/“Radweg” portal) — most European cycle routes publish
     a per-stage / per-town kilometre table.
   - Confirm the **total length** and **each stage length** against that table;
     they must not **drift** from the official figures or be invented. If a stage
     is split differently from the official stages, the summed sub-distances must
     still reconcile with the official town-to-town kilometres.
   - Any number that cannot be tied to a primary source must be **explicitly
     labelled an estimate**, with the basis stated. A plan with unsourced or
     drifting stage distances cannot score above 3/5 here.
9. **Elevation profile present** for the whole route and each stage, with
   direction recommendation.
10. **Sightseeing / POI coverage** — each stage has at least one natural or
    historical highlight.
11. **GPX availability** — a master GPX link is provided, and per-stage GPX
    links (or a clear note on how to obtain/split them); no invented URLs.
12. **Not a previously-ridden route** (Donau Passau–Bratislava, Elbe
    Magdeburg–Prague, Inn St. Moritz–Passau).

Report a final verdict: **Approved**, **Approved with caveats**, or
**Needs revision** (with the specific fixes required). If any hard-constraint
criterion (1–6) Fails, the verdict cannot be "Approved".

## Output format

Deliver a plan containing, in order:

1. **Summary line** — route name, total km, number of days, rough km/day, and
   net elevation (e.g. "−900 m net, downhill-favoured west→east").
2. **Rail plan** — departure city → start and finish → return city, journey
   times, travel-day count, with the 6-bike reservation warning.
3. **Whole-route elevation profile** — an ASCII profile plus total ascent /
   descent and where the steep sections are; recommended riding direction.
4. **Stage table** — | Day | From → To | km | Ascent/Descent | Overnight town |
   Refreshment stops | Sightseeing / POI | GPX |.
5. **GPX downloads** — a master GPX link for the whole route plus a per-stage
   GPX link (or a note on how to split the master track if per-stage isn't
   available).
6. **Per-stage detail** — for each stage, a short paragraph or mini-profile
   with its elevation sparkline and the natural/historical highlights.
7. **Highlights & caveats** — scenery payoff, crowded sections to avoid,
   seasonal weather notes, and which distances/elevations are estimated vs
   verified.
8. **LLM-as-judge scorecard** — the rubric scores and final verdict.

## Deliver as a Markdown file

Write the full plan to a Markdown (`.md`) file, not just inline chat text.

- **File per route.** Create one `.md` file per planned route. Name it
  `<route-slug>-plan.md` (e.g. `drauradweg-plan.md`, `mainradweg-plan.md`).
- **Location.** Save into the session `files/` folder by default, or a
  user-specified directory if given. Tell the user the exact path written.
- **Self-contained.** The file must contain every "Output format" section
  above (summary, rail plan, whole-route elevation profile, stage table,
  GPX downloads, per-stage detail, highlights & caveats, judge scorecard) so it
  can be read on its own without the chat.
- **Valid Markdown.** Use real Markdown: a top-level `#` title, `##` section
  headings, GitHub-style tables for the stage table, fenced code blocks for the
  ASCII elevation profiles, and proper `[text](url)` links for GPX/booking/rail.
- **Multiple routes.** When asked for several routes, write one file each, then
  give a short inline summary plus the list of file paths.
- After writing, also surface the judge verdict inline so the user sees it
  without opening the file.

## Pitfalls to avoid

- Don't quote a single confident kilometre figure from a search summary;
  cross-check and prefer a sourced range.
- Don't confuse "full official route from the source springs" length with the
  practical length from the town where the group will actually start (e.g.
  Main-Radweg is ~600 km from its springs but ~390 km Bamberg→Mainz).
- Don't end a stage at a distance that has no realistic lodging just to hit a
  round number — move the overnight to the nearest viable town.
- Don't ignore train bike capacity; 6 bikes is the binding limit, not the seats.
- Don't re-propose routes the group has already ridden.
