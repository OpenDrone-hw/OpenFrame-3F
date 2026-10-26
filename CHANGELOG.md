# OpenFrame-3F changelog

Each revision is a named version in the Onshape document OpenDrone-V2,
workspace 3", exported once to `releases/<rev>/` (STEP per part, drawing PDF,
`manifest.json` with SHA-256 per file). Onshape is the source for geometry and
for every count below unless a row says otherwise.

```mermaid
flowchart LR
  R1["rev1<br/>2026-07-05<br/>first CNC samples"] --> R2["rev2<br/>2026-10-20<br/>handoff rev F"] --> R3["rev2.1<br/>2026-10-21<br/>handoff rev G"] --> R4["rev2.2<br/>2026-10-24<br/>final CNC and hardware"]
```

| Rev | Onshape version | Microversion | State of | Used for |
|---|---|---|---|---|
| rev1 | `OpenFrame-3F rev1` | `f877e85425d535f6c880527f` | 2026-07-05 17:17 UTC | the first CNC sample frames, cut from these files |
| rev2 | `OpenFrame-3F rev2` | `10c00d2f68e6027651b1b59e` | 2026-10-20 | handoff package rev F |
| rev2.1 | `OpenFrame-3F rev3` | `4a06467185d3153716c3c5bf` | 2026-10-21 (version made 2026-10-24) | handoff package rev G, quoted for the first production frame batch (not ordered on 2026-10-24). Not exported: rev2.2 supersedes it |
| rev2.2 | `standardised and fixed` (branch `3in-fixes`) | `09d82dba2e04b77705035058` | 2026-10-24 10:50 UTC | final CNC carbon, CNC aluminium and bought hardware. [`releases/rev2.2/`](releases/rev2.2) |

rev1 is the only revision produced so far. rev2.x is the next production: rev2 (handoff package rev F), rev2.1 (handoff package rev G; its Onshape version is named `OpenFrame-3F rev3`) and rev2.2, the final CNC parts and hardware. The 5" uses the same numbers, so a frame set has one revision.

## rev2.2

The final state of every CNC carbon part, both CNC aluminium camera side
plates and the bought hardware (founder, 2026-10-24). The printed TPU parts
are preliminary: they fit the DJI O4 Pro only and will change for more video
systems. Shipped TPU colours are black and PCB green, as in the CAD. The aluminium
camera side plates are anodised Pantone 7549 C (gold).

Made by the founder as version `standardised and fixed` of the Onshape branch
`3in-fixes` (from rev2.1). Geometry compared with rev2.1 / handoff package rev G
(STEP, 2026-10-24): arm, cross, middle plate and bottom plate unchanged.

| Change from rev2.1 | Detail |
|---|---|
| Top plate | holes added for future GPS mounts (GPS cut-out 13.1 x 7.0 mm in the rev2.2 specification) |
| Camera side plates (Standoff-L/R) | one M3 tap hole 1 mm shallower: the wall was too thin |
| Arm and cross screws | ISO 7380-1 M3x10 on an M3 washer. Checked on 2026-10-24 against the provisional 2.4 mm insert model: the tip ended flush with the top of the insert and 1.35 mm under the ESC; an M3x12 would reach 2 mm past the insert and touch the ESC parts. Re-check against the M3-0 nut is open (below) |
| Stack | ISO 4762 M2x18 with an ISO 10511 thin nylon lock nut on top (was a button head M2x22 and a plain hex nut). Uncompressed, the M2x18 tip ends 0.3 mm below the top of the nut; the rubber grommets compress when the stack is tightened, so the length stays (founder) |
| Countersunk screws | ISO 10642 M3x8 into the front standoffs |
| Bumper | the two rear bottom side plate holes take an M3x6 without the bumper and an M3x8 with it; both are modelled and both ship |
| M3 inserts | 7 placed (rev2.1 placed 6 of the 7 holes) |
| Screw finish | every frame screw steel class 12.9, black. Nylon patch on the arm, cross, camera side plate and standoff screws; none on the countersunk and stack screws or on screws with TPU under the head |
| Parts | `20mmx4mm` renamed `Standoff M3 F-F 20 OD5` (bought, 7075); `softmount m2` renamed `Grommet M2`; Part Studio `Insert M3 (provisional)` added with PEM KFS2-M3 values. The nuts are settled since (below) |

