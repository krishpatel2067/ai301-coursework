Here is my plan:

**Analysis**

There is no GitHub workflow under `.github/workflows/` that auto-fills the "Time spent (h)" field
based on the "Hours" field.

**Proposed Solution**

I will add a new file (e.g. `autofill-hours.yml`) in `.github/workflows/` that runs when a GitHub
project item is edited. If the "Time spent (h)" field is empty, the workflow will autofill it with
the value from "Hours" field using a GraphQL query sent to `gh api`.

I will NOT be changing anything out the `.github/workflows/` folder, especially NOT any production
code or files since those are out of scope for a GitHub-workflows-oriented issue.

**Implementation Plan**

1. Create `.github/workflows/autofill-hours.yml`.
2. Add config to the newly created file to autofill "Time spent (h)", if empty, with the value from
   "Hours" using `gh api graphql`.
3. Test the workflow using `act`.
