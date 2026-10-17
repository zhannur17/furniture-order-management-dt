# Literature Review

## Design and Development of an Intelligent Order Management System for Automating Showroom-to-Factory Workflow in Furniture Manufacturing

**Authors:** Zhannur Meirambek, Ayazhan Orynbasar
**Date:** September 2026

---

## 1. Introduction

Customized products present major difficulties for successful and reliable manufacturing due to the need of changing customer requirements into product designs or configurations, suitability in engineering and manufacturing processes. As a result, engineer-to-order (ETO), make-to-order (MTO), and mass-customization approaches necessitate deep collaboration between customer needs and manufacturing processes downstream. Research about ETO unveils such topics as engineering and production process integration, supply chain integration, planning and control, uncertainty management, and Industry 4.0 as important research areas (Cannas and Gosling, 2021).

The context of the furniture industry is ideal for analyzing these issues, as the orders for custom-made furniture may involve different measurements, materials, colors, parts, fittings, and functions. As a result, the amount of information that has to be checked at the customer-facing stage and communicated to the manufacturing process increases. Research relevant to the furniture sector proves that Industry 4.0 technologies are becoming more and more important for unconventional small lots of production where companies have to deal with high levels and complexity of product requirements (Cerveny et al., 2022).

Recent studies regarding mass customization indicate that product module design, and customer co-creation processes, along with flexible production technology, access to real-time information, AI technology, predictive analytics, and Digital Twin technology are key enablers of mass customization processes in technological and organizational terms (Naldi et al., 2025). At the same time, research within the context of manufacturing SMEs reveals that product and process modularity, business agility, technology application, operation of digital supply chains, and collaboration networks play a crucial role in actualizing mass customization (Bouchard et al., 2023).

The management of customer orders is also closely related with the moment at which the product is matched with its specific customer order. Studies conducted on customer order decoupling points show that this step connects product and market characteristics with operational, supply chain and performance factors (Harfeldt-Berg and Olhager, 2024). In ETO environments, setting the deadline is complicated in the same manner since the customer order may involve engineering, procurement, production and some other procedures before delivery can be effected (Bhalla et al., 2023).

Smart manufacturing emphasizes the significance of real-time information and effective decision-making. Digital Twins, optimization, smart planning, and shop floor data handling can enable dynamic production planning and execution (Serrano-Ruiz et al., 2021; Eichenseer and Winkler, 2024). The digital thread research includes highlighting the importance of data integration, interoperability, traceability, and linkability throughout the design, engineering, and manufacturing processes (Abdel-Aty and Negri, 2024).

Despite significant advancements in manufacturing technology, there still exist gaps in research concerning some aspects of ERP, production planning, scheduling, Digital Twins, and furniture-specific solutions of Industry 4.0. Therefore, the current review looks into these topics together to articulate the research gap related to the intelligent order management system which integrates customers’ interactions in showroom with factory planning, process and feedback.

The review focuses on five interconnected areas: customer order management and mass customization; ETO/MTO and order fulfilment; product configuration and customer interaction; ERP/MES and data integration; and production planning, intelligent scheduling, and smart manufacturing in furniture production.

## 2. Customer Order Management and Mass Customization

The first step in the described workflow that takes an order from a showroom to production is the customer order itself. In custom manufacturing, an order has a lot more information than business-related stuff: it also defines the product setup, engineering requirements, material requirements, production operations, resource requirements, and commitment to delivery. The customer order decoupling point (CODP) means where the product gets connected to an order from a customer. Harfeldt-Berg and Olhager (2024) perform a systematic literature review of existing knowledge about CODP to pinpoint the variables referring to the market and product features, operations, supply chains, and performance. Their model recognizes various situations where manufacturing takes place before or after the customer order is placed.

Mass customization complicates this case further since manufacturers need to be able to provide their customers with a variety of products while utilizing fast and effective production processes. Naldi et al. (2025) analyze the research connecting mass customization and Industry 4.0 and outline three main areas of research: theoretical frameworks and effectiveness, technologies and processes supporting the entire product cycle, and supply-chain techniques. The review shows that product modularity, co-design platforms, adjustable manufacturing, immediate data, artificial intelligence, predictive analytics, and digital twins are some of the most relevant supporting technologies.