Checked on the rev2.2 STEP export (thread engagement and clearance per screw,
2026-10-24): every screw into an insert ended flush with the insert top (the
provisional 2.4 mm insert, not the M3-0 nut); side plate screws get 3.5 to 4.5 mm
of thread; no screw touches a board.

Handoff package rev2.2 (sent to the suppliers 2026-10-25), settled after the
checks above:

| Item | Value |
|---|---|
| Middle plate nuts | self-clinching, 304 stainless, pressed in by the carbon supplier from the top face. 7 x M3-0: hole Ø4.22, seat Ø6.7 x 1.55, head flush. 4 x M2-2.9: hole Ø4.22, no seat, head 1.5 mm proud (a seat would cut into the Ø2.1 stack holes) |
| Bolt holes Ø3 | Ø3.00 to 3.10 (+0.10/0), as tight as possible for a standard bolt, never below the bolt diameter (was +0.03/0) |
| Cross and arms | press fit, no visible play; production fit agreed on the samples |

Open after rev2.2:

| Item | State |
|---|---|
| Washer M3 | material and size not specified (A2 stainless in the model). Its thickness in the Onshape Part Studio `Washer` is not confirmed: Extrude 1 is 1 mm and Extrude 2 adds 0.5 mm, the resulting thickness was not measured |
| Screw tips into the M3-0 nut | re-check. Stack from the handoff STEP: bottom plate 2.5 + arm or cross 4.0 + middle plate 2.5 = 9.0 mm. An M3x10 with a washer of thickness t ends (1.0 - t) mm above the top face: flush for t = 1.0, 0.5 mm proud for t = 0.5, 0.5 mm below for t = 1.5. The M3-0 nut is 2.26 mm long (head 1.5, shank 0.76 max), ends 0.19 mm above the plate underside, head 0.05 mm proud to 0.20 mm below the top face. The Onshape model still has the provisional insert, so the 1.35 mm ESC clearance is not re-derived |
| Onshape model | Part Studio `Insert M3 (provisional)` is not yet replaced by the M3-0 and M2-2.9 nuts (M2 head 1.5 mm proud: check the stack height and the M2x18 tip against the lock nut) |
| Anti-slip pad | the released pad export (`releases/rev2.2/step/anti-slip-pad.step`) predates the current pad, rev B (founder decision 2026-10-26): one pad for both frames, 15.5 x 93.1 x 2.0 mm, black silicone 50 Shore A, logo debossed 0.5 mm, 3M adhesive back, compression moulded. The export is 15.5 x 77.1 x 2.5 mm (Onshape part `RIDD`); the 3" will use the same 93.1 mm pad as the 5", so the 3" model and export are to be updated. |
| Drawing in Onshape | gives H8 holes and the old cross/arm tolerance; the rev2.2 specification gives +0.10/0 and the press fit |
| Counterbore for M2 heads | Ø4.1 on the rev G drawing, about Ø4.3 proposed |
| Insert | settled: M3-0 and M2-2.9 self-clinching nuts, 304 stainless (see above); the model still uses the provisional PEM KFS2-M3 values |

## rev2.1

Changed in the workspace on 2026-10-21 and sent as handoff package rev G; the
named version was made on 2026-10-24.

| Change from rev2 | Detail |
|---|---|
| Arm bolt | arm bolt hole and the four arm bolt / insert holes in the middle and bottom plates 1 mm further out (22.0 to 23.0 mm from the centre) |
| Rear M3 inserts | the two rear M3 insert holes in the middle plate 0.5 mm further out each (x 7.5 to 8.0 mm), for edge clearance |

