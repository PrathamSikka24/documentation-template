# Modular Architecture
Hyperledger Caliper leverages a modular architecture for enhanced flexibility and customization. This architecture separates core functionalities into independent modules:

  * **Network Modules:** These modules handle interacting with the target blockchain network. Caliper provides network modules for various platforms like Hyperledger Fabric and Ethereum.
  * **Client Modules:** These modules simulate blockchain clients that submit transactions and queries to the network. Caliper offers different client modules depending on the chosen network. 
  * **Benchmark Modules:** These modules define the specific workflows and scenarios used for performance evaluation. Users can create custom benchmark modules or utilize pre-built options provided by Caliper.

This modular design offers several advantages:

  * **Platform Agnostic:** By having separate network modules, Caliper can be easily integrated with different blockchain platforms as long as a compatible network module exists.
  * **Customizable Workloads:** The modular design allows users to define custom benchmark modules tailored to their specific needs. They can modify existing scenarios or create entirely new workflows to evaluate performance under various conditions.


