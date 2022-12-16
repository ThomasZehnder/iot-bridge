# iot-bridge
IoT Bridge MQTT to Rest

## Get from Git
    git clone https://github.com/ThomasZehnder/iot-bridge.git

## Install Node-Red and Libraries   
    npm update


##  Start Node-Red

    node ./node_modules/node-red/red.js ./flows/node-red-flow.json --userDir ./node-red-data/

or start batchfile

    run-node-red-bridge.bat

## RestServices
for assembly-001 (table thanks to https://www.tablesgenerator.com/markdown_tables)

| Service                                   | Method | Data sample         | Sample Response                                                                               | Description                                                                                                                            |
|-------------------------------------------|--------|---------------------|-----------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------|
| http://localhost:1880/assembly-001/state  | GET    | -                   | {"state":"start", "actionCounter": 3, "timeStamp": "xyz", "jobname":"heizung-016","led":true} |                                                                                                                                        |
| http://localhost:1880/assembly-001/ledoff | GET    | -                   |                                                                                               | does only switch off the led                                                                                                           |
| http://localhost:1880/assembly-001/ledon  | GET    | -                   |                                                                                               | does only switch on the led                                                                                                            |
|                                           |        |                     |                                                                                               |                                                                                                                                        |
| http://localhost:1880/assembly-001/form   | GET    | -                   | (HTML of form) #                                                                              | In the dark gray area the actual status is showed.  Based on GET-polling "./assembly-001/state                                         |
| http://localhost:1880/assembly-001/newJob | POST   | jobname=heizung-016 |                                                                                               | set new jobname and start process                                                                                                      |
| http://localhost:1880/ui                  | GET    | -                   | #                                                                                             | Get Test Interface for Bridge and Assembly-001  Every Buttonclick on Job will increment the action counter and adjusts the time stamp. |
