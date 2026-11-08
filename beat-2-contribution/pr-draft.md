# chore(workflows): autofill "Time Spent (h)" field from "Hours" when an issue closes

Fixes #8480

## 📄 Description

Added `autofill-time-spent.yaml` to `.github/workflows/` that runs manually or whenever an issue is
closed. There are multiple cases:

- If the issue does **not** belong to a project -> log and return early.
- If the issue belongs to a project:
  - If "Time Spent (h)" is filled -> logs and return early.
  - If "Hours" is empty (or missing) -> logs and return early.
  - Otherwise -> fill "Time Spent(h)" with the value in "Hours", log, and return.

## 🚀 Demo

Tested manually via issues and a project on my own fork since `act` can't emit Projects events.

| Case                                                           | Output                                                | Sample run link                                                                                       |
| -------------------------------------------------------------- | ----------------------------------------------------- | ----------------------------------------------------------------------------------------------------- |
| "Time Spent (h)" not empty ("Hours" either empty or not empty) | "Time Spent (h)" is already set to 71. Nothing to do. | [View run](https://github.com/krishpatel2067/design-system/actions/runs/42435552893/job/128593502921) |
| "Hours" is empty ("Time Spent (h)" empty)                      | "Hours" is empty. Skipping.                           | [View run](https://github.com/krishpatel2067/design-system/actions/runs/42435500796/job/128593341777) |
| "Time Spent (h)" is empty; "Hours" is not empty                | Set "Time Spent (h)" to 2.067 for #1.                 | [View run](https://github.com/krishpatel2067/design-system/actions/runs/42435408713/job/128593054148) |
| Issue not on a project                                         | #6 is not on a project. Skipping.                     | [View run](https://github.com/krishpatel2067/design-system/actions/runs/42435580195/job/128593588185) |

---

## 🔮 Design review

If visual elements have been modified or added, please ping a member of the design team to ask them
for a design review.

- [ ] Design review done
- [ ] No design review needed

**N/A** - no visual elements were modified or added.

## 🧪 Visual regression tests

- [ ] Visual changes detected and approved _(Check this box if VRT fails and changes are
      intentional)_

**N/A** - no visual elements were modified or added.

## 📝 Checklist

- ✅ My code follows the style guidelines of this project
- 🛠️ I have performed a self-review of my own code
- ~~📄 I have made corresponding changes to the documentation~~ (**N/A** - as far as I know,
  workflows aren't documented separately)
- ⚠️ My changes generate no new warnings or errors
- ~~🧪 I have added tests that prove my fix is effective or that my feature works~~ (**N/A** -
  manual testing needed)
- ✔️ ~~New and~~ Existing unit tests pass locally with my changes

## Other Info

Key assumptions:

- **Both fields are Number fields.** Otherwise, the script ignores them.
- **Closing the issue counts as Done.** The workflow also runs for issues closed as "not planned",
  which could put estimates into the time stats for work nobody did.
- **Access token is PAT and has project write access**: I used `SWISSPOSTDEVS_ACCESS_TOKEN` as per
  some of the other workflows. Please confirm if that is a PAT and has `project` write access, or
  whether I should use a different token.

Note:

- I didn't add a checkbox to the PR template to fill out "Hours" as it was marked as "(tbd)", and I
  didn't receive a response to my question on the issue thread about that.
- I didn't add a changeset since I didn't touch any packages.

Disclosure: I used Claude Opus 5.5 for planning and implementation, but I reviewed the final work
myself.

Happy to adjust anything if you have suggestions.
