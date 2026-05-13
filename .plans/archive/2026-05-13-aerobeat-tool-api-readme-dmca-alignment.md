# AeroBeat Tool API README DMCA Alignment

**Date:** 2026-05-13  
**Status:** Complete  
**Agent:** Chip 🐱‍💻

---

## Goal

Tighten the `aerobeat-tool-api` README so its premium/public-UGC and mod.io-facing wording matches the recently softened AeroBeat docs posture without broadening scope beyond a small truth-alignment pass.

---

## Overview

The larger DMCA / safe-harbor wording pass is already complete in `aerobeat-docs` and `aerobeat-vendor-modio`. The remaining adjacent follow-up is intentionally small: `aerobeat-tool-api` mostly reads carefully already, but its README should better distinguish AeroBeat’s current intended v1 workflow from any implication that the paid-workout / provider legal posture is fully settled.

This repo should continue to describe `aerobeat-tool-api` as the AeroBeat-facing identity/access/entitlement layer above the vendor seam. The point is not to weaken that contract. The point is to keep the README from sounding more legally conclusive than the current docs now do. That means a tight audit, a minimal README wording edit, and a quick QA pass.

This is a README-only truth-alignment pass unless the audit finds a very small adjacent wording dependency that would be misleading if left unchanged.

---

## REFERENCES

| ID | Description | Path |
| --- | --- | --- |
| `REF-01` | Adjacent follow-up recommendation from the docs audit | `/home/derrick/.openclaw/workspace/projects/aerobeat/aerobeat-docs/.plans/2026-05-13-aerobeat-modio-dmca-doc-audit.md` |
| `REF-02` | Current repo README | `README.md` |
| `REF-03` | Softened AeroBeat public UGC policy wording | `/home/derrick/.openclaw/workspace/projects/aerobeat/aerobeat-docs/docs/architecture/v1-ugc-submission-and-review-policy.md` |
| `REF-04` | Softened moderation / DMCA wording | `/home/derrick/.openclaw/workspace/projects/aerobeat/aerobeat-docs/docs/gdd/user-content/policing-content.md` |
| `REF-05` | Softened account / entitlement wording | `/home/derrick/.openclaw/workspace/projects/aerobeat/aerobeat-docs/docs/architecture/account-identity-and-entitlements.md` |
| `REF-06` | Softened vendor monetization wording | `/home/derrick/.openclaw/workspace/projects/aerobeat/aerobeat-vendor-modio/README.md` |

---

## Tasks

### Task 1: Audit the README wording hotspot and define the minimum rewrite

**Bead ID:** `aerobeat-tool-api-55q`  
**SubAgent:** `primary`  
**Role:** `research`  
**References:** `REF-01` through `REF-06`  
**Prompt:** In `aerobeat-tool-api`, claim the bead on start. Audit `README.md` against the recently softened wording in `aerobeat-docs` and `aerobeat-vendor-modio`. Identify exactly where the README could still sound too settled about premium/public UGC, provider-backed ownership, or mod.io legal posture. Recommend the minimum wording changes needed to keep the README truthful and aligned without diluting the repo charter. Update the active plan with exact findings and the smallest file/section edit set.

**Folders Created/Deleted/Modified:**
- `.plans/`

**Files Created/Deleted/Modified:**
- `.plans/2026-05-13-aerobeat-tool-api-readme-dmca-alignment.md`
- `README.md` only if absolutely necessary for audit coherence

**Status:** ✅ Complete

**Results:** Audit complete against `REF-02` through `REF-06`.

Exact README audit:
- `README.md:32-38` is broadly aligned with `REF-03`/`REF-05`: free-to-play framing, free + premium workouts, reviewed public UGC, `mod.io Full Curation`, and official platform/store purchase paths all match the current intended v1 posture.
- `README.md:39` is the main wording drift hotspot. "provider-side ownership sync should rely only on official, non-deprecated surfaces we can legitimately support" is directionally right, but it sounds more settled than `REF-05`, which frames provider-backed premium ownership sync as the **current intended** seam only **where officially supported** and still **pending firmer provider/legal confirmation** on the paid-workout posture.
- `README.md:42` is slightly firmer than the current docs posture because "identity, access, entitlements, discovery, library sync, and downloads for approved/public content" can be read as a fully normalized public-content surface without the nearby caveat that some premium/public UGC distribution assumptions are still the current intended v1 route rather than a fully closed legal conclusion.
- `README.md:44` is already doing the right thing for review-authority drift: it explicitly says AeroBeat should not imply a separate authoritative AeroBeat-owned submission/review/status workflow, matching `REF-03` and `REF-04`.
- The README does **not** currently overclaim direct mod.io wallet/checkout ownership, but unlike `REF-06` it also does not explicitly warn that provider-backed premium/distribution posture should not be read as finally settled. That gap is small and can be fixed in the same strategic-framing block.

Minimum rewrite recommendation:
- Keep the file set to `README.md` only.
- Limit edits to the `## Current strategic framing` bullets plus, if needed, the immediately following paragraph.
- Smallest safe wording changes:
  - revise the ownership-sync bullet to say mod.io/provider-backed ownership sync is the **current intended** v1 seam, only **where officially supported via non-deprecated surfaces**, and still subject to **firmer provider/legal confirmation**;
  - lightly soften the paragraph at `README.md:42` so discovery/library/downloads for approved/public content are described as the current AeroBeat-facing responsibility **without implying the premium/public UGC legal posture is fully settled**;
  - leave the repo charter intact: `aerobeat-tool-api` remains the AeroBeat-facing identity/access/entitlement layer above the vendor seam.

