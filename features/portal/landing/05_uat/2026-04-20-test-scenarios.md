# UAT Scenarios

| Scenario ID | Requirement Ref | Scenario | Pre-Condition | Steps | Expected Result | Tester | Status |
| --- | --- | --- | --- | --- | --- | --- | --- |
| UAT-01 | BR-01, FR-01, AC-01 | User sees the core service benefits on the landing module | Landing module is available | Open landing module | Benefits are visible and understandable without needing to navigate away |  | Not Started |
| UAT-02 | BR-02, FR-02, FR-06, AC-02 | User sees scannable preparation guidance before starting | Landing module is available | Open landing module and review the preparation section | Preparation guidance is visible, easy to scan, and helps the user understand what dossier items or information must be prepared |  | Not Started |
| UAT-03 | BR-03, FR-03, RULE-01, AC-03 | New user can start registration from landing | Registration route is configured | Open landing module and select `Sign up` | User is taken to the registration flow |  | Not Started |
| UAT-04 | BR-04, FR-04, RULE-01, AC-04 | Returning user can access login from landing | Login route is configured | Open landing module and select `Log in` | User is taken to the login flow |  | Not Started |
| UAT-05 | FR-05, NFR-05, AC-05 | User can see information and CTA options without friction on supported device sizes | Landing module is available | Open landing module on supported desktop and mobile viewport sizes | Benefit, preparation, and CTA sections are accessible without confusion or blocking behavior, and both CTAs remain actionable |  | Not Started |
| UAT-06 | BR-02, RULE-02, RULE-04, AC-06 | Preparation guidance matches approved downstream dossier requirements | Approved dossier requirement list exists | Compare landing content with approved dossier requirement list | Landing guidance is accurate, does not contradict downstream requirements, and does not claim an unapproved exhaustive checklist |  | Not Started |
