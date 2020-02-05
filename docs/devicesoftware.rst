Device code
===========

Example of simple sketch

.. code-block:: c

    /***********************
    * libraries and definitions
    ***********************/

    // Fire and forget publishing
    #include <PublishQueueAsyncRK.h>

    /* system configuration */
    STARTUP(WiFi.selectAntenna(ANT_AUTO));                  // continually switches between antennas
    STARTUP(System.enableFeature(FEATURE_RETAINED_MEMORY));
    SYSTEM_THREAD(ENABLED);

    /***********************
    * variables and objects
    ***********************/

    retained uint8_t publishQueueRetainedBuffer[512];
    PublishQueueAsync publishQueue(publishQueueRetainedBuffer, sizeof(publishQueueRetainedBuffer));

    char json_room[622];                                    // json with all variables
    char json_status[150];                                  // json with device status readings

    uint32_t lastTime = 0;								    // to create a low priority timer
    uint32_t now = 0;
    uint16_t seconds = 0;

    void setup() {
        Particle.variable("RoomData", json_room);
        publishQueue.setup();
    }

    void loop() {
        now = millis();
        if ((now - lastTime) >= 1000) {
            lastTime = now;

            if( seconds % 2 == 0 ) {
            };

            if( seconds % 5 == 0 ) {
            };

            if( seconds % 10 == 0 ) {
            };

            if( seconds % 30 == 0 ) {
                snprintf( json_status, 150, "{"             // update device status
                    "\"wis\"      :%.0f,"
                    "\"wiq\"      :%.0f,"
                    "\"mem\"      :%.3f}",
                    WiFi.RSSI().getStrength(),
                    WiFi.RSSI().getQuality(),
                    System.freeMemory() / 83200.0 * 100
                );
            };

            if( seconds % 60 == 0 ) {
            };

            if( seconds % 300 == 0 ) {
            };

            seconds++;
            
            if( seconds > 300 ) {
                seconds = 1;
            };

            snprintf( json_room, 622, "{"                   // update Particle.variable conents
                "\"dev\"    :%s""}",
                json_status
            );
        };
    };

    /***********************
    * functions to read sensors
    ***********************/
