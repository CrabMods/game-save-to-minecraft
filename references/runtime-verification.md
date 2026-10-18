# Native interaction and visual verification

Read this when implementing or accepting a playable target. Select checks for
the capabilities, transforms and environments actually in scope. Test counts
from a previous project are examples of coverage, not a universal pass quota.

## Separate the evidence layers

1. **Pure checks:** validate scene data, identities, transforms, resource coverage
   and deterministic emission. These do not exercise Minecraft interaction.
2. **Native GameTest:** exercise production server rules, collision, ownership,
   occupancy, inventory, timing, persistence and cleanup in controlled fixtures.
3. **Actual packaged client:** verify the installed JAR/resource combination,
   normal selection/use packets, synchronized state, visible pose and movement.
4. **Source comparison and visual review:** compare requested appearances/layout
   and inspect actual rendered frames at useful angles. An API state is not a
   picture, and a promotional camera is not evidence of player traversal.

Use the project's supported build/test workflow. Keep automated games hidden,
unfocused, muted and input/clipboard isolated, using a test instance rather than
the live world. Reuse valid matching receipts before launching an expensive run.
If an automated client lane is unavailable, keep it blocked or unexecuted;
continue other supported work and arrange a user play-check when appropriate.
Do not replace that lane with a visible automated game or mark it passed.

## Exercise the player path

Server tests may call a production handler to isolate rules. Client acceptance
must also reach the intended object with the ordinary picker/raycast and normal
use input/packet. Log the selected owner ID, hit location and observed state.
Trace the chain from selection through server handling to client state and
rendering. A test that directly sets sleeping/riding flags, teleports a player
onto furniture or invokes only the server handler does not prove this path.
Teleporting into a test's starting area is acceptable setup; it must not produce
the interaction or substitute for a claimed walk-through.

Inspect standalone representatives first, then actual saved placements where
neighboring walls, overlap, rotation and scale can change targeting and access.
Include boundary transforms/material families when relevant, not every possible
combination by default. Set tolerances from the target scale and interaction
contract before evaluation; retain the observed measurements.

## Chairs and beds: verify more than a flag

**Chairs:** confirm the clicked object owns the actual seat entity and the player
is its passenger on both sides. Check the transformed cushion/socket against the
player's real attachment/hip position. Inspect front and side renders of the
actual player body; a mounted actor can still float above or sink through a seat.
Use read-only render observations when instrumentation is needed; do not move or
replace the model to make the capture pass. Reject unintended double occupancy.

Exercise normal dismount input. Observe the resulting standing body independently
of the exit-selection routine: full body collision-free, feet supported, no
remaining passenger state, consistent client/server position, empty owned seat
removed. Test an occupied seat's removal/disconnect behavior when supported.
Do not repair a bad exit with test-side teleportation and call it passed.

**Beds/coffins:** use native bed/sleep hooks and verify the actual sleep request,
sleeping position and orientation, with a clear statement of the target sleep
and respawn policy. Daytime, dimension, distance, hazards and occupancy can cause
legitimate native rejection. Set valid conditions for the positive case and
exercise relevant rejection cases separately; do not disable these rules merely
to obtain success or change the live world's time for a test.

Inspect front, side and overhead rendered body placement on the intended resting
surface, including rotated/offset beds. A sleeping flag and a bed-shaped mesh
can both be correct while the body lies beside or below it. Send the normal wake
action, then verify standing clearance, support, state cleanup and any promised
respawn behavior. Restore test-owned time/rule changes after the scenario.

If the actor is not rendered, diagnose spectator/invisibility state, camera
selection, section readiness and which render pass was observed. An empty frame
cannot pass a body-alignment assertion. Keep diagnostics observational and retain
raw frames before captions or filming effects.

## Other applicable behavior boundaries

| Capability | Positive path and important boundaries |
| --- | --- |
| Doors/windows | Correct hinge and transformed collision in both states; normal selection; real player passage; native frame accepted but new obstacles rejected; paired leaves and repeated open/close preserve owner identity |
| Storage/workstations | Real menu/slot readback; source identity, full quantity and original slots across paging; controls/invalid slots reject items; repeated or concurrent operations do not duplicate/loss items; carry/break and reload retain native serialized components |
| Plants | Actual dormant/mature visual variants and selection; harvest yields once; production ticks drive regrowth; saved remaining timing survives reload; collision-free foliage stays selectable without becoming solid |
| Lights/materials | Logical state, emitted light and actual appearance agree; cutout, transparency and emissive surfaces remain valid on exercised renderer paths; state changes invalidate cached geometry |
| Static geometry/traversal | Walk floors/stairs/doorways as a normal actor; verify clearance and support, object/chunk boundaries and safe entry. A free-flying camera reaching an area proves no walkable route |

## Persistence and interrupted assembly

Save, unload and reload the target, then read back instances, ownership, state
and resources through the actual target. Compare native serialized item/component
values as well as convenient amounts or labels; a menu that looks right can hide
a broken round trip. Keep source quantities separate from Minecraft stack limits.

Interrupt generation at a relevant intermediate boundary, including a partially
placed multi-cell object when applicable. Resume without duplicate identities,
missing/colliding fragments, reset inventories or leaked chunk tickets. Test
occupied target cells and out-of-range placement as explicit failures rather
than silently skipping source objects. Resume must reconcile actual owned world
state, not trust only an optimistic progress flag.

For multiplayer claims, exercise a second real client and the relevant
concurrent/disconnect cases. A single-player or mock-player result remains
scoped to that environment. Test promised resource-pack discovery on a clean
target client; a developer's already-loaded model cache is not delivery proof.

## Repair and accept

Preserve the first failure and its input/program/resource identities. Decide
whether it comes from source recovery, target behavior, synchronization,
rendering or test setup. Fix that boundary and rerun its affected checks plus
load-bearing regressions. Keep thresholds and failed coverage visible; do not
lower tolerances, delete a failing scenario or silently switch to an easier
object to claim success.

Freeze verification inputs while the run is active. Read the final exit,
scenario, restoration and post-run artifact receipts. Bind the accepted result
to the delivered JAR, resources, scenario set and test environment. Keep build,
GameTest, client behavior, visual fidelity and performance outcomes separately
visible; a pass in one layer does not repair an open failure in another.
