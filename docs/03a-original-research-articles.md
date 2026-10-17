# Analysis of 10 Original Research Articles

**Author:** Zhannur Meirambek
**Part of:** [Literature Review](03-literature-review.md), Section 8

This document summarizes the ten original technical and research studies selected for the literature review. For each article it states the problem addressed, the methodology, the main findings, the contribution, strengths and limitations, and the relevance to this research. The companion document [03b-review-articles.md](03b-review-articles.md) covers the ten review papers.

---

## 1. Thun, Bakås, and Storholmen (2022)

**Article:** Development and implementation processes of digitalization in engineer-to-order manufacturing: enablers and barriers (Thun et al., 2022).

**Problem addressed.** The study examines how digitalization is developed and implemented in an engineer-to-order manufacturing environment and focuses on the organizational and technical factors that enable or hinder implementation.

**Methodology.** The authors use a qualitative case-study approach based on 15 semi-structured interviews. The study applies a socio-technical perspective and thematic analysis to identify recurring implementation conditions.

**Main findings/results.** Four important enablers are identified: shared trust, shared visual understanding, shared user perspective, and shared learning. Four barriers are also identified: trusting the system, understanding benefits, economic perspectives, and learning to manage scope.

**Contribution.** The study contributes empirical evidence that digital transformation is not only a software or technology problem. It shows that implementation depends on how users understand, trust, and learn to work with the new system.

**Strengths and limitations.** A major strength is the use of a real ETO manufacturing setting and multiple stakeholder interviews. The main limitation is that it is a qualitative single-case study, so the findings are context-dependent and do not directly establish quantitative performance improvements.

**Relevance to this research.** The findings are highly relevant to a showroom-to-factory order-management system because successful implementation requires coordination between showroom employees, planners, production personnel, managers, and digital systems.

---

## 2. Mueller et al. (2022)

**Article:** An approach for the development and implementation of commissioning service configurators in engineer-to-order companies (Mueller et al., 2022).

**Problem addressed.** The study addresses the difficulty of transforming customer requirements into consistent technical specifications in ETO environments, where manual specification can require substantial time and expertise.

**Methodology.** The authors develop a structured five-step approach for developing and implementing a service configurator and demonstrate it in a case company.

**Main findings/results.** The industrial case reports more than 70% reduction in specification time and approximately 40% reduction in the number of people required for the specification activity.

**Contribution.** The study demonstrates how configuration logic can transform customer-facing requirements into structured technical specifications and reduce manual interpretation between sales and engineering.

**Strengths and limitations.** The industrial case and measurable operational results are important strengths. The limitation is that the evidence comes from a specific ETO context and a particular configurator, so the reported reductions should not automatically be generalized to all manufacturers.

**Relevance to this research.** The article directly supports the showroom component of the proposed system, especially the transformation of customer choices into validated product specifications that can be passed to downstream systems.

---

## 3. Cavero et al. (2025)

**Article:** Revenue management optimization for make-to-order and engineering-to-order manufacturing context (Cavero et al., 2025).

**Problem addressed.** The study addresses integrated order acceptance and planning in hybrid MTO/ETO manufacturing, where pricing, delivery feasibility, procurement, machine allocation, and production planning are interdependent.

**Methodology.** The authors combine a literature study, a conceptual framework, a mixed-integer linear programming model, an industrial case study, computational experiments, and validation. The model integrates information from engineering, procurement, operations, sales, finance, and quality.

**Main findings/results.** The case demonstrates that order acceptance can be evaluated together with price, supplier conditions, machine capacity, procurement, and production planning. The reported computational experiments show that the proposed model can produce optimal solutions for the tested instances within practical solution times.

**Contribution.** The study advances order-management research by treating order acceptance as a cross-functional decision instead of a separate sales activity.

**Strengths and limitations.** Strengths include an industrial case, explicit mathematical optimization, and integration of several business and production decisions. Limitations include the specificity of the industrial case and the use of model assumptions that may not represent every production environment.

**Relevance to this research.** The article is highly relevant because an intelligent showroom system should evaluate material, supplier, capacity, and delivery constraints before confirming a customer order.

---

## 4. Červený, Sloup, and Červená (2022)

**Article:** The Potential of Smart Factories and Innovative Industry 4.0 Technologies—A Case Study of Different-Sized Companies in the Furniture Industry in Central Europe (Cerveny et al., 2022).

**Problem addressed.** The study investigates the potential and priorities of Industry 4.0 technologies in furniture manufacturing, including differences between companies of different sizes and production types.

**Methodology.** The authors use structured interviews with project managers or responsible representatives from 31 companies in Germany, the Czech Republic, and Slovakia, followed by qualitative content analysis.

**Main findings/results.** The study finds that Industry 4.0 is particularly relevant to atypical and small-series furniture production. The companies report different priorities according to size: smaller firms emphasize digital design, programming, stock management, networks, and real-time information, while larger firms move toward broader automation and digitalization.

