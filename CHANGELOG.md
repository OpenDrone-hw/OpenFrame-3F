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
| rev2 | `OpenFrame-3F rev2` | `10c00d2f68e6027651b1b59e` | 2026-10-20 | handoff package rev F; the first production batch is cut from rev F plus the unreleased changes below (package rev G) |

## Unreleased (Onshape workspace 3", after rev2)

Changed in the workspace on 2026-10-21 and sent as handoff package rev G. Not
yet a named Onshape version: it becomes rev3, the state the first production
batch is cut from.

| Change from rev2 | Detail |
|---|---|
| Arm bolt | arm bolt hole and the four arm bolt / insert holes in the middle and bottom plates 1 mm further out (22.0 to 23.0 mm from the centre) |
| Rear M3 inserts | the two rear M3 insert holes in the middle plate 0.5 mm further out each (x 7.5 to 8.0 mm), for edge clearance |

Hole positions checked against the workspace on 2026-10-24 (FeatureScript
query of every hole in Arm, Base-Top, Base-Bot and Top).

Hardware spec (2026-10-24): every screw black-oxide alloy steel, class 12.9.
M3 and M4 button heads ISO 7380-1, countersunk ISO 10642. ISO 7380 has no M2:
M2 screws are ISO 4762 or a generic button head. Nylon patch on the arm, cross
and camera side plate screws only; not on screws into TPU, not on the standoff
screws (removed for maintenance), not on the two countersunk standoff screws.

Model review, 2026-10-24 (to fix in Onshape before rev3 is released):

| Item | Finding | Proposed |
|---|---|---|
| Arm and cross screws | M3x10 on a 1.5 mm washer: the tip reaches 1.9 mm into the 2.4 mm insert | M3x12 |
| Rule for screws into threads | no check today | length = everything under the head + full insert length + 0.5 to 1.5 mm |
| M2x10 | 8 of the 10 are prop screws mated to the props | exclude props, prop screws, motor screws and electronics from the BOM |
| M3x6 | one instance has no mate | delete or mate |
| McMaster flat head screws | 5 instances, no mates, not in the BOM | delete |
| M3 inserts | 7 holes, 6 instances | add the 7th |
| Insert model | the insert holes are drawn as Ø4.5 + Ø5.5 x 1.0 counterbores; no insert part number yet | model the chosen insert and size the holes from it |
| M2 hardware called ISO 7380 | ISO 7380-1 covers M3 to M16 | ISO 4762 or generic button head |
| M3x8 countersunk | no standard set in the model ("grade C") | ISO 10642 |
| Stack nut | plain hex nut ISO 4032 | nylon lock nut ISO 10511 |
| Counterbore for M2 button heads | Ø4.1 on the rev G drawing | about Ø4.3 |
| Standoff part | named `20mmx4mm`, modelled with a plain Ø3 bore, marked CNC aluminium | rename to standoff M3 F-F 20 mm OD 5, model the thread, bought part |
| Drawing in Onshape | gives H8 holes; rev G gives +0.03/0 and insert notes | bring the rev G notes into the Onshape drawing |

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
