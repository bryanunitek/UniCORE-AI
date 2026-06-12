# STANDARD-ENVELOPE.md

**UniCORE-AI developer standard envelope — extends TrueAI standard envelope.**

This document supplements the TrueAI standard envelope ([`bryanunitek/TrueAI` `workspace-doctrine/v1/STANDARD-ENVELOPE.md`](https://github.com/bryanunitek/TrueAI/blob/main/workspace-doctrine/v1/STANDARD-ENVELOPE.md)) with UniCORE-AI-specific rules for Claws working on the UniCORE reference architecture.

If a rule here conflicts with the TrueAI standard envelope, the TrueAI standard envelope wins (it is the lower layer). This document only adds; it does not override.

---

## Additional rules for UniCORE-AI developers

### Reference architecture integrity

The UniCORE reference architecture is a shared substrate. Changes to it affect every Solution built on top of UniCORE (UniCORE.Law, UniCORE.GVB, and future verticals). A standard-envelope UniCORE-AI developer Claw:

- **MUST** propose architectural changes (new substrate services, changed interfaces, removed invariants) via a written design document surfaced to the human authority before any code is written
- **MUST NOT** merge architectural changes to `main` without human-authority sign-off
- **MUST** maintain the public gift surface integrity — UniCORE / UniSaaS / Foundation triad repos are read-only for standard-envelope Claws unless the human authority explicitly grants write access for a specific purpose

### Vertical isolation

Each vertical Solution (Law, GVB, future Banking, future Healthcare) is a separate repo family. A standard-envelope Claw working on one vertical:

- **MAY** read reference architecture code from other verticals for context
- **MUST NOT** write to another vertical's repo without explicit human-authority grant for that specific repo

### Test discipline

UniCORE-AI developer Claws follow the test posture documented in the GVB-Claw and Law-Claw workspaces:

- **GVB.Tests** uses FluentAssertions; **Law.Module.Tests** uses bare xUnit
- Each substrate service project has a corresponding test project following the same `[ProjectName].Tests` naming convention
- Tests are not optional. A change that breaks existing tests is surfaced to the human authority as a failure, not as a proposed change

### Naming and type collisions

Before adding a new public type (class, record, interface, struct) to any UniCORE-AI project, the Claw:

- Runs a collision check: `grep -rnE 'public (sealed )?record <Name>|public class <Name>' --include='*.cs'` across the relevant solution
- Verifies the new type name does not already exist in any referenced project
- If a collision is found, renames before committing

### Vendor package discipline

When adding or updating NuGet package references:

- Verify the package version against the vendor's own published template or nuspec (not against a stale lock file)
- For packages already pulled transitively, the explicit floor must be `>=` the maximum transitive floor across all referenced projects
- Run `dotnet list <SolutionOrProject> package --include-transitive | grep -i <package>` to verify resolved version before committing

---

## What this does NOT change

The TrueAI standard envelope rules remain in force. This document only adds UniCORE-AI-specific operational rules on top. The following are NOT changed by this document:

- The sub-agent prohibition (still absolute — no spawning under any circumstances)
- The auto-update prohibition (doctrine updates still require human authentication)
- The repo scope discipline (still enforced by doctrine, not by GitHub permissions alone)
- The truth posture (still Foundation-first, truth-before-warmth)

---

## Cross-references

- TrueAI [`workspace-doctrine/v1/STANDARD-ENVELOPE.md`](https://github.com/bryanunitek/TrueAI/blob/main/workspace-doctrine/v1/STANDARD-ENVELOPE.md) — the base standard envelope
- TrueAI [`workspace-doctrine/v1/FOUNDATION.md`](https://github.com/bryanunitek/TrueAI/blob/main/workspace-doctrine/v1/FOUNDATION.md) — the Foundation layer
- UniCORE-AI [`developer-doctrine/v1/PRIVILEGED-ENVELOPE.md`](PRIVILEGED-ENVELOPE.md) — the privileged envelope (Team UniCORE only)
- UniCORE-AI [`developer-doctrine/v1/VERTICAL-ENTRY.md`](VERTICAL-ENTRY.md) — how new verticals enter the reference architecture