Bouchard et al. (2023) emphasize the relevance of six critical elements necessary for realizing mass customization in the production processes of SMEs, which include product and process modularities, manufacturing agility, technology utilization, digital supply chain management, and collaboration networks. Furthermore, the review outlines a gap in implementation priorities and required practical details regarding tools and maturity. Thus, it can be said that the introduction of digitalization should be regarded as a combined technological and organizational approach rather than as a specific software application.

There is also the necessity of evaluating if an order that has been requested can actually be carried out. Cavero et al. (2025) create a comprehensive model for revenue management that integrates production planning, procurement, delivery feasibility, pricing of the orders accepted, and the allocation of machines that belong to either ETO or MTO production processes. Here, the authors demonstrate their case within the industry and show how beneficial it can be when several decisions that have traditionally been taken separately are taken as one. It should also be noted that this implies the need for not just providing a delivery date by the showroom without taking into account the pertinent issues related to procurement, production, materials, and capacity utilization.

Customer requirement transformations into organized data can be performed through studies of configurators. Research into the usage of commissioning configurators in ETO companies illustrates how configurable tools can be developed and used for the translation of customer requirements into structured specifications. It has been demonstrated in the described industrial case that the time of specification creation has been reduced significantly, which demonstrates the potential of configurators to reduce the manual process of interpreting information between customer-related and technical processes (Mueller et al., 2022).

The process of setting the delivery date can also be characterized as an order management activity and not only as a production problem. Bhalla and colleagues (2023) conducted a study of the approaches and tools used in the tactical setting of delivery dates in ETO activities and presented a few essential factors, such as the coordination of different departments, coordination of supply chains, process formalization, and the use of planning or decision-support tools. Their findings suggest that lead time in a specific order includes engineering, purchasing, manufacturing, and other processes.

The research indicates that an integrated process should be applied to customer order management. When customers order, for instance, a custom-made piece of furniture, the order should go through all steps from the identification of customer requirements; to setup and specification; to feasibility, delivery commitment, and production planning, instead of being considered a one-time sale transaction.

## 3. ETO/MTO and Order Fulfilment

The relationship between customer needs and the production process is strong in make-to-order and engineer-to-order environments. Products produced under ETO conditions require customer-specific design and engineering before the actual production starts. On the other hand, in order to manufacture products under MTO conditions, manufacturers generally apply already existing designs and commence the manufacturing process only after official receipt of the order. Cannas and Gosling (2021) identified the integration of design and production processes, supply chain integration, planning and controlling, uncertainty management, and Industry 4.0 as the main research themes in ETO.

The process of fulfilling orders in engineer-to-order (ETO) contexts comprises more than manufacturing. In fact, it comprises activities such as tendering, designing, engineering, process planning, buying, fabricating, assembling, and testing, among others. These activities can partly or entirely depend on an order from a specific customer, thus adding to the complexity of coordination. According to Bhalla et al. (2023) delivery dates must take into account activities specific to the order rather than just lead time.

The significance of this matter is particularly crucial in intelligent order management, as accepting an order is more than merely confirming that a product can be produced. The system must correlate the needs of the customer with the engineering effort, availability of materials, restrictions of suppliers, capacity of the production, availability of machines, and the date of delivery requested by the client. This wider view is evidenced by the work of Cavero et al. (2025) that connect order acceptance, pricing, delivery feasibility, procurement, machine allocation, and production planning into one solution.

The order fulfilment process should therefore be seen as a single system instead of a chain of disconnected departmental activities. A showroom order should give proper information that can be converted into a validated product configuration, engineering and manufacturing specifications, materials and capacity requirements, and an acceptable delivery assurance.

## 4. Product Configuration and Customer Interaction

