# Country specs

All four country maps in one place. Brazil, Singapore and the UAE are built and
working in the artifact. The United States is researched but not built.

The node, flow and relationship tables for the three built countries were generated
from the artifact source, so they cannot drift from what actually renders. If you
change the build, regenerate them rather than editing by hand.

See `README.md` for the six-layer frame, the design principles and the data model,
and `sources.md` for source tiers and unverified claims.

## Contents

- [Brazil](#brazil--spec-built-and-working) &mdash; built
- [Singapore](#singapore--spec-built-and-working) &mdash; built
- [United Arab Emirates](#united-arab-emirates--spec-built-and-working) &mdash; built
- [United States](#united-states--spec-not-yet-built) &mdash; not built

---

## Brazil — spec, BUILT AND WORKING

Two complete systems run side by side, each with its own money. The government side has no capability-building body of its own and relies on industry’s.

### Lanes

Government (3 cols) and Industry (2 cols), lanes from layer 1.

### Nodes as built

| id | layer | name |
| --- | --- | --- |
| `sci` | 1 | Science ministry |
| `obs` | 1 | Industry Observatory |
| `cndi` | 2 | CNDI |
| `cni` | 2 | CNI |
| `credit` | 3 | Missions unlock credit |
| `prog` | 3 | Custom programmes |
| `mei` | 3 | MEI |
| `feds` | 3 | The federations |
| `bndes` | 4 | BNDES |
| `finep` | 4 | FINEP |
| `embr` | 4 | EMBRAPII |
| `senai` | 5 | SENAI, SESI and IEL |

### Flows as built

- `obs` to `cni`
- `cndi` to `credit`
- `cndi` to `prog`
- `cni` to `mei`
- `cni` to `feds`
- `credit` to `bndes`
- `credit` to `finep`
- `prog` to `bndes`
- `prog` to `finep`
- `prog` to `embr`
- `mei` to `senai`

### Relationships, shown on selection

- `cni` to `cndi` — "holds a voting seat"
- `feds` to `cni` — "they own it"
- `cni` to `embr` — "lobbied it into being"
- `mei` to `finep` — "unblocked its fund"
- `bndes` to `senai` — "public money spent inside"
- `finep` to `senai` — "public money spent inside"
- `embr` to `senai` — "public money spent inside"

### Layer 05 should become these options

Replace the bodies currently at layer 05. Owner named in the role line.

#### Train through the levy

**Owner:** Industry institutes

A compulsory charge on payroll, 1.5% for welfare and 1.0% for training. Needs no annual budget approval, so it does not stop when a government changes. It survived the 2017 reform that made federation dues voluntary because it rests on a different legal basis. 3.3 million training places a year.

#### Co-fund company research

**Owner:** Applied research agency

A ministry contract plus money the company puts in. Industry lobbied the agency into existence in 2013 and holds board seats, so a public agency is partly steered by the private side.

#### Build a new institute

**Owner:** Industry lobbies for it

When a gap is too large for industry alone, it lobbies government for a new instrument. This is how the applied research agency came to exist.

#### Lend against a mission

**Owner:** Development bank

R$653 billion approved across 428,000 projects in two years. Roughly half its resources come from a national workers support fund.

### Findings this map should make visible

- The government column of layer 05 is empty. That is accurate and it is the sharpest thing on the page.
- The only forward-looking body in the chain is owned by industry, not government. Government foresight exists at the science ministry and planning but holds no seat on the industrial council, so it connects to nothing. It is drawn detached.
- The political arm and the delivery arm were split by law in 2017. Federation dues became voluntary; the payroll training levy stayed compulsory. The lobbying side was defunded and the execution side was not.
- Industry’s direction body is older than most government agencies it deals with, founded 1938 and never interrupted, against a government council created in 2004 that sat dormant for eight years.

---

## Singapore — spec, BUILT AND WORKING

One chain, no separate towers. Government, business and unions sit inside the same bodies. A sector plan is traced all the way down into named job roles and funded retraining.

### Lanes

One lane, four columns, no lane header.

### Nodes as built

| id | layer | name |
| --- | --- | --- |
| `csf` | 1 | Strategic Futures centre |
| `review` | 1 | Economic review |
| `cabinet` | 2 | Cabinet |
| `fec` | 2 | Future Economy Council |
| `clusters` | 3 | The seven clusters |
| `leads` | 3 | Sector lead agencies |
| `edb` | 4 | Investment board |
| `esg` | 4 | Enterprise agency |
| `astar` | 4 | Research agency |
| `ssg` | 5 | Skills agency |
| `wsg` | 5 | Jobs agency |
| `e2i` | 5 | Union institute |
| `shared` | 5 | Shared centres and labs |
| `jtc` | 6 | Industrial land agency |

### Flows as built

- `csf` to `cabinet`
- `review` to `cabinet`
- `cabinet` to `fec`
- `fec` to `clusters`
- `fec` to `leads`
- `leads` to `edb`
- `leads` to `esg`
- `leads` to `astar`
- `leads` to `ssg`
- `ssg` to `wsg`
- `esg` to `shared`
- `astar` to `shared`
- `shared` to `jtc`

### Relationships, shown on selection

- `e2i` to `edb` — "a union officer sits here"
- `ssg` to `leads` — "the framework is part of the plan"
- `review` to `fec` — "sets the next direction"

### Layer 05 should become these options

Replace the bodies currently at layer 05. Owner named in the role line.

#### Retrain into a new role

**Owner:** Skills and jobs agencies

A jobs transformation map per sector identifies growth jobs, meaning emerging roles with long-term progression. A skills framework then lists the career pathways, the skills and the actual courses across more than 130 job roles. A career conversion programme then reskills mid-career people into those roles with up to 90 per cent salary support.

#### Redesign the job

**Owner:** Jobs agency

From 2026 a workforce transformation package funds job redesign, pre-approved consultants, and training for human resource teams and line managers.

#### Use a shared facility

**Owner:** Enterprise and research agencies

Innovation centres hosted at the polytechnics and the national manufacturing institute, co-developing robotics, data science, artificial intelligence and additive manufacturing. A remanufacturing centre with a consortium of over 95 members across five industry pillars. A model factory where firms experiment before committing.

#### Open a joint lab

**Owner:** Research agency

A smart manufacturing joint lab set up in 2017 with an engine maker and an engine services firm deployed 18 technologies, delivered over 20 per cent productivity gains, engaged more than 200 local small firms and qualified eight as approved vendors. The agency also runs an operational and technology roadmap service that helps one company work out which capability it is missing.

#### Bring in specialists

**Owner:** Manpower ministry

UNVERIFIED. Work passes for global specialists exist but the current names, tiers and eligibility have not been checked. Verify before publishing.

### Findings this map should make visible

- The skills framework is not bolted on afterwards. It is an integral component of the sector roadmap, so the skills answer is derived from the sector plan rather than guessed at later. This is the tightest capability chain of the four countries.
- A union assistant secretary-general, who also runs the union employment institute, sits on the boards of both the investment board and the enterprise agency. A union officer formally seated on the body attracting global capital.
- Foresight is both continuous and episodic. A permanent unit in the Prime Minister’s Office never closes, and a major review is convened roughly every seven years and then dissolves.
- The Budget is the handoff. Nothing becomes real until it has a budget line and a named owner.
- Each of 23 sector roadmaps has exactly one lead agency. There is no super-agency running everything.

---

## United Arab Emirates — spec, BUILT AND WORKING

One target chosen for the whole country, then the tools divide by whether a sector already exists. Both routes still need land and a licence from an emirate.

### Lanes

Sectors that already exist (3 cols) and Sectors that barely exist yet (2 cols), lanes from layer 3.

### Nodes as built

| id | layer | name |
| --- | --- | --- |
| `pmo` | 1 | Prime Minister\u2019s Office |
| `unido` | 1 | UN industrial agency |
| `apex` | 2 | President and Prime Minister |
| `adec` | 2 | Abu Dhabi Executive Council |
| `cabinet` | 3 | Federal Cabinet |
| `ministry` | 3 | Industry ministry |
| `council` | 3 | Industry Development Council |
| `adrc` | 3 | Abu Dhabi research council |
| `bank` | 4 | Federal development bank |
| `buyers` | 4 | Government-owned buyers |
| `jobs` | 5 | Emirati jobs programme |
| `institute` | 5 | Abu Dhabi research institute |
| `funds` | 4 | Abu Dhabi sovereign funds |
| `dept` | 6 | Abu Dhabi economic department |
| `zones` | 6 | Industrial zones |

### Flows as built

- `pmo` to `apex`
- `unido` to `apex`
- `apex` to `cabinet`
- `adec` to `adrc`
- `cabinet` to `ministry`
- `ministry` to `council`
- `ministry` to `bank`
- `ministry` to `buyers`
- `adrc` to `funds`
- `adrc` to `institute`
- `buyers` to `jobs`
- `jobs` to `dept`
- `institute` to `zones`

### Relationships, shown on selection

- `ministry` to `apex` — "wrote the target"
- `buyers` to `ministry` — "supply the forecasts"
- `council` to `dept` — "gets them to agree"
- `adec` to `apex` — "aligns, not subordinate"
- `ministry` to `adrc` — "names the same sectors"

### Layer 05 should become these options

Replace the bodies currently at layer 05. Owner named in the role line.

#### Place and train Emiratis

**Owner:** Jobs programme

Because the employer already exists, a person is placed into a working factory and trained on the job or through short courses bought from providers. The programme funds and places rather than teaching. It owns no institutes, so it cannot create a skill nobody in the country already practises.

#### Fund a research institute

**Owner:** Abu Dhabi research council

For a sector nobody buys from yet there is no demand to publish and no tender to score, so somebody has to simply choose. The institute covers artificial intelligence, quantum, cryptography, robotics, advanced materials, propulsion and biotechnology. It rents access to foreign machines while learning, then builds its own.

#### Buy the company

**Owner:** Sovereign funds

Purchase rather than persuasion. Controlling shareholder of one of the world’s largest contract chipmakers, whose plants are in New York and Singapore. The country owns a semiconductor asset rather than a domestic semiconductor industry.

#### Attract the firm that has it

**Owner:** Industry ministry and zones

Capability arrives inside a foreign company, against a guaranteed purchase and land.

#### Bring in specialists

**Owner:** Federal government

Long-term visas for scientists and engineers. On the new-sector side this substitutes for training, because there is no employer to learn inside.

### Findings this map should make visible

- No independent body examined whether the target was the right number. The three inputs were the rulers’ own long-term vision, an external UN ranking, and the ministry that would be measured against it.
- The ministry wrote the strategy it now delivers. Its relationship arrow points upward, the only upward arrow in any country map.
- The intelligence apparatus was built after the target, from 2022, and feeds translation rather than direction. The registry became compulsory a year after the number existed.
- The sector list names both established and nascent sectors, but every federal instrument requires an existing purchase, so the federal toolkit cannot serve the nascent half.
- Abu Dhabi set its own target with its own money, most of the national figure, and describes its role as contributing rather than implementing. The link holds because the same ruling circle sits on both sides.
- The licence is the chokepoint. No federal body can issue one.

---

## United States — spec, NOT YET BUILT

Research is complete to roughly the same depth as the other three. Nothing has been
built into the artifact. Everything below is ready to become data.

### The one-line character

Direction is contested by design. Two bodies can create it and neither can overrule
the other, so support reaches companies in two forms with different lifespans: money
that lasts years but takes years to arrive, and prices that appear in months and can
vanish in months.

### Suggested `sub`

> No single body sets direction. Lawmakers create money that outlives an
> administration; the President sets tariffs that a court can cancel. Two systems run
> in parallel: one anticipates technologies that barely exist, the other defends
> industries already lost.

### Lanes

Recommend **two lanes from layer 03**, with layers 01 and 02 shared full width.

| Lane | Label | Cols |
| --- | --- | --- |
| `ahead` | Getting ahead of new technology | 3 |
| `behind` | Defending industries already lost | 2 |

Rationale: this is the genuine split, and it mirrors the UAE's existing/nascent cut
without copying it. The anticipatory system and the remedial system cover almost
entirely different sectors. The forward list contains advanced computing, artificial
intelligence, quantum and biotechnology. The tariff list contains steel, aluminium,
copper, timber, furniture, trucks and buses. The only overlap is semiconductors and
critical minerals, which is exactly what you would expect: the sector where the
forward system spotted the problem and the remedial system was later applied on top.

**Alternative lane cut, if the above feels forced:** Congress and the President as two
lanes running the whole depth. Rejected here because both lanes would then contain the
same delivery agencies, and because the interesting difference is what each system
*covers*, not who signs it.

### Layer 01 Foresight (shared, full width)

Congress has by far the most developed foresight apparatus of the four countries, and
almost none of it carries authority.

| id | name | role | notes for detail |
| --- | --- | --- | --- |
| `crs` | Congress research staff | Answers and anticipates | Nonpartisan shared staff serving committees and members, working solely at the direction of Congress. A separate audit office added a dedicated science and technology team in 2019 at Congress's direction, with engineers, chemists, biologists and physicists. Since 2019 it has issued almost 150 reports with more than 120 policy options, and in 2024 alone provided over 90 technical consultations. It does not only answer questions; it initiates some work by anticipating what members will need. |
| `commissions` | Expert commissions | Study, report, dissolve | Congress creates a temporary commission with a deadline, staffs it with industry, military and academic figures, then legislates from its report. **The transmission mechanism is the membership.** The biotechnology commission has twelve members including two House members and two senators. The legislators who receive the two-year briefing are the ones who write the bill. |
| `ostp` | White House science office | Names the priority technologies | Runs an interagency process producing the critical and emerging technologies list, updated at least every two years. The 2024 update drew on subject matter experts from 18 departments and agencies. **Note the direction of travel: the agencies tell the White House what matters, not the reverse.** The list explicitly does not change any regulatory regime; it is notice, not instruction. |

**The finding for this layer:** foresight is abundant and carries no power. A
recommendation must find a political sponsor to become anything. The semiconductor
recommendation found one. The same commission's recommendation for a White House
technology competitiveness council did not.

### Layer 02 Direction (shared, full width)

| id | name | role | notes for detail |
| --- | --- | --- | --- |
| `congress` | Lawmakers | Slow, durable, hold the money | Only body that can create money. The 2022 technology law made 52.7 billion dollars available for semiconductor manufacturing plus a 25 per cent investment tax credit. Money already appropriated survives a change of administration. |
| `president` | The President | Fast, reversible, sets prices | Uses powers granted decades ago. Section 232 of a 1962 trade act lets the President adjust imports where the trade department finds imports threaten national security. Those measures stay until the President declares the threat over, with no congressional involvement. |
| `courts` | The courts | Can cancel, cannot create | Mark as `kind:'detached'`. On 20 February 2026 the Supreme Court ruled 6 to 3 that emergency economic powers do not authorise tariffs, invalidating both the reciprocal tariffs from April 2025 and the fentanyl-related tariffs. Within hours the White House reimposed tariffs under a different 1974 statute allowing surcharges up to 15 per cent with no prior investigation, but expiring after 150 days unless Congress extends. **The strategy did not change. The legal foundation under it did.** |

**Relationship to draw on selection:** `president → congress`, labelled "can repurpose
the money". The chip grants were appropriated by Congress as grants and converted into
a roughly 10 per cent equity stake in a chipmaker. The senator who drafted the
foundation of that law said it never intended to allow the government to take a major
stake in any company.

### Layer 03 Translation

**Lane `ahead`:**

| id | name | role |
| --- | --- | --- |
| `law` | A law with money in it | Names the agency and the sum |
| `accelerator` | Investment accelerator office | Clears the obstacles |

The accelerator was created by executive order in March 2025 inside the trade
department to facilitate investments above one billion dollars by helping investors
navigate federal regulatory processes, reduce regulatory burden, facilitate research
collaborations with national laboratories, and work with all 50 state governments to
reduce barriers. It absorbed the chip programme office with a mandate to negotiate
better deals. **Note it clears obstacles rather than setting direction: no sector
list, no targets, no plan.**

**Lane `behind`:**

| id | name | role |
| --- | --- | --- |
| `investigation` | Trade department investigation | Asks if imports threaten security |

Can be started by an application from an interested party, a request from any
department head, or by the trade secretary alone. Report due within 270 days. **Any
company can trigger it**, which is a bottom-up route none of the other three countries
has. Sectors run through it since 2025: steel, aluminium and copper; automobiles and
parts; timber, lumber and wood; trucks, parts and buses; critical minerals;
semiconductors; pharmaceuticals. Further investigations opened into polysilicon,
unmanned aircraft and wind turbines.

### Layer 04 Delivery

**Lane `ahead`:** `commerce` trade department (grants and equity), `energy` energy
department (loans), `defense` defence department (buys directly, signs long contracts)

**Lane `behind`:** `tariff` the tariff itself (mark `kind:'mechanism'`), `deal`
company-specific onshoring agreements (`kind:'mechanism'`)

On the onshoring agreements: the trade department has published procedures under which
a pharmaceutical company can apply for a tariff adjustment in exchange for commitments
to move production to the US. Tariff relief traded for a factory.

**The genuinely new instrument, for the equity node's detail:** since January 2025 the
government has announced investments worth 27.6 billion dollars across 37 deals
involving direct ownership. The trade department leads with 24 announced deals
including a roughly 10 per cent stake in a chipmaker; the development finance
corporation has pledged six equity transactions in critical minerals, energy and
infrastructure. In July 2026 the trade department allocated funds to seven more
companies, with the standards institute stating the department will receive a minority
non-controlling equity stake in each as a condition of funding. The head of the
National Economic Council described it as "like a down payment on a sovereign wealth
fund, which many countries have."

Include both criticisms, from opposite directions. On process: the 2008 bank rescue
had a statutory special inspector general reporting quarterly to Congress, a
congressional oversight panel and standing audits; today's portfolio has none of that.
On authority: the senator who drafted the chip law's foundation says it never intended
this. On public opinion: one survey found 19 per cent agreed the government should own
a portion of US companies, 49 per cent disapproved, 32 per cent undecided.

### Layer 05 Capability — options, not bodies

This is where the layer 05 exception applies. Five routes, each with its owner named.

| Option | Owner | Detail |
| --- | --- | --- |
| Attract the firm that has it | Trade department and states | Capability arrives inside a foreign company. Fabs built by foreign chipmakers. |
| Fund the research | Research agencies and national laboratories | Slow. Decades. This is where the technologies on the forward list actually came from. |
| Buy a stake | Trade department, development finance corporation | The state becomes an owner rather than a customer. |
| Buy from allies | Development finance corporation | Minerals agreements with partner countries. |
| Guarantee the demand | Defence department | See the worked example below. |

**Worked example for the guarantee option, the strongest single case in the US map.**
A rare earth magnet package announced in 2025 combined: 400 million dollars of
preferred stock making the Pentagon the largest shareholder, with an option for 350
million more; a 150 million dollar unsecured loan at the ten-year Treasury yield plus
one per cent, repayable within twelve years; a ten-year guaranteed floor price of 110
dollars per kilogram for the relevant oxide, roughly double the market price at the
time, with the government capturing 30 per cent of upside above the benchmark; a
ten-year commitment to buy 100 per cent of the output of a new magnet plant, with a
guaranteed minimum of 140 million dollars annual earnings and profits split above 170
million; a condition that the company not renew its offtake with a Chinese-linked
subsidiary; and recourse allowing the department to terminate, demand early repayment
and pursue damages. Two banks then committed up to one billion dollars of construction
financing.

**The point to make:** the government did not fund the factory, it made the factory
bankable. Each instrument removes a different reason it would not get built. Remove one
and the financing probably fails.

**And the fragility, which is the honest counterweight:** the defence department's
2026 request for the relevant fund was only 266 million dollars, less than the annual
price floor payments would cost at then-current prices. A ten-year commitment rests on
Congress choosing to appropriate every year for a decade.

### Layer 06 Ground

**Probably leave empty.** There is no federal chokepoint equivalent to an emirate
licence or a single national land agency. Land and permitting sit with states and
localities, which layer on their own incentive packages often comparable in size to
the federal offer. If you want the row, one node: `states` States and localities,
"Land, permits and their own money".

### The four-stage money pipeline

This belongs in the detail of the `congress` and `law` nodes and is the single most
useful thing to explain about the US system.

Authorised, then appropriated, then obligated, then disbursed. Durability increases at
each stage.

The chip half of the 2022 law went through all four: 52.7 billion dollars directly
appropriated. The science half mostly stopped at stage one: around 200 billion dollars
remains allocated rather than appropriated. The three research agencies were authorised
26.8 billion for one year and received somewhat above 19 billion, a shortfall of more
than 28 per cent. The research foundation was authorised 81 billion over five years to
double the agency; it did not happen. The manufacturing programme received 51 million
in one year, about half what was authorised.

**A law creates durable money, not durable intent.** Whoever runs the agency later
decides what the money buys. Which is why sophisticated actors prefer tax credits: no
annual appropriation, no agency discretion, no negotiation. The chip law's 25 per cent
credit applies to any eligible facility beginning construction by 31 December 2026.

### Outcomes, to be presented as genuinely disputed

Both readings are true and the artifact should say so.

**Supportive:** factory activity expanded in January 2026 for the first time in over
two years; manufacturing productivity improved steadily through 2025 reversing a
decline; shipments of core capital goods reached a record, peaking near 78.7 billion
dollars; in 2025 the US surpassed Japan in crude steel production for the first time
since 1999.

**Sceptical:** manufacturing employment declined about 1 per cent since the April 2025
tariffs; factory construction spending has declined since 2024, driven by a 44 per cent
slowdown in electronics and semiconductor fab spending since the mid-2024 peak;
excluding electronics, construction spending rose 5.6 per cent, lower than a boom would
imply. Roughly 1.595 trillion dollars in factory commitments coexists with factory jobs
down 82,000.

**The timing argument, which is the strongest defence:** employment lags investment by
years. A semiconductor fab runs a nine-year arc from announcement to full employment
and pharmaceutical validation takes five to seven years, so a 2025 pledge shows up in
employment data around 2030. **The counter-argument is automation:** output can keep
rising without proportional hiring.

### Workforce, the weakest layer

No national skills system. The labour department launched an apprenticeship incentive
fund in December 2025 supporting a talent strategy and several executive orders on
expanding registered apprenticeships. Firm-level help comes through 51 manufacturing
extension centres providing manufacturing, business and process improvement services,
which is the closest US analogue to a factory assessment programme and much older than
the UAE's.

The scale of the problem dwarfs those instruments, and note who produced the forecast:
an industry association, not a government body. It projects the industry needing 3.8
million additional workers by 2033 with 1.9 million potentially unfilled, of which 2.8
million of the need comes from retirements alone. Replacing the workforce, not
expanding it.

### Research still needed before building

- Current status of the tariffs reimposed under the 150-day statute. They were due to
  expire absent congressional extension. **Check what happened.**
- Whether the equity portfolio has grown beyond 37 deals and whether any oversight
  mechanism has since been legislated.
- Names and current terms of the workforce programmes, which I have described
  generically on purpose.
- Whether the accelerator office still exists under that name.

---
