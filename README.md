# resources

Support info for future SEE participants

## About the Capstone project

This information is subject to change, but reflects the 2025 experience.

You will be participating in a NASA program called SEE (Simulation Exploration Experience). Alongside students from other universities, ranging from undergraduate to PhD level, you will have the unique opportunity to join a distributed simulation with a technical focus, likely related to lunar exploration.

Within the Capstone courses, you will be divided up into teams. Some teams will be responsible for conceptual development of entities to place in the simulated environment (our class worked on a lunar rover, an emergency shelter, and a cargo launcher). One team will be responsible for producing local simulations for each of those entities, and joining them to the central simulation on the demo date with NASA. This team will be working on a compressed schedule, because the demo will likely occur weeks before the end of the ENGR 491 course. You will have deliverables for ERAU at predictable dates within the course, but the big event will not be happening on ERAU's timeline.

## Terminology

- **HLA (high-level architecture)** is a technical standard used for managing distributed simulations. This is not software in & of itself, but a standard that defines the terms of engagement for software run on different hosts. (Read more [here](https://pitchtechnologies.com/2023/06/introduction-to-hla/).)
- **RTI (runtime infrastructure)** is software that implements the HLA specification and enables federates & federation to behave in an orderly manner throughout a simulation run. (Read more [here](https://www.mak.com/mak-one/tools/mak-rti/capabilities)).

## Day 1 of ENGR 490

If you are able to join the fall Kick-Start program ahead of the spring SEE program run, we highly recommend it. If you missed it, start in on these items ASAP:

- Get access to SEE's weekly Tech Tag-up call
- Get access to the Discord
- Get access to the [wiki](https://github.com/FlaSpaceInst/SEE-Sim-Smackdown/wiki)
- Find out which provider will be used for the RTI and get license requests in as soon as possible

## Technical decisions

Early on, you will need to decide what framework to use for your simulation. You can use the java-based [HLA Starter Kit](https://github.com/SMASH-Lab/SEE-HLA-Starter-Kit) that was created for this program by the University of Calabria, or align with NASA and use [Trick](https://github.com/nasa/trick) with associated middleware [TrickHLA](https://github.com/nasa/TrickHLA). In our experience, Trick was a great toolset for simply running & developing simulations locally. However, getting the full setup working with the RTI (Pitch) was not straightforward to achieve on Apple Silicon in the time we had available. Challenges we encountered included mainly revolved around producing a build environment using a version of C++ compatible with the RTI, while managing the downstream effects of changes required for the RTI on Trick/simulation code. YMMV with Windows and/or changes that may be introduced to the RTI or TrickHLA by the time you read this, but as of this writing, we recommend either sticking with HLA Starter Kit or expecting to work through some complexity in connecting to the RTI.

You will likely be constrained in choice of RTI by the decision made on the central RTI for the program. In theory, as long as two RTIs adhere to the same HLA specification, they should be interchangeable, and if that were the case you could use a different RTI locally than the one used for the central federation. In practice, we found that this was not the case when proprietary tools came into play. It took us quite some time to get Pitch licenses, so we started looking at other options to be able to test functionality. The best open-source options we found were [OpenRTI](https://github.com/onox/OpenRTI/tree/master) and [Portico](https://github.com/openlvc/portico), but Portico is undergoing an overhaul and OpenRTI is no longer actively developed. We have included our code for reference in case this is an avenue someone wants to pursue, but the best option is just to get your licenses early for the proprietary RTI used.

## Repos 

- [lunar-rover](https://github.com/erau-see-2025/lunar-rover): Simulation code for the rover
- [shelter](https://github.com/erau-see-2025/shelter): Simulation code for the emergency shelter
- [CHUCK](https://github.com/erau-see-2025/CHUCK): Simulation code for the cargo launcher
- [EagleHLA](https://github.com/erau-see-2025/EagleHLA): Our fork of TrickHLA.

Good luck!!!
