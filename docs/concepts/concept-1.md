# Benchmarks and Scenarios

A core concept in Hyperledger Caliper is the use of benchmarks and scenarios. Benchmarks represent pre-defined workflows that simulate real-world blockchain application usage. These standardized workloads enable fair and consistent performance comparisons between different blockchain platforms. Each benchmark can contain multiple scenarios, which represent specific variations within the workflow. These scenarios might focus on different functionalities or use cases of the blockchain network. Caliper provides a set of built-in benchmark scenarios that cover common blockchain operations, allowing users to quickly evaluate platform performance. Some examples include:

  * **Asset Management:** This benchmark simulates a scenario where users create, read, update, and delete assets on the blockchain.
  * **Supply Chain:** This benchmark models a supply chain process where participants track the movement of goods through the chain by adding and updating data on the ledger.
  * **Voting:** This benchmark simulates a voting system where users cast votes and the results are securely stored and tallied on the blockchain.
  * **Financial Transactions:** This benchmark represents a scenario involving financial transactions like payments or transfers, focusing on throughput and latency.