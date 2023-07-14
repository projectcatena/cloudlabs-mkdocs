# Overview

CloudLabs utilizes the [GCP Java Client Library](https://cloud.google.com/java/docs/reference) to interface with GCP's API and execute operations.

To get started with development using the GCP's API, visit the [official GCP guide](https://cloud.google.com/apis/docs/getting-started).

## Authentication

Authentication for development purposes is fairly straightforward, as one only needs to setup the Application Default Credentials (ADC) locally through
the execution of a few simply commands using the `gcloud` command line utility.

1. [Install](https://cloud.google.com/sdk/docs/install) and initialize the gcloud CLI
```bash
gcloud init
```
2. Create your credential file
```bash
gcloud auth application-default login
```

Revoke authentication when not needed:
```bash
gcloud auth application-default revoke
```

After which, the CloudLabs server will be able to authenticate and communicate with GCP's API, if the client library is used. However, a Bearer authentication token will be required for manual requests, including the use of the `curl` utility.
