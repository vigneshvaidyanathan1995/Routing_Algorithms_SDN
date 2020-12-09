# Routing _Protocol_Algorithm_SDN
Final Project for Software Defined Networks TELE 6400 .

By Vignesh Vaidyanathan under the guidelines of Dr Bhumip Khasnabish

## Project Description
My project simuates two routing algorithms; Dijkstra's algorithm and ECMP (Equal Cost Multiple Paths), in a virtual Software-Defined Network topology. It creates a Fattree network using the Mininet, and uses the Python based Pox SDN controller. Suppose you use Mininet as Virtual Machine then you need to SSH into the host machine so as to run the simulations. Also, the academic paper on the Fattree network topology that i tried to recreate can be found [here](http://ccr.sigcomm.org/online/files/p63-alfares.pdf). 



# Instructions to Run

For the implementation of the project you will need to run two different scripts one for the topology/Algorithm and the other one for the controller on two different terminals in your virtual machines. Make sure you have all your dependency file installed in your virtual machines. Scripts needed to run the project are as follows:

Controller Bash Scripts:
1)controller_dij.sh
2)controller_ecmp.sh

Network Topology/ Algorithm Bash Scripts:
1)run_dij.sh
2)run_ecmp.sh

Steps to run the Dijksras part of the project are as follows:
1) In the first terminal run the script for the controller by writng "sudo ./controller_dij.sh"
2) In the second terminal run the script for the Network topology/ Algorithm by writing "sudo ./run_dij.sh"

Steps to run the ECMP part of the project are as follows:
1) In the first terminal run the script for the controller by writng "sudo ./controller_ecmp.sh"
2) In the second terminal run the script for the Network topology/ Algorithm by writing "sudo ./run_ecmp.sh" 

Iperf was used to generate traffic through the network, and its output is saved in library/results/fattree-{dij/ecmp}/{input-file-name}/data

# Network Topology Diagram
The diagram or the visual apprearance of the topology is shown in the below diagram. The file is named Fattree_topology.png:
![Alt text](./Fattree_topology.png?raw=true "Fattree Topology")


# Project Summary

The main aim of the project is the implementation of different routing algorithms like the Dijkstras and the ECMP algorithm in a Data center network(Fattree Network Topology in our case). We build a software defined networking (SDN) network using simulated switches with an SDN controller. Apart from making use of MININET for building the topology the project revolved arounfd the use of POX controller for the deployment of the Algorithm.

Part One of the project is to build a fattree topology with (k=4). The script used to build the topology is in the file named "DCTopo.py" which is basically a python scripts which build the topology along with the number of hosts/servers that will be connected with the switches. This was built in mininet.

Part Two of the project is to run Dijkstra’s algorithm between two pairs of end hosts. We first built the algorithm that takes in a nested dictionary list that holds all nodes and every connected node to that given node. The code for this Algorithm is written in the script "Dijkstra.py". I took a reference of this Algorithm from "http://www.gilles-bertrand.com/2014/03/dijkstra-algorithm-python-example-source-code-shortest-path.html" site. 

Part Three of the project was to implement ECMP which uses a hash function to pick a given path through the fat tree network topology from the k different paths. This was implemented by running dijkstras on a graph object that only had one specific available core switch that is chosen with a hash function which is run by combining any source and destination ip pair. You can find the script for the same in the "HashFunction.py" file

A separate script is written to evaluate each routing scheme using Iperf and the given traffic patterns. 

Finally i also ran wireshark to get the analysis of the flow of packets from one destination to the another and check the throughput and the changes in the throughput when either of the algorithms are implemented. 


Issues Faced:

Iperf Connection Failed: This is seen some times as the output for the iperf client, however I believe it must be due to how iperf not closing the connection properly. 

Termination of the controller: This was witnessed when i first run the dijkstras algorithm and after that when i stop the controller is basically doesnt stop and keeps on running even after the terminal showing it is stopped. Tired to kill the process usinf ps aux, but didnt work. So had to restart the VM inorder to implement the ECMP algorithm.

Programming Errors: Numerous errors related to coding like not importing the functions properly, Syntax mistakes, Not keeping the files in the same directory while running the script and many more coding errors where witnessed while executing the project. 
