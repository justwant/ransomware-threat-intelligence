# AI Usage Disclosure — Week 7

Artificial Intelligence (AI) was used as a supporting tool during the development and documentation of Week 7.

## How AI Was Used

AI assistance was used for:

- Explaining the MITRE Cyber Analytics Repository (CAR).
- Explaining the difference between analytics and detections.
- Assisting with the understanding of CAR-2021-01-001 — Identifying Port Scanning Activity.
- Explaining the relationship between CAR-2021-01-001 and T1046 — Network Service Discovery.
- Assisting with the construction and explanation of the Elasticsearch query.
- Explaining the `cardinality` aggregation used to count unique destination ports.
- Explaining the `bucket_selector` used to implement the detection threshold.
- Providing troubleshooting guidance during the Elasticsearch and Kibana implementation.
- Assisting with the creation and organization of the Kibana visualization and dashboard.
- Assisting with the structure and formatting of the Week 7 documentation.
- Reviewing the wording of the analysis and conclusion.

## What Was Performed by the Student

The following practical activities were performed by the student:

- Worked with the ELK environment using Elasticsearch and Kibana.
- Used the `threat-hunting-lab` Elasticsearch index.
- Created and loaded network connection events into Elasticsearch.
- Worked with source IP, destination IP, destination port, and event category fields.
- Implemented the CAR detection logic in Elasticsearch.
- Grouped network events by source IP.
- Calculated unique destination ports using the `cardinality` aggregation.
- Implemented the detection threshold using `bucket_selector`.
- Executed the detection query in Kibana Dev Tools.
- Verified that source IP `10.0.2.15` generated seven unique destination ports.
- Verified that the detection threshold of more than five ports was satisfied.
- Created a Kibana visualization for CAR-2021-01-001.
- Created the `MITRE CAR - Port Scanning Detection` dashboard.
- Collected screenshots of the Elasticsearch query, detection result, and Kibana visualization.
- Mapped the CAR analytic to T1046 — Network Service Discovery.
- Documented the results in the GitHub repository.

## AI Role and Academic Integrity

AI was used as an assistance and learning tool, not as a replacement for the student's practical work.

The Elasticsearch and Kibana environment, network dataset, queries, visualizations, and detection results were executed and verified by the student.

The final detection result was obtained from the student's laboratory environment. The result showed that source IP `10.0.2.15` contacted seven unique destination ports, exceeding the detection threshold of five.

AI was used to explain the CAR analytic, assist with query construction and troubleshooting, and help organize the documentation.

The student is responsible for the final content, technical implementation, analysis, screenshots, and conclusions presented in Week 7.
