# Common GCP Roles

### Basic Roles
1. **Owner (`roles/owner`)**
    - Full access to all resources.
    - Can manage roles and permissions.

2. **Editor (`roles/editor`)**
    - Edit access to all resources.
    - Can create and update resources but cannot manage roles and permissions.

3. **Viewer (`roles/viewer`)**
    - Read-only access to all resources.

### Predefined Roles
1. **Compute Admin (`roles/compute.admin`)**
    - Full control over Compute Engine resources.

2. **Storage Admin (`roles/storage.admin`)**
    - Full control over Cloud Storage resources.

3. **Storage Object Viewer (`roles/storage.objectViewer`)**
    - Read-only access to Cloud Storage objects.

4. **BigQuery Admin (`roles/bigquery.admin`)**
    - Full control over BigQuery resources.

5. **BigQuery Data Viewer (`roles/bigquery.dataViewer`)**
    - Read-only access to BigQuery data.

6. **BigQuery Data Editor (`roles/bigquery.dataEditor`)**
    - Read and write access to BigQuery data.

7. **Pub/Sub Admin (`roles/pubsub.admin`)**
    - Full control over Pub/Sub resources.

8. **Pub/Sub Editor (`roles/pubsub.editor`)**
    - Can create and update Pub/Sub resources.

9. **Pub/Sub Viewer (`roles/pubsub.viewer`)**
    - Read-only access to Pub/Sub resources.

10. **Kubernetes Engine Admin (`roles/container.admin`)**
    - Full control over Kubernetes Engine resources.

11. **Logging Admin (`roles/logging.admin`)**
    - Full control over Cloud Logging resources.

12. **Monitoring Admin (`roles/monitoring.admin`)**
    - Full control over Cloud Monitoring resources.

### Naming Conventions for Roles

- **Basic Roles:** These roles have simple, short names like `owner`, `editor`, and `viewer`.
- **Predefined Roles:** These roles follow a more structured naming convention:
    - Prefix with the service name or function, such as `compute`, `storage`, `bigquery`, `pubsub`, `container`, `logging`, `monitoring`.
    - Use a descriptive suffix indicating the level of access or control, such as `admin`, `editor`, `viewer`.
    - Combined, they form names like `compute.admin`, `storage.objectViewer`, `bigquery.dataEditor`, etc.