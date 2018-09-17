# Automatic-Robot-Design-MCDPL
Building a land based rover with a catalogue of 4 main types of parts : Batteries, Chassis, Robotic Arm, Motor.
We have 5 functionalities:
velocity (m/s), capacity (J), endurance (s), precision(1/mm), workspace(m), extra_power(W), extra_payload (kg)
and 2 constraints:
cost ($), mass (g)

README
Following are the Instructions to run MCDPL Library for Ground Based Robots: 
1.	Clean-install version:
1.1.	To perform a clean install on your system, please refer to the MCDPL Documentation (https://andreacensi.github.io/mcdp-manual/mcdp-manual.pdf) and follow their step-by-step instructions regarding the installation.
1.2.	Clone the project from the github page: (https://github.com/asrathor/AutomaticDesign).
1.3.	To run the MCDPL solver, execute the command mentioned in 2.4 of this document.  
2.	Pre-installed version:
2.1.	Download the VM from this link: https://drive.google.com/file/d/1cPCjZn4_7Cu2mEREIZ51Cf3aWomZ7_n0/view?usp=sharing 
This VM already has MCDPL pre-installed. 
2.2.	Once you open the VM, log-in to the user Aditya using the password “1441”.
2.3.	Move to the “AutomaticDesign” folder present in the home directory using the terminal.
2.4.	Once in the mentioned folder, the command to run the MCDPL solver is as follows: 
"$ mcdp-solve --imp RoboticArm “<400 s, 0.1 kg, 1 W, 1 1/mm, 0.3 m, 0.0048>"
The indicated numbers in the command represent: endurance (in seconds), extra_payload (in kg), extra_power (in W), precision (in 1/mm), workspace (in m) and velocity (dimensioneless) respectively. Do not change the order of these as the order is dependent on the mcdp code in RoboticArm file.
The option --imp provides the implementation details.

Note that these values depend on the specification of the parts mentioned in our mcdp files (i.e., Joint.mcdp, actuation3.mcdp and chassis1.mcdp). The specifications in these mcdp files can be changed to acquire more accurate upper bound.
2.5.	To create a map of the design, execute the following command:
"$ mcdp-plot --cache –plots ndp_graph_enclosed –D ../.. –d. RoboticArm" 
2.6.	For adding the more parts in the library, simply edit the catalogues present in mcdp files: Joint.mcdp, actuation3.mcdp and chassis1.mcdp.
3.	Known-errors while installation:
3.1.	The repository ‘http://security.ubuntu.com/ubuntu zesty-security Release’ does no longer have a Release file.
Solution: Update the /etc/apt/sources.list file by removing the existing declarations and add the following:
deb http://old-releases.ubuntu.com/ubuntu zesty main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu zesty-updates main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu zesty-security main restricted universe multiverse

3.2.	If the error observed is Getting TypeError: ‘generator’ object has no attribute ‘_getitem_’, then execute the following command in the terminal:
$ sudo pip install networkx==1.11

