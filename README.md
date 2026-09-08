# OAAX Technical Steering Committee

Notes and artifacts from the OAAX Technical Steering Committee. OAAX is a sandbox-stage
project of the [LF AI & Data Foundation](https://lfaidata.foundation/projects/oaax/).

Meeting agendas and notes are in [meeting-notes](meeting-notes), and the release plan is in
[roadmap](roadmap). See [CONTRIBUTING.md](CONTRIBUTING.md) for how to add either.

## Members

| Name | Affiliation | Role |
| ---- | ----------- | ---- |
| Ayoub Assis | Network Optix | Hardware vendor liaison, Core development |
| Josef Joubert| Network Optix | Core development, Tutorials and examples|
| Maxim Podstrechny | Network Optix | Tutorials and examples, Infrastructure and CI, Documentation |
| Robin van Emden | Network Optix | LF liaison, Community relations, Marketing |

## Roles

- **Hardware vendor liaison.** Point of contact for accelerator vendors (Intel, NVIDIA, Hailo,
  DEEPX, MemryX, SiMa, …) integrating their runtime against the OAAX spec.
- **Community relations.** Issue triage, contributor onboarding, and answering questions from
  people outside the TSC.
- **LF liaison.** Interfaces with LF AI & Data Foundation staff, tracks the project's
  sandbox-to-incubation progression, and flags Antitrust Policy / Code of Conduct concerns.
- **Infrastructure and CI.** Keeps the build pipelines, CI runners, and package/artifact hosting
  working across the vendor backends.
- **Documentation.** Keeps the spec and integration guides current as the project changes.
- **Tutorials and examples.** Maintains walkthroughs and sample integrations showing how to use OAAX with real hardware backends.
- **Core development.** TODO
- **Marketing.** Public messaging about the project — blog posts, talks, and social presence.

## How it works

- **Meetings.** First Tuesday of each month, 16:00 CEST. Anyone may attend and speak; only
  members vote.
- **Quorum.** A simple majority of filled seats. Without quorum the meeting is informational
  and nothing is decided.
- **Decisions.** Lazy consensus — no objection during the meeting, or after five business days
  on the [announce list](https://lists.lfaidata.foundation/g/oaax-announce). If a member calls
  a vote, a simple majority of those present decides; ties fail. Every decision is recorded in
  the notes with its vote count.
- **Notes.** The moderator rotates, and whoever moderates commits the notes within 48 hours.
  Merged notes are corrected by a new PR, never rewritten.
- **Agenda.** Open an issue labelled `tsc-agenda` saying in one line what decision you want
  the TSC to make.

Meetings are governed by the
[LF Antitrust Policy](https://www.linuxfoundation.org/legal/antitrust-policy) and the project
[Code of Conduct](https://github.com/OAAX-standard/OAAX/blob/main/CODE_OF_CONDUCT.md).

## License

[Apache-2.0](LICENSE), matching the rest of the project.
