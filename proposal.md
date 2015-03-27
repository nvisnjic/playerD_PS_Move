Name: Niko Visnjic

IRC name: neemo

email contact: in melange (proposal is public)


Abstract:


Project Milestones:

Milestone I: Define the overall design of a high level platform agnostic
playerd API
that can be translated with ease to a multitude of controller schemes and input
devices. The API should expose only abstracted high level predefined actions
(jump, interact, change state from walk to run) to the game designer, while
leaving room for hacking the design if the default design does not fit his
control scheme.

Milestone II: Integrate low level support for webcam drivers in the playerd
service with the intent of accepting a camera video stream as an input vector.
The raw stream should be processed either by reusing existing Move APIs or
writing new processing algorithms using open source computer vision libraries.

Milestone III: The processed video and bluetooth streams will provide location,
orientation and button press information for the Move controller, as well as
changes in these , which will be used as low level events for building higher
level more complex events (eg. corner-to-corner cross motion indicating a
cancel action). These higher level events should constitute a body of standard,
often reused, actions as defined in the playerD API to facilitate ease of
controller setup and straightforward code migration.



Project Description:


