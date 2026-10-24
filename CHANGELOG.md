# OpenFrame-3F changelog

Each revision is a named version in the Onshape document OpenDrone-V2,
workspace 3", exported once to `releases/<rev>/` (STEP per part, drawing PDF,
`manifest.json` with SHA-256 per file). Onshape is the source for geometry and
for every count below unless a row says otherwise.

```mermaid
flowchart LR
  R1["rev1<br/>2026-07-05<br/>first CNC samples"] --> R2["rev2<br/>2026-10-20<br/>first production batch"]
```

| Rev | Onshape version | Microversion | State of | Used for |
|---|---|---|---|---|
| rev1 | `OpenFrame-3F rev1` | `f877e85425d535f6c880527f` | 2026-07-05 17:17 UTC | the first CNC sample frames, cut from these files |
| rev2 | `OpenFrame-3F rev2` | `10c00d2f68e6027651b1b59e` | 2026-10-20 | handoff package rev F |
| rev3 | `OpenFrame-3F rev3` | `4a06467185d3153716c3c5bf` | 2026-10-21 (version made 2026-10-24) | handoff package rev G, the first production batch. `releases/rev3/` not exported yet |

## rev3

Changed in the workspace on 2026-10-21 and sent as handoff package rev G; the
named version was made on 2026-10-24. The first production batch is cut from
rev3. The STEP and drawing export (`releases/rev3/`) is still to do.

| Change from rev2 | Detail |
|---|---|
| Arm bolt | arm bolt hole and the four arm bolt / insert holes in the middle and bottom plates 1 mm further out (22.0 to 23.0 mm from the centre) |
| Rear M3 inserts | the two rear M3 insert holes in the middle plate 0.5 mm further out each (x 7.5 to 8.0 mm), for edge clearance |

Hole positions checked against the workspace on 2026-10-24 (FeatureScript
query of every hole in Arm, Base-Top, Base-Bot and Top). The rev G edits
re-numbered 17 part ids (standoff, side plates, printed parts); the link file
follows rev3.

Hardware spec (2026-10-24): every screw black-oxide alloy steel, class 12.9.
M3 and M4 button heads ISO 7380-1, countersunk ISO 10642. ISO 7380 has no M2:
M2 screws are ISO 4762 or a generic button head. Nylon patch on the arm, cross
and camera side plate screws only; not on screws into TPU, not on the standoff
screws (removed for maintenance), not on the two countersunk standoff screws.

Model review, 2026-10-24. Fixes go into the Onshape branch `3in-fixes` (from rev3) and reach the workspace when it is merged. On the branch every standard screw is steel class 12.9, black finish; the mate errors are the 3 that rev3 already had (Fastened 4, Revolute 24, Parallel 17). `hardware.csv` and `parts.csv` on the matching git branch follow the Onshape branch.

| Item | Finding | Proposed | Branch `3in-fixes` |
|---|---|---|---|
| Arm and cross screws | M3x10 on a 1.5 mm washer: the tip reaches 1.9 mm into the 2.4 mm insert | M3x12 | done: ISO 7380 M3x12, mates kept |
| Rule for screws into threads | no check today | length = everything under the head + full insert length + 0.5 to 1.5 mm | open |
| M2x10 | 8 of the 10 are prop screws mated to the props | exclude props, prop screws, motor screws and electronics from the BOM | open |
| M3x6 | rev2 had one with no mate; in rev3 all 14 are mated | none | n/a |
| McMaster flat head screws | 5 instances, part of the DJI O4 Pro reference subassembly, not frame hardware | keep; leave out of the BOM | n/a |
| M3 inserts | 7 holes, 6 instances | add the 7th | done: 7th insert placed in the centre hole and mated |
| Insert model | the insert holes are drawn as Ø4.5 + Ø5.5 x 1.0 counterbores; no insert part number yet | model the chosen insert and size the holes from it | Part Studio `Insert M3 (provisional)`: PEM KFS2-M3 values as variables, to replace with the measured sample |
| M2 hardware called ISO 7380 | ISO 7380-1 covers M3 to M16 | ISO 4762 or generic button head | done for the stack: ISO 4762 M2x20 (ISO 4762 has no M2x22; the tip still clears the nut by about 1.5 mm). The camera pivots stay button head |
| M3x8 countersunk | no standard set in the model ("grade C") | ISO 10642 | done: ISO 10642 M3x8 |
| Stack nut | plain hex nut ISO 4032 | nylon lock nut ISO 10511 | done: ISO 10511 thin nylon lock nut |
| Counterbore for M2 button heads | Ø4.1 on the rev G drawing | about Ø4.3 | open |
| Standoff part | named `20mmx4mm`, modelled with a plain Ø3 bore, marked CNC aluminium | rename to standoff M3 F-F 20 mm OD 5, model the thread, bought part | renamed `Standoff M3 F-F 20 OD5`; thread not modelled |
| Drawing in Onshape | gives H8 holes; rev G gives +0.03/0 and insert notes | bring the rev G notes into the Onshape drawing | open |

## rev2

| Change from rev1 | Detail |
|---|---|
| Carbon and aluminium parts | Every part except the cross changed geometry: arm, middle plate (Base-Top), bottom plate (Base-Bot), top plate and both aluminium side plates (Standoff-L/R, 22.0 to 24.0 mm wide). rev1 and rev2 parts do not mix in one frame. |
| Screws | No M2.5 screws left: the M2.5 sizes become M3 (ISO 7380 button head). M2 screws remain (M2x5, M2x10, M2x22). |
| Threaded inserts, middle plate | 4x M2 + 6x M2.5 become 7x M3 + 4x M2, flush with the top face |
| Camera mount thread | M2.5 becomes M3 |
| Printed parts | Boot-L/R (2 each) become bootFL, bootFR, bootRL, bootRR; one camera mount becomes Cam-Mount-L and Cam-Mount-R; anti-slip pad added |
| Hardware in CAD | rev1 had no screws in the assembly; rev2 has them. The arm screw choice on the 3" was still open on 2026-10-09 |

Hardware per set, rev2, from the Onshape assembly. This list is the same as [`hardware.csv`](hardware.csv).

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