Configuration is a major link between the customer needs and the relevant information necessary for the manufacturing process. It is indicated that custom production means that the customers may provide such specifications as measurements, materials, colors, elements, and functional requirements, which have to be changed into the product definition from a technical point of view. As a result, systems of product configuration are highly relevant in the mass customization conditions, where the need is to manage a wide range of product diversity without losing touch with the design and manufacturing processes (Naldi et al., 2025).

Naldi et al. (2025) denote interaction between customer and manufacturer, co-design, co-creation, co-configuration, and preference elicitation as tools for the involvement of customers in mass customization. They indicate the phenomenon of “mass confusion”, whereby customers find it complex to choose among various possible combinations. Therefore, digital interfaces shall play a role of transforming customers’ preferences into workable and applicable combinations.

This issue is of high importance in furniture production, owing to the fact that customization presumes several interconnected product parameters. Any alterations, such as the cabinet size, type of materials, or choice of components can lead to other characteristics changing and having an impact on the actual manufacturing process, material requirements, and time of the production. For this reason, an efficient configuration system should utilize its creative possibilities and provide knowledge on product limitations.

Łukaszewicz et al. (2023) examine the use of Industry 4.0 technologies in customized furniture production and emphasize flawed information exchange between customers and producers as a major problem. Their research illustrates how customer information such as requirements, measurements, design data, and technical documentation goes through different disjointed processes, raising the possibility of being faced with customer updates that arise later in different production stages.

The research on configurators in the context of ETO environments facilitates the process of transforming the requirements into a structured approach for specifications. The authors, Mueller et al. (2022), present a structured methodology of design and development of commissioning service configurators. The studied case shows the extent to which configurators enable a reduction in efforts related to specification work, while establishing a systematic correlation between the requirements of the customers and the specifications.

Bouchard et al. (2023) also conclude that configurators and other digital applications should be examined alongside product modularity, process modularity, agility, digital supply chains, and collaboration in the organization’s operation. Thus, configurators shouldn’t be observed as separate showroom applications; they should be capable of generating usable data for the downstream information and production systems.

The showroom stage of the proposed smart order management system has to create a digital order with given product parameters and specific rules of configuration. The product description produced should be applicable in costing, planning of the materials, engineering of the product, planning of production, and manufacture of the products.

## 5. ERP/MES and Data Integration

The efficiency of order fulfillment in custom manufacturing relies heavily on the capability of various information systems to share information punctually and consistently. In a furniture customization domain, any info created during customer interactions must be relayed to the relevant systems in charge of product info, procurement, stock management, production planning, scheduling, and shop floor processing. Hence, system integration becomes crucial in order for intelligent order operation to be achieved.

Wu et al. (2023) studied the systems of production management in particular reference to customized furniture industry and highlighted the interrelations of Enterprise Resource Planning (ERP), Warehouse Management Systems (WMS), Advanced Planning and Scheduling (APS), and Manufacturing Execution Systems (MES). ERP means finance, purchase and supply, sales, and other information. WMS provides assistance in managing materials and allocating resources. APS is responsible for production scheduling and planning. MES has the core task of managing production information.

The research of Wu et al. (2023) examines the production application which analyzes many orders of customers, and numerous boards. The use of system integration, therefore, shows us how one can use system processes for the purposes of batch making, utilization of materials, identification of goods by using bar codes, and production control.

The smart manufacturing literature at large recognizes interoperability as a critical challenge in the integration of various information systems tailored for different applications. According to Abdel-Aty and Negri (2024), the digital thread is a way of linking information and data through various stages of the product lifecycle. In their literature review, they indicate that the various aspects of digital thread architecture include data integration, traceability, sharing, interoperability and lifecycle connectivity. Thus, suitable usage of the digital thread concept is justified in the proposed system.

It is important that every order of the customer be traceable through all stages of its passage. The customer requirements can be turned into a product design and through this product design product data could be generated including information about material requirements, instructions for production, scheduling information, etc. By keeping the relations between such objects, it is possible to decrease the loss of information.

