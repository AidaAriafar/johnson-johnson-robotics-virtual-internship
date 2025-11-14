# johnson-johnson-robotics-virtual-internship (Surgical Robotic Arm Optimization)
This repository contains my 2 completed tasks for the Johnson &amp; Johnson Robotics and Controls Job Simulation on Forage. It documents the process of diagnosing a control system bug, simulating a design level optimization, and proposing solutions to improve the performance of a surgical robotic arm.
## Overview
My mission was divided into two phases:
1.  **Task 1 (Diagnosis):** Identify the root cause of the software latency. 
2.  **Task 2 (Optimization):** Propose and validate physical design modifications to improve the arm's overall performance and durability.

## Task 1: Diagnostic Phase
In this phase, I acted as a software controls engineer to find the source of the reported delay.
### 1. Analysis
I used a Python Jupyter Notebook (`Control_System_Diagnostic_Notebook.ipynb`) provided by the Johnson & Johnson Forage repository,  to test the robotic arm's commands. The initial test confirmed the client's report:
| Command | Observed Response Time |
| :--- | :--- |
| `move_arm` | ~0.105s |
| `rotate_joint` | **~0.155s** |
| `adjust_grip` | ~0.055s |
### 2. Root Cause
A code review of the `check_response_time` function revealed the root cause: a non-essential **`time.sleep(0.15)`** command was hard-coded into the `rotate_joint` function, likely as a placeholder from a previous test.
### 3. Solution & Documentation
I documented this finding in a formal **`Diagnostic_Report.pdf`**. The immediate recommendation was the complete removal of the `time.sleep` line to eliminate the artificial bottleneck.
## Task 2: Optimization Phase
After fixing the software bug, I transitioned to a systems engineer role to address underlying physical design flaws identified in annotated technical drawings.
### 1. Identified Design Flaws
Analysis of the technical images revealed two core problems:
* **Actuator Strain:** The motors for the `rotate_joint` were under excessive strain, reducing efficiency and durability.
* **Sensor Misalignment:** The feedback sensors were not correctly aligned, causing a slight delay in the feedback loop.

### 2. Proposed Modifications
I proposed a holistic solution to address these flaws:
1.  **Upgrade Actuator & Reinforce Joint:** Replace the current actuator with a lightweight, high-efficiency model and reinforce the joint structure with stronger, lightweight composite materials.
2.  **Realign Sensor Array:** Perform a full recalibration and realignment of the feedback sensors.

### 3. Simulation & Validation
I used a Python simulation notebook (`Robotic_Arm_Design_Simulation.ipynb`) to validate the impact of these changes. I modeled the modifications as a **30% improvement in efficiency** and a **20% increase in durability**.

The simulation results were conclusive:

| Metric | Original | **Optimized** |
| :--- | :--- | :--- |
| **Response Time** | 0.20s | **0.14s (30% Faster)** |
| **Durability Score** | 75 / 100 | **90 / 100 (20% Stronger)** |

## Outcome
Gained hands on experience with control loop concepts, including feedback delays, processing bottlenecks, and the relationship between software controls and physical hardware




### 4. Final Documentation
These findings, simulations, and recommendations were compiled into a final **`Design_Proposal.pdf`**.


---
