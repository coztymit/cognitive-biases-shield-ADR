# 26.04.2020
# Should we use Apache Kafka for the project?

## ADR Status

- [x] `Proposed`: The decision has been suggested but not yet discussed or approved.
- [ ] `Accepted`: The decision has been approved and is currently in effect.
- [ ] `Rejected`: The decision was not approved.
- [ ] `Deprecated`: The decision was previously in effect but is no longer relevant or has been replaced.
- [ ] `Superseded`: The decision has been replaced by a newer decision.
- [ ] `Deferred`: The decision is postponed for later due to a lack of information or it not being a priority.
- [ ] `In Review`: The decision is currently being reviewed by the team or stakeholders.

# Decision
_[What decision was made and why?]_

# Context
The current project requires real-time data processing. With the increase in data volume, our current system is not scalable and lacks fault tolerance. Apache Kafka's reputation and capabilities in this area have made it a strong candidate.
- Need for real-time data processing.
- Scalability issues with the current system.
- Lack of fault tolerance in the present setup.


# Decision process 
## 1. Main Solution 

| Main solution | Argument For                                       | Argument Against                                                                   | Why I Like It                                | Why I Don't Like It              |
|---------------|----------------------------------------------------|-----------------------------------------------------------------------------------|-----------------------------------------------|-----------------------------------|
| Apache Kafka  | Highly scalable, robust, and fault-tolerant. Stream processing capabilities. | Requires specialized knowledge and might introduce complexity. Potential for overengineering. | Mature and widely used technology. Strong community support. | Steep learning curve. Requires infrastructure management. |



## 2. Alternative Solutions

| Solution       | Argument For                                             | Argument Against                                                     | Why I Like It                                         | Why I Don't Like It                                             |
|----------------|----------------------------------------------------------|----------------------------------------------------------------------|-------------------------------------------------------|-----------------------------------------------------------------|
| RabbitMQ       | Good for message queuing. Easy setup. Reliable.          | Not primarily designed for data streaming. Limited scalability.      | Simple and lightweight. Established community.        | Doesn't address our need for large-scale streaming. Learning curve. |
| AWS Kinesis    | Managed and scalable. High availability. Integration with AWS services. | Locked into AWS ecosystem. Costs can spike. Limited customization.   | No need to maintain infrastructure. Managed security. | Might get expensive with increasing scale. Vendor lock-in.      |
| NATS Streaming | High performance. Lightweight protocol. Good documentation. | Younger ecosystem compared to Kafka. Limited plugins. Less robust.   | Lightweight and fast. Modern architecture.            | Smaller community. Newer, hence fewer tested scenarios.        |


## 3. Areas and dynamics of change

| Area                  | Area changes dynamic | Proposed solution  |
|-----------------------|----------------------|--------------------|
| Inventory Management  | Dynamic              | Apache Kafka       |
| Customer Notifications| Moderate             | RabbitMQ           |
| Order Processing      | Dynamic              | Apache Kafka       |
| Product Recommendations| Moderate            | RabbitMQ           |
| Payment Processing    | Static               | [Another Solution] |
| User Account Management| Moderate            | RabbitMQ           |

            

- **Area:** Area affected by the solution
- **Dynamic:** The area is currently changing very frequently.
- **Moderate:** The area is changing at a moderate pace.
- **Static:** The area is currently changing very rarely.
- **Proposed solution:** What is the best solution for this area?

## 4. Visualization
Are we able to present any visualizations, statistics, metrics, charts that might assist in making the decision?
- Throughput metrics of Kafka vs. others.
- Scalability charts based on data volume.

## 5. Risk analysis 
### Premortem analysis
"If, one year from now, the chosen solution doesn't meet the requirements and turns out to be a failure, what must have transpired to lead to this outcome?"
- Inadequate Kafka expertise in the team.
- The complexity of Kafka led to operational overhead.
- Unforeseen costs related to scaling and maintenance.
- Integration issues with other parts of the system.
- Frequent downtimes and performance issues.
- Not leveraging Kafka's full capabilities due to a lack of training.
- Vendor lock-in or challenges in migrating data away from Kafka.
- Misalignment of Kafka's features with evolving project requirements.
- Challenges in setting up a high-availability and fault-tolerant system.
- Security vulnerabilities or breaches related to Kafka setup.

## 6. Costs
Can we provide an estimated cost of making the decision?
- Required resources
- Specialist involvement
- Functional requirements
- Non-functional requirements

- **Required resources**: 
  - Hiring 2 Kafka specialists.
  - Kafka training for the entire team.
  - Hardware and infrastructure costs for setting up and scaling Kafka.
  - Licenses (if any) for premium versions or tools associated with Kafka.
  
- **Operational costs**:
  - Ongoing maintenance and monitoring.
  - Potential increased cloud service fees (if hosted on a cloud platform).
  - Periodic upgrades and patches.
  
- **Potential hidden costs**:
  - Downtime or service interruptions leading to business losses.
  - Costs associated with integrating Kafka with other systems.
  - Potential data migration costs if moving away from Kafka in the future.
  - Support and consultancy fees for tackling complex Kafka-related challenges.
  
- **Risk mitigation costs**:
  - Setting up backup and recovery solutions.
  - Investing in security solutions to safeguard Kafka data and operations.



## 7. When can the decision be changed?
Even if the solution is accepted and implemented, there might be reasons for the decision to be altered in the future. Describe the situations in which this could occur.
- Discovery of a better, more cost-effective technology.
- Changes in project requirements making Kafka less suitable.
- Overhead costs and complexities making it unsustainable.
- Significant changes in the Kafka ecosystem or its community.

## 8. Consultations
With whom outside of the team will the decision be consulted?
- Emily Thompson - Software Development Department
- Jordan Martinez - Network Operations Center
