# IDP Workflow Configurations

This repository contains **reference YAMLs** and supporting assets for Harness Proof-of-Value (POV) engagements.  
Each use case includes two YAML types:

| YAML | README | Purpose |
|------|--------|---------|
| `*-pipeline.yml` | `PIPELINE-README.md` | Harness pipeline that orchestrates app provisioning (scaffolds app into monorepo, opens PR, optional Jira/ServiceNow/IDP registration). |
| `*-workflow.yml` (form) | `WORKFLOW-FORM-README.md` | IDP Workflow Form that developers use in the portal; collects inputs, validates repo access, and triggers the pipeline. |

---

## Repository Layout

```
idp-workflow-configs/
├─ harness/
│  └─ e2e-react-app-provisioning/
│     ├─ e2e-react-app-provisioning-pipeline.yml
│     ├─ PIPELINE-README.md
│     ├─ e2e-react-app-provisioning-workflowform.yml
│     └─ WORKFLOW-FORM-README.md
├─ reusable-templates/
│  └─ <idp_use_case>/
│     ├─ <idp_use_case>-pipeline.yml
│     ├─ PIPELINE-README.md
│     ├─ <idp_use_case>-workflowform.yml
│     └─ WORKFLOW-FORM-README.md
├─ scripts/
│  └─ scaffold-customer-workflow.sh
└─ <customer_name>/
   └─ copied templates
```

---

## Usage

### For SEs (Setting up a POV)
1. Create a new customer folder (e.g., `omf/`).  
2. Use the provided script to copy reference YAMLs into that folder:  
   ```bash
   ./scripts/scaffold-customer-workflow.sh omf e2e-react-app-provisioning
   ```
   This copies both pipeline and workflow form YAMLs, along with their READMEs.
3. Update connector refs, secrets, and defaults to match the customer’s environment.

### For Customers (Viewing/Using Configs)
- **Pipeline YAML** defines the automation steps Harness executes when provisioning a new app.  
- **Workflow Form YAML** defines the developer-facing form in IDP that collects inputs and triggers the pipeline.  

Each YAML has its own README explaining parameters, prerequisites, and usage.

---

## Notes
- Keep customer-specific changes inside the `<customer_name>/` folder.  
- Do not modify the reference YAMLs directly—copy them via the script so you always preserve a clean baseline.  
- READMEs are paired with each YAML for easy reference during POVs.
