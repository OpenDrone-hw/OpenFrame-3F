# OpenFrame-3F

The 3" frame. The design source is the Onshape document in
`cad/onshape.json` (OpenDrone-V2, workspace 3"); this repository holds
the link, the released exports and the parts lists. It follows the Incutec
mechanical repository template. Use the Onshape skill for any CAD work.

| | |
|---|---|
| Status | See the `status-*` topic on the repo. Never written here. |
| Validate | `python3 <hardware-tooling>/hardware/mechanical_check.py .` |
| Release | `onshape_release.py cad/onshape.json --version <rev> --apply`, then one commit adding `releases/<rev>/` |
| License | CERN-OHL-S-2.0 |

- Never edit a file under `releases/`. Fix the model in Onshape and release a new revision.
- A part added, removed or re-counted in the Onshape assembly changes `parts.csv` or `hardware.csv` in the same pull request.
- The 3" and 5" frames share one Part Studio in OpenDrone-V2; a change to a shared part affects both repositories.
- Sourcing (suppliers, prices, quotes, RFQs, contacts) is handled by Incutec and never lives in OpenDrone repositories.

## Rules

Identical in every OpenDrone board repo. Do not edit here; edit the template.

- **Never text-edit** `.kicad_sch`, `.kicad_pcb` or `.kicad_dru`. Use KiCad, or
  kicad-skip / the pcbnew API for scripted changes. `.kicad_pro` is JSON and may
  be edited directly for metadata.
- **Metadata yes, connections no.** An agent may write BOM and documentation
  fields (MPN, Manufacturer, LCSC, Cost, Datasheet, text variables). An agent
  may not change nets, wiring, routing, placement, footprint assignment, or any
  value that changes the circuit.
- **Close KiCad before any write to a KiCad file.** KiCad caches library tables
  at process start and overwrites files on save.
- **Reuse before you draw.** Check the `OpenDrone` library and its
  `PARTS-USED.md` first. If the part is there we have already sourced,
  footprinted and shipped it, and its symbol links to the exact committed
  datasheet: place it from `OpenDrone`. Draw a new part into `lib` only when
  the catalogue has nothing that fits, imported with
  `easyeda2kicad` from its LCSC number. Pulling a newer catalogue is a
  deliberate, reviewed commit: `git submodule update --remote
  hardware/KiCad-Library`, then DRC.
- **One person holds a board layout at a time.** KiCad files do not merge. Say
  on Discord that you are taking it. See [CONTRIBUTING.md](CONTRIBUTING.md).
- **Run ERC and DRC before every pull request.** Existing approved findings
  may remain; a new type or increased count must be reviewed before merge.
  Commands are in Environment above.

