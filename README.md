# Agentic Recipes for Disaster

A collection of focused agent skills, each documented by a `SKILL.md` file. Skills are grouped by domain and can include supporting scripts, references, and assets when needed.

## Repository layout

```text
.
├── skills/
│   └── <category>/
│       └── <skill-name>/
│           ├── SKILL.md
│           ├── scripts/       # optional executable helpers
│           ├── references/    # optional supporting documentation
│           └── assets/        # optional files used by a skill
├── templates/
│   └── SKILL.md
├── docs/
│   └── authoring.md
├── LICENSE
└── README.md
```

## Categories

Choose the closest category for each skill. If a skill spans domains, place it where its primary workflow belongs; cross-link it from this list or its documentation when useful. Add a new category when the current choices do not fit.

| Category | Scope |
| --- | --- |
| [`software-design/`](skills/software-design/) Software Design | Architecture, system design, APIs, modeling, and technical decision making. |
| [`software-engineering/`](skills/software-engineering/) Software Engineering | Programming, debugging, testing, code review, and maintenance. |
| [`data-and-ai/`](skills/data-and-ai/) Data And Ai | Data analysis, databases, machine learning, and AI workflows. |
| [`web-and-app-development/`](skills/web-and-app-development/) Web And App Development | Websites, user interfaces, mobile apps, and application delivery. |
| [`it-administration/`](skills/it-administration/) It Administration | Systems administration, cloud, networking, DevOps, and support operations. |
| [`security-and-privacy/`](skills/security-and-privacy/) Security And Privacy | Security engineering, threat analysis, privacy, and incident response. |
| [`writing-and-editing/`](skills/writing-and-editing/) Writing And Editing | Creative, professional, technical, and editorial writing. |
| [`research-and-analysis/`](skills/research-and-analysis/) Research And Analysis | Research planning, source evaluation, synthesis, and decision support. |
| [`text-and-document-work/`](skills/text-and-document-work/) Text And Document Work | Text transformation, document formatting, conversion, and information extraction. |
| [`image-and-graphics/`](skills/image-and-graphics/) Image And Graphics | Image editing, illustration, diagrams, layout, and visual asset workflows. |
| [`audio-and-video/`](skills/audio-and-video/) Audio And Video | Audio production, transcription, video editing, and multimedia workflows. |
| [`entertainment-and-games/`](skills/entertainment-and-games/) Entertainment And Games | Games, interactive fiction, media discovery, and recreational activities. |
| [`business-and-finance/`](skills/business-and-finance/) Business And Finance | Business operations, project planning, accounting, and financial analysis. |
| [`education-and-learning/`](skills/education-and-learning/) Education And Learning | Teaching, tutoring, curriculum design, and learning support. |
| [`science-and-mathematics/`](skills/science-and-mathematics/) Science And Mathematics | Scientific methods, domain research, quantitative reasoning, and modeling. |
| [`productivity-and-automation/`](skills/productivity-and-automation/) Productivity And Automation | Personal workflows, task automation, scheduling, and knowledge management. |
| [`it-support-and-troubleshooting/`](skills/it-support-and-troubleshooting/) It Support And Troubleshooting | End-user help, diagnostics, device setup, and practical technology support. |
| [`accessibility-and-localization/`](skills/accessibility-and-localization/) Accessibility And Localization | Accessible content and interfaces, translation, and cultural adaptation. |
| [`home-and-lifestyle/`](skills/home-and-lifestyle/) Home And Lifestyle | Household planning, cooking, travel preparation, and everyday life tasks. |
| [`health-and-wellbeing/`](skills/health-and-wellbeing/) Health And Wellbeing | General wellness education, fitness planning, and supportive routines. |
| [`law-and-public-services/`](skills/law-and-public-services/) Law And Public Services | Legal information workflows, civic processes, and public-service navigation. |
| [`hardware-and-iot/`](skills/hardware-and-iot/) Hardware And Iot | Electronics, embedded systems, device integration, and physical computing. |

## Skills

No skills have been added yet. Add one directory per skill under the most relevant category; use lowercase kebab-case names and put its instructions in `SKILL.md`.

See [the authoring guide](docs/authoring.md) and start from [`templates/SKILL.md`](templates/SKILL.md).

## License

This project uses the MIT License. See [LICENSE](LICENSE).
