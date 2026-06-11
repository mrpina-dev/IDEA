# IDEA // VANGUARD - Design Direction

This is the north star document. It captures the WHY behind every system so design
intent never has to be restated. When a future decision is ambiguous, resolve it
against this document. `VANGUARD_context.md` holds current state;
`VANGUARD_backlog.md` holds pending work; this file holds direction.

---

## 1. The One-Sentence Brief

VANGUARD is a mean, visceral, desktop-browser arcade shmup where aggression is
rewarded, danger never disappears, and every faction is instantly readable as its
Bosco Tech pathway identity.

---

## 2. Reference Games (the taste benchmark)

- **ULTRAKILL** - primary benchmark. Aggression-as-fuel, style as reward,
  skill expression through parry, relentless pace. Direct quote from the
  developer: "The more it feels like ULTRAKILL the better on track you are."
- **DOOM 2016 / DOOM Eternal** - the audio and violence benchmark. Heavy,
  saturated, punchy. Power fantasy that never removes threat.
- **The Matrix** - the theming and music benchmark. Green-on-black digital
  world, terminal/code aesthetic, dark industrial-electronic score. The IDEA
  palette and mono chrome already live here; lean into it deliberately.
- **Deimos Rising** - the genre ancestor. Classic vertical shmup structure:
  escalating sectors, readable waves, power-up economy, relentless forward
  scroll. When a structural question comes up (pacing, wave flow, pickup
  rhythm), Deimos Rising is the skeleton to check against.

Division of labor: Deimos Rising is the body, ULTRAKILL is the blood, DOOM is
the voice, The Matrix is the skin and the score.

If a proposed feature, sound, or visual would feel at home in a friendly retro
indie game, it is wrong. If it would feel at home in ULTRAKILL, it is right.

Hard line: these are influences only. No actual Matrix or Deimos Rising music,
assets, imagery, or named characters ever ship in the game. All assets remain
CC0 or Sonniss royalty-free.

---

## 3. Design Pillars

### Pillar 1: Aggression is survival
Locked design forks (do not re-litigate):
- Hull heals on parry and on point-blank kills. Passivity starves you.
- STYLE rank is pure reward (coins + score). It never buffs damage or fire rate.
  ULTRAKILL-purist: style measures skill, it does not snowball power.
- Skill expression deepens through the existing PARRY system, not new mechanics
  (the throwable-coin idea was considered and rejected).
- Sitting still should get you killed. Aimed faction fire, bullet curtains, and
  enemy pacing all exist to punish a stationary ship.
- PARRY is a precise timing reward, not an invulnerability button. Pressing
  parry grants no meaningful i-frames on its own; only a successful catch does.
  Whiffs are punished (no protection, extended lockout). A clean catch runs the
  full cooldown; only a PERFECT parry shortens it. Parry healing is a sustain
  reward, never enough to make pure-parry passivity a winning strategy.
  (Precedent: a hardcore run reached sector 10 / 25 min on one life by spamming
  parry plus PHASE COIL. That is the exploit this fork closes.)

### Pillar 2: Readability before everything
- Every enemy must be instantly identifiable as its faction and tech identity.
  No ambiguity about who you are fighting.
- Each faction gets three DISTINCT enemy types, not three detail-copies.
- All six colors stay visually distinct: green (IDEA), orange (ACE),
  purple (BMET), blue (CSEE), yellow (MAT), red (MSET).
- Telegraphs are loud and honest. Unavoidable damage is a bug. The converge
  set-piece fix is the precedent: spread cones with threadable gaps, prominent
  red danger zones, real wind-up time. Hard is fine; cheap is not.
- Visual identity LOCKS before behavior/animation work begins. Always.

### Pillar 3: Beautifully violent
- The chosen feel is visceral/chunky: heavy kick, freeze-frame shock rings on
  elite kills, debris bursts, directional spark fans on every hit, muzzle
  flashes, gore-of-light.
- Weapons are committed playstyles, not four flavors of hold-to-clear:
  SCRAPPER (point-blank shred), OVERHEAT NAILGUN (heat-ramping stream with real
  overheat stakes), RAILSPIKE (charge-tap pierce), SWARM (hands-free but weak,
  frees attention for dodging).
