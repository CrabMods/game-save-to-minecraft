# World contract

The normalized scene schema is `gamesave2minecraft.scene/1`. The adapter exports
metres, right-handed coordinates and Y up. An asset contains an ID, behavior,
visual bounds, collision boxes, mesh reference and capability parameters.
Instances contain a stable normalized ID, asset ID, position, quaternion, scale,
optional parent and a separate state record. Keep the original source identity
and the private mapping when its representation needs normalization.

Use object definitions to share geometry; instances retain independent state.
Parent links can occur before or after their children. Normalize quaternions,
reject non-finite numbers and detect cycles. Retain a full world affine matrix
while flattening a hierarchy; a target cannot discard shear without a declared
bake or approximation step.

The coverage record contains `expected_instances` and explicit excluded source
identities with reasons. Structural coverage checks count and resolve exported
records. Source-oracle checks establish that those records correspond to the
source game. Both are needed for a source-fidelity claim.

`evidence.asset_inventory` reconciles every extracted visual carrier with an
`expected` count and unique `records`. Each record has a `source_id` and either
`status: mapped` with target resource paths, or `status: excluded` with a reason.
Unresolved outcomes fail acceptance. Verify this ledger against the source
extractor's inventory; a self-consistent subset does not establish completeness.

Inventory state includes capacity, original slot, source item identity, amount
and descriptive fields. A source lot may exceed a native stack limit. Select a
target representation that retains quantity and slot identity, and label its
gameplay behavior. Preserved source resources and fully simulated source recipes
are separate claims.

The portable compiler partitions instance plans and asset metadata and emits
acceptance requirements and resource hashes. Full world matrices use row-major
order with column vectors. A Minecraft target emitter consumes those matrices
and capability records; compiler output alone is not a running Minecraft world.

The target emission contract must state supported transform/material forms and
require a bake or explicit unresolved outcome for the others. Only completed
outcomes enter the accepted source coverage denominator.

## Validate before assembling at scale

| Boundary | Required handling |
| --- | --- |
| Missing definitions/resources or duplicate instance identities | Retain the failing source record and repair its binding; do not invent a placeholder and count it as migrated |
| Empty geometry/collision | Distinguish an intentionally invisible or collision-free component from failed decoding. Preserve selection and state when the capability needs them |
| Nonuniform scale, reflection or shear | Bake the unsupported transform into geometry, normals, collision and interaction sockets together, or keep it explicitly unresolved |
| Large or far-away coordinates | Check target precision, height and border limits before writing. Use a documented coordinate mapping when needed, preserving relative layout; do not truncate or silently omit distant objects |
| Many pieces sharing a block/chunk | Keep stable per-instance ownership, selection and state independently of cell fragments and reusable definitions; do not merge unrelated inventories or interactions |
| Partial/repeated import | Reconcile actual fragments and stable IDs; completed state must not duplicate an object or reset player-edited state |

Validate extracted resource paths within the selected output root before writing;
reject traversal or conflicting output identities. Keep original carriers and
the mapping available for diagnosis. Reconcile selected, recovered, excluded and
unresolved source records with reasons; never shrink a denominator merely because
an export omitted records.
