# Project Proposal and Scope

**Authors:** Zhannur Meirambek, Ayazhan Orynbasar

## I. Background and Research Problem

The process of customized furniture orders entails various dimensions, constituents, colors, and parts to mention but a few. In effect, each of such orders becomes equivalent to a small engineering project. Information collected in a store must be transformed into data that could be used in the production process, and the consumer requires knowing the delivery date even if production capacities and supply of materials have not been checked yet. In the literature about custom-made furniture, one can find discussions about the inadequate way the requirements, dimensions, and technical documents exchange between customers and producers which leads to changes in requirements and additional works thereafter [1]. It is difficult to determine a delivery date because lead times include various processes such as engineering and procurement, rather than just the time machine runs [2]. Order confirmation, delivery dates, supply of materials, and production processes are also interconnected and should be handled at the same time [3]. Hence, an untrustworthy delivery date announcement indicates a fail of planning that takes place right at the selling stage.

Industry 4.0 tech is becoming more useful for non-traditional and small batch furniture producers; Enterprise Resource Planning (ERP), Warehouse Management System (WMS), Advanced Planning and Scheduling (APS) and Manufacturing Execution System (MES) enable efficient control of production processes in custom furniture shops [4]. Digital twins and simulation are powerful applications for performance assessment of produced objects, since they give a possibility to simulate a new order against the existing or projected workload [6], [7]. In most cases, it occurs that these systems are analyzed as separate from the shop floor, thus the benefits they can provide for the client-facing production operations are omitted.

**Scope.** The diploma project presents the development and testing of a prototype order management system for a furniture manufacturing enterprise with make-to-order model. The proposed system features a back office, digital twin of the factory and simple web-based interface dedicated to a shop manager. The shop manager submits the digitally organized and entered order into the system and the system checks its validity and, using the digital twin and data on availability of required materials, determines the order delivery time at the moment of acceptance of the order. The interface includes an order form and a screen where information about the estimated delivery time, estimated delivery time range, as well as factors influencing the request has been presented.

The project only partially addresses the issue of product configurator, product visualization in three dimensions, pricing, serves to support design automation, shop floor scheduling optimization, connects to physical machines, and deployment in real factories. The presented interface is only demonstrated and not tested in real conditions; the measurement method is related to the accuracy of the delivery date estimate only. This limitation of the application of the showroom to factory communication is a conscious choice in order to carry out the project as expected in the given timeframe.

## II. Literature Review and Research Gap

A. Search procedures and criteria for selection


Sources and criteria for selection were examined in Scopus, Web of Science and Google Scholar using the following keywords, the combinations of which were varied: "engineer to order," "mass customization," "delivery time," "product configurator," "digital twin" and "producing schedule."
After that articles were screened according to their titles and abstracts, and full texts were used to conduct a selection. The criteria for inclusion are as follows: peer-reviewed article published in the period of 2021–2025 (i.e., it must not contain any earlier foundational sources), works being written in English and focusing on such aspects of works as order management, configuration, system integration, digital twin or scheduling and furniture.
Papers presented at conferences, books or unpublished works were not included. As a result, a total of twenty articles were selected.

B. Order acceptance and delivery-date setting

In reviews of engineer-to-order research, it has been noted that the themes of engineering production integration, planning and control and management of uncertainties are interlinked [12]. One research involving 40 empirical studies classifies 32 factors responsible for gaining entry to the production stage into market/product, operations, supply chain and performance categories [17]. Concerning delivery dates specifically, Bhalla et al. [2] state that available tools are more concerned with tactical capacities and cycle times than with coordination between functions and the overall lead time consideration. Cavero et al. [3] present order acceptance, pricing, procurement, and machine assignment as one mathematical model and prove its effectiveness in practice.

C. Configuration and customer interaction

Research on mass-customization has been done in two ways. One analysis included findings from 3441 articles [18], while the other was based on a review of 49 studies concerning SMEs [19]. Finally, the enablers of mass-customization are defined as modularity, co-design platforms, real-time data and digital twins. Bouchard et al. point out that there is not enough guidance on implementation priorities and concrete tools. However, Mueller et al. [9] describe a five-step approach for service configurators in engineer-to-order companies and speak of over 70% time reduction in specification in one of the industrial cases, which means that configuration logic can substitute for manual interpretation. The finding comes from one company only and cannot be generalized. In furniture sector, Łukaszewicz et al. [1] develop a customer-to-manufacturer model and suggest the idea of a unified platform with configurators and product data management, but the framework lacks some practical tests or implementations.

