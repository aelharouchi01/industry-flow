# Rebuild notes

The artifact was rebuilt from `README.md` and `countries.md` rather than copied.
Two things the handover listed as unfinished are now done: layer 05 holds routes
instead of bodies in every country, and the United States is built.

Still one self-contained HTML file with no dependencies. It opens by double
click and can be emailed.

## What changed against the handover build

**Layer 05 is now routes, not bodies.** New node kind `option`, allowed at layer
05 only. The card carries the route name and the line under it names the body
that owns the route. Marked with a sage rule along the top, which is the one
palette colour the old build defined and never used.

**The United States is built.** Six layers, two lanes from layer 03, 19 boxes.

**Empty layers can now be drawn.** New `absent` field on a country renders the
layer with its label and a dashed strip saying why nothing is there. The old
build skipped empty layers entirely, so an absence could not be seen, which
contradicted the note in the README that an empty layer is often the most
interesting thing on the page. The United States layer 06 uses it.

**Disputed outcomes can be shown.** New `dispute` field renders a two column
block under the legend. Used once, for the United States, because the research
insists both readings of the record are true.

## Bugs found in the old build and fixed

These were all live in the handover artifact. The first three were invisible
because nothing checked for them.

1. **A flow that skipped a layer crossed the boxes in between.** It ran down the
   left channel and then turned in at the target's own height, so it cut through
   every box standing between the channel and the target. It now crosses in the
   empty gap above the target row. This mattered immediately: with layer 05
   filled on both sides, Brazil and the Emirates both had flows that would have
   run straight through a card.
2. **A flow inside one row ran through the box it pointed at.** Three of these
   exist in the data, `cabinet` to `fec` in Singapore and two in the Emirates.
   The vertical gap between the two boxes is negative, so the connector was
   drawn back through the row. Lateral flows now run edge to edge, and dip below
   the row if another box stands between them.
3. **The fan stagger landed on the row below when a parent had four children.**
   The spread was `0.34 + 0.22 * index`, which reaches exactly 1.0 at the fourth
   child and puts the horizontal on the target row. It now spreads across a fixed
   fraction of the gap whatever the number of children.
4. **Only one arrowhead was drawn per board.** Every flow was concatenated into a
   single `path`, and `marker-end` paints at the last vertex of the path, not of
   each subpath. Each flow is now its own `path` and carries its own arrowhead.

## The gap the old validators could not catch, now closed

The README flagged that neither python script checked whether a connector crosses
a text label, and that it had to be caught by eye. The label placer now samples
every drawn line and tests candidate positions against the lines as well as the
boxes, scoring each and taking the best. It searches along the curve, above and
below, and to either side, because a label on a vertical curve has the same x at
every point and can only escape a vertical connector sideways.

Validation is built into the file. Open it with `?check` for a panel, or call
`check()` in the console. It reports: arrows that miss a box, upward flows,
routes outside layer 05, bodies left at layer 05, layers marked empty that are
not, text overflowing a card, overlapping cards, and connectors crossing a card
or a label.

Verified clean for all four countries at 1024, 1220 and 1400 pixels wide, with
every node selected in turn, and with every detail panel populated.

## Judgement calls, each of which you may want to reverse

**Brazil.** The four routes are placed by owner, so the government lane holds two
of them. The old finding that the government column of layer 05 is empty no
longer holds literally, because lending against a mission and co-funding company
research are government owned. The truer statement, and the one the cards now
make, is that the only route on the row that creates a skill is owned by
industry, and the government routes close a money gap. The third government
column is left empty.

**Singapore.** The union institute moved from layer 05 to layer 04. Under the
route model it would otherwise have disappeared as a box, taking the union
officer relationship with it, which is the sharpest finding in that map. It
delivers placement and retraining, so layer 04 is defensible. It has no inbound
flow, exactly as in the old build, and its detail says why.

**Singapore.** The talent pass route is left out. `sources.md` records it as
unverified and kept out of the artifact, so it stays out. That is why Singapore
has four routes and the Emirates has five.

**United States.** Buying a stake and buying from allies are one card, not two.
The finance corporation that runs the second is not a body anywhere at layer 04,
so a separate card would have needed an invented connector. Both are described
in that card's detail. Restoring the fifth route means adding the corporation at
layer 04 first.

**United States.** The workforce card is drawn detached rather than as a route,
because nothing in the map above produces it. That is the finding the research
supports: no national skills system, and no path from direction into training.

**United States.** Layer 05 splits across the two lanes, which puts attracting a
firm on the defensive side. The onshoring agreement, tariff relief traded for a
factory, is exactly that move, so the flow from onshoring agreements into it is
the honest one. The forward system also attracts firms, and the card says so.

## One claim in the research that does not hold

