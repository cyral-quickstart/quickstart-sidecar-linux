# Configuring certificates for Linux sidecars

_Added in sidecar version v4.7_

To provide a custom certificate to the sidecar, you can use the following
environment variables:

```shell
CYRAL_SIDECAR_TLS_CERT=        # x509 TLS certificate
CYRAL_SIDECAR_TLS_PRIVATE_KEY= # private key corresponding to TLS cert
CYRAL_SIDECAR_CA_CERT=         # CA Cert for TLS
CYRAL_SIDECAR_CERT_DIRECTORY=  # Directory for cert storage, defaults to /etc/cyral/cyral-certificate-manager/bundles
```

Export the environment variables of your choice before running the script.

Note that the contents of the environment variables **must be encoded in
base64**. For instance, if your TLS certificate is:

```
-----BEGIN CERTIFICATE-----
aGVsbG8gd29ybGQK
-----END CERTIFICATE-----
```

You would provide the following input to `CYRAL_SIDECAR_TLS_CERT`:

```
CYRAL_SIDECAR_TLS_CERT=LS0tLS1CRUdJTiBDRVJUSUZJQ0FURS0tLS0tCmFHVnNiRzhnZDI5eWJHUUsKLS0tLS1FTkQgQ0VSVElGSUNBVEUtLS0tLQo=
```

To learn more about sidecar certificates, visit the official Cyral docs:
[Sidecar Certificates](https://cyral.com/docs/sidecars/deployment/certificates).