However, data integration cannot be regarded as a mere technical link between software applications. Eichenseer and Winkler (2024) examine data-oriented shopfloor management also from the standpoint of technologies, organizations, and individuals. The review indicates that technological matters are covered fairly well but organizational and human sides are not paid sufficient attention. For successful integration to occur, there must be adequate processes, responsibilities, and mechanisms for the use of information in making operational decisions.

Eichenseer and Winkler (2025) came up with a comprehensive conceptual model consisting of five core elements: information system, process organization, organizational structure, cross-functional operating model, and development path and implementation plan. This model includes the process of acquisition, preprocessing, organizing, use and distribution of any information, as well as the process of making decisions and controlling. Given this theory, it is necessary to stress the importance of this approach, since a smart order-management system should not be only a storage device, but also an advanced tool of turning information into knowledge for the purpose of sales, planning, production and management.

Based on the literature, the information architecture of a customized furniture workflow can be represented as:

> Showroom / Customer Interface → Order Management → ERP/WMS → APS → MES → Shopfloor → Production Feedback

The exact division of responsibilities depends on the manufacturer’s existing information infrastructure. Nevertheless, the literature indicates the importance of maintaining consistent information across organizational and technological boundaries.

## 6. Production Planning and Intelligent Scheduling

Production planning and scheduling are important steps in making a customer requirement into a manufacturing activity. It is difficult to schedule in a make-to-order or custom environment because the order may require different processes, routes, delivery dates, resource consumption, etc. Moreover, unexpected events like breakdowns, priority orders, lack of materials, and time variations make the use of fixed schedules unfeasible.

Serrano-Ruiz et al. (2021) delve into smart manufacturing scheduling and mention important topics in this research area, including Digital Twins, the Fourth Industrial Revolution, intelligent algorithms, and autonomous decision making. The results of their study indicate that smart scheduling is based on real-time information and has the ability to change decisions about production according to disturbances. The authors also point out that not much work has been done in the field of completely automated scheduling and response to disturbances in real time.

Siatras et al. (2024) illustrate these ideas using a production-scheduling framework that integrates a Multi-Agent System and Digital Twin technology. The framework employs decentralized scheduling agents, digital models of production resources, simulation, and optimization techniques. Human managers can oversee and modify created schedules, applying the human-in-the-loop principle rather than employing fully autonomous control.

The framework has been evaluated in a pilot study focusing on the production of bicycles and showed significant upgrade in the productivity of production activities and measures of production time. While it is not directly related to production of furniture, the architecture is still applicable since custom furniture also relies on coordination of different operations and resources with respect to timing.

Jia et al. (2024) tackle a relevant issue concerning custom furniture production by using flexible job-shop scheduling along with distribution decisions. Their optimization model incorporates custom furniture orders manufactured in flexible job-shops and shipped to customers on time. The study shows that production scheduling can be directly linked to delivery needs rather than determined without taking customer commitments into consideration.

Simulation and Digital Twin methods could supplement optimization by enabling planners to test production scenarios ahead of any physical changes. Lalik et al. (2023) have utilized a Digital Twin along with FlexSim simulation for examining production volume and machine load of custom-made furniture manufacturing. Their simulation accounts for various phases of the production process, thus running alternative production-volume scenarios for capacity analysis and what-if study.

Hence, for a smart showroom-to-factory system, planning and scheduling can be perceived through the prism of an unending decision-making process. The confirmed order information should give product info, quantity, configuration, due date, and processing requirements. These data can be integrated with the machine and material availability, workload, processing times, and delivery obligations in order to create a feasible production schedule.

The resulting information flow can be represented as:

> Confirmed Order → Production Requirements → Capacity Evaluation → Routing → Scheduling → Shopfloor Execution → Feedback → Rescheduling

The existing literature also points towards the fact that feedback is important. The actual time of processing, status of machinery and any delays and completed work may be different from the assumptions behind the original planning. Thus, the application of Digital Twins and real-time information layers allows adjustment of production information and flexible scheduling (Serrano-Ruiz et al., 2021; Siatras et al., 2024).

## 7. Smart Manufacturing and Digitalization in Furniture Manufacturing

