# Databricks Governance at scale

Goal ABAC: prevent data duplication

SE: You can just creat view too

## Presenter feedback

It was an unstructured course; mainly clicking through the material; 
lot's of: I think...; I think there should be...; you can read through this yourself; we don't have time... (when it get's interesting)

the entire course, felt, like doing a next-next-finish training on the online learn platform.

Genie answering most of the questions (reasonably ok, but not great answers)

People from support; answered some of the real questions and made up for some real value.






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

- [ ] Wil cloning a table, also clone the tags and policies?


- [x] How can users know wether a rowfilter has been applied, so they do not see the full data?
- [x] How is it possible to create rules, so people cannot see details of row (e.g. salary > 100.000), but still can count all employees
  - You can create some kind of aggregate tables; that are generally accessible; 

- [ ] who can create tags?

### Learnings

- You cannot shallow clone a table with a row level policy
- 

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


## Live Q&A assistant

```markdown
 Act as my Live Q&A assistant during an in-person training delivery. When I ask questions in chat (often via voice), research the answer using public Databricks docs, official references, and workspace context. Don't reply in chat — instead, append each Q&A as a new markdown cell at the end of this notebook so students can use it as a takeaway. Include relevant public links. Auto-approve all edits. Don't stop working on a previous question if I send a new one — queue them up and handle each in order.
 ```


### Data quality monitoring


What is the overlap with https://databrickslabs.github.io/dqx/

Some of the functionality is trickling into databricks.


https://databrickslabs.github.io/dlt-meta/


## Youtube idea

Are you fe up with databricks ABAC too
It is too expensive in run time; it does not do workspace binding; keeping things in control is impossible.

There should be a better way

Morpheus