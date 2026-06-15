# Databricks Governance at scale

Goal ABAC: prevent data duplication

SE: You can just creat view too

## Apply policies:

Teraform or DAB

use terraform policies to automatically generate...

Governed tags are set at the corporate level? not on the lower levels.

  

## questions

- [ ] When is ABAC applicable and when not?
- [ ] Why and when do we need terraform?
- [ ] Is the tagging auditable over time?
  - [ ] How can I tell is a specific user had access to a data column/row 
    - [ ] at a certain point in time
    - [ ] somewhere in the a period

- [ ] There was an example about the env tag; what dos it mean?

- What are dynamic views?
- How do you manage the tags?
- How do you separate based on environment/workspace?
  - Can we separate on Azure subscription?
  - 

- How is ABAC is connected to users?

- How does this perform?
  - Can you say something about how this works?
  - how does it compare to views?

#### A-B testing

Tool: databricks **security analysis tool** put in the user names; show actual

https://github.com/databricks-industry-solutions/security-analysis-tool/tree/main

https://databricks-industry-solutions.github.io/security-analysis-tool/

https://www.databricks.com/blog/2023/02/03/announcing-multi-cloud-support-security-analysis-tool-sat.html



### nice to know

- How do you prove that all sensitive information is not reaching the wrong people?
- 

### scenario's

Access when 

## Random learnings

- **Delta sharing** is renamed to **open sharing**

## Nice remarks

- **Tokenomics** optimizing token usage


