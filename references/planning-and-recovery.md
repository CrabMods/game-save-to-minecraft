# Planning, user decisions and recovery

## Match effort to the requested result

Infer intent from the request and existing decisions before presenting options.
Use these as scope choices, not fixed time estimates or mandatory questions.

| Outcome | Work to prioritize | Completion boundary |
| --- | --- | --- |
| Feasibility or visual preview | Identify the save/client, recover a small representative region, trace one object end to end and expose missing bindings | Describe exactly what was recovered and viewed; a preview does not establish playable migration |
| Working migration | Recover the selected content, implement its target behaviors, run native and packaged-client checks, and correct visible interaction failures | Requested content and interactions work in the selected target; remaining exclusions and untested environments are explicit |
| Complete selected-world delivery | Reconcile all in-scope instances/assets, exercise relevant material and transform families, persistence, resume, traversal and agreed compatibility/performance targets | Final source-bound artifact meets the agreed acceptance contract; exact exclusions remain visible |

Without a specified effort mode, default to the working migration. For an
unfamiliar format, first prove one saved instance can be recovered, rendered,
used and reloaded. Include representative difficult content in that slice: a
composite/rotated object, a dynamic object and a source inventory when present.
Then expand coverage; do not repeatedly polish the easy fixture while leaving
the selected source world unexamined.

Spend early effort on source identity and a functioning end-to-end path. Profile
when scale or an observed bottleneck warrants it. Define the user's actual goal
before pursuing shader parity, all source mechanics or another loader/version.
Respect explicit time, compute, disk and gameplay constraints. Do not invent a
fixed token budget, promise a runtime, or reduce selected coverage silently.

## Ask questions that change the work

Use the smallest focused question that resolves the uncertainty. State the
observation, the practical choice and your recommendation. Offer a few concrete
options when useful; allow the user to describe another outcome.

- If supplied saves/clients disagree and the matching pair cannot be inferred,
  identify those candidates and ask which pair/region to migrate.
- Ask about source appearance versus a Minecraft-style reinterpretation when
  the requested visual goal is unclear. Do not ask for a style choice again
  after the user has made it.
- Ask when semantics require a product choice: preserve a resource quantity,
  map it to native items, reproduce a workstation's recipes, or keep only its
  storage. Explain the consequence; implement routine plumbing independently.
- If the requested world cannot fit an agreed budget or a major new engine
  investigation is necessary, show the smallest useful proven result and the
  remaining work. Ask whether to extend the budget, select a smaller region,
  accept a specific approximation or stop at the current evidence.
- Obtain a decision before destructive placement or an unrequested change to
  the user's live game, original save or distribution rights. Existing scoped
  authorization remains valid; do not add a new permission gate for each tool.

Do not ask the user to diagnose an adapter bug, locate an already supplied path,
or answer a question the available artifacts can establish. While an essential
answer is pending, continue independent investigation or tests; do not execute
the branch whose result depends on that answer. Silence is not a scope decision.

## Resolve the observed blocker

Installing the Skill supplies instructions. It does not install REA, source
decoders, Java, a loader or a test runner. Use actual available tools and their
installed schemas/versions. Working tools do not need repeated readiness checks.

| Observation | Next investigation or action |
| --- | --- |
| Unknown save/container or a missing client dependency | Inspect format/version and the declared dependency; use a matching source runtime/export route when available. Keep unsupported records unresolved rather than substituting the demo decoder |
| Tool absent, disconnected, blocked or provider unavailable | Distinguish availability from host permission and input-format failure. Repair only the observed problem within scope; continue supported work without claiming the unavailable result |
| Exporter heartbeat but incomplete world | Check source streaming, object enumeration, terminal completion and counts. A process still running or an empty partial export is not a completed recovery |
| Meshes present but parts invisible or malformed | Trace renderer hierarchy, variants, transforms, alpha/material channels and growth states before simplifying geometry or dropping objects |
| Interaction handler succeeds but player use fails | Trace target selection, normal input/packet, server state, client state, rendered pose and exit separately; use the runtime verification guide |
| Test setup fails on a valid collision-free asset | Frame and select it using appropriate visual/selection bounds. Correct the harness assumption without changing production collision or weakening behavior assertions |
| Counts/appearance differ after an optimization | Check loaded identities, culling, cache invalidation and renderer fallback before treating faster timing as a success |
| Import stops mid-object or on world limits | Retain the failure and source ID. Reconcile actual placed fragments with the saved cursor; resume idempotently or repair only owned data, without resetting user inventory or overwriting unrelated blocks |

After a failed attempt, record the first failing boundary and change a specific
hypothesis, input or implementation before retrying. Repeating a rejected call,
identical decode or expensive full suite without new information is not progress.
Preserve the last useful output and the unresolved record; do not restart the
entire migration to conceal partial failure.

## Leave resumable state

Reuse the project's existing report/receipt structure. Keep a compact record of
source/client identity, selected scope, decisions, artifact hashes, mapped and
unresolved counts, current stage, first failure and the next concrete action.
Keep detailed source identities and player data private. For asynchronous work,
retain the run/job identifier and terminal/exit receipt; do not launch a second
run against the same world or modify the inputs of an in-flight verification.

A passed receipt covers its exact inputs, program, resources, environment and
scenarios. Reuse a matching valid receipt under project policy; invalidate only
affected contracts after a change. Keep provenance and original failures when
adding a new result. State whether completion is a preview, a tested migration
or a partial result still awaiting a named input or test lane.
