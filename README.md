# OpenFrame-3F

The 3" OpenFrame: a CNC carbon fibre freestyle FPV frame in the
incutec OpenDrone line. The 3" and 5" frames are separate repositories:
[OpenFrame-3F](https://github.com/OpenDrone-hw/OpenFrame-3F) and
[OpenFrame-5F](https://github.com/OpenDrone-hw/OpenFrame-5F).

| Assembled | Exploded |
|:---:|:---:|
| <img src="images/assembly.png" width="100%" alt="OpenFrame-3F assembled, frame and hardware only, render" /> | <img src="images/exploded.png" width="100%" alt="OpenFrame-3F exploded view, render" /> |

[![Status](https://img.shields.io/endpoint?url=https://opendrone.be/api/status/OpenFrame-3F.json)](https://github.com/OpenDrone-hw/.github/blob/main/CONTRIBUTING.md#the-life-of-a-project)

The CNC carbon parts, the CNC aluminium camera side plates and the bought
hardware are final in rev2.2. The printed TPU parts are preliminary: they
fit the DJI O4 Pro only and will change to fit more video systems. They are
printed by Incutec in black and PCB green. The aluminium camera side plates
are anodised Pantone 7549 C (gold).

## At a glance

| | |
|---|---|
| Wheelbase | 141 mm |
| Props | 3" |
| Top / middle / bottom plate | 2.0 / 2.5 / 2.5 mm carbon |
| Arms, cross | 4 mm carbon |
| Camera side plates | 6 mm CNC aluminium |
| Stack mount | 20 x 20 M2 (inserts), 25.5 x 25.5 (Ø2.1 through) |
| Motor mount | 9 x 9 and 12 x 12, M2 |
| Standoffs | 20 mm, M3 female-female, OD 5 |
| Weight | 80 g measured: carbon, aluminium and hardware, without the TPU parts |

## Revisions

```mermaid
flowchart LR
  R0["rev1<br/>2026-07-05<br/>first CNC samples, the only produced revision"] --> R1
  R1["rev2<br/>2026-10-20<br/>handoff package rev F"] --> R2
  R2["rev2.1<br/>2026-10-21<br/>handoff package rev G, not exported"] --> R3
  R3["rev2.2<br/>2026-10-24<br/>final CNC parts and hardware, next production"]
```

| Rev | Date | Used for | Files |
|---|---|---|---|
| rev1 | 2026-07-05 | first CNC samples, the only produced revision | [`releases/rev1`](releases/rev1) |
| rev2 | 2026-10-20 | handoff package rev F | [`releases/rev2`](releases/rev2) |
| rev2.1 | 2026-10-21 | handoff package rev G, not exported | named Onshape version only |
| rev2.2 | 2026-10-24 | final CNC parts and hardware, next production | [`releases/rev2.2`](releases/rev2.2) |

Every revision is a named version in the Onshape document OpenDrone-V2, exported
once to `releases/<rev>/` (STEP per part, drawing PDF, `manifest.json` with
SHA-256 per file) and never edited. rev2.2 is the Onshape version
`standardised and fixed` of the branch `3in-fixes`. Changes per revision:
[`CHANGELOG.md`](CHANGELOG.md).

| | |
|---|---|
| Source | [Onshape document OpenDrone-V2](https://cad.onshape.com/documents/78e093d02798373a79bc68d0/w/0fcddf153f58a0417231386c) |
| Link file | [`cad/onshape.json`](cad/onshape.json): document, workspace, element and part ids |
| Bill of materials | [`bom.csv`](bom.csv): every part and every piece of hardware in a set, counted from the assembly |
| Standard | Incutec mechanical repository template |

## What is in a set

From [`bom.csv`](bom.csv) (rev2.2). Materials are as set in the Onshape
model and blank where the model sets none (printed parts are marked PLA in the
model and printed in TPU); the process column is not from the model.

```mermaid
flowchart TB
  SET["OpenFrame-3F set"] --> CF["CNC carbon"]
  SET --> AL["CNC aluminium side plates"]
  SET --> TPU["TPU parts, preliminary"]
  SET --> KIT["Hardware kit"]
  SET --> PAD["Anti-slip pad"]
```

**CNC carbon**

| Part | Type | Qty | Thickness |
|---|---|---|---|
| Arm | arm | 4 | 4 mm |
| Base-Bot | plate | 1 | 2.5 mm |
| Base-Top | plate | 1 | 2.5 mm |
| Cross | cross | 1 | 4 mm |
| Top | plate | 1 | 2 mm |

**CNC aluminium**

| Part | Type | Qty | Thickness |
|---|---|---|---|
| Standoff-L | camera side plate | 1 | 6 mm |
| Standoff-R | camera side plate | 1 | 6 mm |

**Bought**

| Part | Type | Qty | Thickness |
|---|---|---|---|
| Standoff M3 F-F 20 OD5 | standoff | 4 |  |

**Moulded**

| Part | Type | Qty | Thickness |
|---|---|---|---|
| anti-slip pad | pad | 1 |  |

**3D printed TPU (preliminary)**

| Part | Type | Qty | Thickness |
|---|---|---|---|
| Airtag/Antenna-Mount | mount | 1 |  |
| bootFL | arm boot | 1 |  |
| bootFR | arm boot | 1 |  |
| bootRL | arm boot | 1 |  |
| bootRR | arm boot | 1 |  |
| Bumpr | bumper | 1 |  |
| Cam-Mount-L | camera soft mount | 1 |  |
| Cam-Mount-R | camera soft mount | 1 |  |
| VTX-Mount | air unit mount | 1 |  |
| xt30Mount | XT30 mount | 1 |  |

Threaded inserts (7 x M3 + 4 x M2) are pressed into the middle plate by the
carbon supplier.

## Hardware kit

<img src="images/kit.png" width="860" alt="OpenFrame-3F kit laid out, render: letters are frame and printed parts, numbers the hardware kit" />

One bag per frame: every screw and nut kind of the frame plus 2 spares
(49 screws in 7 kinds). Every screw is black-oxide alloy steel, class 12.9.
The bumper holes get an M3x6 without the bumper and an M3x8 with it; both ship.

| IPN | Item | Nylon patch | In the frame | In the kit | Where |
|---|---|---|---|---|---|
| `FAS-M3X10-BH-NP` | ISO 7380-1 M3x10 | yes | 5 | 7 | arms + cross, on a washer |
| `FAS-M3X6-BH-NP` | ISO 7380-1 M3x6 | yes | 14 | 16 | camera side plates, standoff ends, XT30 mount |
| `FAS-M3X8-BH` | ISO 7380-1 M3x8 | no | 4 | 6 | AirTag/antenna mount, bumper option |
| `FAS-M3X8-CSK` | ISO 10642 M3x8 | no | 2 | 4 | front standoff bottoms |
| `FAS-M2X18-SHCS` | ISO 4762 M2x18 | no | 4 | 6 | stack |
| `FAS-M2X10-BH` | M2x10 button head | no | 2 | 4 | camera pivots |
| `FAS-M2X5-CSK` | ISO 10642 M2x5 | no | 4 | 6 | air unit |
| `FAS-NUT-M2-NYL` | ISO 10511 thin nylon lock nut M2 |  | 4 | 6 | stack |
| `FAS-WSH-M3` | M3 washer |  | 5 | 5 | under arm and cross screws |
| `GRM-M2-SIL50` | silicone grommet M2 |  | 8 | 8 | stack |
| `FRM-SO-3-20` | standoff M3 F-F 20 mm OD 5, aluminium |  | 4 | 4 |  |

Motor screws (16 x M2x6) and prop screws (8 of the 10 M2x10 in the assembly) ship with the motors and props and are not frame hardware.

Hardware per set as counted in the Onshape assembly ([`bom.csv`](bom.csv), kind `hardware`):

| Item | Standard | Size | Qty |
|---|---|---|---|
| Socket button head screw M3x0.5 x 10 | ISO 7380-1 | M3x10 | 5 |
| Socket button head screw M3x0.5 x 6 | ISO 7380-1 | M3x6 | 14 |
| Socket button head screw M3x0.5 x 8 | ISO 7380-1 | M3x8 | 4 |
| Hex socket countersunk head screw M3x0.5 x 8 | ISO 10642 | M3x8 | 2 |
| Hex socket head cap screw M2x0.40 x 18 | ISO 4762 | M2x18 | 4 |
| Prevailing torque nut thin M2x0.40 | ISO 10511 | M2 | 4 |
| Socket button head screw M2x0.4 x 10 | ISO 7380 (Onshape library; ISO 7380-1 starts at M3) | M2x10 | 10 |
| Hex socket countersunk head screw M2x0.4 x 5 | ISO 10642 | M2x5 | 4 |
| m2 pressnut |  | M2 | 4 |
| m3 pressnut |  | M3 | 7 |
| Grommet M2 |  | M2 | 8 |
| Washer M3 |  | M3 | 5 |

## Checks on rev2.2

Run on the STEP export of rev2.2 on 2026-10-24: thread engagement and clearance
for every screw, and a geometry comparison of every CNC part with the previous
revision (see [`CHANGELOG.md`](CHANGELOG.md)).

| Check | Result |
|---|---|
| Screws into inserts | arm and cross M3x10 end flush with the 2.4 mm insert, 1.35 mm under the ESC |
| Side plate screws | 3.5 to 4.5 mm of thread |
| Stack | M2x18 with a thin nylon lock nut: 2.5 mm in the nut before the grommets are compressed; the grommets compress when tightened, so the tip reaches through the nylon ring |
| Duplicates | none (the bumper M3x6 / M3x8 pair is the deliberate option) |

## Key dimensions

From the drawing in Onshape and the rev G frame parts specification.

| | |
|---|---|
| M3 bolt holes | Ø3; the Onshape drawing says H8 (3.000-3.010), the rev G spec says +0.03/0 (3.00-3.03) |
| M2 bolt holes | Ø2.1 |
| Insert holes, middle plate | Ø4.5 (M3), Ø3.5 (M2), reference only: sized to the insert used |
| Countersinks, middle plate | Ø3 + 1.8 mm 45° (M3 countersunk) |
| Bolt-head counterbore, bottom plate | Ø4.1 (M2 button head) |

Chamfers 0.5 mm 45°, outer fillets R1.0 mm, inner fillets R1.05 mm unless the
drawing says otherwise. The cross-to-arm fit is the tightest tolerance in the design:
0.000-0.100 mm between both parts on the drawing.

## Licence

Hardware licensed under [CERN-OHL-S-2.0](https://ohwr.org/cern_ohl_s_v2.txt),
see [LICENSE](LICENSE). Contributing: [CONTRIBUTING.md](CONTRIBUTING.md).
