# Reading metrics from Linux sidecars

Each Cyral service that is deployed by the installer generates various
metrics in Prometheus format. Details regarding these metrics can be
found in the [metrics specification](../../sidecars/monitoring/metrics.mdx).

Each of the deployed services exposes a HTTP service that provides
metrics on the `/metrics` path.

Below is an example of querying the metrics service associated with
the dispatcher service:

```
# curl localhost:9015/metrics

# HELP cyral_bypass_wire_count The total count of connection bypassed to repository directly grouped by bypass_reason.

# TYPE cyral_bypass_wire_count counter

cyral_bypass_wire_count{asg_instance="i-abc123",bypass_reason="dial_failed",repo_id="repo123",repo_name="Oracle-DB-1",repo_type="oracle",service="dispatcher",service_type="",sidecar_id="sidecar1234",sidecar_name="aws-cft",sidecar_version="unknown",start_timestamp="1643723971633447036"} 0

cyral_bypass_wire_count{asg_instance="i-abc123",bypass_reason="dial_failed",repo_id="repo456",repo_name="sql2019-srss",repo_type="sqlserver",service="dispatcher",service_type="",sidecar_id="sidecar1234",sidecar_name="aws-cft",sidecar_version="unknown",start_timestamp="1643723971633447036"} 0

cyral_bypass_wire_count{asg_instance="i-abc123",bypass_reason="dial_failed",repo_id="repo789",repo_name="sql2016-srss",repo_type="sqlserver",service="dispatcher",service_type="",sidecar_id="sidecar1234",sidecar_name="aws-cft",sidecar_version="unknown",start_timestamp="1643723971633447036"} 0

cyral_bypass_wire_count{asg_instance="i-abc123",bypass_reason="dial_failed",repo_id="repo101112",repo_name="Snowflake",repo_type="snowflake",service="dispatcher",service_type="",sidecar_id="sidecar1234",sidecar_name="aws-cft",sidecar_version="unknown",start_timestamp="1643723971633447036"} 0
```

Similar metrics are available for each service. The below table
provides a subset of services that might be present and their
corresponding metrics port:

| Cyral Service Port | Metrics Port |
| -- | -- |
| cyral-dispatcher | TCP/9015 |
| cyral-oracle-wire | TCP/9032 |
| cyral-sqlserver-wire | TCP/9022 |
| cyral-sidecar-exporter | TCP/9023 |
| cyral-dremio-wire | TCP/9019 |
| cyral-mysql-wire | TCP/9018 |
| cyral-pg-wire | TCP/9016 |
| cyral-s3-wire | TCP/9024 |
| cyral-mongodb-wire | TCP/9017 |
| cyral-rest-wire | TCP/9036 |
| cyral-dynamodb-wire | TCP/9038 |
