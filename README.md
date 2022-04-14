# MinIO package

MinIO(R) is an object storage server, compatible with Amazon S3 cloud storage service, mainly used for storing unstructured data (such as photos, videos, log files, etc.).

## MinIO parameters

|Parameter|Description|Type|Default|
|---------|-----------|----|-------|
|pullPolicy|image pull policy|string|IfNotPresent|
|auth.rootUser|MinIO root username|string|admin|
|auth.rootPassword|Password for MinIO root user|string|""|
|auth.existingSecret|Use existing secret for credentials details (auth.rootUser and auth.rootPassword will be ignored and picked up from this secret). The secret has to contain the keys root-user and root-password)|string|""|

## MinIO deployment/statefulset parameters

|Parameter|Description|Type|Default|
|---------|-----------|----|-------|
|containerPorts.api|MinIO® container port to open for MinIO® API|integer|9000|
|containerPorts.console|MinIO® container port to open for MinIO® Console|integer|9001|
|podSecurityContext.enabled|Enable pod Security Context|string|TRUE|
|containerSecurityContext.runAsUser|User ID for the container|integer|1001|
|containerSecurityContext.runAsNonRoot|Avoid running as root User|string|TRUE|
|livenessProbe.enabled|Enable livenessProbe|string|TRUE|
|livenessProbe.initialDelaySeconds|Initial delay seconds for livenessProbe|integer|5|
|livenessProbe.periodSeconds|Period seconds for livenessProbe|integer|5|
|livenessProbe.timeoutSeconds|Timeout seconds for livenessProbe|integer|5|
|livenessProbe.failureThreshold|Failure threshold for livenessProbe|integer|5|
|livenessProbe.successThreshold|Success threshold for livenessProbe|integer|1|
|readinessProbe.enabled|Enable readinessProbe|string|TRUE|
|readinessProbe.initialDelaySeconds|Initial delay seconds for readinessProbe|integer|5|
|readinessProbe.periodSeconds|Period seconds for readinessProbe|integer|5|
|readinessProbe.timeoutSeconds|Timeout seconds for readinessProbe|integer|1|
|readinessProbe.failureThreshold|Failure threshold for readinessProbe|integer|5|
|readinessProbe.successThreshold|Success threshold for readinessProbe|integer|1|
|startupProbe.enabled|Enable startupProbe|string|FALSE|
|startupProbe.initialDelaySeconds|Initial delay seconds for startupProbe|integer|0|
|startupProbe.periodSeconds|Period seconds for startupProbe|integer|10|
|startupProbe.timeoutSeconds|Timeout seconds for startupProbe|integer|5|
|startupProbe.failureThreshold|Failure threshold for startupProbe|integer|60|
|startupProbe.successThreshold|Success threshold for startupProbe|integer|1|
|initContainers|Add additional init containers to the MinIO® pods|string|[]|

##  Traffic exposure parameters

|Parameter|Description|Type|Default|
|---------|-----------|----|-------|
|service.type|MinIO® service type|string|LoadBalancer|
|service.ports.api|MinIO® API service port|integer|9000|
|service.ports.console|MinIO® Console service port|integer|9001|
|service.loadBalancerIP|loadBalancerIP if service type is LoadBalancer (optional, cloud specific)|string|""|
|ingress.enabled|Enable ingress controller resource|string|FALSE|
|ingress.hostname|Default host for the ingress resource|string|minio.local|
|ingress.path|The Path to MinIO®. You may need to set this to / in order to use this with ALB ingress controllers|string|/|
|ingress.pathType|Ingress path type|string|ImplementationSpecific|
|ingress.servicePort|Service port to be used|string|FALSE|
|apiIngress.hostname|Default host for the ingress resource|string|minio.local|
|apiIngress.path|The Path to MinIO®. You may need to set this to / in order to use this with ALB ingress controll|string|/|
|apiIngress.pathType|Ingress path type|string|ImplementationSpecific|
|apiIngress.servicePort|Service port to be used|string|minio-api|
|networkPolicy.enabled|Enable the default NetworkPolicy policy|string|FALSE|

##  Persistence parameters

|Parameter|Description|Type|Default|
|---------|-----------|----|-------|
|persistence.size|PVC Storage Request for MinIO® data volume|integer|8Gi|

##  RBAC parameters

|Parameter|Description|Type|Default|
|---------|-----------|----|-------|
|serviceAccount.automountServiceAccountToken|Enable/disable auto mounting of the service account token|string|TRUE|