**Contribution.** The study connects furniture-specific manufacturing conditions with Industry 4.0 adoption and shows that implementation priorities depend on company size, production type, and existing technological maturity.

**Strengths and limitations.** Its main strength is direct evidence from 31 furniture companies. The limitation is the interview-based design and Central European context; reported efficiency improvements are perceptions or reported outcomes rather than controlled experimental effects.

**Relevance to this research.** The article provides direct furniture-industry evidence that an order-management solution should be designed around the manufacturer’s existing digital maturity and production characteristics.

---

## 5. Jia, Zhou, and Fu (2024)

**Article:** A multi-objective brain storm optimization for integrated distributed flexible job shop and distribution problems (Jia et al., 2024).

**Problem addressed.** The study addresses integrated production and distribution scheduling for custom furniture orders, where production decisions and delivery decisions must jointly satisfy customer due dates.

**Methodology.** The authors formulate a mixed-integer mathematical programming model and develop a multi-objective brain storm optimization method. The proposed approach is compared with advanced optimization methods.

**Main findings/results.** The study demonstrates that production scheduling and distribution can be optimized together for custom furniture orders rather than treating factory scheduling and delivery as independent problems.

**Contribution.** The work contributes an integrated optimization perspective that links flexible job-shop production with downstream distribution.

**Strengths and limitations.** The furniture-specific application and multi-objective formulation are important strengths. The limitation is that the study concentrates on optimization after production requirements are known and does not address showroom order capture or customer configuration.

**Relevance to this research.** It supports the downstream planning layer of the proposed system, particularly the need to connect production scheduling with delivery commitments.

---

## 6. Siatras et al. (2024)

**Article:** Production Scheduling Based on a Multi-Agent System and Digital Twin: A Bicycle Industry Case (Siatras et al., 2024).

**Problem addressed.** The study addresses dynamic production scheduling in a complex manufacturing environment where static schedules can become ineffective because of disturbances and changing production conditions.

**Methodology.** The framework combines a Multi-Agent System, Digital Twin, discrete-event simulation, mathematical optimization, deep reinforcement learning, and heuristic optimization. Three AI-based scheduling agents coordinate production decisions while human managers retain supervisory control.

**Main findings/results.** The industrial pilot reports improvements in production rate and production time, together with dynamic coordination and earlier identification of bottlenecks. The study also reports short response times for rescheduling and close agreement between the Digital Twin and observed production times.

**Contribution.** The study demonstrates how Digital Twins and decentralized agents can support adaptive scheduling and human-in-the-loop decision-making.

**Strengths and limitations.** Strengths include industrial validation, multiple computational methods, and explicit human supervision. The main limitation is that the case is in bicycle manufacturing rather than furniture, and the Digital Twin still has deviations caused by model assumptions, stochasticity, manual operations, and human errors.

**Relevance to this research.** The architecture is relevant to furniture manufacturing because the proposed order-management system also needs adaptive scheduling and production feedback rather than a one-time static plan.

---

## 7. Lalik et al. (2023)

**Article:** Simulation Modeling for Mass Customization Furniture Production: Investigating Production Volume and Machine Load in scope of Industry 4.0 standard (Lalik et al., 2023).

**Problem addressed.** The study investigates how production volume affects machine load and capacity in mass-customized furniture production.

**Methodology.** The authors build a Digital Twin and FlexSim 3D simulation model using historical production data from a real furniture company. The model represents a sequence including panel cutting, edge banding, drilling, CNC processing, painting, and staging, and evaluates multiple production-volume scenarios.

**Main findings/results.** The simulations show how increasing order volume changes machine workloads and provide a basis for identifying capacity constraints and possible equipment requirements. The study demonstrates the value of what-if analysis before physical production changes are made.

**Contribution.** The research contributes a practical simulation-based method for capacity analysis in customized furniture production.

**Strengths and limitations.** Strengths include direct furniture-industry data, multiple scenarios, and practical capacity recommendations. Limitations are the single-company context and the focus on simulation and capacity rather than live order-management or customer-facing control.

**Relevance to this research.** The results support the capacity-evaluation component of an intelligent order-management system, where a new order can be checked against current and future production capacity.

---

## 8. Łukaszewicz, Urban, and Krawczyk-Dembicka (2023)

**Article:** Conceptualization of Industry 4.0 technology for the production of tailor-made furniture—a case study (Lukaszewicz et al., 2023).

**Problem addressed.** The study addresses inefficient information exchange between customers and a manufacturer during tailor-made furniture development and production.

**Methodology.** The authors use a case study, process modelling, and conceptualization of an Industry 4.0-based cooperation framework.

**Main findings/results.** The existing process contains fragmented customer information, measurements, design data, technical documentation, and production activities. The proposed framework includes a unified cooperation platform, digital product information, visualization, product data management, computer-aided manufacturing, configurators, and other digital technologies.

**Contribution.** The study provides a conceptual customer-to-production workflow for tailor-made furniture and emphasizes earlier customer validation to reduce downstream changes and rework.

