Communication
=============
The Particle cloud is great, but be repectful with API requests, getting the temperature every second from 10 devices is currently possible, but requesting the temperature every 6 minutes will give you more than enough detail for most everything.

`Particle.variable <https://docs.particle.io/reference/device-os/firmware/argon/#particle-variable->`_
------------------------------------------------------------------------------------------------------
Data that changes infrequently: temperature, humidity, air quality.

When loading the webpage you want everything, all data from every device. A `JSON <https://www.json.org/json-en.html>`_ (JavaScript Object Notation) string can contain all device data limited to containing 622 bytes. "There is an API rate limit of approximately 10 calls per second to api.particle.io from each public IP address." `1 <https://docs.particle.io/reference/device-cloud/api/#api-rate-limits>`_

TODO: example of a string converted to JSON

`Particle.publish <https://docs.particle.io/reference/device-os/firmware/argon/#particle-publish->`_
----------------------------------------------------------------------------------------------------
Events that you want to be alerted of: motion.

When sensing motion you want to be notified as soon as possible. "Currently, a device can publish at rate of about 1 event/sec, with bursts of up to 4 allowed in 1 second. Back to back burst of 4 messages will take 4 seconds to recover." `2 <https://docs.particle.io/reference/device-os/firmware/argon/#particle-publish->`_ If this is overused it is no longer an alert.

`Particle.function <https://docs.particle.io/reference/device-os/firmware/argon/#particle-function->`_
------------------------------------------------------------------------------------------------------
Controlling a Particle device by sending a command: light on/off/color, buzzer.

`Particle.subscribe <https://docs.particle.io/reference/device-os/firmware/argon/#particle-subscribe->`_
--------------------------------------------------------------------------------------------------------
Device to device communication: device publishes motion -> another device turns on a light.
