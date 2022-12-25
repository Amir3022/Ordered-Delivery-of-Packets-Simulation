# Ordered Delivery of Packets Simulation using C++

* Simulatation the arrival of packets of a communication system to the receiver. Due to the unpredictable network
conditions, these packets can be lost or arrive out of order. That’s why the system is simulated using circular inorder priority
queues to simulate 3 buffers: Received, Waiting and Dropped.

## Design of the Circular Inorder Priority Queue

* The queue is implemented using static implementation (array based implementation) with priority, all items with the same priority
are arranged in order inside the queue, items with lower priority are arranged after them. It’s circular queue, when reaching rear
element it rotates on itself again. The priority system is ascending, which mean that 1 has a higher priority than 2.

* Methods used by the Queue class:
  * Enqueue(QueueElemType,Priority): Adds the PacketID to queue, its arranged inside based on order and priority.
  * Dequeue(): Outputs the front element of the queue, and delete it from the queue.
  * FrontElem(): Checks for front elemnt of the queue without deleting it.
  * IsEmpty(): Checks if the queue is empty.
  * Search(QueueElemType,Priority): Searches the queue for a PacketID having the argument value and priority.
  
* Here is a demonstration for How items are arranged in queue, and adding a new item

![](Figures/Image1)

![](Figures/Image2)

## Main Flows
### Error Handling

* The Following is a flow chart showing the Error handling operation in the main code:

![Flowchart showing error handling operation](Figures/Image3)


### Main Operation

* The following is a flowchart that shows the main operation of the code, assuming no errors happened and all input entered
SeqNumBits, WinSize, InitSeq, PacketsID are all valid:

![Flowchart showing main program operations](Figures/Image4)

## Discussing The main program main points

* The input to the program is a string containing SeqNumBit(which is used to generate maxseq), WinSize, InitSeq and all
the PacketsID. After going through the error handling phase and having no errors, then all values are valid and ready to
be used in the next portion of the code.

* InitSeq is set as the Expected value, Expected value and WinSize are then used to generate the window of upcoming
expected PacketIDs.

* 3 Queue are created: Received contains the received packets in order, Waiting contains the Packets that are in the
window but are not the expected value so are kept in waiting to keep the received values in order, Dropped contains the
dropped Packets that are either out of bounds(not present in the window) or already present in the received queue.
