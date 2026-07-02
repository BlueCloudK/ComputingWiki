# Fowler Pattern Map

## Source Info

- Source: `https://martinfowler.com/eaaCatalog/`
- Version: link-only
- Type: Enterprise application architecture pattern catalog
- Use for: enterprise/application architecture pattern nodes

## Extracted Knowledge Tree

- [[Enterprise Application Architecture Pattern]] - reusable patterns for enterprise application structure. `area` `source: PEAA catalog`
  - [[Layering Pattern]] - patterns for separating domain, presentation, and data responsibilities. `area` `source: PEAA catalog`
    - [[Service Layer]] - defines application boundary and operations. `pattern` `source: PEAA Service Layer`
    - [[Domain Model]] - object model of domain behavior and data. `pattern` `source: PEAA Domain Model`
    - [[Transaction Script]] - procedural organization of business logic per request/transaction. `pattern` `source: PEAA Transaction Script`
    - [[Table Module]] - business logic organized around database tables. `pattern` `source: PEAA Table Module`
  - [[Data Source Architectural Pattern]] - patterns for database access organization. `area` `source: PEAA catalog`
    - [[Table Data Gateway]] - object acting as gateway to a database table. `pattern` `source: PEAA`
    - [[Row Data Gateway]] - object acting as gateway to a single row. `pattern` `source: PEAA`
    - [[Active Record]] - object combining domain data and persistence methods. `pattern` `source: PEAA`
    - [[Data Mapper]] - layer mapping objects to database while keeping them independent. `pattern` `source: PEAA`
  - [[Object Relational Behavioral Pattern]] - patterns for object/relational behavior. `area` `source: PEAA catalog`
    - [[Unit of Work]] - tracks changes and coordinates database writes. `pattern` `source: PEAA`
    - [[Identity Map]] - ensures one in-memory object per database identity. `pattern` `source: PEAA`
    - [[Lazy Load]] - delays loading data until needed. `pattern` `source: PEAA`
  - [[Web Presentation Pattern]] - patterns for web UI control/presentation. `area` `source: PEAA catalog`
    - [[Model View Controller]] - separates model, view, and controller responsibilities. `pattern` `source: PEAA MVC`
    - [[Page Controller]] - one controller per page/action. `pattern` `source: PEAA`
    - [[Front Controller]] - centralized request handling entry point. `pattern` `source: PEAA`
  - [[Distribution Pattern]] - patterns for remote boundaries and transferred data. `area` `source: PEAA catalog`
    - [[Remote Facade]] - coarse-grained facade over remote calls. `pattern` `source: PEAA`
    - [[Data Transfer Object]] - object for carrying data across process/network boundaries. `pattern` `source: PEAA`

## Candidate Nodes

| Node | Parent | Type | Meaning | Source Trace | Use in library |
|---|---|---|---|---|---|
| [[Service Layer]] | [[Layering Pattern]] | pattern | application operation boundary | PEAA | candidate node |
| [[Repository]] | [[Data Source Architectural Pattern]] | pattern | collection-like interface over persistence | PEAA adjacent/common | candidate node |
| [[Unit of Work]] | [[Object Relational Behavioral Pattern]] | pattern | track and commit changes | PEAA | candidate node |
| [[Data Mapper]] | [[Data Source Architectural Pattern]] | pattern | map objects to database independently | PEAA | candidate node |
| [[Active Record]] | [[Data Source Architectural Pattern]] | pattern | object with persistence methods | PEAA | candidate node |
| [[DTO]] | [[Distribution Pattern]] | pattern | carry data across boundary | PEAA | candidate node |
| [[MVC]] | [[Web Presentation Pattern]] | pattern | split model/view/controller | PEAA | candidate node |

## Notes

- Link-only; keep pattern definitions one-line in maps.