Why this is the minimum: `README.md:44` already handles the custom-review-platform risk, and the repo does not otherwise need scope changes. The drift is concentrated in how settled the premium/public UGC ownership/distribution wording sounds, so a narrow wording pass in the existing strategic-framing section should be sufficient.

---

### Task 2: Apply the README wording alignment

**Bead ID:** `aerobeat-tool-api-g0j`  
**SubAgent:** `primary`  
**Role:** `coder`  
**References:** `REF-01` through `REF-06`  
**Prompt:** In `aerobeat-tool-api`, claim the bead on start. Apply the minimum README wording changes from the audit. Keep the AeroBeat-facing contract explicit, but avoid implying that premium-workout / provider legal posture is more settled than the current docs say. Run a proportionate validation/sanity check, commit/push by default, and update the active plan with exact results.

**Folders Created/Deleted/Modified:**
- `.plans/`

**Files Created/Deleted/Modified:**
- `.plans/2026-05-13-aerobeat-tool-api-readme-dmca-alignment.md`
- `README.md`

**Status:** ✅ Complete

**Results:** Applied the minimum README-only wording pass in the `## Current strategic framing` section.

Exact changes made:
- Updated the provider-sync bullet so it now says ownership sync should follow the **current intended v1 seam** only where **official, non-deprecated surfaces** exist that AeroBeat can legitimately support, and explicitly notes that **firmer provider/legal confirmation on the long-term paid-workout posture is still pending**.
- Softened the immediately following paragraph so `aerobeat-tool-api` remains the manager for **identity, access, entitlements, discovery, library sync, and downloads for approved/public content**, but frames that responsibility as part of the **current intended v1 model** rather than as a fully settled long-term legal/distribution conclusion.
- Left the repo charter intact: `aerobeat-tool-api` still reads as the AeroBeat-facing identity/access/entitlement layer above vendor seams, with no scope expansion and no changes outside the relevant strategic-framing block.

Outcome:
- The README now matches the Task 1 audit recommendation and better aligns with `REF-03`, `REF-05`, and `REF-06` without weakening the package boundary.
- Proportionate validation passed with `git diff --check` on the changed files.
- Commit/push completed on `main` in `9981dd9` (`docs: soften tool-api README legal posture`).

---

### Task 3: QA/audit the final README pass

**Bead ID:** `aerobeat-tool-api-5x8`  
**SubAgent:** `primary`  
**Role:** `qa` / `auditor`  
**References:** `REF-01` through `REF-06`  
**Prompt:** In `aerobeat-tool-api`, claim the bead on start. Independently verify that the README now matches the softened AeroBeat and vendor-doc posture without weakening the repo’s technical charter. Make only minimum necessary fixes if needed, run a proportionate validation/sanity check, and close only if the final README is concise, truthful, and aligned.

**Folders Created/Deleted/Modified:**
- `.plans/`

**Files Created/Deleted/Modified:**
- `.plans/2026-05-13-aerobeat-tool-api-readme-dmca-alignment.md`
- `README.md` only if minimum necessary fixes are required

**Status:** ✅ Complete

**Results:** Final QA/audit completed against `REF-02` through `REF-06`.

Audit findings:
- `README.md:32-40` now aligns with the softened posture in `REF-03`, `REF-04`, `REF-05`, and `REF-06`: it preserves the free-to-play + free/premium workout framing, keeps **mod.io Full Curation** as the current v1 gate, requires official platform/store purchase paths, and explicitly softens provider-backed ownership sync to the **current intended v1 seam** pending firmer provider/legal confirmation.
- `README.md:42-44` keeps the repo charter explicit and intact: `aerobeat-tool-api` still owns the AeroBeat-facing identity/access/entitlement/discovery/library/download contract, while clearly avoiding any claim that AeroBeat already owns the authoritative v1 submission/review/status workflow.
- No wording found that still overstates provider certainty, legal certainty, or direct AeroBeat ownership of the current public review gate.
- No unnecessary scope drift was introduced: the change remains confined to the strategic-framing block, with no repo-boundary expansion or policy broadening elsewhere in the README.

Validation evidence:
- Reviewed the active plan, final `README.md`, and the coherence references in `REF-03` through `REF-06`.
- Verified the landed README wording directly at `README.md:32-44`.
- Confirmed the repo is clean after the prior README commit and that `git diff --check` passes.

Disposition:
- Pass. No additional README edits were necessary.
- No commit/push performed because the audit required no code or doc changes.

---

## Final Results

**Status:** ✅ Complete

**What We Built:** A README-only wording alignment pass for `aerobeat-tool-api` that keeps the repo positioned as the AeroBeat-facing identity/access/entitlement layer while softening premium/public-UGC and provider/legal-posture language to match the current AeroBeat docs set.

**Reference Check:** `REF-02` now coheres with `REF-03`, `REF-04`, `REF-05`, and `REF-06`. The README preserves the explicit repo charter, keeps mod.io Full Curation as the current v1 public gate, avoids overstating provider-backed premium ownership/legal certainty, and does not introduce extra scope beyond the targeted strategic-framing block.

**Commits:**
- `9981dd9` - `docs: soften tool-api README legal posture`
- `b173668` - `docs: record tool-api README task result`

**Lessons Learned:** For adjacent doc-alignment passes, the safest pattern is to keep the package/repo charter firm while softening only the sentences that imply more provider or legal certainty than the current source-of-truth docs actually support.

---

*Drafted on 2026-05-13*
