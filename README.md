# UDM
# Unified Data Management (UDM)
//===============================================================
Unified Data Management (UDM) is a crucial component within the 5G Core Network (5GC) architecture, as defined by the 3GPP specifications for 5G networks.

UDM plays a central role in managing subscription-related data and providing authentication and authorization services for users within a 5G network. It serves as a repository for subscriber profiles, subscription policies, and authentication credentials. Additionally, UDM interfaces with other network functions to facilitate session management and mobility management in 5G networks.

In simpler terms, UDM is responsible for maintaining subscriber data integrity and enabling secure and efficient communication services in 5G networks. It ensures that users are authenticated and authorized to access network services, while also enabling seamless handovers and mobility across the network.

//================================================================>

# Pipeline Overview
This Jenkins pipeline automates the build, testing, and deployment process for a Dockerized application using Jenkins, Docker, Helm, and AWS EKS.

## Pipeline Stages:
Verify Branch:

Displays the current Git branch being built.
### Login to Dockerhub:

Logs in to Dockerhub using stored credentials.
### Pulling base image from Dockerhub:

Pulls the latest base image from Dockerhub (abodiaa/udm-base:latest).
### Docker Build:

Lists Docker images.
Builds a Docker image tagged as abodiaa/udm:latest.
Lists Docker images again.
### Scan Image for Common Vulnerabilities and Exposures:

Scans the Docker image for common vulnerabilities and exposures using Trivy.
Generates a JSON report of vulnerabilities.
### Pushing to Dockerhub:

Pushes the built Docker image (abodiaa/udm:latest) to Dockerhub.
### Build and Package Helm Chart:

Packages the Helm chart located in ./helm/.
### Configure Kubernetes Context:

Configures the Kubernetes context for AWS EKS cluster 5G-Core-Net.
### Deploy Helm Chart on EKS:

Upgrades or installs the Helm chart named udm onto the EKS cluster.
## Post-build Actions:
### Always:
Archives the Trivy vulnerability report.
Removes Docker images (abodiaa/udm:latest and abodiaa/udm-base:latest).

