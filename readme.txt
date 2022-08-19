Project Topic :  Simulating Selfish Mining and Stubborn Mining attack using the P2P Cryptocurrency Network Simulator

Team Members:
AKASH KUMAR (Roll number- 213050020)
HRISHIKESH SALOI (Roll number- 213050057)
MANOJ KUMAR MAURYA (Roll number- 213050067)

Inputs to be provided by user:
n : number of nodes
fast = percentage of nodes which are fast (in %)
total_sim = number of events the node should execute (Number of events to simulate)
attacker_id = node id of attacker (node id = 0 recommended)
attack = 0 for selfish mining and 1 for stubborn mining
hashing_pow = hashing power of first node., Rest hashing power is equally distributed among rest of the nodes

Compiling and running:
The inputs can be provided by user in the code itself and executing the code will automatically create network, nodes, coins for each node and start the threads.
The log files is created automatically and the events details can be viewed by refreshing the log file with time. The last node (node id=n-1) is made to do 
	double spend attack whenever it is mining on a block with chain length >= 1 (i.e except genesis , as genesis dont have any transactions).
The protocols of blockchain is maintained.
The timer is synchronized with real time.
The log files shows how the state change transition happens during attack.
The blockchain and longest chain is created as image(png) file in the same folder which contains the code file.
The report gives further detailed analysis with various parameters.

Working of code:
Bitcoin network is created between n nodes such that the network is connected
log files are created for each node which stores detailed view of the event simulation
coins are initally created randomly for each node with values ranging from 20 to less than 40
The n number of nodes are created by passing the unique node_id, whether it is fast or not, its connected adjacent neighbours and the coin list
Every node will maintain its own transaction pool(list of transactions generated or recieved), Blockchain tree, coins list, 
	block timestamp(stores time when the respective block in blockchain was first seen by this node).
Every node will create its own event queue i.e queue present at queue[node_id] and queue size list(maintains number of events present in the node's queue)
Event Queue is made such that at any instant the events are always stored in the order of scheduled time for their respective execution
The timer is synchronized with real time.
For each node we create a thread which invokes the run method of that respective node
run_method initally creates txn_gen and block_gen events scheduled at time = current time + respective interarrival time
run_method for a thread runs until number of simulation for that thread reaches total_sim
run_method for a thread invokes an event only when the current time reaches the scheduled time for  that event
Here, the simulation starts and one event creates zero or  more events and this continues till run_method runs
The attacker node attempts attack based on attack id provided. The state change transition is printed in the log file for clear analysis of attack.
All the details are stored at the respective thread's log file

