NeosExplorer is an agent simulation system developed on the Rhino-Grasshopper platform, with source code written in C#. Its primary function is to simulate exploratory movement or predictive path-guided behaviors of agents in 2D space, applicable to pedestrian simulations or behavioral studies of other organisms.

Development Background：
NeosExplorer was developed as a viable alternative to the Grasshopper (GH) pedestrian simulation tool PedSim, which is no longer available through public platforms or channels. While PedSim's internal implementation details remain unclear to users, its simulation results suggest it was designed to guide agents toward goals via shortest paths.

Core Algorithm & Modes：
NeosExplorer shares the same core algorithm as PedSim—the Social Force Model from pedestrian dynamics. Version since 1.2.2 offers two simulation modes:

Exploration Mode (using Explorer Simulator):This mode operates without path guidance. Upon encountering obstacles, agents identify the nearest feature point within their field of view, adjust their direction, visit points of interest (PoI) for a designated duration, and then proceed toward the destination. PoIs are optional, and multiple PoIs are supported.
(Note: This mode currently has limited adaptability for complex scenes; regular geometric shapes are recommended for obstacle outlines.)

Path Guidance Mode (using Pedestrian Simulator):
This mode pre-computes the shortest path from the start point to the destination via PoIs using a 2D visibility graph and the A* algorithm, guiding agent behavior accordingly. It includes a reliable movement assurance mechanism suitable for scenes with complex obstacle contours.

Version 2.0.0 has added input ports for evacuation zones and output ports for evacuation time, enabling building space optimization based on evacuation duration.
A hybrid simulator is added to NeosExplorer 3.0, integrating two behavior modes—exploratory movement and guided movement—with parameters in the simulation settings controlling the proportion of agents in each mode.

Flexibility & Accessible Data:
NeosExplorer exposes most adjustable parameters to users for flexibility, including desired speed, maximum speed, mass, field-of-view angle, and visibility range. Adjusting these parameters allows adaptation to diverse scenarios. Users can also access comprehensive agent data during simulations—such as current position, velocity, resultant force, movement trajectory, and field of view—to support varied research needs.

Core Engine & Operation:
The core engines are the Explorer Simulator and Pedestrian Simulator, requiring iterative computation via Grasshopper’s Trigger (Timer) component.

Critical Note: 
If closed polylines acting as obstacles are manually drawn point-by-point, they must be drawn counter-clockwise (unless a value of 0 is input to the Navigation Offset, NO parameter).

Key Concept: 
"Time" in this simulation refers to iteration time steps. For example:If the Trigger’s time interval = 100 ms (i.e., iterates every 100 ms),and an agent’s stay duration at a PoI = 5,the actual stay duration is only 500 milliseconds.This may render stays imperceptible during real-time simulation. The same principle applies to inertia duration and departure interval.

Component Info & Test Environment:
NeosExplorer is part of the author’s Neos series of Grasshopper components. Upon installation, it appears under the Neos Category and NeosExplorer Subcategory in the Grasshopper toolbar.
First version tested on: Windows 11, Rhino 8 SR20 (v8.20.25157.13001, 2025-06-06) – Grasshopper 1.0.0008 (2025-06-06).
![INTRO1 2 2](https://github.com/user-attachments/assets/4c674615-44c6-44e9-ab64-94dbdc93ad2e)
![GH script](https://github.com/user-attachments/assets/45f9471a-5db7-4be1-a14a-b68b5c41951b)
![evacuation0](https://github.com/user-attachments/assets/2bfae2be-6ee2-47fa-932c-934224d298f4)
![pass through bottleneck](https://github.com/user-attachments/assets/61502e8c-3e23-46e0-b992-cd9c3c7af99c)


