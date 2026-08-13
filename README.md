# Industry competitiveness flow maps: handover

This folder carries everything needed to rebuild and extend the interactive flow
diagram in a new chat or in Claude Code, without repeating the design work.

## Contents

| File | What it is |
| --- | --- |
| `README.md` | The frame, the principles, the data model, the open issues |
| `countries.md` | All four country specs. Brazil, Singapore and UAE built; USA researched but **not built** |
| `sources.md` | Source quality tiers and unverified claims |
| `BUILD-NOTES.md` | What the rebuild changed, the bugs it fixed, the judgement calls, and the as-built tables |

The working artifact is `industry-flow.html`, in this folder.

The two python validators named in earlier versions of this file were not in the
handover archive. Their checks, and the one they were missing, are now built into
the artifact itself. See "Run the validators" below.

## What this thing is for

Comparing how four countries govern industrial competitiveness, from who sees a
problem coming to how a capability gap actually gets closed. The audience includes
people meeting these systems for the first time.

## The six-layer frame

Every country is mapped onto the same six layers. A country may leave a layer empty,
and an empty layer is often the most interesting thing on the page.

| Layer | Question it answers |
| --- | --- |
| 01 Foresight | Who studies what is coming. Advises only, no authority. |
| 02 Direction | Who decides what the country will back. |
| 03 Translation | Who turns a decision into something a company can answer. |
| 04 Delivery | Who holds the money, the demand and the support. |
| 05 Capability | How a skills or know-how gap actually gets closed. |
| 06 Ground | Land and permission. Who can let a factory open. |

## Design principles, agreed and load-bearing

These were arrived at through several rebuilds. Changing one usually breaks
something that took a while to get right.

1. **A box is a named body, not a takeaway or an output.** One exception, layer 05,
   described below.
2. **A box carries a name plus three or four words of role.** Everything else lives
   in the click-through panel. This is what creates the room.
3. **No acronyms on cards.** Plain names on the box, real names and abbreviations in
   the detail panel. "Industry ministry" on the card, "Ministry of Industry and
   Advanced Technology" inside.
4. **Default view shows downward flow only.** Sideways and upward relationships
   appear only when a box is selected.
5. **A body appears once.** If it has two functions, show the second as a
   relationship, not a second box.
6. **Flows connect adjacent layers.** A flow that skips a layer routes down a clear
   channel in the left margin. If it runs through the intervening row it will hide
   behind those boxes and look broken.
7. **Lanes only where two things genuinely run apart**, and lane meaning differs by
   country. Brazil: government and industry. UAE: sectors that exist and sectors that
   do not. Singapore: one lane, no header.
8. **Layout is a CSS grid, connectors are measured from the rendered boxes.**
   No hand-placed coordinates anywhere.
9. **Calibri only, near-monochrome, white ground, one accent.** No em dashes anywhere
   in the content.
10. **Fits a laptop width without horizontal scrolling.**

## The layer 05 exception, now implemented

Layer 05 is the only layer where boxes are **options rather than bodies**,
because there the useful question is "what can be done" rather than "who owns it".
The owning body is named in the role line or the detail.

Implemented as `kind:'option'`, which the built-in validator allows at layer 05
only, and which it also flags if a plain `body` is left on that row. The card
carries the route name; the line beneath it names the owner.

The intended reading is: layer 04 sets up the mechanisms, layer 05 shows the routes
available when a specific gap appears.

## Data model

```js
LAYERS = [ { num:'01', name:'Foresight', note:'Studies what is coming.' }, ... ]

country = {
  id, name, flag,           // flag is an inline SVG string
  sub,                      // two or three sentences under the country name
  lanesFrom: 3,             // optional: layers above this are full width
  lanes: [ { key, label, cols } ],
  nodes: [ node ],
  flow: [ { from, to } ],   // solid, always drawn, downward or lateral
  rel:  [ { from, to, label, note } ],  // curved, on selection only
  absent: { 6: 'Why nothing sits here.' },   // draws the empty layer as a finding
  dispute: { title, sides:[[label,text]], foot }  // two columns under the legend
}

node = {
  id, layer,                        // 1..6
  lane, col, span,                  // for laned layers
  gcol, gspan,                      // for shared layers above lanesFrom
  kind,                             // see below
  name, role,                       // role is 3 or 4 words
  detail: [ ['Label','Fact'], ... ] // shown in the panel below
}

kind = 'body'        white box, hairline border
     | 'mechanism'   shaded, no border: a route where no institution exists
     | 'option'      sage rule on top: a capability route, layer 05 only.
                     name = the route, role = the body that owns it
     | 'detached'    dashed border: connects to nothing
     | 'shared'      shaded: needed by both lanes
     | 'tripartite'  accent bar on the left: government, business and unions inside
```