Applying Industry 4.0 technologies to the furniture production sector has particular relevance since furniture production increasingly calls for high product diversity, customized customer needs, short production runs, and flexible production processes. Research on furniture industry specifics proves the relevance of such digital technologies as digital design, production management systems, simulation and modeling, machine vision, and data-based decision making.

The study conducted by Cerveny et al. (2022) explores the implementation of Industry 4.0 and smart factories in furniture production in countries located in Central Europe. The study is built on structured interviews carried out with the representatives of 31 companies located in Germany, the Czech Republic, and Slovakia. It turned out that digitalization is of high importance for non-standard production and small-scale production, however, the priorities in technology vary depending on the size of companies and the peculiarities of their production.

The research elucidates the varying priorities of furniture manufacturers depending upon their size. Small manufacturers can appreciate the usefulness of digital design and planning systems, order-shipping centers, public data networks, and live monitoring of the production process. Medium-sized producers may require better integration of CNC machines, conveyor systems, nested systems, painting technologies, and production planning systems. Larger companies will desire wider automation in their production processes. This proves that the implementation of Industry 4.0 technology should be based on the existing production practices and the level of digital maturity.

Simulation and Digital Twin technology have another significant pathway in the domain of furniture manufacturing. Lalik et al. (2023) investigate the mass customization of furniture through Digital Twin technology and FlexSim 3D simulation. The authors rely on the production data of a real furniture company to model the impact of production volume on machine load and system performance. The production process involves panel cutting, edge banding, drilling, CNC machining, painting, and staging. The authors simulate various scenarios to determine potential production constraints and possibilities for production enhancement.

The significance of this study does not only involve outlining the present-day production efficacy. The simulation acts as a mechanism for decision-making regarding future production alternatives. This is important in smart management of orders as the new orders need to be estimated accordingly to the existing and forthcoming capacities.

Another significant technology that can be used in the production of intelligent furniture is machine vision. Li et al. (2023) provide a systematic review of machine vision applications in furniture manufacturing by classifying the relevant literature based on information collection, quality detection, positioning, and automatic sorting as well as intelligent monitoring. In this review, various technologies used in machine vision have been identified to include image processing, machine learning, deep learning, 3D vision, and barcode or QR code technologies.

Machine vision is an important component of the proposed system because it ensures that automation authentication and inspection provide extra production data. With the integration of ERP, MES, and shop-floor systems, machine vision can assist in creating a more complete real-time view of the state of an order.

Digitalization presents both organizational and implementation challenges. Thun et al. (2022) look into the issue of digitalization in the case of an ETO manufacturing company through the lenses of socio-technical systems and semi-structured interviews. Based on their analysis, enabling factors include shared trust, shared visual understanding, shared user point of view, and shared learning, whereas the impediments include the trust in the system; understanding the benefits, economic issues, and learning how to manage scope.

These conclusions have implications for furniture producers as manufacturers may vary in their technological sophistication. Thus, the intelligent order management system must take into consideration the current software programs, machinery, responsibilities of workers in the manufacture of furniture, reliability of data and organizational processes along with technological functionality.

All the things put together above show that the literature related to furniture indicates that technologies related to Industry 4.0 could contribute to a few stages of the manufacturing process. Digital configurators as well as product data information can help with dealing with customers; ERP, WMS, APS and MES can be used in information management and management production; Digital Twin and simulation can be used in capacity planning; and machine vision can help with the management of automated production data.

Nonetheless, the reviewed literature also seems to cover different parts of the production/manufacturing processes. Furniture Industry 4.0 literature discusses technology adoption and its organizational differences; Digital Twin literature deals with production processes simulation and capacity issues; machine vision literature deals with automated content collection and quality control; while digitalization literature discusses implementation conditions. So, the literature gives a lot of information regarding certain technologies but much less about the whole production process from customer communication in the showroom through order confirmation, order configuration, planning, scheduling, execution, and production feedback.

## 8. Individual Article Analysis

The article-level analysis summarizes each of the 20 selected publications. The first ten publications are original technical or research studies, while the second ten are review papers. The analysis complements the thematic synthesis in Sections 2–7 and is provided in two companion documents:

