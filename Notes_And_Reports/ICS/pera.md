# Purdue Enterprise Reference Architecture (PERA)

> This high-level report focuses on understanding PERA, breaking down related tools used within EA,
> and analyzing the cybersecurity implications of said topics.

## Table of Contents

- [Introduction](#introduction)
- [Enterprise Architecture](#enterprise-architecture)
- [PERA Layers & Vulnerabilities](#pera-layers)
  - [Layer 0: Physical Processes](#layer-0-physical-processes)
  - [Layer 1: Intelligent Devices](#layer-1-intelligent-devices)
  - [Layer 2: Control Systems](#layer-2-control-systems)
  - [Layer 3: Manufacturing Operations Systems](#layer-3-manufacturing-operations-systems)
  - [Layer 4: Business Logistics](#layer-4-business-logistics)
- [Security Implications](#security-implications)
- [Conclusion](#conclusion)

## Introduction

The **Purdue Enterprise Reference Architecture** is a common model used to describe the control processes within **Enterprise Architecture**.
This model is a useful tool to understand the data and systems utilized within enterprises, and how enterprises work to optimize goal-metrics.
Additionally, this model allows for understanding how end-users and vendors can integrate applications. From a security angle, it helps to
break down the different attack vectors within industrial control systems (ICS) and operational technology (OT) by separating concerns into PERA layers.

## Enterprise Architecture

Enterprise Architecture (EA) is concerned with the behaviors of a business in processes and roles that create and use business data.

**For example**, imagine that there is a paper-selling office located in Scranton. One day, this office has a safety training,
and one of the employees starts a fire and destroys the CPR dummy.

***The following would concern EA:***
- Financial expenditures of any damages
- Delay in shipping and sales
- Reductions on employee utilization

***The following would not concern EA:***
- A cat was thrown into the ceiling
- The CPR dummy's face and imaginary organs were removed
- This event resulted in a roasting session of the office branch's boss

EA has a primary goal of developing practices and creating well-defined decisions in how a business makes decisions.
Primarily, enterprises use these structures to execute its strategies by adjusting how it uses business capabilities, information, process,
and technology. EA's primary scope is within IT design, ecosystem adaptation, and integration.

By maintaining EA, this allows technology-related decision-making to be standardized- which reduces complexity, allows for consolidation,
reduces system failures, and improves connectivity between systems. Other techniques/strategies can be used to maintain enterprise technology,
though similar procedures generally chase same goals that EA attempts to achieve.

## PERA Layers

PERA is divided into 5 Layers, with layers 0-2 being grouped into one layer as real-time control, as they are all involved with physical processes.

![PERA Diagram from Wikipedia](../assets/PERA_Decision-making_and_control_hierarchy.jpg)

### Layer 0: Physical Processes

#### Description

This is the actual materials and non-programmable/passive devices. Physical processes are conducted by passive devices
onto manufacturing materials. Pretty straightforward.

#### Vulnerabilities

This is the simplest layer in terms of vulnerabilities, as nearly everything is physical.

- **Supply-Chain Trust** - Availability/Integrity - Are the materials and machines being acquired trustworthy and quality?
- **Unauthorized Access/Espionage** - Integrity/Confidentiality - Are individuals with access to the manufacturing floors authorized and trustable?
- **Physical Sabotage** - Availability/Integrity - Can the physical processes be manipulated to do unintended things?
- **Environmental Exposure** - Availability - Is the plant/manufacturing site secure against environmental disasters?
- **Effective Physical Processes** - Availability - Is the plant/manufacturing site designed well?

#### Examples

1. **Accelerator Pedal Recall (2010)** - Toyota had to recall 8.5 million vehicles due to defective accelerator pedals supplied by a third-party vendor. This is a faliure in supply-chain trust that violated availability.
2. **Coca-Cola Trade Secret Theft (2018)** - Three employees were stealing trade secrets from Coca-Cola with the intent to sell information to a competitor. This is unauthorized access that violated integrity.
3. **Australian Federal Police v. NTC Company (2010)** - NTC Company discovered that a long term employee at their industrial chemical plant was adding foreign substances to chemicals, which caused products to fail quality control. This is physical sabotage that violated availability.

### Layer 1: Intelligent Devices

#### Description

This is where things actually start getting fun. Intelligent devices sense and manipulate the physical processes in Layer 0.

#### Vulnerabilities

### Layer 2: Control Systems

#### Description

### Layer 3: Manufacturing Operations Systems

#### Description

#### Vulnerabilities

### Layer 4: Business Logistics

#### Description

Business logistics is all about how a business is using its resources. The decisions made in business logistics
occur over the scale of years, months, and weeks. Typically, business logistics use **Enterprise Resource Planning (ERP)**,
or something similar. ERP is a model that organizes material use, shipping & inventory, and the basic plant production schedule-
all while planning to meet future business objectives.

ERP leverages business management software- typically cloud-based. It continuously updates core business processes in real-time
using database management systems. It tracks cash, materials, production capacities, orders, purchases, and payroll. ERP applications
can share data across varying departments and manage connections with external stakeholders.

![ERP Modules from Wikipedia](../assets/ERP_modules.png)

Business logistic concerns are grouped into modules following ERP. A few ERP modules are as follows:

- **Sales** - pricing, sales analysis and reporting, and order entry
- **Project Management** - project planning, project costing, time and expense, performance and activity, and resource planning
- **Financial accounting** - ledger, assets, payment, cash management, and financial consolidation
- **Management accounting** - budgeting, cost management, billing, and invoicing
- **Product Lifecycle Management (PLM)** - engineering, bill of materials, work orders, scheduling, capacity, quality control, and maufacturing process
- **Supply Chain Management (SCM)** - suppy chain planning, supplier scheduling, purchasing, inventory, and warehousing
- **Human Resources (HR)** - recruiting, training, rostering, payroll, benefits, retirement, diversity, and separation.
- **Customer Relationship Management (CRM)** - sales, marketing, commissions, service, customer contact, and call center support
- **Supplier Relationship Management (SRM)** - suppliers, orders, and payments

#### Connections to other Layers

Business logistics is unique as it seems quite removed from the actual "ICS part" of OT technology. But, the logistics of the business 
have direct effect on the decisions made within plants/factories. Additionally, ERP system software is still very much is a control system- 
just with human and financial resources instead of material resources.

With that being said, ERP systems vary in how integrated they are with lower levels of PERA. It depends on ERP systems, but there are 3 main integration types:

- **Direct Integration** - This can only occur if a vendor for ERP software offers specific support for plant floor equipment. This connects Layer 4 directly to the other layers of PERA, therefore meaning ERP systems can have built-in software that we see in Layer 3.
- **Database Integration** - ERP systems connect to plant floor data sources through staging tables in databases. This connects Layer 4 directly to Layer 3.
- **Enterprise Appliance Transaction Modules (EATM)** - EATM directly talks to both plant floor equipment and ERP systems. In this case, EATM plays the role of Layer 3.

#### Vulnerabilities

-
-

#### Examples



## Security Implications



## Conclusion

-