Relationship `note` is a full sentence used in the detail panel. `label` is two to
four words drawn on the curve.

## Rendering rules that matter

- Two SVG layers per board. Flows and relationship curves sit **behind** the boxes.
  Relationship labels sit **above** them, or they disappear.
- Relationship label placement walks seven points along the curve and takes the first
  that clears every box. A denser country could exhaust the candidates.
- Same-row relationships dip below the row rather than running through it.
- Fan-outs from one parent stagger their horizontal segment so two parents never share
  a line.
- The lane header needs `position:relative` and a `background`, or connectors draw
  across its text.
- Layer labels live in a reserved left column so connectors can never cross them.

## Run the validators before shipping any change

They live inside the artifact now, so there is nothing to install and nothing to
keep in sync with the data.

Open the file with `?check` appended to the URL for a panel in the corner, or
call `check()` in the console, which returns an array and is empty when clean.

It checks: every arrow starts and ends on a real box; no flow runs upward, which
is what `rel` is for; no route sits outside layer 05 and no plain body sits on
it; a layer marked empty really is; no text overflows its card; no two cards
overlap; and no connector runs through a card or through a label.

**The old known gap is closed.** The label placer now tests candidate positions
against every drawn line as well as every box, so a connector crossing wording
is caught rather than left to the eye. Still worth a look at a screenshot after
a large change, since nothing checks whether the result reads well.

## Open issues, honestly

1. ~~Layer 05 exception is unimplemented.~~ Done. All four countries.
2. **Singapore has a real modelling problem.** The same agency often writes the sector
   roadmap and delivers it. The monetary authority writes the financial services
   roadmap and regulates the sector. So translate-then-deliver is genuinely blurred
   there, unlike Brazil and the UAE. The investment board is one box at Delivery, but
   the Translation row is still thinner than the truth. The lead agencies card now
   says so in its detail, which is a label on the problem rather than a fix.
3. ~~"Investment board attracts investment" is too generic.~~ The card now says it
   leads the roadmaps for the sectors where attraction is the main lever, and that it
   is not a whole-economy function.
4. ~~USA is unbuilt.~~ Built. Two lanes from layer 03, a detached courts box in
   Direction, and an explicitly empty Ground layer.
5. **Verify before publishing.** See `sources.md`, and the carried-forward list at the
   end of `BUILD-NOTES.md`.
6. **New, from the rebuild.** `countries.md` claims the UAE ministry arrow is the only
   upward arrow in any map. Brazil's federations arrow is also upward. The artifact
   never claimed uniqueness, but do not repeat it in a deck.

## On the plan to move to Claude Code

Splitting research on claude.ai from building in Claude Code is the right division.
Research needs web search and argument; the build needs file editing and test loops.

Three things worth doing in that order:

**Carry the principles across, not just the code.** Most of the rebuilds in this
project came from re-litigating decisions that had already been made. The principles
list above is the expensive part of this folder.

**Take the validators with you and wire them into the loop.** Claude Code can run them
after every edit, which is the main advantage it has here. Add a check for connectors
crossing text labels, which is the one gap I know about.

**Research one country to completion before building it.** The three rebuilt countries
each got restructured because research arrived after the build. `countries.md` is
structured so research fills each country in before any code is written.

One caution: the artifact is a single self-contained HTML file with no dependencies,
which is what makes it easy to hand around. If Claude Code proposes a build step, a
framework or a package manager, weigh that against losing the property that you can
email the file to a client and it opens.
