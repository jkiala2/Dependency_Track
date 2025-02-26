# Getting Started with Dependency Track
*Last updated: 20/10/2024*

![dependency-track logo](./images/logo.png)

## Introduction

I will introduce you to Dependency Track, an open-source tool designed to help development and security teams manage vulnerabilities in software dependencies.

## Why use Dependency Track?

Securing the software supply chain has become a critical issue with the rise of cyberattacks targeting software dependencies and third-party components. In a context where many companies use open-source libraries and tools, it is essential to ensure that every component used in their projects is secure and free from known vulnerabilities.

Another important aspect of securing the supply chain is the adoption of the Zero Trust principle. This concept is based on the idea that no element of the system should automatically be considered secure, even within your network. When applied to dependency management, this means that each component must be continuously verified, regardless of its origin or apparent reliability.

It is therefore crucial to maintain continuous analysis of your dependencies over time, not just at the time of initial integration. Vulnerabilities in open-source components can be discovered long after they have been integrated into your projects. This is where **Dependency Track** comes in, providing continuous monitoring of the integrity of your dependencies.

## Key Concepts to Understand

To fully understand how Dependency Track works, it’s important to grasp some fundamental concepts that are central to the tool.

- **SBOM (Software Bill of Materials)**: This term refers to the complete list of dependencies and components used in a project. It is the central element of Dependency Track, as it is based on this list that the tool identifies security flaws.
  
- **Vulnerabilities**: Dependency Track continuously scans your projects for security flaws, using public databases like the National Vulnerability Database (NVD). Each vulnerability found is linked to a specific dependency, allowing you to know which component needs to be updated or fixed.

- **CVSS Scoring (Common Vulnerability Scoring System)**: Each identified vulnerability is assigned a score using the CVSS method. This score measures the severity of the vulnerability, with a scale from 0 to 10. The higher the score, the more critical the vulnerability. This helps you prioritize actions to address the most severe issues first.

- **Components**: This term refers to each library, framework, or other module used in your project. Dependency Track identifies each component by its version and compares the information with vulnerability databases to detect security flaws.

## Key Features of Dependency Track

Dependency Track offers a range of powerful features to help you manage the security of your dependencies throughout the lifecycle of your projects.

- **Dependency Analysis**: Dependency Track automatically scans the dependencies of your projects and generates a comprehensive report on their security status.

- **Vulnerability Detection**: By connecting to public sources such as the National Vulnerability Database (NVD), it detects vulnerabilities in real-time that are associated with your dependencies.

- **Project Management**: You can create and track multiple projects simultaneously. Each project corresponds to a set of components or dependencies, making it easier to manage and prioritize vulnerabilities for each application or module.

- **Update Tracking**: The tool alerts you as soon as a new version of a component is available, especially if it addresses a known vulnerability. This ensures that you always use secure versions of libraries in your projects.

- **Integration with DevOps Tools**: Dependency Track easily integrates with tools like Gitlab CI to automate dependency analysis in your CI/CD pipelines. This allows you to analyze each new version of your applications before deploying them to production.

## Prerequisites for Installing Dependency Track

Before installing Dependency Track, it's important to ensure that your environment meets certain prerequisites to guarantee optimal performance.






