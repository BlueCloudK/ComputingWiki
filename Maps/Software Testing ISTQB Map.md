# Software Testing ISTQB Map

## Source Info

- Source: `D:\Learning\Book for IT\Foundations of software testing - ISTQB Certification.pdf`
- Version: local PDF
- Type: Software testing foundation book
- Use for: testing concepts, test levels, techniques, test management

## Extracted Knowledge Tree

- [[Software Testing]] - process for evaluating software products and related work products. `area` `source: Chapter 1`
  - [[Why Testing Is Necessary]] - reasons testing reduces risk and informs decisions. `topic` `source: Ch01.1`
    - [[Software Failure]] - visible incorrect behavior during use. `concept` `source: Ch01.1`
    - [[Defect]] - flaw that may cause a failure. `concept` `source: Ch01.1`
    - [[Risk]] - possibility of negative outcome. `concept` `source: Ch01.1/Ch05`
    - [[Quality]] - degree to which software meets needs/requirements. `quality` `source: Ch01.1`
  - [[What Is Testing]] - testing as lifecycle process, not only execution. `topic` `source: Ch01.2`
    - [[Test Process]] - activities from planning to completion. `practice` `source: Ch01.2/Ch05`
    - [[Static Testing]] - testing without executing software. `practice` `source: Ch01.2/Ch03`
    - [[Dynamic Testing]] - testing by executing software. `practice` `source: Ch01.2`
    - [[Test Objective]] - purpose of a test activity. `concept` `source: Ch01.2`
  - [[Fundamental Test Process]] - planning, analysis, design, implementation, execution, and completion. `practice` `source: Ch01/Ch05`
    - [[Test Planning]] - deciding test scope, approach, resources, and schedule. `practice` `source: Ch05`
    - [[Test Analysis]] - identifying what should be tested. `practice` `source: Ch04/Ch05`
    - [[Test Design]] - deriving test cases and test data. `practice` `source: Ch04`
    - [[Test Execution]] - running tests and recording results. `practice` `source: Ch01/Ch05`
  - [[Testing Throughout Software Life Cycle]] - aligning testing with lifecycle stages. `area` `source: Chapter 2`
    - [[Component Testing]] - testing individual components. `practice` `source: Ch02`
    - [[Integration Testing]] - testing interactions between components/systems. `practice` `source: Ch02`
    - [[System Testing]] - testing a complete integrated system. `practice` `source: Ch02`
    - [[Acceptance Testing]] - testing readiness for business/user acceptance. `practice` `source: Ch02`
  - [[Test Design Techniques]] - methods for selecting meaningful tests. `area` `source: Chapter 4`
    - [[Black Box Testing]] - derive tests from specifications/behavior. `practice` `source: Ch04`
    - [[White Box Testing]] - derive tests from code/internal structure. `practice` `source: Ch04`
    - [[Experience Based Testing]] - derive tests from tester experience and intuition. `practice` `source: Ch04`
  - [[Test Management]] - organizing, estimating, monitoring, and controlling testing. `area` `source: Chapter 5`
    - [[Risk and Testing]] - using risk to focus test effort. `practice` `source: Ch05`
    - [[Incident Management]] - tracking and handling discovered issues. `practice` `source: Ch05`
  - [[Tool Support for Testing]] - using tools to support test work. `topic` `source: Chapter 6`

## Candidate Nodes

| Node | Parent | Type | Meaning | Source Trace | Use in library |
|---|---|---|---|---|---|
| [[Testing and Verification]] | [[Software Testing]] | MOC | testing and checking software correctness | Ch01-Ch02 | MOC |
| [[Test Process]] | [[Software Testing]] | practice | lifecycle activities of testing | Ch01/Ch05 | candidate node |
| [[Unit Test]] | [[Component Testing]] | practice | test a small code unit/component | Ch02 | existing node |
| [[Integration Test]] | [[Integration Testing]] | practice | test interactions between parts | Ch02 | candidate node |
| [[System Test]] | [[System Testing]] | practice | test whole integrated system | Ch02 | candidate node |
| [[Acceptance Test]] | [[Acceptance Testing]] | practice | test business/user acceptance | Ch02 | candidate node |
| [[Static Testing]] | [[What Is Testing]] | practice | inspect without execution | Ch03 | candidate node |
| [[Test Design Technique]] | [[Test Design Techniques]] | practice | method for deriving tests | Ch04 | candidate node |
| [[Test Management]] | [[Software Testing]] | area | planning and controlling test work | Ch05 | candidate node |

## Notes

- PDF had no useful outline; extracted from early text and standard chapter structure.