**Strengths and limitations.** Its main strength is direct furniture-industry relevance and a clear process perspective. The limitation is that the proposed benefits are conceptual and the framework is not presented as a fully implemented and experimentally validated order-management system.

**Relevance to this research.** This is one of the most directly relevant papers because it addresses the customer-to-manufacturer information flow that forms the front end of the proposed showroom-to-factory system.

---

## 9. Wu et al. (2023)

**Article:** Investigation of the customized furniture industry’s production management systems (Wu et al., 2023).

**Problem addressed.** The study examines the complex production-management and information-system requirements of customized furniture manufacturing.

**Methodology.** The authors analyze an industrial production-management architecture and its application, focusing on ERP, WMS, APS, and MES and their roles in the production process.

**Main findings/results.** ERP supports functions including finance, purchasing, supply, sales, and product information; WMS supports material management and resource allocation; APS supports production planning and scheduling; and MES provides production execution and communication. The reported production application includes hundreds of orders and thousands of boards, demonstrating coordinated batching, material utilization, identification, warehousing, and traceability.

**Contribution.** The study contributes a furniture-specific view of how enterprise, warehouse, planning, and execution systems can be integrated around customized production.

**Strengths and limitations.** Its main strength is the direct customized-furniture application with real production data and system functions. The limitation is that the architecture is tied to a particular industrial context and focuses more on production management than on the initial showroom interaction.

**Relevance to this research.** The article provides a key technical foundation for the ERP/WMS/APS/MES layer of the proposed order-management architecture.

---

## 10. Eichenseer and Winkler (2025)

**Article:** Data-oriented shopfloor management: an inductively developed holistic conceptual model (Eichenseer and Winkler, 2025).

**Problem addressed.** The study addresses the need for a holistic model of data-oriented shopfloor management that supports operational decisions in increasingly complex and digital production environments.

**Methodology.** The authors conduct seven semi-structured expert interviews and use the Gioia methodology, theoretical saturation, and member checking to develop and verify the conceptual model.

**Main findings/results.** The model contains five core elements: information system, process organization, organizational structure, cross-functional operating model, and development path and implementation plan. It describes data acquisition, preparation, structuring, utilization and distribution, decision-making, and control.

**Contribution.** The study extends data-oriented shopfloor research beyond technology by integrating organizational structures, processes, and implementation requirements. It also emphasizes the role of human-in-the-loop decision-making for critical production activities.

**Strengths and limitations.** Strengths include a systematic qualitative development process and a holistic socio-technical model. Limitations include the small qualitative sample and the conceptual nature of the model, which requires further empirical validation.

**Relevance to this research.** The model is relevant because the proposed order-management system must turn production data into actionable information for sales, planning, production, and management rather than simply storing data.

---

## References

Cavero, J. V., Alemany, M. M. E., Esteso, A., and Gimenez, A. (2025). Revenue management optimization for make-to-order and engineering-to-order manufacturing context. *International Journal of Production Economics*, 288:109715.

Cerveny, L., Sloup, R., and Cervena, T. (2022). The potential of smart factories and innovative industry 4.0 technologies—a case study of different-sized companies in the furniture industry in Central Europe. *Forests*, 13(12):2171.

Eichenseer, P. and Winkler, H. (2025). Data-oriented shopfloor management: an inductively developed holistic conceptual model. *The International Journal of Advanced Manufacturing Technology*, 138:999–1021.

Jia, Y., Zhou, Y., and Fu, Y. (2024). A multi-objective brain storm optimization for integrated distributed flexible job shop and distribution problems. *Heliyon*, 10(16):e36318.

Lalik, K., Rumin, R., Pawlowski, G., Jurczyk, K., Gieracki, L., and Jedrzychowski, S. (2023). Simulation modeling for mass customization furniture production: Investigating production volume and machine load in scope of industry 4.0 standard. *Industry 4.0*, 8(4):116–122.

Lukaszewicz, K., Urban, W., and Krawczyk-Dembicka, E. (2023). Conceptualization of industry 4.0 technology for the production of tailor-made furniture – a case study. *Bulletin of the Polish Academy of Sciences: Technical Sciences*, 71(1):e144587.

Mueller, G. O., Mortensen, N. H., Hvam, L., Haug, A., and Johansen, J. (2022). An approach for the development and implementation of commissioning service configurators in engineer-to-order companies. *Computers in Industry*, 142:103717.

Siatras, V., Bakopoulos, E., Mavrothalassitis, P., Nikolakis, N., and Alexopoulos, K. (2024). Production scheduling based on a multi-agent system and digital twin: A bicycle industry case. *Information*, 15(6):337.

Thun, S., Bakas, O., and Storholmen, T. C. B. (2022). Development and implementation processes of digitalization in engineer-to-order manufacturing: enablers and barriers. *AI and Society*, 37(2):725–743.

Wu, Z., Zong, F., Zhang, F., Wang, J., Zhu, Z., Guo, X., and Cao, P. (2023). Investigation of the customized furniture industry’s production management systems. *Journal of Engineering Research*, 11(3):164–175.