`countries.md` says of the Emirates that the ministry's relationship arrow
pointing upward is the only upward arrow in any country map. Brazil already had
one: the federations own the confederation, layer 03 pointing up to layer 02.
Nothing in the artifact ever made the uniqueness claim, so nothing needed
changing, but do not repeat it in a deck.

## Still unresolved, carried forward from the research

- The status of the United States tariffs reimposed under the 150 day statute.
  Flagged on the President card.
- Whether the investment accelerator office still exists under that name.
  Flagged on its card.
- Whether the equity portfolio has grown past 37 deals, and whether any oversight
  has since been legislated.
- Real names and current terms of the United States workforce programmes, which
  are described generically on purpose.
- The Emirates local content mechanics and the strategy launch month, both still
  out of the artifact per `sources.md`.

Singapore and the United States are both mid transition. Re-check both before
client use. Brazil and the Emirates are more stable.

## As built

Generated from the running artifact, so it cannot drift from what renders.
Regenerate rather than editing by hand.

## Brazil

Lanes: Government (3), Industry (2), from layer 1

| id | layer | kind | name | role or owner |
| --- | --- | --- | --- | --- |
| `sci` | 1 | detached | Science ministry | Foresight that connects to nothing |
| `obs` | 1 | body | Industry Observatory | Projects the skills gap ahead |
| `cndi` | 2 | body | CNDI | Government council, sets missions |
| `cni` | 2 | body | CNI | Industry own confederation |
| `credit` | 3 | mechanism | Missions unlock credit | The default route |
| `prog` | 3 | mechanism | Custom programmes | Built one at a time |
| `mei` | 3 | body | MEI | Platform of chief executives |
| `feds` | 3 | body | The federations | Political force, not delivery |
| `bndes` | 4 | body | BNDES | The development bank |
| `finep` | 4 | body | FINEP | The innovation agency |
| `embr` | 4 | body | EMBRAPII | Research agency, co-funds work |
| `cofund` | 5 | option | Co-fund company research | Applied research agency |
| `loan` | 5 | option | Lend against a mission | Development bank |
| `train` | 5 | option | Train through the levy | Industry institutes |
| `newinst` | 5 | option | Build a new institute | Industry lobbies for it |

Flows: `obs` to `cni`, `cndi` to `credit`, `cndi` to `prog`, `cni` to `mei`, `cni` to `feds`, `credit` to `bndes`, `credit` to `finep`, `prog` to `bndes`, `prog` to `finep`, `prog` to `embr`, `bndes` to `loan`, `embr` to `cofund`, `mei` to `train`, `mei` to `newinst`

Relationships: `cni` to `cndi` "holds a voting seat", `feds` to `cni` "they own it", `cni` to `embr` "lobbied it into being", `mei` to `finep` "unblocked its fund", `bndes` to `train` "public money spent inside", `finep` to `train` "public money spent inside", `embr` to `train` "public money spent inside"

Counts: 15 boxes, 4 of them capability routes, 14 flows, 7 relationships.

## Singapore

Lanes: One chain, all parties inside it (4), from layer 1

| id | layer | kind | name | role or owner |
| --- | --- | --- | --- | --- |
| `csf` | 1 | body | Strategic Futures centre | Permanent, never closes |
| `review` | 1 | tripartite | Economic review | Convened, reports, closes |
| `cabinet` | 2 | body | Cabinet | Funds it in the Budget |
| `fec` | 2 | tripartite | Future Economy Council | Standing body, owns it |
| `clusters` | 3 | tripartite | The seven clusters | Co-chaired by both sides |
| `leads` | 3 | tripartite | Sector lead agencies | One for each of 23 sectors |
| `edb` | 4 | tripartite | Investment board | Attracts investment |
| `esg` | 4 | tripartite | Enterprise agency | Grows local firms |
| `astar` | 4 | body | Research agency | Does the science |
| `e2i` | 4 | body | Union institute | Places and retrains |
| `retrain` | 5 | option | Retrain into a new role | Skills and jobs agencies |
| `redesign` | 5 | option | Redesign the job | Jobs agency |
| `facility` | 5 | option | Use a shared facility | Enterprise and research agencies |
| `joint` | 5 | option | Open a joint lab | Research agency |
| `jtc` | 6 | body | Industrial land agency | Holds most of the land |

Flows: `csf` to `cabinet`, `review` to `cabinet`, `cabinet` to `fec`, `fec` to `clusters`, `fec` to `leads`, `leads` to `edb`, `leads` to `esg`, `leads` to `astar`, `leads` to `retrain`, `leads` to `redesign`, `esg` to `facility`, `astar` to `facility`, `astar` to `joint`, `facility` to `jtc`

Relationships: `e2i` to `edb` "a union officer sits here", `e2i` to `esg` "a union officer sits here", `retrain` to `leads` "the framework is part of the plan", `review` to `fec` "sets the next direction"

Counts: 15 boxes, 4 of them capability routes, 14 flows, 4 relationships.

## United Arab Emirates

