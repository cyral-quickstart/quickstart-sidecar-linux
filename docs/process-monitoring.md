# Perform process monitoring on Linux sidecars

In addition to metrics monitoring, you may also leverage a
local service that checks for the existence of expected processes. In
order to help you determine which processes to monitor, the
below table defines the various services that are installed by this
installer. The table provides a brief description of each service
along with whether it is critical to the proper operation of the
sidecar:

| Cyral Service Name | Critical | Description |
| -- | -- | -- |
| cyral-forward-proxy | Yes<sup>1</sup> | Used to establish connectivity from the sidecar to the Cyral control plane. |
| cyral-dispatcher | Yes | Layer 4 service that handles connections through the sidecar for clients connecting to the database. |
| cyral-certificate-manager | Yes | This service renders certificates to cyral-dispatcher. |
| cyral-alerter | No | This service catalogs and sends notifications for alert-worthy events. |
| cyral-mysql-wire | Yes | Layer 7 service that provides inspection of MySQL specific queries and commands. |
| cyral-oracle-wire | Yes<sup>2</sup> | Layer 7 service that provides inspection of Oracle specific queries and commands. |
| cyral-authenticator | No<sup>3</sup> | This service talks to identity and MFA providers on behalf of other Cyral services. |
| cyral-pg-wire | Yes<sup>2</sup> | Layer 7 service that provides inspection of Postgres specific queries and commands. |
| cyral-sqlserver-wire | Yes<sup>2</sup> | Layer 7 service that provides inspection of SQL Server specific queries and commands. |
| cyral-sidecar-exporter | No | Exports sidecar's information, like its endpoint, cloud, region, sidecar version, etc… |
| cyral-push-client | No | Service that sends metrics and other information to the Cyral control plane. |
| cyral-dremio-wire | Yes<sup>2</sup> | Layer 7 service that provides inspection of Dremio specific queries and commands. |
| cyral-s3-wire | Yes<sup>2</sup> | Layer 7 service that provides inspection of S3 specific queries and commands. |
| cyral-mongodb-wire | Yes<sup>2</sup> | Layer 7 service that provides inspection of Mongo DB specific queries and commands. |
| cyral-rest-wire | Yes<sup>2</sup> | Layer 7 service that provides inspection of REST API specific queries and commands. |
| cyral-dynamodb-wire | Yes<sup>2</sup> | Layer 7 service that provides inspection of Dynamo DB specific queries and commands. |

Footnotes:

1. This service is not critical for the proper operation of the
   sidecar and its ability to support connections to databases. This
   service is required for all other components to communicate with
   the Cyral control plane for configuration updates.
   
2. This service is critical for the proper logging and policy
   enforcement on the sidecar if the respective repo is added to the
   sidecar.

3. If you integrate with an identity provider such as Okta,
   Azure, GSuite, or similar, for authenticating users through the
   sidecar, then this service would become critical for this purpose.
