# Master Thesis 
## Axel Vislie Mikkelsen and August Heiervang Dahl

This repository is made in connection with our master's thesis in Engineering and ICT at NTNU. 
Please follow the instructions below to run the simulation model:

* Download the AnyLogic University version (free 30-day trial): https://www.anylogic.com/downloads/
* Download this repository as a zip file and un-zip the folder in your preferred location
* Open AnyLogic University and the MasterThesis.alp file
* Navigate to the Monte Carlo Experiment (MC: Main) and run the file
* Choose one method (Conventional, Pathmind, Heuristic) and one of the 11 scenarios on the left-hand side
* If the heuristic method is chosen, you are free to choose one of the four pickup/release policy combinations listed. Note that the pickup/release policy is only available for the heuristic method. 
* Start the experiment in the bottom left corner. The performance statistics will appear in the histograms.
* If you want to compare different methods, you can do the following:
  1. Wait until the first experiment is finished
  2. Click on the pause button in the bottom left corner
  3. Change to the method you want to compare with and run the experiment again

It is also possible to run a single simulation run to analyze the forklifts' behavior. To do this, you follow the same procedure as above, but now with the Simulation Experiment (Simulation: Main)

## Abstract
Efficient handling of materials and products on manufacturing shop floors is essential to reduce production costs and improve productivity. Although the scientific community has embraced automated material-handling equipment in the wake of Industry 4.0, human-operated vehicles like forklifts and pallet trucks are still the most commonly used equipment for material handling. This thesis investigates how a cloud-enabled shop floor can facilitate dynamic dispatching by automating human and autonomously operated material-handling equipment through a centralized system, coined as the Cloud Material Handling System (CMHS).

The main objective of this study is to determine how a CMHS may improve material handling activities in manufacturing. Specifically, the study evaluates a CMHS in different scenarios to support when it is particularly beneficial in material handling operations. Multiple dispatching methods like heuristic dispatching rules and reinforcement learning policies are evaluated to support how a CMHS can be implemented. A literature study was conducted to disclose research gaps addressed by a CMHS, while a simulation model based on a case study was developed to demonstrate its use in practice. 

The results have shown the CMHS's ability to achieve higher productivity in terms of product throughput and equipment utilization compared to the conventional non-automated benchmark. Performance increases were observed in all scenarios, while the number of required material-handling equipment was reduced by 40\%.

The simulation results revealed that the CMHS with reinforcement learning is particularly beneficial for uncertain product arrival rates and workstation failures when product loads were kept in line relative to production capacity. Most prominent were normal product loads, resulting in a 197\% gain in total product throughput. The lower-complexity heuristic methods were on a par, or superior, to the reinforcement learning policy for predictable material flows with high arrival rates. 

Further evaluation of the CMHS should be done in collaboration with a practical business case to extract key operation parameters, reducing the number of assumptions, and develop a rigorous economical model for the CMHS.