D. Information-system integration

Wu et al. [5] give examples of how ERP, WMS, APS and MES work together in the area of furniture customization, dealing with numerous orders involving many boards. Their areas of interest include production management after order arrival in the factory. Reviews dedicated to smart manufacturing highlight issues of interoperability of different systems, including the ones based on old technologies, the necessity to develop common data models [14], and the application of the concept of digital thread, which allows keeping track of an order as one object of information during its life cycle [20]. Research in the area of data-oriented shop floor indicates that coverage of the technology aspect is greater than coverage of organizational and human aspects [11], [15], and a research conducted in an engineer-to-order company shows the significance of trust and mutual understanding in achieving digitalization [8]. Interviews with the representatives of 31 furniture companies reveal that technological priorities depend on the size and maturity of the company [4].

E. Digital twins, simulation and scheduling

The analysis of 68 sources indicates that intelligent scheduling uses digital twins and real-time information, however, independent responses to disturbances is not sufficiently developed [13]. Siatras et al. [7] implement the multi-agent approach together with the digital twin at a bicycle manufacturing company and achieve a higher production rate and time. According to their findings, there are still differences between the twin and the actual situation due to the assumptions of the model, randomness and labor input. In turn, Lalik et al. [6] create a digital twin of a tangible furniture production line (cutting, edge banding, drilling, CNC machines, painting and staging) and use it to conduct what-if analysis regarding volumes and machine loads instead of analyzing specific orders. In their turn, Jia et al. [10] apply the concept of flexible scheduling to custom furniture production in order to fulfill deadlines but only after determining production requirements. Machine vision can provide automatic data about the current state of production [16], which can be useful for future feedback.



**Table I.** Comparison of reviewed themes

| Theme | Typical method | Main limitation |
|---|---|---|
| Delivery date | Review, MILP model | Not furniture-specific; no showroom input |
| Configuration | Case study, concept | Conceptual or single-company evidence |
| Integration | System analysis | Starts after order enters the factory |
| Twins and scheduling | Simulation, agents | Offline or starts from known orders |

### F. Synthesis and research gap

The themes in the studies are summarized in Table I. Three studies identify the gap present in the studies. Łukaszewicz et al. [1] demonstrate that transfer of information between showroom and factory is fragmented although it presents a mere concept being examined. Cavero et al. [3] provide evidence that order acceptance involves capacity and procurement, although it describes situations unrelated to furniture or using a configurator for placing orders. Lalik et al. [6] affirm that a digital twin can analyze capacity of furniture without connection to order acceptance. Finally, according to Bhalla et al. [2], delivery date tool does not take into account order-related data in full measure.

**Research gap.** No study reviewed has utilized an organized showroom order as data input for an evaluation of available capacity and materials based on the digital twin approach that would be able to provide a delivery date upon order acceptance in customized furniture production, nor has there been a comparison of the accuracy of such a delivery date in relation to simpler methods of estimation used in practice.

## III. Research Question and Objectives

**Primary research question.** How can an intelligent order management system with an integrated digital twin be designed to improve the accuracy of delivery-date commitments at the showroom order-acceptance stage in customized furniture manufacturing?

**Subquestions.**

- **SQ1:** What structured digital-order representation is needed to pass showroom configuration data to the digital twin and planning systems?
- **SQ2:** Does twin-based estimation give smaller deviation from actual completion dates than the baseline methods B1 and B2 under different load and disturbance conditions?

**Aim.** To design and evaluate an order-management system, consisting of a manager web interface, a backend and a simulation-based digital twin of the factory, in order to improve the accuracy of delivery-date commitments at the showroom order-acceptance stage in customized furniture manufacturing.

**Objectives.**

- **O1:** Identify the information requirements of a structured digital order that connects showroom configuration data with production planning.
- **O2:** Design the system architecture and data model linking the digital order, ERP/WMS data and the digital twin.
- **O3:** Develop a calibrated digital twin of a representative customized furniture production line.
- **O4:** Implement a prototype consisting of a backend API, the digital twin and a minimal manager web interface that validates an order and returns its estimated delivery date with reasons.
- **O5:** Evaluate the accuracy of the estimates against the baseline methods B1 and B2.

**Hypotheses.**

- **H1:** The mean absolute deviation between committed and actual completion dates is smaller for the proposed system than for each baseline (B1 and B2).
- **H2:** A larger share of orders is completed by the committed date under the proposed system than under each baseline.

O1–O4 are design tasks and need no hypotheses.

