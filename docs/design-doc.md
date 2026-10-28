# Lunch Rush — Design Doc

Oct 26, 2026 · @Peter

## Overview

Lunch Rush is a match-3 cooking roguelite: match ingredients to fill customer orders during a timed shift, then spend tips on recipes, seats and upgrades before a harder shift. It should feel like Overcooked's chaos on a match-3 board, with Balatro-style "break the game" builds.

**Pillars**

- **Chaos you can manage:** several jobs compete for attention (board, grill, tickets, hazards), but every failure is readable.
- **Start tiny, end crazy:** small numbers and 3 ingredients at the start; wild synergies by the end of a run.
- **Your menu is your deck:** the recipes you pick decide what appears on the board and how you score.

**Platform:** mobile first (portrait, one screen), with PC/web as secondary.

**Prototypes:** [Lunch Rush v1](https://claude.ai/artifact/SY9t8HerabTin8Nq4LUXcU), a single 2½ minute shift; [Lunch Rush Roguelite](https://claude.ai/artifact/UW2TTHAeGqTAuaQuhS9Br7), the five-day roguelite run (v2), updated through the 27 Oct playtest.

## Core loop

During a shift, the player matches ingredient tiles to stock a pantry, then taps tickets to serve dishes before customers lose patience.

1. **Match:** swipe or tap to swap adjacent tiles on a 7×7 board. A 3-match gives 1 ingredient, a 4-match 2, a 5-match 3. Cascades count.
2. **Stock:** matched ingredients go to the pantry, capped at 3 per type so players can't hoard.
3. **Cook:** meat goes to the grill instead of the pantry. Tap it when it's done to move the cooked patty into the pantry.
4. **Serve:** a ticket glows green when the pantry holds everything it needs. Tap it to serve and earn a tip.
5. **Tip:** base pay per dish, plus a speed bonus and a streak bonus for consecutive serves without a walkout.

Missing ingredients show greyed out on each ticket so players always know what to match next. When no moves remain, the board reshuffles.

## Run structure

The game is a hybrid: a short handcrafted tutorial campaign, then roguelite runs as the main mode.

**Tutorial campaign (4–5 shifts)** introduces one mechanic per shift so the first playtest problem doesn't repeat:

1. Salad bar: matching, pantry, serving. No grill, no hazards.
2. Grill opens: meat, cooking and plating. Overcooked patties burn but don't catch fire.
3. Fresh produce: lettuce and tomato spoil into mould.
4. Fire: burnt patties ignite and fire spreads across the board.
5. First full lunch rush with everything on.

Completing campaign stages can unlock content for runs, such as a Taco Truck stage adding taco recipes to the run pool.

**A roguelite run** is about 5–7 rounds, targeting a 15–20 minute session:

1. Play a shift with a tip target. Missing the target closes the restaurant and ends the run.
2. Pick 1 of 3 new recipes.
3. Visit the shop.
4. Repeat with a higher target. Later rounds add hazards and complications, and the final round is a boss.

**Meta-progression** between runs unlocks new restaurant types (taco truck, sushi bar) and new starting options, adding variety rather than raw power.

## Economy and shop

Superseded by **Scoring: points and stars** below. In the v2 playtest, paying tips as money let a strong Monday earn $100 and buy most of the shop. The notes below are kept for reference.

**Starting state:** 3 ingredients (bread, cheese, tomato), 1 recipe slot, 2 seats, no abilities. A toastie pays about $3; early upgrades cost $5–8.

**Shop between shifts:**

- 3–4 random items each visit, with a paid reroll.
- Cheap one-shot consumables next to expensive permanent upgrades, so players choose between surviving tonight and scaling for later.
- Sell an item back for half price to pivot a build.
- Items include recipe slots, seats, seat types, ingredient upgrades, abilities and relics.

**Tension:** every dollar spent is a dollar not banked toward the shift target.

**Anti-snowball levers:**

- Rent or ingredient costs due each shift.
- Shop prices rise each round.
- Optional loan shark relic: big cash now, nasty complications later.

## Recipes and menu slots

The menu works like a deck: after each shift the player picks 1 of 3 recipes, and only menu recipes are ordered.

- **Recipes add ingredients to the board.** A recipe needing onion adds onion tiles, so a focused menu with fewer ingredient types makes matching easier.
- **Slots are limited and buyable.** With a full menu, a new recipe replaces an old one.
- **Trade-off:** simple recipes pay little but serve fast; complex ones pay well but clog the board with more ingredient types.
- An ambitious top dish attracts bigger payouts from big tippers and critics.

Example recipes from the prototype:

| Recipe | Ingredients | Notes |
| --- | --- | --- |
| Toastie | bread, cheese | Starter dish |
| Garden Salad | lettuce, tomato, onion | No grill needed |
| Grilled Cheese | bun, cheese, cheese | Tests pantry cap |
| Cheeseburger | bun, patty, cheese | First grill dish |
| Onion Smash | bun, patty, onion |  |
| The Deluxe | bun, patty, lettuce, tomato | Uses spoiling produce |
| Double Stack | bun, patty, patty, cheese | Needs both grill slots |

## Ingredients and upgrades

Each ingredient type can be upgraded in the shop, and upgrades stack so players can build around one ingredient, such as a "cheese build".

| Upgrade | Effect |
| --- | --- |
| Double harvest | 20% chance a match gives 2 instead of 1 |
| Regular | 25% chance a served customer orders again straight away |
| Fresh stock | That ingredient spoils slower |
| Golden tiles | Occasional gold tiles that add a tip bonus when used |
| Bulk | 4-matches give 3 instead of 2 |
| Better quality | You can charge more for recipes using this ingredient |

Percentages are starting values for balancing.

## Seating and customers

Seats cap how many tickets can be open at once: more seats mean more income but more juggling.

**Seating**

- Start with 2 seats; buy more in the shop.
- Customers queue outside with their own patience bar and leave if seats stay full too long.
- Seat types: a booth for groups (bigger orders and tips), a counter stool (quick snack orders), a VIP booth reserved for big tippers.

**Customer types.** Every customer orders only from the current menu, so no order is impossible.

| Customer | Behaviour | Reward or risk |
| --- | --- | --- |
| Normal | Standard order and patience | Base tip |
| Grumpy | Short patience | Double tip if served on time |
| Regular | Always orders the same dish | Tips more each visit |
| Picky | Wants a premium version (4-match ingredients) | Higher tip |
| Group | Orders 2–3 dishes, fills several seats | Big combined tip |
| Big tipper | Rare, visibly fancy; orders your hardest menu dish, a premium version, a double order or with tight timing | 3–5× tip, or a free reroll or relic |
| Critic | Rare outside boss rounds | Huge reward or penalty, affects reputation |
| Influencer | Pay in "exposure" i.e no money/tips. Orders one of everything |  |

Big tipper frequency can be raised by a fancy décor upgrade. Grumpy customers punish slowness, while big tippers punish being unprepared.

## Hazards

Hazards arrive gradually across a run so the first shifts stay calm. Prototype timings are starting points.

- **Grill:** 2 slots. A patty cooks for 6s, is ready for 5s, smokes for 3s, then burns. Early on a burnt patty must be binned with a tap; later it catches fire.
- **Grill fire:** blocks the slot (tap 3 times to douse), lights 2 board tiles, and lights another every 5s until doused. Patties matched while the grill is on fire are wasted, so this needs a clear warning message (a playtest confusion point).
- **Spoilage:** lettuce and tomato fade about 7s before turning into mould after 22–34s. Mould can't be swapped and is cleared by any match next to it.
- **Board fire:** fire tiles block swaps, take 2 taps to douse, and have a 25% chance to spread to a neighbour every 4s.

**Complications** added in later rounds: power cut (board dark except near your finger), rat that eats tiles, dirty plates that block serving, a spill that makes tiles slide.

**Dirty dishes** (later days or a "dishwasher's off sick" modifier): each serve may drop a dirty plate onto the board, so faster service makes a messier board. Matching 3 plates washes them for a small bonus, and plates next to a match get washed too. Related items: Dishwasher staff (clears a plate every 10s), Paper plates relic (no plates, but fewer points per serve).

## Abilities and relics

Players start with no abilities and 2 ability slots, so early shifts stay simple. Abilities are active and on cooldown; relics are passive and rule-bending.

**Abilities (cooldown)**

| Ability | Effect |
| --- | --- |
| Pre-prepped | Instantly gives 1 ingredient the oldest ticket needs (long cooldown) |
| Focused prep | Clears 3 random tiles of the ingredient you have least of |
| Fire warden | Puts out every fire on the board |
| Extra hands | Auto-serves the next ready ticket |
| Rush hour | Halves patience drain for 5s |
| Lucky ladle | Triggers a random match somewhere on the board |
| Professional cleaner | Removes all of ingredients on the board |

Upgrades can cut cooldowns or add effects, such as a fire warden whose doused flames drop free ingredients.

**Relics and staff (passive)**

- Heat lamp: finished patties don't burn for one cycle.
- Third grill slot, bigger pantry, fridge that stops spoilage for one ingredient.
- Sous-chef auto-plates done patties; dishwasher bins mould every 10s; waiter serves ready tickets.
- Wildcard: 4-matches of an ingredient spawn a tile that matches anything.
- Every 5th order served slows time for 3s.

**Relics with a catch**

- Turbo grill: cooks twice as fast, burns twice as fast.
- Cheap supplier: double ingredients, produce spoils twice as fast.
- Flamethrower grill: instant cooking, lights a random tile each use.
- Slot machine: spins after every serve for double tips or a free fire.
- Clumsy sous-chef: fast, but sometimes knocks tiles off the board.
- Flame grilled - fire can be used to match meat. Require at least 2 meat

## Boss rounds

The final round of a run is a boss, and each boss punishes a different build. Players can see the upcoming boss a few rounds ahead to prepare in the shop.

| Boss | Rule | Tests |
| --- | --- | --- |
| Health inspector | Checks the board every 15s; mould, fire or burnt patties earn a strike, and 3 strikes fails the shift. A clean shift earns a reputation bonus. | Hazard control; punishes messy high-volume kitchens |
| Food critic | Orders a tasting menu: one of every menu dish, in sequence, each premium quality. The final review multiplies the shift's tips. | Menu depth; punishes narrow menus |

Later boss ideas: wedding catering order, celebrity chef taking over half the board.

## Future ideas

These are parked for later; none are needed for the roguelite prototype.

- **Split grid:** two smaller boards, a prep counter (produce, bread) and a grill station (meat, cheese). Orders need both. Later, a conveyor moves unmatched tiles between them.
- **Rotating grid:** rotate the whole board 90° so gravity reflows, or a storm level where the galley board rotates on its own timer. Cheaper version: rotate one 3×3 section as a special move.
- **Kitchen layout shifts:** mid-shift events like a wall splitting the board in two.
- **Co-op:** two players share a board, one matching and one running the grill and tickets.
- **Restaurant themes:** taco truck, sushi bar, each with its own ingredients and hazards. Could go down the route, something like How many dudes, synergies if your menu has the same kind of dish

**Food-group matching (planned v3 experiment).** Tiles are coloured by group (meat, veg, carbs, dairy, seafood), so the board stays at about 5 colours however big the menu grows. That fixes the current problem where every new recipe adds a colour and makes matching harder.

- A mixed match gives each tile's own ingredient (beef, beef, chicken gives 2 beef and 1 chicken).
- A pure match of one ingredient gives a premium version, which links to picky customers and the critic.
- Each ingredient keeps its quirk: salmon needs two matches, steak burns fast, bananas ripen their neighbours.
- Risk: with few colours, matches are everywhere and cascades feel random. The pure-match bonus, a 6th group or blocker tiles can tune this.

## Scoring: points and stars

Points and money are split: points are the in-shift score, and stars are the currency you take home and spend.

**Points**

- Earned for every dish served and only used to beat the day's target, so they can grow as big as you like.
- Planned: score = dish value × multiplier. Speed, streak, grumpy and big tipper become multipliers rather than flat bonuses.

**Stars: 3 per shift**

| Star | How to earn it |
| --- | --- |
| ★ | Hit the target. Required to survive the day. |
| ★★ | Hit 1.5× the target. |
| ★★★ | Complete the day's objective. |

**Bonus stars** (rare, so stars stay scarce)

- A big tipper leaves a ★; serving the influencer earns a ★ for the exposure.
- Closing early with 20+ seconds left earns a ★. A rare golden ticket pays a ★ if filled in time.
- A 4th star for 2.5× the target, or for finishing an optional second objective.
- Boss win: +2★, plus 1 more for a clean win (no strikes, or a critic review of ×2 or better).
- Economy items: Star chart relic (+1★ for a 3-star shift), Savings tin relic (+1★ per 5★ held), Penny-pincher chef, and sell-backs that return some stars.

**Prices:** about 1★ for ingredient upgrades and seats, 2★ for abilities and relics, 3★ for rare relics or a 4th recipe slot. One free reroll per shop, then 1★. A full run earns about 15★; a strong run should not reach 25–30. Items must be punchy enough to be worth a star, e.g. +50% points for cheese dishes rather than +$1.

**Close early:** once the target is hit, a Close early button ends the shift with a time bonus. Staying open earns overflow points, but walkouts, fires and boss rules still apply.

## Objectives

Each day offers 2 objectives at the day intro; the player picks 1, and it earns the third star.

- Tracked live with a HUD chip (e.g. "Streak 3/5").
- Scaled by day (streak of 3 on Monday, 6 on Thursday).
- Only offered if possible with the current menu and kit, and only if the player controls the outcome. Luck-based ones are out, e.g. "serve 4 of the same dish in a row" or "serve 2 grumpy customers".

| Group | Examples |
| --- | --- |
| Service | No walkouts; reach a streak of 5; serve every ticket before its bar turns red |
| Speed | Hit the target with 15s to spare; serve 8 orders; first serve within 10s |
| Menu | Serve every dish at least once; serve your priciest dish 3 times |
| Cleanliness | No mould at the end; no fire burning longer than 5s; never burn a patty; no more than 2 hazards at once |
| Matching | Make a 5-match; trigger a 3-step cascade; make three 4-matches |
| Restraint | Use no abilities; never let the pantry fill up; serve with only 1 seat in use at a time |

## Builds and recipe levels

No menu is strictly best: base dish values stay roughly fair per ingredient, and shop items decide which build is strong, like Balatro's pair builds.

| Build | Menu | Board | Feel | Fed by |
| --- | --- | --- | --- | --- |
| Snack bar | 2–3 cheap dishes | Easy, few ingredient types | Frantic and steady | Streaks, per-serve bonuses, extra seats |
| Fine dining | Fewer, bigger dishes | Harder, more types | Tense and swingy | Value multipliers, big tippers, premium ingredients |
| Hybrid | Cheap filler plus one showpiece | Medium | Streaks plus jackpots | Recipe level-ups on the showpiece |

- **Recipe level-ups** (like Balatro planet cards): each level adds base value and multiplier to one dish, so a level-5 Cheese Toastie can beat a level-1 Double Stack.
- **Volume items** reward serving often (+1 mult per serve until a walkout, chained serves, flat +2 per serve). **Value items** reward big dishes (×2 for 4+ ingredients, +50% for grill dishes).
- **Menu focus synergies** reward a tight menu (all sandwiches, all 2-ingredient dishes).
- **Bored customers:** serving the same dish repeatedly lowers its points (about −10% per repeat in a row). Playtest: a one-dish Onion Smash menu made the run too easy.
- The critic's payout scales with menu size, so a one-dish menu earns a weak review.

Full item list and Balatro parallels: lunch-rush-builds.xlsx (shared in chat, 27 Oct).

## Chefs

The player picks a chef at the start of each run; each has a bonus, usually a catch, and sometimes a different starting recipe. The Line cook is available from the start and the others unlock through meta-progression (e.g. serve 5 influencers to unlock the Celebrity chef). Chefs come before dirty dishes in priority because they add variety without adding more to watch during a shift.

| Chef | Bonus | Catch |
| --- | --- | --- |
| Line cook | None; the all-rounder | None |
| Grill master | Starts with Cheeseburger; patties cook 30% faster | Fires spread faster |
| Baker | Bread drops more often and doubles 25% of the time | Grill dishes pay less |
| Neat freak | Produce spoils slower; the inspector boss is easier | Dirty plates drop more often |
| Celebrity chef | Big tippers and influencers show up more | Grumpy customers are grumpier |
| Penny-pincher | Shop prices 20% lower; starts with +2★ | Fewer points per dish |
| Fire-eater | Doused fire tiles drop free patties | Flare-ups happen more often |

## Board, controls and feedback

These were decided and built during the 27 Oct playtest of v2.

**Board**

- **Menu-weighted drops:** each ingredient's weight is 1.5 plus the number of times it appears across menu recipes; ingredients no dish uses weigh 1. The board keeps at least 4 types, and unused ones stay full colour (greyed tiles read as broken).
- **Mould** can be swapped out of the way but never matches. If no moves remain, the game scrubs some mould or reshuffles within a second.
- **Match hint:** two matchable tiles wiggle after 5 seconds without a match.
- **Speed:** swipes made mid-animation are buffered and played when the board settles; animations run 110–150 ms. True simultaneous swapping (Bejeweled Blitz style) is deferred to the Godot build.
- **Match sizes:** 3 in a row gives 1 ingredient, 4 gives 2, 5 gives 3. This needs visible "+2" feedback; later, 4+ matches could give a premium ingredient.

**Pacing**

- Shifts ramp up through the week: Mon 40s, Tue 50s, Wed 60s, Thu 70s, Fri 80s (prototype targets $10, $18, $30, $45, $60, to rebalance once scoring changes).
- An empty seat with no queue refills within about a second, so there's no dead time (Overcooked never lets the order list empty).
- A pause button, plus auto-pause when switching away.

**Serving and the grill**

- Serving stays a manual tap, because it's part of the chaos. Planned: overflow matches give "spare prep" points, a full pantry flashes, saving a ticket in the red pays a Clutch bonus, and auto-serve is only a purchase (Waiter staff or a chef perk).
- A ready patty is kept warm instead of burning while the pantry has no room for it.
- A burning grill pauses all cooking and its label says so.
- Planned: a raw tray of 2–3 slots that holds raw patties when the grill is full and feeds the grill automatically.

**Signals** (the player's eyes stay on the board, so cues come to the board)

| Signal | Means |
| --- | --- |
| Green ticket, wobble, "ding ding" | Ticket ready to serve |
| Gold grill slot and gold board outline, "🍖 Ready!", sizzle burst | Patty ready to grab |
| Red fast flash on grill and board outline, crackle | Patty about to burn |
| Time bar on the board turns red; alarm at 10s; ticks in the last 5s | Shift ending |
| Ability pulses gold; chime when ready | Ability ready and useful right now |
| Low buzz | Walkout, can't serve, burnt patty |

## Tech stack and prototype plan

Prototype in plain HTML/JS for fast iteration, then build the real game in Godot. No 3D engine such as Three.js is needed.

- **Prototype:** single-file HTML/JS, playable in the browser on a phone. Good for tuning feel and balance.
- **Production:** Godot (free, strong 2D, exports to iOS, Android, PC and web). Phaser or PixiJS with TypeScript is the alternative if staying on the web.
- **Data-driven:** keep recipes, ingredients, upgrades, customers, abilities and relics in data files (JSON or Godot resources) rather than code.

**Roguelite v2 (built 27 Oct):** [Lunch Rush Roguelite](https://claude.ai/artifact/UW2TTHAeGqTAuaQuhS9Br7)

- [x] Five-day run (Mon–Fri) on a visible calendar, with rising targets
- [x] Start with 1 recipe, 2 seats and small numbers
- [x] Pick 1 of 3 recipes after each shift, with swapping or buying a slot when the menu is full
- [x] Shop: seats, recipe slots, ingredient upgrades, abilities, relics, reroll and sell-back
- [x] One hazard introduced per day (spoilage, then fire, then the rush)
- [x] Clear warning when the grill is on fire and can't cook
- [x] Big tipper, grumpy and influencer customers
- [x] Food critic or health inspector boss on Friday
- [x] Playtest fixes: pause, swappable mould, match hints, buffered swaps, menu-weighted drops, board signals and sounds

**Next prototype: v3**

- [ ] Split points and stars; 3 stars per shift plus bonus stars
- [ ] Objectives: pick 1 of 2 per day, tracked on the HUD
- [ ] Close early button once the target is hit
- [ ] Multiplier scoring and recipe level-ups
- [ ] Bored customers for repeated dishes
- [ ] 2–3 chefs to pick from
- [ ] "+2" feedback on 4+ matches; overflow "spare prep" points; Clutch bonus
- [ ] Raw tray for patties
- [ ] Food-group matching as a toggle to compare

## Open questions

- What ends a run: missing a tip target, or a reputation meter drained by walkouts and fires?
- Run length: 15 minutes for mobile sessions, or longer runs for deeper builds?
- Should serving stay a manual tap, or should ready tickets auto-serve with an upgrade?
- How many ingredient types can a board hold before matching feels random? (Prototype used 6.)
  - Maybe you can start adding types? So all meat can match, all veggies, carbs, seafood, drinks, dessert? Not sure if we'd get enough variety if we do it that way.&#32;
  - Then each can have different properties. Salmon needs to get cut/matched  twice or something. Another one instead of spoiling just disappears. Steak can burn fast. Bananas make everything around them ripen faster. Then when you add a mostly meat menu they're still all a bit different
- Does the shop show the next boss, and how many rounds ahead?
  - Probably have some sort of track that's visible. Or a calendar&#32;
- Is the split grid a core mechanic or a later restaurant type?
  - Maybe restraunt type. Maybe a challenge mode. Your restaurant is on the sea only seafood dishes are available
