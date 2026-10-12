# OpenFrame-3F

The 3" frame. Design source is the Onshape document in `cad/onshape.json`; this repository holds the link, the released exports and the parts lists.

Validate: `python3 <hardware-tooling>/hardware/mechanical_check.py .`

## Boundaries

- Never edit a file under `releases/`: fix the model in Onshape and release a new revision.
- The 3" and 5" frames share one Part Studio in OpenDrone-V2: a change to a shared part affects both repositories.
- Sourcing (suppliers, prices, quotes, RFQs, contacts) never lives in OpenDrone repositories.

## Pointers

- Release: `onshape_release.py cad/onshape.json --version <rev> --apply`, then one commit adding `releases/<rev>/`
- CAD work: Onshape skill
