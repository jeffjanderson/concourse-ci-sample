**Concourse CI Setup**

This repository contains configuration files for setting up and running Concourse CI pipelines locally using Docker Compose.

**Contents**

-   docker-compose.yaml - Docker Compose configuration for running Concourse CI
-   hello-pipeline.yml - Simple "Hello World" starter pipeline
-   advanced-pipeline.yml - More complex pipeline demonstrating resources, multiple jobs, and dependencies

**Getting Started**

**Prerequisites**

-   Docker and Docker Compose
-   Concourse fly CLI tool

**Setting Up Concourse**

1.  Start the Concourse server using Docker Compose:

bash

docker-compose up -d

1.  Access the Concourse web interface at <http://localhost:8080>

-   Default login: username admin, password admin

3.  Target your local Concourse instance with the fly CLI:

bash

fly -t main login -c http://localhost:8080 -u admin -p admin

**Deploying Pipelines**

**Hello World Pipeline**

Deploy the simple hello-world pipeline:

bash

fly -t main set-pipeline -p hello-world -c hello-pipeline.yml

fly -t main unpause-pipeline -p hello-world

**Advanced Pipeline**

Deploy the more complex pipeline with multiple jobs:

bash

fly -t main set-pipeline -p advanced-pipeline -c advanced-pipeline.yml

fly -t main unpause-pipeline -p advanced-pipeline

**Useful Commands**

-   Trigger a job manually:

bash

fly -t main trigger-job -j pipeline-name/job-name

-   Watch job output:

bash

fly -t main watch -j pipeline-name/job-name

-   Destroy a pipeline:

bash

fly -t main destroy-pipeline -p pipeline-name

-   Stop and remove Concourse containers:

bash

docker-compose down

**Resources**

-   [Concourse CI Documentation](https://concourse-ci.org/docs.html)
-   [Fly CLI Documentation](https://concourse-ci.org/fly.html)
