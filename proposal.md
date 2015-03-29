__Name:__ Niko Visnjic

__IRC name:__ neemo

__email contact:__ in melange (proposal is public)


## Abstract ##
Providing an abstract platform agnostic service for associating players to input devices is a solution that simplifies controller setup both from a players and a game designers perspective. This project proposes to apply high level action descriptors through a standardized API which would allow users and developers to utilize the PlayStation Move controller as a highly flexible input device using standard webcams.

## Project Milestones: ##

__Milestone I:__ Define the overall design of a high level platform agnostic
playerD API
that can be translated with ease to a multitude of controller schemes and input
devices. The API should expose only abstracted high level predefined actions
(jump, interact, change state from walk to run) to the game designer, while
leaving room for hacking the design if the default design does not fit his
control scheme.

__Milestone II:__ Integrate low level support for webcam drivers in the playerD
service with the intent of accepting a camera video stream as an input vector.
The raw stream should be processed either by reusing existing Move APIs or
writing new processing algorithms using open source computer vision libraries.

__Milestone III:__ The processed video and bluetooth streams will provide location,
orientation and button press information for the Move controller, as well as
changes in these , which will be used as low level events for building higher
level more complex events (eg. corner-to-corner cross motion indicating a
cancel action). These higher level events should constitute a body of standard,
often reused, actions as defined in the playerD API to facilitate ease of
controller setup and straightforward code migration.



## Implementation: ##

Following the goals outlined in the project milestones, we would look into
implementing the project in roughly the same order. The first and most broad
issue is defining the API we intend to use in the future playerD interface.
A preliminary concept of the API can be found in the design documentation in the source code for playerD [1], which we will broaden to develop a general API specification to build this project on. 
As mentioned in the design documentation, the user-facing API should only expose those high level elements needed for controller and input setup, while pushing the platform specific low level processes in the background. 
While the API will be defined in discussion with the mentor prior to starting
the coding period, it should be modified and improved upon testing the API with
the PS Move controller as a use case which will be developed during this
project. An early draft of the API should be made in the coming weeks and
submitted to the mailing list for improvement suggestions.

Low level device support is needed for all hardware we intend to use in
this project, namely bluetooth driver support and webcam support. Since the
playerD system intends to be platform agnostic, the hardware need to be
supported in major operating systems. Linux support for bluetooth peripherals
is already implemented with the bluez driver stack. Bluetooth support in
Windows support is currently not implemented, but should be implemented either in the scope of a separate GSoC 2015 project or can be implemented as a stretch goal in this project, past completion of Linux support.
Webcam integration and video processing would be added using the OpenCV
library, which supports multiple platforms and webcams setups. 

The PlayStation Move controller will be added as a supported controller device
into the playerD API developed in phase I, allowing high level control scheme
configuration for a controller which supports a wide set of complex action
events.
Complex action definition will be provided by lower level actions described by inertial readouts and button press events collected via bluetooth, as well as, a processed video stream from the webcam. 
Having multiple data streams will allow us to define action events in greater detail and achieve further diversification between similar action events, for example, 
differentiating between a sword swing action and a guard action could be done either through button inputs or using inertial measurements and computer vision for a more organic controlling scheme.
A number of APIs [2,3] have already been written for the PlayStation Move
controller and it would be wise to investigate how such code could be reused in
this GSoC project. Any missing functionality will be developed in OpenCV to
accommodate for the playerD API use cases.

The complete system should be tested before the end of the GSOC coding period,
with documentation and examples to accompany the project. The API will be further
refined during testing with feedback from the community to make a viable and
simple controller setup scheme. 


[1] http://hg.playerd.org/playerd 

[2] http://thp.io/2010/psmove/

[3] https://github.com/thp/psmoveapi


## Timeline ##

__Pre-GSoC period:__

* Define a draft of the playerD API and engage with community for feedback
* Go through a couple of iterations of the API and agree on a minimal workable
  set
* Research the MoveAPI and estimate how much of it can be reused
* Look into other APIs as well
* Agree on complex actions set to be defined by API and implement any take note
  of any missing functionality to be implemented with OpenCV

__Midterm period:__

* Week1: Get inertial and button press readouts from the PS Move through the
  bluez module in playerD
* Week2: Complete sensor fusion either though code reuse from an available API
  or write new code
* Week3: Test inertial data and button press events, build basic actions sets
  from available data
* Week 4: Set up webcam data integration into playerD 
* Week 5: Process webcam data I - use existing APIs and/or write new code
* Week 6: Process webcam data II - use existing APIs and/or write new code
* Week 7: Build basic set of vision data actions

__Final period:__

* Week 8: Test vision data processing and actions, clean up any code issues
* Week 9: Implement complex actions by combining multiple basic actions
* Week 10: Implement final API concepts depending on feedback and use cases
* Week 11: Code cleanup, document API and example use cases

__Post GSoC:__

* Make a video on the usage and capabilities of the playerD interface
* Consider future expansions of the API and how to make it easily
  expandable

## Availability ##
I'll be able to devote between 40 and 50 hours per week on the project during
the coding period. Since I'm currently on an exchange program, my university
load is much lighter then usual, so I'll be able to dedicate about the same
amount of time in the pre-coding period as well.


## Personal Info ##
I'm a first year graduate student at the Faculty of Engineering in Rijeka, Croatia, pursuing a degree in Electrical Engineering. My studies are mostly in
automation and robotics, though I strive to engage myself equally in Linux development and open source software in general. 

Previously I've contributed to the Mozilla initiative and plan to continue doing so in the future.
Most of the software work I've done is in OpenCV object tracking algorithms in Python and C++ and ARM programming in C, 
with a bit of simulation in Matlab and machine learning in Octave.
From the software and hardware projects I have worked on, 
recent ones include OpenCV tracking and localization algorithms for a quadrotor
flight control system and developing an ARM based on-board autonomous flight interface for the Parrot AR.Drone.
The autonomous system will be hosted on GitHub in the near future.

I host a blog on GitHub and plan to write about the development experience
during GSoC about every week or two. It should provide others interested in the
playerD interface with a good paper trail on how to contribute themselves.

I'm sure this project would make for an interesting and productive summer and I'm confident I can contribute to it in a meaningful way.

Mozilla profile: https://reps.mozilla.org/u/nvisnjic_fer/

Blog: nvisnjic.com

