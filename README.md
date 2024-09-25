

# README - Network Simulation with ns-3

This project demonstrates how to set up and run a network simulation using the ns-3 simulator. The simulation will model various network topologies and protocols to study performance metrics such as latency, throughput, and packet loss.

## Introduction

The **ns-3** (Network Simulator 3) is a discrete-event network simulator used to model and simulate various network protocols and configurations. This project includes a set of scripts that demonstrate network simulations, such as point-to-point networks, WiFi simulations, and TCP/UDP protocol performance.

## Prerequisites

Before running the simulations, ensure the following software is installed:

- **ns-3**: Version 3.35 or later
- **Python**: Optional, for running helper scripts
- **g++/gcc**: For compiling C++ code

### System Requirements

- Linux (recommended), MacOS, or Windows with a Linux environment (e.g., WSL).
- Minimum 4 GB RAM.
- 10 GB of free disk space for ns-3 installation and simulations.

## Installation

To set up ns-3 on your system, follow these steps:

### 1. Download and Install ns-3

Clone the ns-3 repository and navigate to the directory:

```bash
git clone https://gitlab.com/nsnam/ns-3-dev.git
cd ns-3-dev
```

### 2. Build ns-3

Run the following commands to build ns-3:

```bash
./waf configure --build-profile=optimized --enable-examples --enable-tests
./waf build
```

### 3. Verify Installation

To verify that ns-3 was installed correctly, run:

```bash
./waf --run hello-simulator
```

You should see output indicating that the simulator is running correctly.

## Running Simulations

Once ns-3 is installed, you can run the provided simulation scripts. Below are some example simulations and instructions for running them.

### 1. Point-to-Point Network Simulation

This simulation creates a simple point-to-point network and measures the latency and throughput.

1. Navigate to the **point-to-point** simulation directory:
   ```bash
   cd scratch/point-to-point
   ```

2. Run the simulation:
   ```bash
   ./waf --run point-to-point-simulation
   ```

3. Output will display latency and throughput statistics.

### 2. WiFi Network Simulation

This script simulates a basic WiFi network with multiple nodes and measures packet loss and performance over time.

1. Navigate to the **wifi** simulation directory:
   ```bash
   cd scratch/wifi
   ```

2. Run the simulation:
   ```bash
   ./waf --run wifi-simulation
   ```

3. Output will show performance metrics such as packet loss and latency.

### 3. TCP/UDP Protocol Performance Simulation

This script compares the performance of TCP and UDP in a simulated network.

1. Navigate to the **tcp-udp** simulation directory:
   ```bash
   cd scratch/tcp-udp
   ```

2. Run the simulation:
   ```bash
   ./waf --run tcp-udp-simulation
   ```

3. The simulation will output the results of the comparison between the two protocols.

## Customization

You can modify the simulation parameters such as bandwidth, delay, packet size, and node count by editing the corresponding C++ scripts.

### Example: Modifying Bandwidth in Point-to-Point Simulation

1. Open the `point-to-point-simulation.cc` file located in `scratch/point-to-point/`.
2. Look for the following line of code:
   ```cpp
   pointToPoint.SetDeviceAttribute ("DataRate", StringValue ("5Mbps"));
   ```
3. Modify the `"5Mbps"` value to your desired bandwidth setting.
4. Save the file and recompile ns-3:
   ```bash
   ./waf build
   ```

### Example: Adding More Nodes

To increase the number of nodes in a simulation, locate the section in the script where nodes are created. For instance, in the WiFi simulation script, you will find:

```cpp
NodeContainer wifiNodes;
wifiNodes.Create (4);  // Creates 4 WiFi nodes
```

Change the `Create(4)` parameter to the desired number of nodes.

## Common Issues

### 1. Permission Denied
If you encounter permission errors while running simulations, try running the commands with `sudo` or ensuring your user has the correct permissions.

### 2. Simulation Crashes
Ensure that you have enough system resources to run the simulation, especially when increasing the number of nodes or the complexity of the network.

### 3. Missing Files
If you get an error about missing files, ensure all required scripts are in the `scratch/` directory and that you are running the commands from the correct path.

## References

- **ns-3 Documentation**: https://www.nsnam.org/docs/
- **ns-3 Tutorials**: https://www.nsnam.org/docs/tutorial/html/
- **GitHub Repository**: https://gitlab.com/nsnam/ns-3-dev

