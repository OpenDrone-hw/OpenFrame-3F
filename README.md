# OpenFrame-3F

The 3" OpenFrame: a CNC carbon fibre freestyle FPV frame in the
incutec OpenDrone line. The 3" and 5" frames are separate repositories:
[OpenFrame-3F](https://github.com/OpenDrone-hw/OpenFrame-3F) and
[OpenFrame-5F](https://github.com/OpenDrone-hw/OpenFrame-5F).

<p>
<img src="images/assembly.png" width="420" alt="OpenFrame-3F with electronics, Onshape assembly" />
<img src="images/frame.png" width="420" alt="OpenFrame-3F frame parts, Onshape part studio" />
</p>

[![Status](https://img.shields.io/endpoint?url=https://opendrone.be/api/status/OpenFrame-3F.json)](https://github.com/OpenDrone-hw/.github/blob/main/CONTRIBUTING.md#the-life-of-a-project)

## Where the design lives

```mermaid
flowchart LR
  O["Onshape<br/>OpenDrone-V2, workspace 3 inch"] --> V["Named version"]
  V --> E["onshape_release.py"]
  E --> R["releases/rev/<br/>STEP, drawings, manifest"]
  R --> S["Suppliers"]
```

| | |
|---|---|
| Source | [Onshape document OpenDrone-V2, workspace 3"](https://cad.onshape.com/documents/78e093d02798373a79bc68d0/w/0fcddf153f58a0417231386c) |
| Link file | [`cad/onshape.json`](cad/onshape.json): document, workspace, element and part ids |
| Released exports | `releases/<rev>/`, written by `onshape_release.py`, never edited |
| Parts per set | [`parts.csv`](parts.csv) |
| Fasteners and hardware | [`hardware.csv`](hardware.csv) |
| Standard | Incutec mechanical repository template (`templates/mechanical-repository` in the hardware tooling) |

## A set

17 part types, 23 pieces, 8 of them carbon. Taken from the
Onshape assembly; materials are as set in the model.

| Part | Qty | Material | Thickness | Made by |
|---|---|---|---|---|
| Arm | 4 | Carbon fiber epoxy (61%) | 4 mm | CNC carbon plate |
| Boot-FL | 1 | PLA |  | 3D print |
| Boot-FR | 1 | PLA |  | 3D print |
| Boot-RL | 1 | PLA |  | 3D print |
| Boot-RR | 1 | PLA |  | 3D print |
| Cam-Mount-L | 1 | PLA |  | 3D print |
| Cam-Mount-R | 1 | PLA |  | 3D print |
| Cross | 1 | Carbon fiber epoxy (61%) | 4 mm | CNC carbon plate |
| Airtag/Antenna-Mount | 1 | PLA |  | 3D print |
| VTX-Mount | 1 | PLA |  | 3D print |
| anti-slip pad | 1 | not set in the model |  |  |
| Base-Bot | 1 | Carbon fiber epoxy (61%) |  | CNC carbon plate |
| Base-Top | 1 | Carbon fiber epoxy (61%) |  | CNC carbon plate |
| Top | 1 | Carbon fiber epoxy (61%) |  | CNC carbon plate |
| 20mmx4mm | 4 | Aluminum |  | CNC aluminium |
| Standoff-L | 1 | Aluminum |  | CNC aluminium |
| Standoff-R | 1 | Aluminum |  | CNC aluminium |

Fasteners and hardware per set, from the same assembly:

| Item | Qty |
|---|---|
| Black-Oxide Alloy Steel Hex Drive Flat Head Screw | 5 |
| Hex nut grade A & B M2x0.4 | 4 |
| Hex socket countersunk head screw M2x0.4 x 5 | 4 |
| Hexalobular socket pan head screw M2.5x0.45 x 10 | 4 |
| Hexalobular socket pan head screw M2.5x0.45 x 6 | 16 |
| Hexalobular socket pan head screw M2x0.40 x 20 | 4 |
| Hexalobular socket pan head screw M2x0.40 x 6 | 17 |
| m2 pressnut | 4 |
| m2.5 pressnut | 6 |
| softmount m2 | 8 |

## Model checks

Found when this repository was set up on 2026-09-25. They stay listed until
the model is fixed.

| Check | Finding |
|---|---|
| Unused parts | `Receiver/Antenna-Mount` and `Part 19` are in the frame Part Studio but not in the 3" assembly |
| Materials | `anti-slip pad` has no material set in the model |

## Dimensions from the last released drawing

| | 3" |
|---|---|
| Top plate | 2.0 mm |
| Middle plate | 2.5 mm |
| Bottom plate | 2.5 mm |
| Cross | 4.0 mm |
| Arm | 4.0 mm |
| Bolt holes | Ø2.1 (M2), Ø2.6 (M2.5) |
| Press-nut holes | Ø3.5 (M2), Ø4.0 (M2.5) |
| Bolt-head counterbore | Ø3.8 (M2 ISO 7380) |
| Countersink | Ø2.6 + 1.5 mm 45° (M2.5 ISO 10643) |
| Camera mount thread | M2.5 |

Chamfers 0.5 mm 45°, outer fillets R1.0 mm, inner fillets R1.05 mm unless the
drawing says otherwise. The cross-to-arm interface is a press fit and is the
tightest tolerance in the design. The earlier drawings, STEP files and supplier
pack are at the `pre-reset-2026-08-13` tag of OpenFrame-5F; they are history,
not the current release.

## Licence

Hardware licensed under [CERN-OHL-S-2.0](https://ohwr.org/cern_ohl_s_v2.txt),
see [LICENSE](LICENSE). Contributing: [CONTRIBUTING.md](CONTRIBUTING.md).