The question addresses the gap directly: it joins the showroom order (SQ1, O1–O2), the digital twin (O3) and the delivery commitment (O4), and tests the result against the baselines (SQ2, O5). It is feasible because it concerns one decision and can be tested with simulated data.

## IV. Proposed Methodology

### A. Approach and design

The initiative takes a design science research approach that involves using a quantitative experimental evaluation. The use of a design science approach is appropriate since the main output is a system as an artefact, and the quantitative comparison against the baseline comes under H1 and H2 provisions. A slight qualitative aspect will support the hypothesis O1 through two to three consultations with furniture practitioners to verify the validity of the identified order characteristics and the proposed process route; and as a result of the qualitative findings only the data model will be refined.

### B. Data and selection criteria

Since an authentic order history is typically unavailable, the analysis will be based on the use of documented synthetic data. The parameters will be extracted from the published furniture research focusing mainly on production sequences and machine loading structures, and from consultations with practitioners or partners if the latter are available. The orders will have the form of cabinet-type items with different features in terms of sizes, materials, fittings, and quantities, thus making it possible for each order to determine a certain trajectory of panel cutting, edge banding, drilling, CNC machining, painting, and staging. Stock levels and lead times of suppliers will be considered in terms of material availability, having a controlled proportion of shortages. All assumptions will need to be stated, since Siatras et al. [7] indicate that twin results depend on these assumptions.

### C. Tools and system development

The prototype will be implemented in the Python programming language. This involves several components: an order structure in the configurator view represented in JSON; a database used for storing order and inventory-related data; a simulation of the manufacturing process created with the help of SimPy framework; a backend service used for providing information on the delivery date; and a simplified interface for the manager. A technology comparison section explains why those technologies were used. The information entering the simulation comes from the factory emulation, which represents a more realistic and complex stochastic model of the manufacturing process. This simulator performs all the steps of the production process, thus producing the “actual” delivery date.

**Table II.** Methodology alignment

| Obj. | Method / data | Output or analysis |
|---|---|---|
| O1 | Literature, expert consultation | Order attribute list |
| O2 | Design science, data modelling | Architecture, schema |
| O3 | Discrete-event simulation | Calibrated twin |
| O4 | Prototype implementation | Working prototype (API, twin, interface) |
| O5 | Experiments vs. B1, B2 | MAE, on-time share, Wilcoxon test |

### D. Evaluation plan

Two baselines will be compared with the proposed system: B1, a manual rule (average historical lead time plus a fixed buffer, with no capacity check), and B2, a static capacity check without feedback from the factory. Experiments will cover three load levels (low, medium, high utilisation) and two disturbance settings (normal, high), with about 30 independent replications of roughly 200 orders per scenario. All three methods will be applied to the same generated orders and random seeds in each replication, so that the comparison is paired. Outcome measures are mean absolute error, mean absolute percentage error and bias of the committed date, the share of orders completed by the committed date, and estimation time.

Since deviations can often be nonnormal, paired replications would be compared with the Wilcoxon signed-rank test α = 0.05 with Holm adjustment and the effect sizes will be presented. To analyze robustness, sensitivity analysis will be performed by varying different input parameters including the processing time and supplier lead time. Before running the main experiments, the emulator will be validated against the twin with a baseline scenario and the route and order characteristics will be reviewed by practitioners for plausibility purposes. The seeds, parameters, and code will also be documented to facilitate the replication of the experiments and defend them from critique.

## V. Expected Contribution and Practical Plan

**Contribution:** an implementation-oriented design and a tested prototype linking showroom orders to a digital twin for delivery-date commitment, with evidence on accuracy.

**Feasibility and risks:** the main risk is the lack of real factory data; synthetic data with documented assumptions will manage it, and results will be presented as simulation-based only and may not transfer directly to other factories. A second risk is the workload of building a complete system with an interface; the scientific core (digital twin, emulator, comparison with B1 and B2) therefore has priority, and the interface will be kept minimal if time is short.

**Ethics:** the project uses no personal data; practitioner consultations will be voluntary and anonymous, with consent and any required approval obtained first.


## References

[1] K. Lukaszewicz, W. Urban, and E. Krawczyk-Dembicka, “Conceptualization of industry 4.0 technology for the production of tailor-made furniture – a case study,” *Bulletin of the Polish Academy of Sciences: Technical Sciences*, vol. 71, no. 1, p. e144587, 2023.

[2] S. Bhalla, E. Alfnes, and H.-H. Hvolby, “Tools and practices for tactical delivery date setting in engineer-to-order environments: a systematic literature review,” *International Journal of Production Research*, vol. 61, no. 7, pp. 2339–2371, 2023.

