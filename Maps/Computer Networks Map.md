# Computer Networks Map

## Source Info

- Source: `D:\Learning\Book for IT\computer-networking-a-top-down-approach-8th-edition.pdf`
- Version: 8th edition
- Type: Computer networking textbook
- Use for: network, protocol, web, transport, routing, security basics

## Extracted Knowledge Tree

- [[Computer Networks]] - systems that connect computers and exchange data through protocols. `area` `source: contents`
  - [[Internet]] - global network of networks and service platform. `area` `source: Ch01`
    - [[Network Edge]] - hosts, access networks, and end systems. `topic` `source: Ch01.2`
    - [[Network Core]] - packet/circuit switching and backbone networks. `topic` `source: Ch01.3`
    - [[Delay Loss and Throughput]] - basic network performance measures. `concept` `source: Ch01.4`
    - [[Protocol Layer]] - layered organization of network services. `concept` `source: Ch01.5`
  - [[Application Layer]] - protocols used by network applications. `area` `source: Ch02`
    - [[HTTP]] - web application protocol. `protocol` `source: Ch02.2`
    - [[SMTP]] - email transfer protocol. `protocol` `source: Ch02.3`
    - [[DNS]] - naming system that maps names to records/addresses. `protocol/system` `source: Ch02.4`
    - [[Socket Programming]] - programming interface for network communication. `practice` `source: Ch02.7`
  - [[Transport Layer]] - host-to-host process communication services. `area` `source: Ch03`
    - [[UDP]] - connectionless transport protocol. `protocol` `source: Ch03.3`
    - [[TCP]] - reliable connection-oriented transport protocol. `protocol` `source: Ch03.5`
    - [[Reliable Data Transfer]] - mechanisms for reliable communication. `concept` `source: Ch03.4`
    - [[Flow Control]] - prevent sender overwhelming receiver. `concept` `source: Ch03.5`
    - [[Congestion Control]] - prevent sender overwhelming network. `concept` `source: Ch03.6-Ch03.7`
  - [[Network Layer]] - routing and forwarding across networks. `area` `source: Ch04-Ch05`
    - [[Router]] - device that forwards packets. `component` `source: Ch04.2`
    - [[IP]] - Internet Protocol for addressing/routing packets. `protocol` `source: Ch04.3`
    - [[Routing Algorithm]] - method for computing paths. `concept` `source: Ch05`
    - [[BGP]] - interdomain routing protocol. `protocol` `source: Ch05`
  - [[Network Security]] - threats and protections in networking. `area` `source: security chapter`
  - [[Network Management]] - observing and controlling networks. `area` `source: management chapter`

## Candidate Nodes

| Node | Parent | Type | Meaning | Source Trace | Use in library |
|---|---|---|---|---|---|
| [[Network]] | [[Computer Networks]] | area | connected systems exchanging data | Ch01 | candidate node |
| [[HTTP]] | [[Application Layer]] | protocol | web protocol | Ch02.2 | candidate node |
| [[DNS]] | [[Application Layer]] | system/protocol | name resolution | Ch02.4 | candidate node |
| [[TCP]] | [[Transport Layer]] | protocol | reliable transport | Ch03.5 | candidate node |
| [[UDP]] | [[Transport Layer]] | protocol | connectionless transport | Ch03.3 | candidate node |
| [[IP]] | [[Network Layer]] | protocol | packet addressing/routing | Ch04.3 | candidate node |
| [[Congestion Control]] | [[Transport Layer]] | concept | control network overload | Ch03.6 | candidate node |

## Notes

- Avoid lab sections; use only stable network concepts.
