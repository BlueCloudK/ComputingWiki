# SRE Map

## Source Info

- Source: `https://sre.google/books/`
- Version: link-only
- Type: Site Reliability Engineering books
- Use for: operations, reliability, monitoring, incident response

## Extracted Knowledge Tree

- [[Site Reliability Engineering]] - engineering approach to operating reliable services. `area` `source: Google SRE books`
  - [[Reliability]] - ability of a service to work as expected over time. `quality` `source: SRE book`
  - [[Risk]] - potential for service/user harm or failure. `concept` `source: SRE book risk chapter`
  - [[Service Level Objective]] - target level of service reliability. `artifact/concept` `source: SLO chapters`
  - [[Error Budget]] - allowed unreliability budget derived from SLO. `concept/practice` `source: SLO chapters`
  - [[Monitoring]] - observing service behavior and health. `practice` `source: monitoring chapter`
  - [[Alert]] - notification requiring human/action response. `artifact/practice` `source: monitoring/alerting`
  - [[Incident Response]] - coordinated response to service disruption. `practice` `source: incident chapters`
  - [[Postmortem]] - review of an incident to learn and improve. `artifact/practice` `source: postmortem guidance`
  - [[Toil]] - repetitive manual operational work that scales poorly. `concept` `source: toil chapter`
  - [[Automation]] - replacing repeatable manual work with software. `practice` `source: automation chapters`
  - [[Release Engineering]] - controlled process of building and releasing software. `practice` `source: release engineering`
  - [[Capacity Planning]] - planning resources for expected load. `practice` `source: capacity planning`
  - [[Overload Handling]] - protecting service during excessive load. `practice` `source: overload chapters`

## Candidate Nodes

| Node | Parent | Type | Meaning | Source Trace | Use in library |
|---|---|---|---|---|---|
| [[Deployment and Operations]] | [[Site Reliability Engineering]] | MOC | running services after release | SRE books | MOC |
| [[Reliability]] | [[Site Reliability Engineering]] | quality | service works over time | SRE book | candidate node |
| [[Monitoring]] | [[Site Reliability Engineering]] | practice | observe service health | monitoring chapter | existing node |
| [[SLO]] | [[Service Level Objective]] | artifact/concept | target service level | SLO chapters | candidate node |
| [[Incident]] | [[Incident Response]] | event | service-impacting problem | incident chapters | existing node |
| [[Postmortem]] | [[Incident Response]] | artifact/practice | learn from incident | postmortem guidance | candidate node |
| [[Automation]] | [[Site Reliability Engineering]] | practice | reduce manual ops work | automation chapters | candidate node |

## Notes

- Link-only reference for operations/reliability; not a full SRE summary.
