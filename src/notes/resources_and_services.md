# GCP Resources and Services

### Kubernetes

- **Features**
    - Can be configured to automatically scale node pools and clusters across multiple node pools based on changing workload requirements.
    - Auto-repair can be enabled to perform health checks on nodes.
    - Cloud Logging and Cloud Monitoring can be enabled via simple checkbox configurations.
    - Kubernetes version can be set to auto-upgrade with the latest release patch.
    - Supports Docker container format.
    - Integrates with Google Container Registry, allowing easy access to private Docker images.
- **kubectl**
    - The main CLI tool for running commands and managing Kubernetes clusters.
- **Cluster**
    - All of the Kubernetes objects that represent your containerized applications run on top of a cluster.
- **Node**
    - Nodes are the worker machines that run your containerized applications and other workloads.
    - A cluster typically has one or more nodes.
    - Kubernetes runs your workload by placing containers into pods that run on nodes.
- **Node Pool**
    - A node pool is a set of nodes within a cluster that have similar configurations.
- **Cluster Autoscaler**
    - Cluster Autoscaler automatically resizes the number of nodes in a given node pool based on the demands of your workloads.
- **Kubernetes API Objects**
    - **Pods**
        - The smallest deployable units of computing that you can create and manage in Kubernetes.
        - Every pod has its own IP address.
        - Every pod can run multiple containers.
    - **Deployment**
        - Describes the desired state in a deployment, and the Deployment Controller changes the actual state to the desired state at a controlled rate.
    - **Service**
        - Acts as a load balancer to distribute traffic across a set of pods.
        - Types of services:
            - **ClusterIP:** Exposes the service on a cluster-internal IP.
            - **NodePort:** Exposes the service on each node’s IP at a static port (the NodePort).
            - **Load Balancer:** Exposes the service externally using a cloud provider’s load balancer.
