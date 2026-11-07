I've reproduced the issue:

**Environment Setup**

No specific environment needed - just the `design-system` repo cloned locally and open in a text
editor.

**Steps to Reproduce**

1. Look at all the files in `.github/workflows/`. None indicate they are to autofill the "hours"
   field.
2. Perform a repo-wide search on "hours". Nothing shows up.

**Reproduction Evidence**

- **Commit showing reproduction:** none
- **Screenshots/logs:**

Files in `.github/workflows/` via `tree`:

```plaintext
├── build-documentation.yaml
├── build-tokens.yaml
├── create-token-pr.yaml
├── deploy-documentation.yaml
├── dry-run-publish.yaml
├── e2e-tests.yaml
├── fetch-icons-v9.yaml
├── fetch-icons.yaml
├── label-stale-review-prs.yaml
├── lint.yaml
├── playwright-tests.yml
├── pr-title-lint.yaml
├── release-documentation.yaml
├── release.yaml
├── scripts
│   ├── check-packages-on-npm.mjs
│   ├── icons.mjs
│   └── validate-icons.mjs
├── snapshot-tests.yaml
├── sonar-analysis.yaml
├── stale.yaml
├── unit-tests.yaml
├── validate-icon-downloads.yaml
└── visual-tests.yaml

2 directories, 23 files
```

Search results from step 2:

```plaintext
6 results - 4 files

apps/documentation/src/stories/misc/migration-guide/migrationv9-10.component.ts:
  1074                                <code-block
  1075:                                 code=${`<!-- template.html -->\n<ngb-timepicker\n  [(ngModel)]="appointmentTime"\n  [seconds]="true"\n  [spinners]="true"\n  [meridian]="false"\n  [hourStep]="1"\n  [minuteStep]="5"\n  [secondStep]="10"\n  [readonlyInputs]="false"\n></ngb-timepicker>`}
  1076                                ></code-block>

  1100                                  <li>
  1101:                                   <strong>Step behavior (<code>hourStep</code>,
  1102                                    <code>minuteStep</code>, <code>secondStep</code>):</strong>

packages/icons/src/icons/post/report.json:
  13129            "Express 24/7",
  13130:           "Expressed 24 hours a day",
  13131            "Espresso 24 ore su 24",

packages/internet-header/CHANGELOG.md:
  801
  802: - Sanitized hours fields in footer against XSS "Incomplete multi-character sanitization" issue. (by [@imagoiq](https://github.com/imagoiq) with [#2807](https://github.com/swisspost/design-system/pull/2807))
  803

```

- **My findings:** There is no existing GitHub workflow (or something similar) to autofill the
  "hours" field in the associated GitHub project.
