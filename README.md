# Overview
This repository provides a robust simulation framework designed to replicate real-world vehicular scenarios in a controlled environment. Utilizing SUMO, NS-3, and NetAnim, this framework allows researchers and developers to accurately model vehicular movement and communication, facilitating the evaluation of VANET protocols and algorithms.

# Features
- SUMO Integration: Convert OpenStreetMap data into SUMO network files for realistic vehicular movement simulation.
- NS-3 Compatibility: Transform SUMO-generated traces into NS-2 format, enabling customizable simulations with NS-3.
- NetAnim Visualization: Enhance simulation visualization to observe vehicular movement and communication patterns.
- Comprehensive Evaluation: Supports the exploration of new VANET protocols and scalability assessments for more reliable vehicular communication systems.

# Prerequisites
- SUMO: Simulation of Urban MObility
- NS-3: Network Simulator 3
- NetAnim: Network Animator
- Python: For running scripts and utilities
- OpenStreetMap Data: Source for generating realistic simulation environments

# Procedure
- Step1: Create Sumo-gui or Sumo configuration file using the open street map.
- Step2: Create the mobility.tcl
- Step3: Run the ns2-mobility-trace-file with nodeNum, duration, logfile.
- Step4: Include the NetAnim code and run the simulation.


Step2: How to create the mobility.tcl file:
- sumo -c osm.sumo.cfg --fcd-output trace.xml
- cd sumo/tools
- python3 traceExporter.py -i trace.xml --ns2mobility-output=mobility.tcl
Now check the number of nodes in the mobility.tcl file

Move the mobility.tcl into the home folder

Step3: ./waf --run "scratch/ns2-mobility-trace --traceFile=/home/pranav/mobility.tcl --nodeNum=46 --duration=100.0 --logFile=ns2-mob.log"


Step4: Include NetAnim Code,
#include "ns3/netanim-module.h"

include the following line above the Simulator::Run()
AnimationInterface anim("vehicularmobility.xml");


How to run NetAnim
cd ns-allinone-3.39/ns-3.29
./NetAnim
