# Interaction mapping

An interaction rule binds visual parts, selection surfaces, collision, server
state transitions, network updates and persistence. Parameters are supplied by
the adapter or explicitly authored target policy. Rules are extensible.

| Capability | Parameters/state | Native observations |
| --- | --- | --- |
| Door | Hinge, rotation, open state, swept clearance | Open/close changes visuals and collision; obstruction rejected; state survives reload |
| Seat | Seat/exit sockets, occupancy | Correct placement; mounting/dismounting; double occupancy rejected; removal cleans up the seat entity |
| Bed | Sleep socket, occupancy, dimension policy | Target sleep rules; occupied rejection; wake/exit and synchronized position |
| Storage | Capacity, original slots, item/lot mapping | Pagination, invalid slots, quantity, moving/breaking with contents, reload |
| Plant | Growth appearances, timing, yield mapping | Visible harvest/growth stages; target regrowth; persisted timing |
| Light | Active state, emissive and light policy | Appearance and lighting update together; network state and reload |
| Workstation | Recipe/processing policy, storage | Explicit target operations, menu validity and retained contents |
| Static | Geometry, selection and collision | Placement/removal, traversal and reload |

Rules describe target semantics. A source coffin may become a Minecraft bed;
that mapping retains a useful sleep interaction while the source game's entire
death/recovery system remains a separate mechanic. Record such decisions at the
capability level, without silently treating target behavior as source equivalence.

Transform sockets, hinge axes, collision, selection and visible parts through
the same instance transform. Pick representative rotations, scales and nearby
obstacles; an axis-aligned standalone object does not establish behavior in its
saved placement. Keep door opening angle, source growth timing, inventory mapping
and recipe approximations explicit. Ask the user when an unresolved mapping
changes their requested gameplay; routine implementation details need no vote.

Use [runtime verification](runtime-verification.md) for observable success and
failure checks. Seats and beds require both native state and actual rendered
body alignment; exits require supported, unobstructed standing space. A menu
requires real slot/state readback. A plant or light requires visible state change
as well as a server flag.

Render-plan caches must invalidate when relevant state changes. Door articulation
and plant growth cannot be frozen by a static optimization. An occupied object
also needs an explicit removal/owner-disconnect policy.
