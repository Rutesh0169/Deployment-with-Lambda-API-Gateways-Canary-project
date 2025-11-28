📌 Project Objective :-
The main goal of this project is to build a serverless, scalable, and resilient API architecture that allows seamless feature rollout and testing using canary deployments. This ensures new Lambda code versions are tested safely with a small portion of traffic before a full release, reducing downtime and minimizing risks of errors in production.

📌 Project Description:-
This setup uses AWS Lambda for running backend code without provisioning servers, and Amazon API Gateway to expose Lambda as a REST or HTTP API to external users. A canary deployment strategy is applied in API Gateway, where a small percentage of API traffic is routed to the new Lambda version while the rest continues using the stable version. If the canary performs well, traffic is gradually shifted, or else rolled back quickly.

This approach enables:

Continuous delivery with minimal risks.

Easier debugging and monitoring of new features.

Controlled rollout and fast rollback of new Lambda versions.

📌 Architecture Flow :-

<img width="717" height="271" alt="image" src="https://github.com/user-attachments/assets/77d4e06f-bd4a-49dc-9e38-e8b424da3d53" />


  Canary metrics are analyzed to decide whether to roll forward or roll back.
image
📌 Benefits of This Setup:-
✅ Serverless Architecture – No infrastructure management; automatic scaling.

✅ Cost-Effective – Pay only for execution time and requests.

✅ Controlled Rollouts – Canary deployment minimizes risk by testing new versions on a subset of traffic.

✅ High Availability – API Gateway and Lambda are fully managed, ensuring resilience.

✅ Faster Iterations – Supports CI/CD pipelines for quick feature releases.

✅ Safe Rollbacks – Easy rollback if the canary version causes issues.

✅ Observability – CloudWatch provides detailed monitoring and insights into canary performance.
