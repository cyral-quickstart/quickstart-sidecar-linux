# Configure the Linux sidecar for SSO

Some environments might require the use of environment variables to
store native credentials. Additional details regarding setting up
native credentials for a repository can be found here.

When using environment variables to store native credentials on the
local server, you will need to supply the variable(s) to the Cyral
Authenticator service (cyral-authenticator). Perform the following
steps to make sure the cyral-authenticator is configured to use these
credentials.

1. SSH to the sidecar.
1. Edit the environment variables for the Cyral authenticator server.
   ```
   sudo vi /etc/default/cyral-authenticator
   ```
1. Add a new line that contains the secret credentials. In the below
   example, the new line containing the credentials is in blue text.
   The name of the environment variable should match the name
   configured in the Cyral control plane.
   ```
   CYRAL_AUTHENTICATOR_CONTROLPLANE_HOST=
   CYRAL_AUTHENTICATOR_CONTROLPLANE_PORT=
   CYRAL_AUTHENTICATOR_WRAPPER_NAME=
   CYRAL_DBSECRETS_REPO_ADMIN='tk"username":"admin", "password": "Some-S3cure_Pa$$word!"tkend'
   ```
1. Save the file.
1. Restart the *cyral-authenticator* to load the new changes.
   ```
   sudo systemctl restart cyral-authenticator
   ```