[3] J. V. Cavero, M. M. E. Alemany, A. Esteso, and A. Gimenez, “Revenue management optimization for make-to-order and engineering-to-order manufacturing context,” *International Journal of Production Economics*, vol. 288, p. 109715, 2025.

[4] L. Cerveny, R. Sloup, and T. Cervena, “The potential of smart factories and innovative industry 4.0 technologies—a case study of different-sized companies in the furniture industry in central europe,” *Forests*, vol. 13, no. 12, p. 2171, 2022.

[5] Z. Wu, F. Zong, F. Zhang, J. Wang, Z. Zhu, X. Guo, and P. Cao, “Investigation of the customized furniture industry’s production management systems,” *Journal of Engineering Research*, vol. 11, no. 3, pp. 164–175, 2023.

[6] K. Lalik, R. Rumin, G. Pawlowski, K. Jurczyk, L. Gieracki, and S. Jedrzychowski, “Simulation modeling for mass customization furniture production: Investigating production volume and machine load in scope of industry 4.0 standard,” *Industry 4.0*, vol. 8, no. 4, pp. 116–122, 2023.

[7] V. Siatras, E. Bakopoulos, P. Mavrothalassitis, N. Nikolakis, and K. Alexopoulos, “Production scheduling based on a multi-agent system and digital twin: A bicycle industry case,” *Information*, vol. 15, no. 6, p. 337, 2024.

[8] S. Thun, O. Bakas, and T. C. B. Storholmen, “Development and implementation processes of digitalization in engineer-to-order manufacturing: enablers and barriers,” *AI and Society*, vol. 37, no. 2, pp. 725–743, 2022.

[9] G. O. Mueller, N. H. Mortensen, L. Hvam, A. Haug, and J. Johansen, “An approach for the development and implementation of commissioning service configurators in engineer-to-order companies,” *Computers in Industry*, vol. 142, p. 103717, 2022.

[10] Y. Jia, Y. Zhou, and Y. Fu, “A multi-objective brain storm optimization for integrated distributed flexible job shop and distribution problems,” *Heliyon*, vol. 10, no. 16, p. e36318, 2024.

[11] P. Eichenseer and H. Winkler, “Data-oriented shopfloor management: an inductively developed holistic conceptual model,” *The International Journal of Advanced Manufacturing Technology*, vol. 138, pp. 999–1021, 2025.

[12] V. G. Cannas and J. Gosling, “A decade of engineering-to-order (2010–2020): Progress and emerging themes,” *International Journal of Production Economics*, vol. 241, p. 108274, 2021.

[13] J. C. Serrano-Ruiz, J. Mula, and R. Poler, “Smart manufacturing scheduling: A literature review,” *Journal of Manufacturing Systems*, vol. 61, pp. 265–287, 2021.

[14] A. Schlemitz and V. Mezhuyev, “Approaches for data collection and process standardization in smart manufacturing: Systematic literature review,” *Journal of Industrial Information Integration*, vol. 38, p. 100578, 2024.

[15] P. Eichenseer and H. Winkler, “A data-oriented shopfloor management in the production context: a systematic literature review,” *The International Journal of Advanced Manufacturing Technology*, vol. 134, pp. 4071–4097, 2024.

[16] R. Li, S. Zhao, and B. Yang, “Research on the application status of machine vision technology in furniture manufacturing process,” *Applied Sciences*, vol. 13, no. 4, p. 2434, 2023.

[17] M. Harfeldt-Berg and J. Olhager, “The customer order decoupling point in empirical operations and supply chain management research: a systematic literature review and framework,” *International Journal of Production Research*, vol. 62, no. 17, pp. 6380–6399, 2024.

[18] L. D. Naldi, F. G. Galizia, M. Bortolini, M. Gabellini, and E. Ferrari, “Unlocking the potential of mass customization through industry 4.0: Mapping research streams and future directions,” *Applied Sciences*, vol. 15, no. 13, p. 7160, 2025.

[19] S. Bouchard, S. Gamache, and G. Abdulnour, “Operationalizing mass customization in manufacturing smes—a systematic literature review,” *Sustainability*, vol. 15, no. 4, p. 3028, 2023.

[20] T. A. Abdel-Aty and E. Negri, “Conceptualizing the digital thread for smart manufacturing: a systematic literature review,” *Journal of Intelligent Manufacturing*, vol. 35, pp. 3629–3653, 2024.


