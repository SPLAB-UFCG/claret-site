---
title: "Process"
date: 2018-08-21T19:58:21-03:00
weight: 14
---

An overview of Claret regarding its tool support and related artifacts is shown below.

![Process](images/process.png?classes=shadow)

For the sake of simplicity, it focus on activities concerned with test generation, use case creation, and changes. 
Note that Claret is a central artifact for both RE and MBT. Moreover, we follow the iterative philosophy of Agile RE assuming that the RE process includes activities such as Change Management and Requirements Management to support continuous changes to requirements, by creating/updating Claret documents – a key feature for effectiveness of both Agile RE and MBT [1], [2].

The RE flow of artifacts starts with the user requirements list (for example, the product backlog) that is the base for creating Claret use cases. From it, use cases can be created and updated continuously. As needed during the agile cycles, the Claret tool compiles the use case specifications for generating: i) [Trivial Graph Format](https://en.wikipedia.org/wiki/Trivial_Graph_Format) test models for MBT and ii) RE Docs for communication with stakeholders in the RE process. In the scope of MBT, the TGF artifacts can be visually analyzed using the [yEd](https://www.yworks.com/products/yed) tool in order to seek for possible inconsistencies and unspecified scenarios that leads to change requests.

In the MBT flow, from (validated) TGF models, test cases can be generated using the LTS-BT tool [3]. LTS-BT can generate test cases extracting paths from TGF models using a Depth-First Search (DFS) algorithm based on coverage criteria and also test suite reduction strategies. Generated test cases can be exported in an XML format accepted as input by [Testlink](http://www.testlink.org), a test management tool that supports manual test case execution. For execution, a test plan can be defined and manually executed on the system under testing. Testlink provides reports on test results that may lead to change requests.


#### References

[1] T. Chow and D.-B. Cao. A survey study of critical success factors in agile software projects. Journal of Systems and Software, 81(6):961 – 971, 2008. Agile Product Line Engineering.

[2] I. Inayat, L. Moraes, M. Daneva, and S. S. Salim. A reflection on agile requirements engineering: Solutions brought and challenges posed. In Scientific Workshop Proceedings of the XP2015, XP ’15 workshops, pages 6:1–6:7, New York, NY, USA, 2015. ACM.

[3] E.G.Cartaxo,W.L.Andrade,F.G.O.Neto,andP.D.L.Machado.LTS- BT: A tool to generate and select functional test cases for embedded systems. In Proceedings of the 2008 ACM Symposium on Applied Computing, SAC ’08, pages 1540–1544, New York, NY, USA, 2008. ACM.