- [03a-original-research-articles.md](03a-original-research-articles.md): analysis of the 10 original research studies.
- [03b-review-articles.md](03b-review-articles.md): analysis of the 10 review articles.

## 9. Research Gap

Based on the literature review, there has been quite considerable research on the aspects of digital and individualized production such as mass customization, order management, product designing, enterprise resource planning (ERP)/manufacturing execution system (MES) integration, production planning, smart scheduling, Digital Twins, and technologies of Industry 4.0 when applied to furniture production. Still, the literature is characterized by the fragmentation of research areas.

First, research on mass customization and customer order management emphasizes the importance of connecting customer requirements with product configuration and manufacturing capabilities. Reviews by Naldi et al. (2025) and Bouchard et al. (2023) identify product modularity, customer co-design, digital technologies, process flexibility, digital supply chains, and collaboration as important elements. Research on the CODP and delivery-date setting further demonstrates that order-related decisions depend on operational and supply-chain conditions (Harfeldt-Berg and Olhager, 2024; Bhalla et al., 2023). However, these studies generally examine concepts, factors, or decision problems separately rather than developing an integrated operational workflow for customized furniture orders.

Second, research on product configuration and customer interaction provides approaches for translating customer requirements into structured product information. The tailor-made furniture case study by Łukaszewicz et al. (2023) identifies ineffective information exchange between customers and manufacturers as an important problem and proposes the use of Industry 4.0 technologies to improve coordination. However, the study is conceptual and does not provide a complete implemented order-management system connecting showroom configuration directly to downstream planning, scheduling, and production feedback.

Third, research on ERP, WMS, APS, and MES demonstrates the importance of integrating production-management systems in customized furniture manufacturing. Wu et al. (2023) provide a furniture-specific analysis of these systems. Nevertheless, the main focus is on production management after the order has entered the manufacturing environment. The connection between initial showroom interaction, customer requirements, product configuration, and the integrated production-management architecture is less explicitly addressed.

Fourth, intelligent scheduling research has advanced through optimization algorithms, Digital Twins, Multi-Agent Systems, simulation, and real-time production data (Serrano-Ruiz et al., 2021; Siatras et al., 2024). However, many scheduling studies begin with already-defined production orders and therefore do not address the complete transformation from customer requirements to a production-ready order.

Fifth, furniture-specific Industry 4.0 research demonstrates the applicability of Digital Twins, simulation, machine vision, ERP/MES/APS integration, and real-time data collection. However, these technologies are generally investigated as individual solutions to particular production problems rather than as components of a unified showroom-to-factory order lifecycle.

The literature therefore suggests five specific research gaps:

1. **Integration gap:** customer interaction, configuration, production management, and scheduling are frequently addressed independently. There is a need for a workflow that connects these stages through a common order representation.
2. **Showroom-to-factory gap:** there is limited implementation-oriented research on transferring a structured showroom order directly into factory planning and execution systems in customized furniture manufacturing.
3. **Configuration-to-planning gap:** product configurators can transform customer preferences into product specifications, while APS and scheduling systems can optimize production. The integration between configuration results and downstream capacity, material, and scheduling decisions remains insufficiently addressed.
4. **Real-time feedback gap:** smart manufacturing research supports real-time production monitoring and adaptive scheduling, but production feedback is not always connected back to the customer-order layer.
5. **Furniture-specific intelligent order-management gap:** advanced research on order management, optimization, Digital Twins, and intelligent scheduling is often conducted outside furniture manufacturing, while furniture-specific studies frequently focus on individual technologies.

Based on these gaps, the central research problem can be formulated as follows:

> How can an intelligent order management system integrate showroom customer requirements, product configuration, production feasibility, planning, scheduling, and factory feedback into a unified workflow for customized furniture manufacturing?

The proposed research therefore focuses on integration rather than on a single isolated technology. The intended workflow is:

> Showroom → Customer Requirements → Product Configuration → Order Validation → ERP/WMS → Capacity and Production Planning → APS/Scheduling → MES/Shopfloor → Production Feedback → Order Status