## rev2

| Change from rev1 | Detail |
|---|---|
| Carbon and aluminium parts | Every part except the cross changed geometry: arm, middle plate (Base-Top), bottom plate (Base-Bot), top plate and both aluminium side plates (Standoff-L/R, 22.0 to 24.0 mm wide). rev1 and rev2 parts do not mix in one frame. |
| Screws | No M2.5 screws left: the M2.5 sizes become M3 (ISO 7380 button head). M2 screws remain (M2x5, M2x10, M2x22). |
| Threaded inserts, middle plate | 4x M2 + 6x M2.5 become 7x M3 + 4x M2, flush with the top face |
| Camera mount thread | M2.5 becomes M3 |
| Printed parts | Boot-L/R (2 each) become bootFL, bootFR, bootRL, bootRR; one camera mount becomes Cam-Mount-L and Cam-Mount-R; anti-slip pad added |
| Hardware in CAD | rev1 had no screws in the assembly; rev2 has them. The arm screw choice on the 3" was still open on 2026-10-09 |

Hardware per set, rev2, from the Onshape assembly (7 M3 inserts is the hole count; the rev2 assembly places 6). This is the rev2 list; [`bom.csv`](bom.csv) follows rev2.2.

| Item | Standard | Qty |
|---|---|---|
| Button head screw M3x6 | ISO 7380 | 14 |
| Button head screw M3x8 | ISO 7380 | 2 |
| Button head screw M3x10 | ISO 7380 | 5 |
| Button head screw M3x6, with collar | ISO 7380-2 | 1 |
| Button head screw M2x10 | ISO 7380 | 10 |
| Button head screw M2x22 | ISO 7380 | 4 |
| Countersunk screw M3x8 | ISO 10642 | 2 |
| Countersunk screw M2x5 | ISO 10642 | 4 |
| Hex nut M2 | ISO 4032 | 4 |
| Washer M3 | | 5 |
| Threaded insert M3, middle plate | | 7 |
| Threaded insert M2, middle plate | | 4 |
| Soft-mount grommet M2 | | 8 |
| Standoff, aluminium, 20 mm, OD 5 (part `20mmx4mm`) | | 4 |

Open in the model, rev2:

| Item | State |
|---|---|
| M3 inserts | 7 holes on the drawing, 6 instances in the assembly |
| `BigBoot`, `Bumpr`, `xt30Mount` | in the assembly, not in `parts.csv` (printed parts not yet decided for the set) |
| `TopBumpr` | in the Part Studio, not in the assembly |
| Drawing notes | the drawing in Onshape gives bolt holes as H8 (3.000-3.010 mm) |
| Part names | `20mmx4mm` is 20 x 5 mm; `Standoff-L/R` are the aluminium camera side plates; `Base-Top` is the middle plate |

## rev1

The state the first CNC samples were cut from. The carbon and aluminium STEP
files in `releases/rev1/step/` have the same geometry as the files sent for
manufacture on 2026-07-05 (point-for-point comparison, 7 of 7 parts).

Screws were not in the CAD yet. The rev1 hardware list below is the design list
the frame was drawn around (2026-07-02), not an Onshape count. The press-nut
counts are from the rev1 assembly.

| Item | Standard | Qty |
|---|---|---|
| Button head screw M2.5x6 | ISO 7380 | 8 |
| Button head screw M2.5x10 | ISO 7380 | 12 |
| Countersunk screw M2.5x10 | ISO 10642 | 2 |
| Button head screw M2x20 | ISO 7380 | 4 |
| Countersunk screw M2x5 (air unit) | ISO 10642 | 4 |
| Press nut M2 | | 4 |
| Press nut M2.5 | | 6 |
| Standoff M2.5, 20 mm, OD 4.6 | | 4 |
