# Paper-Development-of-a-Real-time-solver-for-the-Local-Eigenvalue-Modification-Procedure

Real-time model updating for active structures experiencing high-rate dynamic events such as; hypersonic vehicles, active blast mitigation, and ballistic packages require that continuous changes in the structure’s state beupdated on a timescale of 1 ms or less. This requires the development of real-time model updating techniques capable of tracking the structure’s state. The Local Eigenvalue Modification Procedure (LEMP) is a structural dynamic modification procedure that converts the computationally intensive global eigenvalue problem used in modal analysis into a set of second-order equations that are more readily handled. Implementation of LEMP for tracking a structure’s state results in secular equations that must be solved to obtain the modified eigenvalues of the structure’s state. In this work, the roots of the secular equations are solved iteratively using a divide and conquer approach, leading to faster root convergence. The present study reports on developing a real-time computing module to perform LEMP in the context of real-time model updating with a stringent timing constraint of 1 ms or less. In this preliminary work, LEMP is applied to tracking the condition of a numerical cantilever beam structure, which depicts changes in a structure’s state as a change in the roller position. A discussion of variations in timing results and accuracy are discussed.

# LEMP flowchart
![LEMP flowchart](https://user-images.githubusercontent.com/69466658/172226549-e21c87b6-1d2a-4825-bb0d-4fbdf241ae99.png)

# LEMP algorithm pseudocode
![lemp algorithm](https://user-images.githubusercontent.com/69466658/172226969-67b26d91-49e8-4ca8-8a7d-98784d232051.PNG)