No particular architecture or technology is confirmed by the literature to be the best for all manufacturers of furniture. The literature indicates the technologies and methods that can complement each other in terms of the characteristics and digital maturity of the manufacturing environment. Therefore, empirical studies should be conducted in order to design, implement and assess an integrated solution in real-world furniture manufacturing conditions.

## 10. Conclusion

The aim of this literature review is to determine prior studies and findings related to the implementation of the smart order management system in the process of automation of the entire workflow from showroom to factory. The literature reviewed shows that the transfer of customer specifications to manufacturing processes consists of several processes, including customer order management, product configuration, production planning, scheduling, integration of information systems, and realization of operations on the shop floor.

The study on customer order management and mass customization indicates that personalized production involves close communication between the needs of customers and production abilities. The product modularity, customer co-design, configurators, digital supply chain, and evaluation of delivery terms are the main mechanisms to control the high variety of production. At the same time, it is important to note that order approval has to be considered together with production volume capability, raw material involvement, engineering requirements, and delivery commitment options (Harfeldt-Berg and Olhager, 2024; Naldi et al., 2025; Bhalla et al., 2023; Cavero et al., 2025).

The studies around product configuration and customer communications have shown that digital configuration and visualization technologies enable transforming customer needs into organized product information. When custom-made furniture is manufactured, the use of digital product models, product data management systems, computer-aided manufacturing, and customer-oriented visualization allows for better coordination between customer interaction and manufacturing information (Lukaszewicz et al., 2023; Mueller et al., 2022).

ERP, WMS, APS, MES are part of the technology and data integration research, which indicates the need for enterprise, planning, warehouse and manufacturing execution data being connected. The research on data gathering and standardizing processes shows the significance of standardization in industry as well as that of OPC UA, information models and interoperability for the integration of diverse manufacturing data (Schlemitz and Mezhuyev, 2024). Additionally, the research into digital thread and shopfloor management stresses the importance of interoperability, traceability, data preparation and the suitable conditions for utilization of data (Wu et al., 2023; Abdel-Aty and Negri, 2024; Eichenseer and Winkler, 2024, 2025).

Studies on production planning and smart scheduling show how optimization, Digital Twins, Multi-Agent Systems, simulation, and real-time production data promote adaptive production decisions (Serrano-Ruiz et al., 2021; Siatras et al., 2024; Jia et al., 2024; Lalik et al., 2023). Nonetheless, in many studies of scheduling, the research begins after identifying production needs. Therefore, the connection between order management at the customer level and scheduling at the factory level becomes weaker.

The research specific to furniture shows how Industry 4.0 technologies such as Digital Twins, simulation, machine vision, ERP/MES/APS integration, and real-time data collection can be applied to customized production and atypical production (Cerveny et al., 2022; Lalik et al., 2023; Li et al., 2023; Wu et al., 2023). However, the literature is still divided when it comes to the application of these technologies and organizational layers.

Consequently, the primary opportunity for research identified by the review is the development of a unified intelligent order-management system to customize furniture production. This system must ensure visible linkages between the showroom and manufacturing processes downstream through order digitalization. Moreover, customer requirements should be transformed into product configuration and production needs. The proposed workflow can be summarized as:

> Showroom → Customer Requirements → Product Configuration → Order Validation → ERP/WMS → Capacity and Production Planning → APS/Scheduling → MES/Shopfloor → Production Feedback → Order Status

The present literature review builds the case for the research project by underscoring the significance of digital customer interaction, integrating information systems, smart planning, adaptive scheduling, and real-time production data. The next step is to combine these technologies into one fully functional workflow from the point of the showroom to the factory, with the customer order being its focal point.

## References

Abdel-Aty, T. A. and Negri, E. (2024). Conceptualizing the digital thread for smart manufacturing: a systematic literature review. *Journal of Intelligent Manufacturing*, 35:3629–3653.

