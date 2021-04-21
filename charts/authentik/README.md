# authentik Helm Chart

| Name                              | Default                 | Description |
|-----------------------------------|-------------------------|-------------|
| image.name                        | beryju/authentik        | Image used to run the authentik server and worker |
| image.name_static                 | beryju/authentik-static | Image used to run the authentik static server (CSS and JS Files) |
| image.tag                         | 2021.4.3                | Image tag |
| image.pullPolicy                  | IfNotPresent            | Image Pull Policy used for all deployments |
| serverReplicas                    | 1                       | Replicas for the Server deployment |
| workerReplicas                    | 1                       | Replicas for the Worker deployment |
| kubernetesIntegration             | true                    | Enable/disable the Kubernetes integration for authentik. This will create a service account for authentik to create and update outposts in authentik |
| config.secretKey                  |                         | Secret key used to sign session cookies, generate with `pwgen 50 1` or `openssl rand -base64 36` for example. |
| config.errorReporting.enabled     | false                   | Enable/disable error reporting |
| config.errorReporting.environment | customer                | Environment sent with the error reporting |
| config.errorReporting.sendPii     | false                   | Whether to send Personally-identifiable data with the error reporting |
| config.logLevel                   | warning                 | Log level of authentik |
| config.email.host                 | localhost               | SMTP Host Emails are sent to |
| config.email.port                 | 25                      | SMTP Port Emails are sent to |
| config.email.username             |                         | SMTP Username |
| config.email.password             |                         | SMTP Password |
| config.email.use_tls              | false                   | Enable StartTLS |
| config.email.use_ssl              | false                   | Enable SSL |
| config.email.timeout              | 10                      | SMTP Timeout |
| config.email.from                 | authentik@localhost     | Email address authentik will send from, should have a correct @domain |
| pvc.mode                          | ReadWriteMany           | Mode that the PVCs are created in (uploads and GeoIP, if enabled) |
| pvc.uploadsSize                   | 5Gi                     | Size for the uploads PVC |
| pvc.uploadsStorageClass           | null                    | Storage class for the uploads PVC (default: use default storage class) |
| pvc.geoIpSize                     | 1Gi                     | Size for the GeoIP PVC |
| pvc.geoIpStorageClass             | null                    | Storage class for the GeoIP PVC (default: use default storage class) |
| geoip.enabled                     | false                   | Optionally enable GeoIP |
| geoip.accountId                   |                         | GeoIP MaxMind Account ID |
| geoip.licenseKey                  |                         | GeoIP MaxMind License key |
| geoip.image                       | maxmindinc/geoipupdate:latest  | GeoIP Updater image |
| backup.accessKey                  |                         | Optionally enable S3 Backup, Access Key |
| backup.secretKey                  |                         | Optionally enable S3 Backup, Secret Key |
| backup.bucket                     |                         | Optionally enable S3 Backup, Bucket |
| backup.region                     |                         | Optionally enable S3 Backup, Region |
| backup.host                       |                         | Optionally enable S3 Backup, to custom Endpoint like minio |
| ingress.annotations               | {}                      | Annotations for the ingress object |
| ingress.hosts                     | [authentik.k8s.local]   | Hosts which the ingress will match |
| ingress.tls                       | []                      | TLS Configuration, same as Ingress objects |
| install.postgresql                | true                    | Enables/disables the packaged PostgreSQL Chart
| install.redis                     | true                    | Enables/disables the packaged Redis Chart
| postgresql.postgresqlPassword     |                         | Password used for PostgreSQL, generated automatically.

For more info, see https://goauthentik.io/ and https://goauthentik.io/docs/installation/kubernetes/
