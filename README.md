This example connects to the broker aws using ssl transport and as a demonstration subscribes/unsubscribes and send a message on certain topic. (Please note that the public broker is maintained by the community so may not be always available, for details please see this disclaimer)

It uses ESP-MQTT library which implements mqtt client to connect to mqtt broker.

How to use example
Hardware Required
This example can be executed on any ESP32 board, the only required interface is WiFi and connection to internet.

Configure the project
Open the project sdkconfig
Configure Wi-Fi ssid and password.
Replace your ca root certificate mqtt_eclipseprojects_io.pem, device certificate and private key with esp32.cert.pem and esp32.private.key respectively.
Edit the mqtt_event_handler to subscribe and publish to the required topic.
in the MQTT_EVENT_DATA case you can find the sent data in event->data, compare it and take actions.
Build and Flash
Build the project and flash it to the board, then run monitor tool to view serial output:

idf.py -p PORT flash monitor
(To exit the serial monitor, type Ctrl-].)

See the Getting Started Guide for full steps to configure and use ESP-IDF to build projects.

Example Output
I (3714) event: sta ip: 192.168.0.139, mask: 255.255.255.0, gw: 192.168.0.2
I (3714) system_api: Base MAC address is not set, read default base MAC address from BLK0 of EFUSE
I (3964) MQTT_CLIENT: Sending MQTT CONNECT message, type: 1, id: 0000
I (4164) MQTTS_EXAMPLE: MQTT_EVENT_CONNECTED
I (4174) MQTTS_EXAMPLE: sent publish successful, msg_id=41464
I (4174) MQTTS_EXAMPLE: sent subscribe successful, msg_id=17886
I (4174) MQTTS_EXAMPLE: sent subscribe successful, msg_id=42970
I (4184) MQTTS_EXAMPLE: sent unsubscribe successful, msg_id=50241
I (4314) MQTTS_EXAMPLE: MQTT_EVENT_PUBLISHED, msg_id=41464
I (4484) MQTTS_EXAMPLE: MQTT_EVENT_SUBSCRIBED, msg_id=17886
I (4484) MQTTS_EXAMPLE: sent publish successful, msg_id=0
I (4684) MQTTS_EXAMPLE: MQTT_EVENT_SUBSCRIBED, msg_id=42970
I (4684) MQTTS_EXAMPLE: sent publish successful, msg_id=0
I (4884) MQTT_CLIENT: deliver_publish, message_length_read=19, message_length=19
I (4884) MQTTS_EXAMPLE: MQTT_EVENT_DATA
TOPIC=/topic/qos0
DATA=data
I (5194) MQTT_CLIENT: deliver_publish, message_length_read=19, message_length=19
I (5194) MQTTS_EXAMPLE: MQTT_EVENT_DATA
TOPIC=/topic/qos0
DATA=data