- **Workload Resources**
    - [**ReplicaSet**](https://kubernetes.io/docs/concepts/workloads/controllers/replicaset/)
        - Maintains a stable set of replica pods running at any given time to ensure availability.
    - [**StatefulSets**](https://kubernetes.io/docs/concepts/workloads/controllers/statefulset/)
        - Manages stateful applications, ensuring the ordering and uniqueness of pods.
        - Maintains a sticky identity for each pod, which is not interchangeable.
    - [**DaemonSet**](https://kubernetes.io/docs/concepts/workloads/controllers/daemonset/)
        - Ensures that all (or some) nodes run a copy of a pod.
        - As nodes are added or removed from the cluster, pods are added or garbage collected accordingly.
    - **ConfigMaps**
        - Allows separation of configuration data from application code, keeping workloads portable.
- **GKE Sandbox**
    - Provides an additional layer of security between containerized workloads on GKE using gVisor.
    - Cannot be enabled on a default node pool and requires at least two node pools.
    - Does not support accelerations such as GPUs or TPUs.
- **Autopilot**
    - Manages node pool configuration, Autoscaler configuration, overall cluster configuration (network, logging, monitoring), and network and pod security policies.

---

### Compute Engine

- **Instance Groups**
    - A set of virtual machine instances that you can manage as a single entity.
        - **Managed Instance Groups (MIG)**
            - Operates apps on multiple identical VMs.
            - Supports autoscaling, auto-healing, regional deployment, and automatic updating.
            - Can perform auto-healing by triggering health checks and recreating unhealthy instances.
- **Preemptible Instances**
    - VMs that can be provisioned at a lower price point than regular instances.
    - Compute Engine might stop preemptible instances at any time due to system events.
    - Suitable for fault-tolerant applications that can handle instance preemption.
- **Sole-tenant Nodes**
    - A physical Compute Engine server dedicated exclusively for your use.

---

### App Engine

- **Standard and Flexible Environment**
    - **Standard**
        - Based on container instances running on Google’s infrastructure.
    - **Flexible**
        - Allows management of the underlying compute infrastructure.
- **Scaling**
    - **Basic**
        - Creates instances when your application receives requests.
        - Instances shut down when the application is idle.
    - **Automatic Scaling**
        - Creates instances based on request rate, response latencies, or specified application metrics.
    - **Manual Scaling**
        - Allows manual specification of the number of instances that continuously run, regardless of load level.

---

### Cloud Functions

- **Features**
    - Serverless execution environment for building and connecting cloud services.
    - Automatically scales down to zero when not in use, saving costs.
    - Supports various programming languages such as Node.js, Python, Go, and more.
    - Can be triggered by HTTP requests, Cloud Pub/Sub, Cloud Storage, and other event sources.
- **Limits**
    - The maximum timeout duration is 60 minutes (3600 seconds) for HTTP functions and 9 minutes (540 seconds) for event-driven functions.

---

### Cloud Storage

- [Cloud Storage Classes](https://cloud.google.com/storage/docs/storage-classes)
- **Bucket Configurations**
    - **Life Cycle Management**
        - Define conditions that trigger data deletion or transition to a cheaper storage class.
    - **Versioning**
        - Store old copies of objects when they are deleted or overwritten.
    - **Retention Policies**
        - Define minimum retention periods for storing objects.
    - **Object Holds**
        - Place an object on hold to prevent deletion.
    - **Encryption Keys**
        - Customer-managed or customer-supplied encryption keys.
    - **Access Permissions**
        - Access Control List (ACL), uniform bucket-level access, and object and bucket-level permissions.
- **Uploading Objects to Google Cloud Storage**
    - **Simple Upload**
        - Suitable for small files with no metadata requirements.
    - **Multipart Upload**
        - Suitable for small files requiring metadata.
    - **Resumable Upload**
        - Suitable for large files, offering a more reliable transfer.
    - [**Parallel Composite Upload**](https://cloud.google.com/storage/docs/parallel-composite-uploads)
        - Suitable for high-speed networks and large files, uploading in parallel chunks.
    - **Transfer Appliance**
        - Hardware appliance for securely migrating large volumes of data (hundreds of terabytes to 1 petabyte) without disrupting operations.

---

### Databases

- [Google Cloud Database Options](https://cloud.google.com/blog/topics/developers-practitioners/your-google-cloud-database-options-explained)
- **Relational**
    - **Cloud SQL**
        - Managed MySQL, PostgreSQL, and SQL Server.
        - Suitable for general-purpose SQL databases.
        - Point-in-time recovery (PITR) uses binary logs.
    - **Cloud Spanner**
        - Cloud-native with large scale, consistency, and horizontal scaling.
        - Suitable for RDBMS+ scale, high availability (HA), and hybrid transactional/analytical processing (HTAP).
        - Avoid using incremental keys for optimal performance: Using sequential or incremental primary keys can lead to hotspots. It is recommended to use a more random distribution for primary keys to ensure balanced load distribution.
    - **Bare Metal**
        - Lift and shift Oracle workloads to Google Cloud.
- **Non-Relational (NoSQL)**
    - **Firestore**
        - Serverless, NoSQL document database, backend-as-a-service.
        - Suitable for large-scale, complex hierarchical data.
    - **Cloud BigTable**
        - NoSQL wide-column store for large-scale, low-latency workloads.
        - Suitable for heavy read/write events.
- **In-Memory**
    - **Memory Store**
        - Fully managed Redis and Memcached for sub-millisecond data access.
        - Suitable for in-memory and key-value store.

---

### Virtual Private Cloud (VPC)

- [Shared VPC](https://cloud.google.com/vpc/docs/shared-vpc)
    - Allows an organization to connect resources from multiple projects to a common VPC network, enabling secure and efficient internal communication using internal IPs.
- [VPC Network Peering](https://cloud.google.com/vpc/docs/vpc-peering)
    - Enables connectivity between two VPC networks, even if they are in different projects or organizations.
- [Load Balancers](https://cloud.google.com/load-balancing/docs/choosing-load-balancer)
    - Distributes user traffic across multiple instances of your applications, reducing the risk of performance issues.
- **Cloud VPN vs. Cloud Interconnect**
    - **Cloud Interconnect**
        - Provides low-latency and high availability for data transfer between on-premises and VPC networks.
        - **Dedicated Interconnect:** Direct physical connection between your on-premises network and Google's network.
        - **Partner Interconnect:** Connectivity through a supported service provider.
    - **Cloud VPN**
        - Sets up IPSec VPN tunnels between your networks if low-latency and high availability are not required.
        - Requires only a VPN device in your on-premises network.

---

### Cloud DNS

- **Features**
    - Managed DNS service that allows you to publish your domain name to the global DNS.
    - Supports creating and managing DNS zones and records.
    - Provides low-latency, high-availability DNS serving from Google’s worldwide network of Anycast name servers.
- **DNS Records**
    - **A Records**
        - Maps a domain name to an IPv4 address.
        - Used to point your domain to the IP address of your web server or hosting.
    - **CNAME Records**
        - Maps a domain name to another domain name (canonical name).
        - Often used to alias a subdomain (`www`, `home`, etc.) to another domain or to point to the domain of another service provider (e.g., GitHub Pages, AWS S3).

---

### Cloud Logging

- **Features**
    - Write custom logs from any source into Cloud Logging using public write APIs.
    - Integrates with Cloud Monitoring to set alerts on log events and logs-based metrics.
    - Export data in real-time to BigQuery for advanced analytics and SQL-like query tasks.
    - Use Error Reporting to automatically analyze logs for exceptions and aggregate them into meaningful error groups.
- **Cloud Audit Logs**
    - **Admin Activity Logs**
        - Log entries for API calls or administrative actions that modify configuration or metadata of resources.
        - Viewable with IAM roles *logging/logs.viewer* or *project/viewer*.
        - Always written and cannot be disabled.
    - **Data Access Logs**
        - Log entries for API calls that read configuration or metadata of resources.
        - Viewable with IAM roles *logging/private.logs.viewer* or *project/owner*.
        - Must be explicitly enabled; disabled by default.
    - **System Event Logs**
        - Log entries for administrative actions taken by Google Cloud.
        - Always written and cannot be disabled.
    - **Exporting Audit Logs**
        - Export log entries to Cloud Storage, BigQuery, or Pub/Sub.
        - Create a logs sink and specify the audit log types to export.
        - For exporting log entries for an organization, folder, or billing account, review aggregated sinks.

---

### Cloud Monitoring

- **Workspaces**
    - Manage monitoring data for a single Google Cloud project or multiple Google Cloud projects and AWS accounts.
    - A Google Cloud project or an AWS account can only be associated with one Workspace at a time.
    - Required IAM roles for creating a Workspace:
        - Monitoring Editor
        - Monitoring Admin
        - Project Owner
- **Cloud Monitoring Agent**
    - A `collectd`-based daemon that collects application and system metrics from virtual machine instances.
    - Collects disk, network, CPU, and process metrics by default.
    - Can be configured to monitor third-party applications.

---

### Cloud IAM

- **Features**
    - Authorize specific actions on resources to maintain full control and visibility of Google Cloud services.
    - Permissions are represented in the form *service.resource.verb*.
- **Roles**
    - A role contains a set of permissions that allow specific actions on Google Cloud resources.
    - Users are granted roles, not direct permissions.
    - Types of roles:
        - **Basic Roles:** Owner, Editor, Viewer.
        - **Predefined Roles:** Granular access for specific services, managed by Google Cloud.
        - **Custom Roles:** User-defined list of permissions for granular access.
- **Service Accounts**
    - Used by applications or virtual machine instances, not people.
    - Applications use service accounts to make authorized API calls.
    - Service accounts have associated public/private RSA key pairs for authentication.
    - Types of service accounts:
        - **User-managed Service Accounts**
        - **Default Service Accounts**
            - Created by Google when using Google Cloud services.
            - A service account is also a resource with IAM policies attached.
- **Best Practices**
    - Enforce least privilege at all times.
    - Mirror your Google Cloud resource hierarchy structure to your organization structure.
    - Set policies at the organization level and project level rather than the resource level.
    - Manage members in Google groups for easier policy updates.
    - Rotate service account keys using the IAM service account API.
    - Use user-managed service accounts for production workloads instead of default service accounts.

---

### Cloud Billing

- **Cloud Billing Account**
    - Access control established by IAM roles.
- **Google Payments Profile**
    - Stores information about who is responsible for the profile.
    - Serves as a document center for viewing invoices and payment history.
- **Cloud Billing Reports**
    - View Google Cloud usage costs and analyze trends.
    - Forecast future costs up to 12 months in advance.
- **Cloud Billing Budgets**
    - Define the scope of the budget to apply to:
        - Entire Cloud Billing account.
        - One or more projects.
        - One or more products.
        - Other applicable budget filters.
    - Specify the budget amount based on requirements or previous month’s spend.
    - Set up email alerts for budget notifications:
        - Role-based option for billing admins and users.
        - Use Cloud Monitoring to notify other organization members.
        - Use Pub/Sub for programmatic notification.
- **Overview of Cloud Billing Roles in IAM**
    - **Billing Account Creator (roles/billing.creator)**
        - Create new self-service billing accounts.
        - Assigned at the organization level.
        - Required for initial billing setup or creating additional billings.
    - **Billing Account Administrator (roles/billing.admin)**
        - Manage billing accounts (excluding creation).
        - Assigned at the organization level or billing account.
        - Manage payment instruments, configure billing exports, view cost information, link/unlink projects, and manage user roles on the billing account.
    - **Billing Account User (roles/billing.user)**
        - Link projects to billing accounts.
        - Assigned at the organization level or billing account.
        - Restricted permissions, typically combined with Project Creator role.
    - **Billing Account Viewer**
        - View billing account cost information and transactions.
        - Assigned at the organization level or billing account.
        - Usually granted to finance teams for spend information access.
    - **Project Billing Manager (roles/billing.projectManager)**
        - Link/unlink projects to/from a billing account.
        - Assigned at the organization level or billing account.
        - Allows project attachment to billing accounts without resource access.