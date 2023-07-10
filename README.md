# Paper-Development-of-a-Real-time-solver-for-the-Local-Eigenvalue-Modification-Procedure

Real-time model updating for active structures experiencing high-rate dynamic events such as; hypersonic vehicles, active blast mitigation, and ballistic packages require that continuous changes in the structure’s state be updated on a timescale of 1 ms or less. This requires the development of real-time model updating techniques capable of tracking the structure’s state. The Local Eigenvalue Modification Procedure (LEMP) is a structural dynamic modification procedure that converts the computationally intensive global eigenvalue problem used in modal analysis into a set of second-order equations that are more readily handled. Implementation of LEMP for tracking a structure’s state results in secular equations that must be solved to obtain the modified eigenvalues of the structure’s state. In this work, the roots of the secular equations are solved iteratively using a divide-and-conquer approach, leading to faster root convergence. The present study reports on developing a real-time computing module to perform LEMP in the context of real-time model updating with a stringent timing constraint of 1 ms or less. In this preliminary work, LEMP is applied to track the condition of a numerical cantilever beam structure, which depicts changes in a structure’s state as a change in the roller position. A discussion of variations in timing results and accuracy are discussed.

[paper citation] Emmanuel Ogunniyi, Austin R. J. Downey, and Jason Bakos. Development of a real-time solver for the local eigenvalue modification procedure. In Daniele Zonta, Zhongqing Su, and Branko Glisic, editors, Sensors and Smart Structures Technologies for Civil, Mechanical, and Aerospace Systems 2022. SPIE, apr 2022. doi:10.1117/12.2613208

# LEMP flowchart
![LEMP flowchart](https://user-images.githubusercontent.com/69466658/172226549-e21c87b6-1d2a-4825-bb0d-4fbdf241ae99.png)

# LEMP algorithm pseudocode
![lemp algorithm](https://user-images.githubusercontent.com/69466658/172226969-67b26d91-49e8-4ca8-8a7d-98784d232051.PNG)

# Timing Study
The LEMP algorithm is broken down into five steps to easily study the time it takes using LEMP to update the state of a high-rate dynamic system.

step 1: Adding roller condition: which depicts the changes in physical space from the initial state to the altered state

step 2: Spectral decomposition of ∆K12

step 3: Set truncation: include only contributing nodes

step 4: Obtain Ω2 using Divide and Conquer

step 5: Solve for new frequencies

step 6: Update roller position

![Lemp_process_time](https://user-images.githubusercontent.com/69466658/172229337-2960c53d-699b-45d9-b0e2-239f120d88ca.png)

The figure above shows the timing of each steps above using the algorithm described in section 3, step 1 takes approximately 0.0019 ms, step 2, 0.0662 ms, step 3, 0.0074 ms, step 4, 0.3353 ms and step 5, 0.0184 ms. A computer with processor Intel(R), Core(TM) i7-10700K CPU 3.80GHz was used for running the test. The total time for a single state estimation using LEMP is approximately 0.4296 ms. Step four in the LEMP process, where divide and conquer is used to solve for the altered state frequencies, took the most time at 0.335 ms. This step accounts for approximately 84% of total LEMP time. 

![element_time](https://user-images.githubusercontent.com/69466658/172229847-2f485891-152e-4339-97d5-1f0fe70266d0.png)

The figure aboves shows the maximum time required for state estimation using beam with element number 4 to 30.

# State estimation comparison using LEMP and GE

![modes4](https://user-images.githubusercontent.com/69466658/172230675-31eda883-7ef7-4ab7-bc36-a7bdfdd9af34.png)

A close system state estimation is seen using the Local eigenvalue modification algorithm when compared to the reference general eigenvalue algorithm. Here, the frequencies obtained using the generalized eigenvalue approach is assumed to be the true value, while the LEMP is the estimated frequency value. Small deviations are seen in the fifth mode; however, the percentage error observed is low, and a considerable high SNR is seen in the first four modes as shown in figure below. This result demonstrates the feasibility of the of the LEMP algorithm with the divide and conqure solver for simple structure. It’s viability for more complex state estimations are topic for future works.

![SNR_error4](https://user-images.githubusercontent.com/69466658/172231051-32b71f8d-c557-4c4d-b33a-2ce9cb2f26fb.png)


