# Roadmap

What the project intends to ship, and when. Kept here so the plan is visible without reading
branch activity.

Dates are targets set by the TSC, not commitments. Changes are decided in a meeting and
recorded in the [notes](../meeting-notes) before this file is updated.

## 2.0 — target [October] 2026

A breaking revision of the standard. Development happens on the `oaax-v2` branches and merges
to `main` at release.

| Area | Change |
|---|---|
| Runtime interface | One runtime can host several models on the same accelerator; models load from memory as well as from disk |
| Request tracking | Every inference request carries an ID that is echoed on its result, so multiple requests can be in flight |
| Non-blocking inference | Wait with a deadline instead of polling for results |
| Introspection | Query the active device, models loaded, requests in flight and how busy the accelerator is |
| ABI | A strict, versioned surface — runtimes export only the documented OAAX API, so two vendors' runtimes can load into one application |
| Lifecycle | Load, unload and re-initialise correctness on Linux and Windows |

**Hardware at release:** CPU reference implementation, Intel (OpenVINO), NVIDIA (CUDA/cuDNN),
Hailo (HailoRT 4.17–4.20), DEEPX, MemryX, SiMa.

## 2.1 — TBD

Not yet scoped. Candidates are tracked as `tsc-agenda` issues.

## How this is maintained

Each release has a milestone in the repository it ships from, and each heading here links to
it. To propose something, open an issue labelled `tsc-agenda` describing the change and its
compatibility impact.
