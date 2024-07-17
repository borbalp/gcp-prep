# GCP Resource Cheat Sheet

### Compute Solutions

| **Service**            | **Auto Scales to 0** | **Max Execution Time**    | **Supports Docker** | **VM-Based**      | **Serverless**   | **Notes**                                                                                      |
|------------------------|----------------------|---------------------------|---------------------|-------------------|------------------|-----------------------------------------------------------------------------------------------|
| Compute Engine         | No                   | N/A                       | No                  | Yes               | No               | Full control over VMs, supports custom machine types and GPUs.                                 |
| Kubernetes Engine (GKE)| Yes (with Autopilot) | N/A                       | Yes                 | Yes               | No               | Managed Kubernetes, supports Docker, integrates with GCR, auto-scaling.                        |
| App Engine Standard    | Yes                  | N/A                       | No                  | No                | Yes              | PaaS, supports multiple languages, automatic scaling.                                         |
| App Engine Flexible    | No                   | N/A                       | Yes                 | Yes               | Yes              | PaaS, custom runtimes, more flexible than Standard, supports Docker.                           |
| Cloud Functions        | Yes                  | 60 minutes (HTTP)         | No                  | No                | Yes              | FaaS, event-driven, supports various triggers (HTTP, Pub/Sub, etc.), auto-scaling.             |
| Cloud Run              | Yes                  | 60 minutes                | Yes                 | No                | Yes              | Serverless, fully managed, supports Docker containers, auto-scaling.                           |

### Storage Options

| **Service**            | **Lifecycle Management** | **Versioning** | **Retention Policy** | **Max Object Size** | **Notes**                                                                                      |
|------------------------|--------------------------|----------------|----------------------|---------------------|-----------------------------------------------------------------------------------------------|
| Cloud Storage          | Yes                      | Yes            | Yes                  | 5 TB                | Object storage, various classes (Standard, Nearline, Coldline, Archive), global availability.  |
| Persistent Disk        | No                       | No             | No                   | 64 TB               | Block storage for VMs, SSD and HDD options, regional availability.                            |
| Filestore              | No                       | No             | No                   | 100 TB              | Managed NFS, high performance, regional availability.                                          |
| Local SSD              | No                       | No             | No                   | 3 TB                | Directly attached to VM, very high performance, data not preserved after VM termination.       |

### Databases

| **Service**            | **Relational** | **Horizontally Scalable** | **Managed** | **Serverless** | **Notes**                                                                                      |
|------------------------|----------------|--------------------------|-------------|----------------|-----------------------------------------------------------------------------------------------|
| Cloud SQL              | Yes            | No                       | Yes         | No             | Managed MySQL, PostgreSQL, SQL Server, supports replicas, backups, and point-in-time recovery.|
| Cloud Spanner          | Yes            | Yes                      | Yes         | No             | Horizontally scalable, global consistency, suitable for mission-critical apps.                |
| Firestore              | No             | Yes                      | Yes         | Yes            | NoSQL document database, real-time sync, serverless, suitable for mobile/web apps.            |
| Cloud Bigtable         | No             | Yes                      | Yes         | No             | NoSQL wide-column store, low-latency, suitable for analytics and operational workloads.       |
| Memory Store           | No             | No                       | Yes         | No             | Managed Redis and Memcached, sub-millisecond latency, in-memory data store.                   |
| Bare Metal             | Yes            | No                       | Partially   | No             | Dedicated hardware for Oracle workloads, lift and shift, high performance.                    |
