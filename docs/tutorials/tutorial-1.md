# Benchmarking Multiple Blockchain Platforms with Hyperledger Caliper

## Target Audience
Developers working with multiple blockchain platforms who want to compare their performance characteristics.

## Learning Objectives
- Understand the considerations and challenges involved in benchmarking different blockchain platforms.
- Learn how to configure Caliper to work with various blockchain platforms and their specific network adapters.
- Gain insights into the relative performance strengths and weaknesses of different platforms under various workloads.

## Prerequisites
- Node.js and npm (or yarn) installed on your system.
- Basic understanding of Hyperledger Caliper and YAML configuration files.
- Running instances of multiple blockchain platforms (e.g., Hyperledger Fabric, Ethereum) for testing purposes.

## Steps

### Project Setup

Create a new directory for your project:
```bash
mkdir caliper-multi-platform && cd caliper-multi-platform
```

### Initialize a new project (optional):
```bash
npm init -y
```
### Install Caliper CLI (if not already installed):
```bash
npm install -g @hyperledger/caliper-cli
```

### Define the Benchmark Scenario
Create a new file named common_scenario.js within your project directory. This file will contain the JavaScript code for your benchmark scenario that can be executed on different platforms.

Here's an example scenario that performs a simple asset transfer on the blockchain:

```bash
const { CaliperClient } = require('@hyperledger/caliper-core');

module.exports = async (workerIndex, totalWorkers, runConfig) => {
    const client = new CaliperClient();

    // Replace with your actual asset transfer function call based on the platform
    await client.invoke('transferAsset', { arguments: ['Alice', 'Bob', 100] });

    client.close();
};
```

This scenario demonstrates invoking a generic transferAsset function. You'll need to replace this with the appropriate function call specific to each platform you're benchmarking.

### Configure Benchmarks for Each Platform
Create separate YAML files for each platform benchmark (e.g., fabric-benchmark.yaml, ethereum-benchmark.yaml).

Here's an example configuration for Hyperledger Fabric:
```bash
name: fabric-asset-transfer

## Client configuration (adjust as needed)
client:
    type: basic
    number: 10  # Number of simulated clients

## Scenario configuration
scenario:
    type: caliper-worker
    worker: ./common_scenario.js  # Path to your common scenario file

## Network configuration (replace with your Fabric details)
type: fabric
...  # Fabric-specific connection information and chaincode details

## Define workload parameters (optional)
## Refer to Caliper documentation for available options
## https://hyperledger.github.io/caliper/docs/configuration.html
# workload:
#   ...
```

Repeat this configuration for each platform you want to benchmark, replacing the network configuration details with the specifics of each platform's adapter.

### Running Benchmarks
Navigate to your project directory in the terminal.

(Optional) Bind the Caliper CLI to the platform you're benchmarking (if necessary):
```bash
caliper bind --platform <platform-name> 
```

### Run the benchmark for each platform using its respective YAML configuration file:
```bash
caliper benchmark run --name fabric-asset-transfer
```

Repeat the caliper benchmark run command for each platform configuration file you created.

### Analyze the Results
Caliper will generate separate report files (typically HTML) for each benchmark run.

Analyze the reports to compare performance metrics (throughput, latency) across different platforms under the same workload scenario. This will help identify strengths and weaknesses of each platform for your specific use case.