# Analysis Playbooks

Use these heuristics when converting raw input into BA outputs.

## Requirement Elicitation

Look for:

- business objective
- actor or user type
- trigger
- normal flow
- exceptions
- business rules
- data inputs and outputs
- dependencies
- measures of success

Flag ambiguity when:

- multiple stakeholders imply different outcomes
- a rule has exceptions but the exceptions are not defined
- acceptance wording is subjective
- the source mixes business need with a chosen implementation

## Story Refinement

Prefer stories that:

- describe one business outcome
- can be tested independently
- have explicit acceptance criteria
- note dependencies and edge cases

Split a story when:

- it serves different actors
- it combines create, edit, approve, and report behaviors
- permissions or business rules differ by path
- the acceptance criteria require several unrelated scenarios

## Gap Analysis

Compare:

- current process vs target process
- current data vs required data
- current systems vs required capability
- current rules vs future policy
- current roles vs future ownership

Distinguish:

- root cause vs symptom
- missing requirement vs missing decision
- delivery task vs governance issue

## UAT Design

Include:

- happy path
- exception path
- permission or role path
- boundary data case
- integration handoff case where relevant

Avoid:

- purely technical test cases with no business meaning
- vague expected results
- scenarios with no data or pre-condition context
