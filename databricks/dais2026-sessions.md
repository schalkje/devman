# Sessions

In this document I gather information about the sessions I have reviewed.

Sessions are scored on two dimensions (industry-style conference evaluation):

- **Value (Relevance / Impact)**: How useful this is for my work.
- **Quality (Clarity / Structure / Delivery)**: How well the session is presented.

Use a 1 to 5 scale for both dimensions:

- **1**: Poor - little value or hard to follow, unstructured
- **2**: Fair - some useful points, but weak clarity/flow
- **3**: Good - useful and understandable, but not exceptional
- **4**: Very good - strong value, clear structure, easy to follow
- **5**: Excellent - high impact, very clear, well-structured, actionable

Overall recommendation (optional):

- **Skip**: mostly 1-2
- **Optional**: around 3
- **Recommended**: around 4
- **Must watch**: around 5

Common industry criteria for talks:

- Relevance to audience or business goals
- Clarity of message and communication
- Logical structure and flow
- Technical depth and correctness
- Actionable takeaways
- Evidence (demo, data, examples)

## Technology overview
|technology|State|Remarks|
|---|---|---|
|metric views|||
|onthology|||
|lakehouse rt|||
|LTAP||Joining OLTP and OLAP; joiing delta and lakebase, with one storage layer, just different engines|


Governance Hub|beta|Nice, want access asap


## Ontology

|||
|---|---|
title|A–Z of Unity Catalog Business Semantics: Open and Unified Semantics for Agents, Apps and BI
value|5
quality|5
topics|Metrivs views, Glossary, OSI
url | https://www.databricks.com/dataaisummit/session/z-unity-catalog-business-semantics-open-and-unified-semantics-agents

## Omnigent

|||
|---|---|
title | Agent Ops on Databricks, Powered by Omnigent
value | 5
quality | 1
topics | Omnigent



## Unity Catalog

|||
|---|---|
title | Unity Catalog: Advanced, Field-Proven Patterns from Experts
value | 5
quality | 5
topics | Unity Catalog
url | https://www.databricks.com/dataaisummit/session/unity-catalog-advanced-field-proven-patterns-experts

|||
|---|---|
title | Your guide to fine-grained access control: Permissions, ABAC, and RBAC in Unity Catalog
value | 5
quality | 5
topics | Access control, ABAC, RBAC, Governance Hub
url | https://www.databricks.com/dataaisummit/session/your-guide-fine-grained-access-control-permissions-abac-and-rbac-unity

### Discussed capabilities and release status

- Granular permissions in Unity Catalog to improve task-fit access control: **Private Preview**
- Split of `MANAGE` into `READ METADATA` and `MANAGE ACCESS CONTROL`: **Private Preview**
- Split of broad `MODIFY` into finer actions (`INSERT`, `UPDATE`, `DELETE`, etc.): **Private Preview**
- ABAC policies (attribute-based access control), including row filters and column masks: **GA**
- ABAC content protection extended to AI services (MCP/model-service scenarios): **Public Preview**
- ABAC grant and deny permission policies: **GA**
- Deny policy pattern to block data engineers from granting access on created tables: **GA**
- Governed tags + identity/request attributes for dynamic policy conditions: **GA**
- Automated data classification for sensitive tags (DatabricksIQ): **Public Preview**
- Governed tag propagation to derived assets (for example CTAS/view flows): **Public Preview**
- RBAC with role assumption to isolate active access context: **Private Preview**
- RBAC option to assume any group: **Public Preview**
- Metastore-level policies: **Public Preview**
- Policy composition for row filters and masking precedence: **Public Preview**
- Predefined masking functions for common protection patterns: **Public Preview**
- Governance Hub for governance visibility and operations: **Beta**
- Governance Hub access insights (who can access what and why): **Public Preview**



## Low value or low quality