Lanes: Sectors that already exist (3), Sectors that barely exist yet (2), from layer 03

| id | layer | kind | name | role or owner |
| --- | --- | --- | --- | --- |
| `pmo` | 1 | body | Prime Minister Office | Holds the long term vision |
| `unido` | 1 | body | UN industrial agency | Ranks countries on industry |
| `apex` | 2 | body | President and Prime Minister | Choose the national target |
| `adec` | 2 | body | Abu Dhabi Executive Council | Chooses its own targets |
| `cabinet` | 3 | body | Federal Cabinet | Makes it law |
| `ministry` | 3 | body | Industry ministry | Designs the instruments |
| `council` | 3 | body | Industry Development Council | Gets the emirates to agree |
| `adrc` | 3 | body | Abu Dhabi research council | Picks the technologies |
| `bank` | 4 | body | Federal development bank | Lends so it gets built |
| `buyers` | 4 | body | Government-owned buyers | Promise to buy the output |
| `funds` | 4 | body | Abu Dhabi sovereign funds | Own the capability |
| `place` | 5 | option | Place and train Emiratis | Jobs programme |
| `attract` | 5 | option | Attract the firm that has it | Industry ministry and zones |
| `specialists` | 5 | option | Bring in specialists | Federal government |
| `research` | 5 | option | Fund a research institute | Abu Dhabi research council |
| `buyco` | 5 | option | Buy the company | Sovereign funds |
| `dept` | 6 | shared | Abu Dhabi economic department | Issues the licence |
| `zones` | 6 | shared | Industrial zones | Supply land and utilities |

Flows: `pmo` to `apex`, `unido` to `apex`, `apex` to `cabinet`, `adec` to `adrc`, `cabinet` to `ministry`, `ministry` to `council`, `ministry` to `bank`, `ministry` to `buyers`, `adrc` to `funds`, `buyers` to `place`, `buyers` to `attract`, `cabinet` to `specialists`, `adrc` to `research`, `funds` to `buyco`, `place` to `dept`, `research` to `zones`

Relationships: `ministry` to `apex` "wrote the target", `buyers` to `ministry` "supply the forecasts", `council` to `dept` "gets them to agree", `adec` to `apex` "aligns, not subordinate", `ministry` to `adrc` "names the same sectors", `specialists` to `research` "stands in for training"

Counts: 18 boxes, 5 of them capability routes, 16 flows, 6 relationships.

## United States

Lanes: Getting ahead of new technology (3), Defending industries already lost (2), from layer 03

| id | layer | kind | name | role or owner |
| --- | --- | --- | --- | --- |
| `crs` | 1 | body | Congress research staff | Answers and anticipates |
| `commissions` | 1 | body | Expert commissions | Study, report, dissolve |
| `ostp` | 1 | body | White House science office | Names the priority technologies |
| `congress` | 2 | body | Lawmakers | Slow, durable, hold the money |
| `president` | 2 | body | The President | Fast, reversible, sets prices |
| `courts` | 2 | detached | The courts | Can cancel, cannot create |
| `law` | 3 | mechanism | A law with money in it | Names the agency and the sum |
| `accelerator` | 3 | body | Investment accelerator office | Clears the obstacles |
| `investigation` | 3 | mechanism | Trade department investigation | Asks if imports threaten security |
| `commerce` | 4 | body | Trade department | Grants, and now equity |
| `energy` | 4 | body | Energy department | Lends, and holds the labs |
| `defense` | 4 | body | Defence department | Buys, and signs long contracts |
| `tariff` | 4 | mechanism | The tariff itself | A price, not a programme |
| `deal` | 4 | mechanism | Onshoring agreements | Company by company |
| `research` | 5 | option | Fund the research | Research agencies and national laboratories |
| `stake` | 5 | option | Buy a stake | Trade department and the finance corporation |
| `demand` | 5 | option | Guarantee the demand | Defence department |
| `attract` | 5 | option | Attract the firm that has it | Trade department and the states |
| `workforce` | 5 | detached | Train the workforce | No national system |

Layer 06 is deliberately empty, and says so on the page: there is no national land agency and no federal licence to open a factory, so nothing corresponds to an emirate economic department or Singapore land agency. Land and permitting sit with states and localities.

Flows: `crs` to `congress`, `commissions` to `congress`, `ostp` to `president`, `congress` to `law`, `president` to `accelerator`, `president` to `investigation`, `law` to `commerce`, `law` to `energy`, `law` to `defense`, `accelerator` to `commerce`, `investigation` to `tariff`, `investigation` to `deal`, `energy` to `research`, `commerce` to `stake`, `defense` to `demand`, `deal` to `attract`

Relationships: `president` to `congress` "can repurpose the money", `courts` to `president` "can cancel, cannot create", `tariff` to `deal` "relief traded for a factory"

Counts: 19 boxes, 4 of them capability routes, 16 flows, 3 relationships.