- Heavies are earned in-run, sector-gated, expensive. Commitment, not shopping.
- Every weapon and combat system carries a this-or-that keystone fork, unlocked
  at mastery 4+ and sector 3+. WAVE and BOMB forks are utility-shaped, never
  boss-burst.
- BUZZSAW is a pure melee weapon; ranged capability is an explicit upgrade
  (BLADE LAUNCHER). SPREAD is the brawler shotgun: deterministic fan,
  point-blank reward.

### Pillar 4: Fair competition
- The playfield is FIXED (currently 630x840) for leaderboard fairness across
  devices. Never change it.
- CONFIGURE BUILD gives every player the same flat budget. No structural
  advantage for anyone.
- HARDCORE means hardcore: one life, no extra lives from CORE.
- The leaderboard is the social spine of the classroom deployment. Anything
  that breaks score comparability across players is rejected.

### Pillar 5: Danger never goes away
- Boss HP follows the derived quadratic (90 + 24s + 24s^2), built backward
  from target time-to-kill (7-14s by sector), not vibes. The player power
  curve is S-shaped; threat curves must be shaped against it, not linear.
- The economy is tuned so the full upgrade tree cannot be bought by sector 3.
  Kill-coin coefficient is the master income dial (currently 0.14).
- Boss-delete buttons are bugs (the 7x bomb multiplier and Wave Motion
  precedent). No single purchase should trivialize a boss.
- Weapon unlocks are sector-gated in-run. Runs start SPREAD-only.
- Balance proposals always state the numbers: named constants, exact values,
  and the fastest dials to turn if the change overshoots.
- No heavy weapon sustains near-100% uptime. The SINGULARITY one-active rule
  and post-implosion lockout are the precedent.
- Ambient extra lives drop only at low lives, max one per sector. Lives are
  scarce by design.

---

## 4. Audio Direction

Source quality is the foundation. The Kenney era is over: no synthesized, retro,
clean, or friendly sounds anywhere in the SFX set.

- **Tonal family:** dark, mechanical, saturated. A candidate that sounds clean
  or bright is cut no matter how good it is in isolation.
- **Sources:** Sonniss GDC bundles (primary, royalty-free) + Freesound CC0
  (gap-fill). License provenance is CC0 + Sonniss royalty-free; track it.
- **Loudness tiers:** combat at target level; UI/pickups 4-6 dB under;
  boss/death events may ring louder.
- **Length discipline:** combat SFX under ~200ms; only big one-shot events
  (boss spawn, player death) ring out.
- **Frequency lanes:** player weapons own mids + sub thump; enemy deaths own
  low-mid crunch; UI stays thin and high. No two layers fight.
- **Per-shot pitch jitter** in code, always.
- **Faction-keyed death sounds** by body type: mechanical crunch (ACE),
  organic squelch (BMET), electrical fry (CSEE), energy snap (MAT),
  crystalline break (MSET). Audio reinforces the readability pillar.
- Raw source swaps get ~70% of the way; budget light processing (layered
  transient + body + sub + tail, saturated, compressed, trimmed tight) for
  the last 30%.

### Music Direction (the Matrix lane)

The score target is the Matrix sound: dark industrial electronic, driving
breakbeat/techno energy for combat, ominous synth tension for boss warns and
menus. Selection rules for the CC0 catalog and any future additions:

- **Keep:** industrial, dark techno, breakbeat, drum-and-bass, dark ambient
  with pulse, anything that sounds like a hostile system running.
- **Cut:** chiptune, heroic orchestral, friendly synthwave, anything warm.
- **Context mapping:** menus get cold ambient tension; gameplay gets driving
  industrial pulse; boss waves get the heaviest, most aggressive tracks;
  victory/sector-clear gets brief release, never triumphal fanfare.
- Music and SFX share frequency discipline: the score leaves the mids and
  sub-thump lane open for player weapons.

### Matrix Theming (visual lane)

- The existing green-on-black phosphor palette IS the Matrix skin. Protect it:
  bg stays near-black, IDEA green stays the dominant signal color, mono
  fonts stay the chrome voice.
- Digital-system flavor is welcome in UI and ambient layers (terminal
  readouts, code-stream textures, glitch accents on damage or warnings) so
  long as it never costs combat readability. Pillar 2 outranks theming.
- Frame the fiction accordingly: the IDEA ship runs inside a hostile system;
  the factions are its processes. Flavor text, tutorial copy, and UPDATE LOG
  voice can lean on this.

