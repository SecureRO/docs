#### i08072024
- Captures whether the screen is being captured or shared
- Fixes network url slashes

#### i03072024
- Reworks the general way events are collected and reported
- Makes the `muid` be the first session to arrive
- Makes `smuid` the device identifier with the generation date at the beginnning

#### i23052024
- Fixes events storage
- Fixes bom sending with the correct csid

#### i22052024.2
- Exposing sdk version to the consumer

#### i22052024.1
- Changes value ordering of touch event storage/reporting
- Collecting additional device info controlled by configs

#### i22052024
- Implements better motion, orientation collection

#### i21052024
- Fixes location permission flag in the permission collector

#### i17052024.1
- Respects config on whether to explicitly ask for location when collecting data

#### i17052024
- Additional logging and checks for sending context events
- Reads ca51 config for making sure the right time and repetitions are used for camera image capture

#### 16052024
- Adding support for configuration csinc2
- Implements remote log reporting when enabled via configuration

#### 05052024
- Changes to configuration variable names
- Improvements to the timer creation/update logic
- Sending `csid` with the captured image for face recognition improvements

