# Installing Hyperledger Caliper: A Step-by-Step Guide

This guide details two primary methods for installing Hyperledger Caliper:

## Methods of Installation

### 1. Local NPM Installation
Utilizing Node Package Manager (npm) for direct installation on your development machine.

### 2. Docker Image
Leveraging a pre-built Docker image containing Caliper and its dependencies for a streamlined process.

## Choosing the Right Method

- **Local NPM Installation**: Offers flexibility for customization and development but requires Node.js and npm setup.
- **Docker Image**: Provides a simpler and faster installation, especially for Docker users, but limitations for deep customization might exist.

## Local NPM Installation

### Prerequisites

- **Node.js and npm**: Ensure you have Node.js (version 10 or later) and npm (version 5.6 or later) installed. Verify their installation by running `node -v` and `npm -v` in your terminal. If not installed, download them from the [official Node.js website](https://nodejs.org/en).

### Steps

1. **Create a Project Directory**: Open your terminal and navigate to your desired workspace directory. Use the `mkdir` command to create a new directory for your project, for example:

    ```bash
    mkdir caliper-project && cd caliper-project
    ```

2. **Initialize Project (Optional)**: While not mandatory, initialize a project directory using `npm init`. This creates a `package.json` file for project metadata. You can either answer the prompts or use `npm init -y` for default settings.

3. **Install Caliper CLI**: Install the Caliper Command Line Interface (CLI) globally on your system using the following command:

    ```bash
    npm install -g @hyperledger/caliper-cli
    ```

#### Optional: Local Project Installation

For better organization, you can install Caliper locally within your project instead of a global installation.

- Run the following command in your project directory:

    ```bash
    npm install @hyperledger/caliper-cli
    ```

- Access the Caliper CLI within your project using `npx` like this:

    ```bash
    npx @hyperledger/caliper-cli
    ```

## Using Docker Image

### Prerequisites

- **Docker**: Ensure you have Docker installed and running on your system. You can find installation instructions on the [Docker website](https://docs.docker.com/engine/install/).

### Steps

1. **Pull the Caliper Docker Image**: Download the latest Caliper image from Docker Hub using the following command in your terminal:

    ```bash
    docker pull hyperledger/caliper
    ```

2. **Run Caliper Container (Interactive)**: This command starts a new Docker container from the Caliper image in interactive mode:

    ```bash
    docker run -it hyperledger/caliper
    ```

    This will launch a bash shell within the container, allowing you to interact with Caliper tools.

3. **Run Caliper Container (Background)**: To run the container in the background without a shell, use this command:

    ```bash
    docker run -d hyperledger/caliper
    ```

### Using Caliper within Container

Once the container is running, you can access Caliper commands within the container's shell. For example, to view the Caliper version, type:

```bash
caliper version
```