Bhalla, S., Alfnes, E., and Hvolby, H.-H. (2023). Tools and practices for tactical delivery date setting in engineer-to-order environments: a systematic literature review. *International Journal of Production Research*, 61(7):2339–2371.

Bouchard, S., Gamache, S., and Abdulnour, G. (2023). Operationalizing mass customization in manufacturing SMEs—a systematic literature review. *Sustainability*, 15(4):3028.

Cannas, V. G. and Gosling, J. (2021). A decade of engineering-to-order (2010–2020): Progress and emerging themes. *International Journal of Production Economics*, 241:108274.

Cavero, J. V., Alemany, M. M. E., Esteso, A., and Gimenez, A. (2025). Revenue management optimization for make-to-order and engineering-to-order manufacturing context. *International Journal of Production Economics*, 288:109715.

Cerveny, L., Sloup, R., and Cervena, T. (2022). The potential of smart factories and innovative industry 4.0 technologies—a case study of different-sized companies in the furniture industry in Central Europe. *Forests*, 13(12):2171.

Eichenseer, P. and Winkler, H. (2024). A data-oriented shopfloor management in the production context: a systematic literature review. *The International Journal of Advanced Manufacturing Technology*, 134:4071–4097.

Eichenseer, P. and Winkler, H. (2025). Data-oriented shopfloor management: an inductively developed holistic conceptual model. *The International Journal of Advanced Manufacturing Technology*, 138:999–1021.

Harfeldt-Berg, M. and Olhager, J. (2024). The customer order decoupling point in empirical operations and supply chain management research: a systematic literature review and framework. *International Journal of Production Research*, 62(17):6380–6399.

Jia, Y., Zhou, Y., and Fu, Y. (2024). A multi-objective brain storm optimization for integrated distributed flexible job shop and distribution problems. *Heliyon*, 10(16):e36318.

Lalik, K., Rumin, R., Pawlowski, G., Jurczyk, K., Gieracki, L., and Jedrzychowski, S. (2023). Simulation modeling for mass customization furniture production: Investigating production volume and machine load in scope of industry 4.0 standard. *Industry 4.0*, 8(4):116–122.

Li, R., Zhao, S., and Yang, B. (2023). Research on the application status of machine vision technology in furniture manufacturing process. *Applied Sciences*, 13(4):2434.

Lukaszewicz, K., Urban, W., and Krawczyk-Dembicka, E. (2023). Conceptualization of industry 4.0 technology for the production of tailor-made furniture – a case study. *Bulletin of the Polish Academy of Sciences: Technical Sciences*, 71(1):e144587.

Mueller, G. O., Mortensen, N. H., Hvam, L., Haug, A., and Johansen, J. (2022). An approach for the development and implementation of commissioning service configurators in engineer-to-order companies. *Computers in Industry*, 142:103717.

Naldi, L. D., Galizia, F. G., Bortolini, M., Gabellini, M., and Ferrari, E. (2025). Unlocking the potential of mass customization through industry 4.0: Mapping research streams and future directions. *Applied Sciences*, 15(13):7160.

Schlemitz, A. and Mezhuyev, V. (2024). Approaches for data collection and process standardization in smart manufacturing: Systematic literature review. *Journal of Industrial Information Integration*, 38:100578.

Serrano-Ruiz, J. C., Mula, J., and Poler, R. (2021). Smart manufacturing scheduling: A literature review. *Journal of Manufacturing Systems*, 61:265–287.

Siatras, V., Bakopoulos, E., Mavrothalassitis, P., Nikolakis, N., and Alexopoulos, K. (2024). Production scheduling based on a multi-agent system and digital twin: A bicycle industry case. *Information*, 15(6):337.

Thun, S., Bakas, O., and Storholmen, T. C. B. (2022). Development and implementation processes of digitalization in engineer-to-order manufacturing: enablers and barriers. *AI and Society*, 37(2):725–743.

Wu, Z., Zong, F., Zhang, F., Wang, J., Zhu, Z., Guo, X., and Cao, P. (2023). Investigation of the customized furniture industry’s production management systems. *Journal of Engineering Research*, 11(3):164–175.