---

## 5. Faction Identity Doctrine

Each faction is a Bosco Tech pathway made hostile. Identity table is in
`VANGUARD_context.md`; the direction rules are:

- Theme drives silhouette, attack pattern, projectile type, death sound, and
  boss design as one coherent identity per faction.
- Bosses are bespoke (THE RAISING, THE BLOOM, THE AMPLIFIER, THE FRAME,
  THE SCOPE), never scaled-up grunts.
- Hybrids (FOREMAN, VECTOR) are rare late-game elites only: sector 4+, max 2
  alive, never in normal rotation. Scarcity is what makes them special.
- Formations have archetypes (pincer, swarm, flank, spear) and roles
  (rusher, zoner, grunt, anchor). Anchors are the ULTRAKILL-Idol analog:
  visible buff tethers, priority-target gameplay, panic on death.
- Enemies that reach the bottom loop off-screen and re-enter from the top or a
  flank. No on-screen yo-yo climb-back. Half-climb, hover, or stuck-at-bottom
  behavior is a bug. Free divers loop at most twice, then leave.
- Each faction biases toward signature formations. A wave should feel like its
  faction even with eyes closed.

---

## 6. Platform and UX Direction

- PRISM BEAM is a standard heavy: it scales with HEAVY POWER and lives in the
  HEAVY group. No dedicated BEAM tab.
- **VANGUARD is a desktop browser game.** This is a commitment, not a default.
  The cabinet layout (fixed playfield flanked by console panels) is the visual
  language. Touch support exists but desktop drives design.
- Mobile controls are a twin-zone virtual gamepad: a floating velocity joystick
  under the left thumb (steers a direction; the ship moves at its own speed and
  never teleports to the finger) and all combat actions clustered under the
  right thumb. Position-follow and relative-drag touch steering were both tried
  and rejected as too weak for a fast shmup.
- Single self-contained file (`vanguard/index.html`) stays the architecture.
  Assets (audio) may live alongside it in the repo; game logic does not split.
- No redundant UI. Information appears once in the layout (precedent: duplicate
  wordmarks and controls lists were stripped from the consoles).
- First-run players get the tutorial automatically; returning players are never
  nagged (localStorage flags).
- Classroom loop: students play, scores hit the Sheets leaderboard, the
  suggestion box feeds development, the UPDATE LOG shows them the game evolving.
  This feedback loop is a feature; protect it.

---

## 7. Data-Driven Tuning

- Telemetry fires on every run end as an anonymous fire-and-forget beacon,
  because opt-in score submission is a biased sample that hides early deaths
  and frustration quits. Balance decisions should consult telemetry once
  enough runs accumulate.
- The server accepts all submissions; the Audit tab exists for manual review.
  Trust plus verification, not gatekeeping code.
- When auditing balance, read the actual code and compute exact values
  (scripts, not estimates). Backlog and memory drift from code reality;
  the file is ground truth.

---

## 8. Standing Rejections and Cautions

Decisions already made; do not re-propose without new evidence:
- No throwable ricochet coin (parry depth instead).
- No STYLE damage/fire-rate buffs.
- No playfield resizing.
- No extra lives in HARDCORE.
- No pre-game weapon unlocks in CONFIGURE BUILD (runs start SPREAD-only).
- No full Code.gs rewrites, no new Apps Script deployments.
- Upgrade-driven ship appearance: concept to be rethought, do not build as
  originally scoped.
- Boss coin drops: no magnetization (drops should not fly to the player).
- No press-to-invuln panic parry, and no cooldown reset on ordinary catches
  (perfect-parry only). PHASE COIL rides the catch window, never the press.
- SIEGE column-wall formation removed from rotation. Do not reintroduce the
  descending full-width column barrage.

---

## 9. How to Use This Document

When proposing anything new, check it against the pillars in order:
1. Does it reward aggression or passivity?
2. Is it instantly readable?
3. Does it look and sound mean?
4. Does it keep competition fair?
5. Does it preserve danger?

If a proposal fails a pillar, redesign before presenting. If two pillars
conflict, readability and fairness win, in that order.

This file is version-controlled in the repo and edited by Claude Code, never by
manual re-upload. When a session locks a new design decision, the CC prompt that
ships the related change includes a surgical edit to this file in the same commit.
Design-only decisions ship as a standalone CC prompt editing only this file.
