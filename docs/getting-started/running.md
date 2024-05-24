# Running a Hyperledger Caliper Benchmark: A Step-by-Step Guide

Once you've successfully installed Hyperledger Caliper (refer to the installation guide for details), you're ready to leverage its capabilities to benchmark a blockchain platform. Here's a breakdown of the steps involved in running a Caliper project:

## Prerequisites

- **Installed Caliper**: Ensure you have Caliper installed using either the local NPM method or the Docker image approach.
- **Blockchain Network**: You'll need a running blockchain network to target your benchmarks. Specific configuration steps might vary depending on the chosen platform (e.g., Hyperledger Fabric, Ethereum).

## Project Setup

- **Workspace Directory**: Create a dedicated directory for your Caliper project. This will house your configuration files, benchmark definitions, and test artifacts.

- **Configuration Files**: Caliper utilizes YAML files to define various aspects of the benchmark run. These files typically include:

  - `network.yaml`: This file specifies the target blockchain network configuration, including connection details and network artifacts (e.g., channel names, chaincode paths for Fabric).
  - `benchmarks.yaml`: This file defines the benchmark scenarios you want to execute. It includes details like workload types, configurations, and the number of clients to simulate.

### Example Configuration (`network.yaml`):

```yaml
type: fabric
```  