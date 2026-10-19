# Existing System Comparison

**Author:** Ayazhan Orynbasar

## 1. Purpose

Before building anything, we wanted to see what a furniture manufacturer can already buy or use. This document compares existing software for custom furniture orders and production planning with the system we propose. We look at it through one question: can the tool help a showroom manager give a customer a reliable delivery date at the moment the order is accepted?

## 2. Selected Systems

We chose five systems. They are not five competitors of the same kind. Each one represents a different type of tool that a furniture company might use, and together they show how the parts of our problem are usually handled in separate products.

| # | System | Category | Source |
|---|---|---|---|
| S1 | Klipboard | ERP for furniture and wood products | [1] |
| S2 | imos | CAD/CAM and ERP suite for furniture | [2] |
| S3 | Allmoxy | Online ordering for cabinet and furniture makers | [3] |
| S4 | Tacton configured order fulfillment | Configuration (CPQ) and handoff to production | [4] |
| S5 | Siemens Tecnomatix Plant Simulation | Factory simulation and digital twin | [5], [6] |

## 3. Comparison Criteria

We applied the same eight criteria to every system.

| ID | Criterion | Why we look at it |
|---|---|---|
| C1 | Furniture or wood-industry focus | Furniture has its own materials, finishes and production routes |
| C2 | Order entry and product configuration | A custom order has to be captured in a structured form |
| C3 | Validation of the configuration | Impossible combinations should be caught before production |
| C4 | Link between order and production or ERP | The order should reach production without being typed again |
| C5 | Production scheduling or capacity visibility | A date depends on how busy the factory is |
| C6 | Delivery-date estimation at order acceptance | This is the decision our project is about |
| C7 | Simulation or digital twin of the factory | Needed to test dates when things go wrong |
| C8 | Explanation or uncertainty of the date | A manager needs a range and reasons, not a single number |

## 4. Comparison Table

How to read the table: **Yes** means the source page states it. **Partly** means a related feature is mentioned without much detail. **Not stated** means the source page does not mention it. Please note that "Not stated" does not prove the feature is missing. It only means we could not confirm it from the source we cite.

| Criterion | S1 Klipboard | S2 imos | S3 Allmoxy | S4 Tacton | S5 Siemens Plant Simulation |
|---|---|---|---|---|---|
| C1 Furniture focus | Yes: furniture and wood ERP | Yes: parametric 3D furniture and interior design | Yes: cabinet and furniture makers | No: general manufacturing | No: general manufacturing |
| C2 Order entry and configuration | Partly: configurable products with modular BOM, colours, sizes, options | Yes: order entry, job management, room planning and point-of-sale configuration | Yes: online storefront and 3D catalog, order management | Yes: configuration and CPQ output | Not stated |
| C3 Validation | Not stated | Not stated | Not stated | Yes: prevention of invalid combinations, rule-based validation | Not stated |
| C4 Link to production / ERP | Yes: production orders tracked through stages | Yes: CNC connectivity from CAD, shop-floor control | Yes: integrates with Cabinet Vision, CutRite, Microvellum, Mozaik, QuickBooks, NetSuite | Yes: automated handoff, ERP integration, MES support, automatic bill of materials | Partly: sends shop-floor data back to simulation and scheduling |
| C5 Scheduling / capacity | Yes: schedules production with capacity visibility across departments | Not stated | Partly: production scheduling and tracking listed, no detail | Not stated | Yes: schedule optimisation, throughput and resource utilisation |
| C6 Delivery-date estimation | Not stated (only delivery windows) | Not stated | Not stated | Not stated | Partly: "predict order delivery dates and optimize schedules" |
| C7 Simulation / digital twin | Not stated | Not stated | Not stated | Not stated | Yes: production digital twin, predictive simulation engine |
| C8 Reasons / uncertainty | Not stated | Not stated | Not stated | Not stated | Not stated |

## 5. What Each System Does

**S1 Klipboard.** A furniture ERP. It handles configurable products, production orders and scheduling, and it gives visibility of capacity across departments. The source does not mention a promise date or any simulation. For delivery it talks about delivery windows and proof of delivery [1].

**S2 imos.** A suite that links furniture design, order and job management, CNC machines and shop-floor control. It is clearly strong on the design and production side. The source says nothing about planning, scheduling or estimating dates [2].

**S3 Allmoxy.** An online ordering platform with a 3D catalog, order management and production scheduling. It connects to cabinet-making software and accounting systems. It looks good for taking orders, but the source does not mention delivery-date estimation [3].

**S4 Tacton.** Turns a validated configuration into structured manufacturing data, blocks invalid combinations and passes the order on to ERP and MES. It solves the digital-order part, but not the delivery date or the load of the factory [4].

**S5 Siemens Tecnomatix Plant Simulation.** A production digital twin built on simulation. Its description includes predicting order delivery dates and optimising schedules [5]. However, it is a general factory tool. It is not made for furniture, it does not take orders from a showroom, and the sources do not explain how an incoming order becomes an input for the simulation [5], [6].

## 6. What We Found

- The furniture-specific tools (S1, S2, S3) are good at taking orders, configuring products and running production. None of their sources describes a delivery date based on the current state of the factory.
- The configuration tool (S4) produces a clean digital order, but it stops at the handoff to production.
- The only tool whose source mentions both simulation and delivery-date prediction (S5) is a general factory tool with no connection to a showroom order.
- None of the sources says that the system explains the date or shows how uncertain it is (C8).

## 7. Conclusion: Why Our Solution Is Needed

Among the systems we reviewed, none combines three things: capturing a custom furniture order at the showroom, simulating the factory in its current state, and giving the manager a delivery-date range with reasons to pass on to the customer. The separate pieces exist. Configurators and furniture ERPs handle the order, scheduling modules handle the load, and general simulation tools handle what-if analysis. What is missing is the connection between them at the moment the order is accepted.

Our system is meant to fill exactly this gap. It has a minimal manager interface, a backend with a structured digital order, and a simulation-based digital twin that returns a date range with reasons. This matches what the literature says: tools for delivery-date setting mostly support tactical capacity planning and fit poorly with what industry needs [7].

## 8. Limitations of This Comparison

- We relied on vendor documentation and product pages. We did not install or test the software, so a feature may exist even if its page does not describe it.
- Vendor pages are written in marketing language, so we record a function as "stated" or "not stated" rather than "present" or "absent".
- Five systems cannot cover the whole market. We picked them to represent the main categories of tools.
- We did not compare prices, licences or technical limits.

## References

[1] Klipboard, "Purpose-built ERP software for furniture and wood products manufacturers." https://www.klipboard.com/sectors/manufacturing/furniture-wood

[2] ForestSource, "imos." https://forestsource.io/software/imos

[3] ForestSource, "Allmoxy." https://forestsource.io/software/allmoxy

[4] SoftwareOne Marketplace, "Tacton Configured Order Fulfillment." https://platform.softwareone.com/product/tacton-configured-order-fulfillment/PCP-4115-9657

[5] Siemens, "Tecnomatix: Optimize my plant." https://www.siemens.com/lt-lt/products/tecnomatix/offerings/optimize-my-plant/

[6] Siemens, "Revolutionize plant production with digitalization." https://blogs.sw.siemens.com/tecnomatix/revolutionize-plant-production-with-digitalization/

[7] S. Bhalla, E. Alfnes, and H.-H. Hvolby, "Tools and practices for tactical delivery date setting in engineer-to-order environments," *International Journal of Production Research*, vol. 61, no. 7, 2023.
