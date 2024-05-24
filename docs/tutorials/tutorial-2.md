# Building Custom Benchmarks with Hyperledger Caliper

## Target Audience
Developers with a basic understanding of Hyperledger Caliper and blockchain technology.

## Learning Objectives
- Understand advanced concepts like custom scenario development, workload parameter manipulation, and integrating Caliper with external tools.
- Learn how to tailor benchmarks to specific use cases and explore platform-specific optimizations.
- Gain insights into performance bottlenecks and identify areas for improvement in blockchain platforms.

## Prerequisites
- Node.js and npm (or yarn) installed on your system.
- Basic understanding of Hyperledger Caliper and YAML configuration files.
- A running blockchain network (e.g., Hyperledger Fabric) for testing purposes.

## Steps

### Setting Up the Project

Create a new directory for your project:
```bash
mkdir caliper-custom-benchmark && cd caliper-custom-benchmark
```

### Initialize a new project (optional):
```bash
npm init -y
```

### Install Caliper CLI (if not already installed):
```bash
npm install -g @hyperledger/caliper-cli
```
### Define the Custom Scenario

Create a new file named custom_scenario.js within your project directory. This file will contain the JavaScript code for your custom scenario.

Here's an example scenario that reads and writes data to a key-value store on the blockchain:
```bash 
const { CaliperClient } = require('@hyperledger/caliper-core');

module.exports = async (workerIndex, totalWorkers, runConfig) => {
    const client = new CaliperClient();

    // Replace with your actual key-value store name and data
    const key = 'my-key';
    const value = `Data from worker ${workerIndex}`;

    console.log(`Worker ${workerIndex}: Writing value '${value}' to key '${key}'`);
    await client.invoke('writeValue', { arguments: [key, value] });

    console.log(`Worker ${workerIndex}: Reading value for key '${key}'`);
    const response = await client.query('readValue', { arguments: [key] });
    console.log(`Worker ${workerIndex}: Read value: '${response.payload}'`);

    client.close();
};
```
This scenario demonstrates writing and reading data using Caliper's invoke and query methods. You can modify this example to implement your specific logic.

### Configure the Benchmark (benchmarks.yaml)
Create a new file named benchmarks.yaml in your project directory.

Here's an example configuration referencing your custom scenario:
```bash
name: my-custom-benchmark

## Client configuration (adjust as needed)
client:
    type: basic
    number: 5  # Number of simulated clients

## Scenario configuration
scenario:
    type: caliper-worker
    worker: ./custom_scenario.js  # Path to your custom scenario file

## Define workload parameters (optional)
## Refer to Caliper documentation for available options
## https://hyperledger.github.io/caliper/docs/configuration.html
# workload:
#   ...
```

This configuration defines a benchmark named my-custom-benchmark that utilizes five basic clients and executes the custom scenario defined in custom_scenario.js. You can adjust the client configuration and define workload parameters as needed.

### Configure the Network (network.yaml)
Create a new file named network.yaml in your project directory. Configure this file according to your specific blockchain platform (e.g., Hyperledger Fabric requires details like connection information and chaincode paths).

### Run the Benchmark
Navigate to your project directory in the terminal.

(Optional) Bind the Caliper CLI to your platform (if necessary):

```bash 
caliper bind --platform <platform-name> 
```
Run the benchmark:
```bash
caliper benchmark run --name my-custom-benchmark
```