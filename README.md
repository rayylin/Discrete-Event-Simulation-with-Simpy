# Discrete-Event-Simulation-with-Simpy
Discrete event simulation can help businesses use computer modeling to virtually test manufacturing methods and procedures, greatly reducing the time and costs that physical testing of a manufacturing system would incur. In this project, we use Simpy to carry out a discrete event simulation and allow users to test a range of scenarios before buying tooling, reserving capacity, or coordinating other expensive production resources. Simulation can help users determine exactly what is needed to achieve their goals, such as inventory levels, replenishment rates, batch sizes, production planning, etc.

# Process flow 
In this project we are going to use an toy factory as an example. The process flow is shown in the picture below.

![simu](https://user-images.githubusercontent.com/58899897/197322197-3f6dfc01-17f2-4bfe-b06c-bdf18448fbcb.jpg)


We are going to simulate production scenarios with different safety level, labor hour, number of machines, and storage capacity.
First we need to determine how long we are going to run the simulation

![image](https://user-images.githubusercontent.com/58899897/197322321-c06f6953-0ef9-4d4e-badf-e1f2d1e5d4ef.png)

For all the triangle objects, we need to determine the storage capacity and initial stock.

![image](https://user-images.githubusercontent.com/58899897/197322371-5aea8230-99b1-4f22-a391-d5ad562088c0.png)

For the rectangle objects, we need to determine how many employees we have and how much time each process take. We can use different distributions and select the one that best fit the raw data. Here we are going to use Normal Distribution and need to determine the mean and standard deviation for each process.

![image](https://user-images.githubusercontent.com/58899897/197322458-0e3b2996-0573-4f0e-b13f-21b2d4f6186d.png)

For each raw material we need to create a container instance. Containers model the production and consumption of a homogeneous, undifferentiated bulk. It may either be continuous (like water) or discrete (like apples).

For each process we need to create a Simpy process instance. The Process instance that is returned by Environment.process() can be utilized for process interactions. 

![image](https://user-images.githubusercontent.com/58899897/197322832-17861522-0033-47c9-a805-d6c25b3a66a9.png)

Next is to define what a process exactly should do. By yielding the Process instance that Environment.process() returns, the run process starts waiting for it to finish. Take assemble as an example, an assembler need to take one wood body, one wood head, one electronic, and an IC to assemble a toy. The time a assembler takes to finish one product follows normal distribution. An important event type is the Timeout. Events of this type are triggered after a certain amount of (simulated) time has passed. "Get" function would take one unit from the raw material, and the "put" function would add one more unit to the raw material.

![image](https://user-images.githubusercontent.com/58899897/197322965-75363c1f-7f07-4fda-b994-b94c169e8a68.png)



# Run the simulation
A simulation environment manages the simulation time as well as the scheduling and processing of events. It also provides means to step through or execute the simulation.

![image](https://user-images.githubusercontent.com/58899897/197323190-ae667bee-3093-4bab-a9cd-375db2921a7f.png)

# How simulations help decision-making?
We could use simulation to try different production scenarios, a method that could greatly reduce the time and costs that physical testing of a manufacturing system would incur. For example, the first production scenario hires one IC tester, and the total toys made is 166.

![image](https://user-images.githubusercontent.com/58899897/197323335-036b874a-a6a6-4031-aa2b-4cb242ee815a.png)

If we hire 3 IC testers, the total toys made would become 329.

![image](https://user-images.githubusercontent.com/58899897/197323416-dd811306-1229-43c4-a92c-849d99362d09.png)

Another example is that we could use simulation to determine the storage capacity.
When the IC capacity is 600, the total toys made is 334. When we change the capacity to 150, the total toys made is 331, meaning that IC do not require that much storage space.

![image](https://user-images.githubusercontent.com/58899897/197323486-c4099573-be0e-4b32-8e7f-fd539596e7b6.png)





