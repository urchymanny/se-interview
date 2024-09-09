Key topics for system design interviews

1. **DNS (Domain Name System)**: Translates domain names into IP addresses.

   - _GCP_: Cloud DNS
   - _AWS_: Route 53

2. **CDN (Content Delivery Network)**: Distributes content to users based on geographic proximity to reduce latency.

   - _GCP_: Cloud CDN
   - _AWS_: CloudFront

3. **Load Balancer**: Distributes incoming traffic across multiple servers to ensure high availability and reliability.

   - _GCP_: Cloud Load Balancing
   - _AWS_: Elastic Load Balancing (ELB)

4. **Rate Limiter**: Controls the number of requests a user can make in a given time period to prevent overloading systems.

   - _GCP_: Cloud Endpoints with Quota
   - _AWS_: API Gateway with throttling

5. **Cloud Storage**: Stores and retrieves large amounts of unstructured data.

   - _GCP_: Cloud Storage (Blob)
   - _AWS_: S3

6. **Database**: Organized collection of structured data.

   - _GCP_: Cloud SQL, Firestore
   - _AWS_: RDS, DynamoDB

7. **Application Servers/Containers/Pods**: Hosts applications in isolated environments.

   - _GCP_: GKE (Google Kubernetes Engine)
   - _AWS_: ECS (Elastic Container Service) / EKS (Elastic Kubernetes Service)

8. **Services (Microservices)**: Independent, modular services that communicate over a network.

   - _GCP_: Cloud Run
   - _AWS_: Lambda, ECS

9. **Job Servers**: Executes background tasks asynchronously.

   - _GCP_: Cloud Tasks
   - _AWS_: AWS Batch

10. **Job Queue**: Queues tasks for asynchronous processing.

- _GCP_: Pub/Sub
- _AWS_: SQS (Simple Queue Service)

11. **Caching Services**: Temporary storage to speed up data retrieval.

- _GCP_: Memorystore (Redis)
- _AWS_: ElastiCache (Redis/Memcached)

12. **Full-Text Search Service**: Allows full-text searching across large datasets.

- _GCP_: Elastic Cloud on GCP
- _AWS_: Elasticsearch Service (OpenSearch)

13. **Data Warehouse**: Centralized repository for large-scale analytics and reporting.

- _GCP_: BigQuery
- _AWS_: Redshift

14. **Data Firehose**: Service for real-time data streaming to storage or analytics.

- _GCP_: Pub/Sub + Dataflow
- _AWS_: Kinesis Firehose

15. **Cloud Storage (Blob)**: Object storage for unstructured data.

- _GCP_: Cloud Storage
- _AWS_: S3

These definitions and examples provide a quick overview of key topics for system design interviews with cloud-based solutions.
