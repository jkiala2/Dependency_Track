# Prerequisites for Installing Dependency Track

Before installing Dependency Track, it's important to ensure that your environment meets certain prerequisites for optimal performance.

## Hardware Requirements

### API Server:
- **Memory**: Minimum 4.5 GB of RAM (16 GB recommended)
- **CPU**: 2 CPU cores (4 cores recommended)

### Front-end:
- **Memory**: Minimum 512 MB of RAM (1 GB recommended)
- **CPU**: 1 CPU core (2 cores recommended)

## Software Requirements
You must have a recent version of Docker installed on your system. No other dependencies are required to use Docker and deploy Dependency Track.

For more information, see the [Docker Installation page](https://docs.docker.com/get-docker/).

## Installing Dependency Track

The installation of Dependency Track is relatively simple and can be customized according to your infrastructure needs. You have several methods available for deploying the tool, whether for a test or production environment.

**Warning**  
When installing Dependency Track via Docker, after the initial launch, the system will perform a vulnerability data mirroring process. This process may take between 10 and 30 minutes, or more, depending on the connection and available resources. It’s important not to interrupt this step. You can monitor progress by checking the `dependency-track.log` file or the Docker container console.

### Installation with Docker

For this demonstration, we will use the Docker Compose method to set up Dependency Track. This allows you to easily run the application on a remote machine by modifying certain settings in the Docker configuration file.

Here’s an example of a `docker-compose.yml` file you can use. It contains two services: the API server and the frontend. You’ll need to modify the IP or domain of the remote machine so the interface is accessible via a public URL.

**Modification for a remote machine**: In the file above, replace `<yourIP>` with the public IP address or domain name of your remote machine. This allows the frontend to access the API on that machine. This will enable you to monitor logs and ensure the initial vulnerability mirroring process is complete before using the user interface.

Once the installation is finished, you can access Dependency Track through your browser by visiting the configured URL (for example, `http:yourIP:8080`).

### Default Login
The first time you log in, use the default credentials:
- **Username**: admin
- **Password**: admin

After this initial login, you’ll be prompted to change your password for securing the administration of your Dependency Track instance.

## Performing the First SBOM Analysis

### Creating a Team
To allow the sending of SBOMs and creating projects via the API, you need to create a team, assign the appropriate permissions, and generate an API key.

1. Go to **Administration > Teams** and click **Add Team**.
2. Name the team (e.g., “Developers”).
3. Assign the permissions `BOM_UPLOAD` (to send SBOMs) and `PROJECT_CREATION_UPLOAD` (to create projects via the API).
4. Add a new key and copy it.

### Generating the SBOM File with Trivy
To generate an SBOM file in CycloneDX format, you can use the Trivy tool. Here’s an example command to analyze a Docker image and generate an SBOM file for the PostgreSQL 16 image:

- trivy image --format cyclonedx --output result.json postgres:16-bullseye

This command creates a result.json file containing the dependencies and vulnerabilities information of the Docker image.

Sending the SBOM to Dependency Track

Once the SBOM file is generated, you can send it to Dependency Track using an HTTP POST request with the API. Here’s an example of a curl command to send the file:

curl -X "POST" "http://<Remote_Machine_IP>:8081/api/v1/bom" \

-H "Content-Type: multipart/form-data" \

-H "X-Api-Key: odt_ePcRsAdQ2FZukqRS8ucJOF4zejdxWuqF" \

-F "autoCreate=true" \

-F "projectName=test" \

-F "projectVersion=0.1" \

-F "bom=@result.json"

This command:

Sends the SBOM file (result.json) to the Dependency Track server.

If the project doesn't already exist, it will be created automatically using the autoCreate=true parameter.

The project will be named test and versioned as 0.1.

Using this method, you can easily integrate dependency analysis into your workflows and projects.

Analyzing the Results and Key Information to Extract

The analysis results in Dependency Track rely on several indicators that help you track and prioritize actions for your dependencies.

## Vulnerabilities by Project
For each project, Dependency Track provides a detailed list of vulnerabilities in the dependencies. Each vulnerability is associated with a Risk Score, which combines the CVSS score and the EPSS (Exploit Prediction Scoring System). This helps you prioritize the most critical vulnerabilities and identify those likely to be exploited.

## CVSS Score
The CVSS score allows you to measure the severity of a vulnerability on a scale from 0 to 10. High-scoring vulnerabilities require immediate attention, while lower-scoring ones can be addressed later.

## Exploit Prediction
A two-dimensional table indicates the likelihood that a vulnerability will be exploited based on its EPSS score. This indicator is essential for assessing the risk of an attack.

## Trends and Alerts
You can track the evolution of vulnerabilities over time and configure alerts, for example via email or Teams, to be notified when a new critical vulnerability is detected.

These indicators provide an overview of the security of your projects and help you proactively manage and anticipate risks.

## Best Practices for Using Dependency Track
To use Dependency Track effectively and maximize the security of your projects while optimizing tool performance, follow these best practices:

## Update Regularly: Ensure that Dependency Track and its dependencies are always up-to-date to benefit from the latest features and security fixes.
Prioritize Vulnerabilities: Regularly prioritize the most critical vulnerabilities and address them promptly.
