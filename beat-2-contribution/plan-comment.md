Here is my plan:

**Analysis**

There is no GitHub workflow under `.github/workflows/` that auto-fills the "Hours" field based on
the "Time spent (h)" field.

**Proposed Solution**

I will add a new file (e.g. `autofill-hours.yml`) in `.github/workflows/` that runs when a GitHub
project item is edited. If the "Hours" field is empty, the workflow will autofill it with the value
from "Time spent (h)" field using a GraphQL query sent to `gh api`.

I will NOT be changing anything out the `.github/workflows/` folder, especially NOT any production
code or files since those are out of scope for a GitHub-workflows-oriented issue.

**Implementation Plan**

1. Create `.github/workflows/autofill-hours.yml`.
2. Add config to the newly created file to autofill "Hours", if empty, with the value from "Time
   spent (h)" using `gh api graphql`.
3. Test the workflow using `act`.
