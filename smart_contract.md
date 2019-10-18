Participants

There are three types of participants here: exporters, importers, and shippers. 
Following are the participants of the network along with their properties.

Exporter

Exporter ID: This is the unique ID of the exporter, which is 
used to track the exporter details.

Datatype: String

Email of the exporter: This is the unique email of the exporter, which is 
used to track the exporter details.

Datatype: String

Address of the exporter: This is the address for the exporter, which will be 
used to track the location.

Datatype: String

Account balance: This is the account balance of the exporter.

Datatype: Double



Shipper

Shipper ID: This is the unique ID of the shipper, which is used 
to track the shipper details.

Datatype: String

Email of the shipper: This is the unique email of the shipper, which is 
used to track the shipper details.

Datatype: String

Address of the shipper: This is the address for the shipper, which is 
used to track the location.

Datatype: String

Account balance: This is the account balance of the shipper.

Datatype: Double



Importer:

Importer ID: This is the unique ID of the importer, which is used 
to track the importer details.

Datatype: String

Email of the importer: This is the unique email of the importer, which is used 
to track the importer details.

Datatype: String

Address of the importer: This is the address for the importer, which is 
used to track the location.

Datatype: String

Account balance: This is the account balance of the importer.

Datatype: Double



Lists
Before defining assets, create the following lists for maintaining the type of asset, 
the status of the asset and compass direction for GPS.

 

Asset type

The following values can be taken as the asset type; students are free to add more if required. 
ie Medicine , Fuel , Trucks , Wires, Tables, Laptops, Chairs

Shipment status

It maintains three types of status for the project:
ie Created , In transit , Arrived

Compass direction

It maintains the compass direction as a list to map GPS locations:
ie N, S, E, W

Assets
The system has two types of assets in the case study: one to maintain the contracts 
and another to maintain the shipments. The following are the assets along with their 
properties:

 

Shipment

Shipment ID: This is a unique ID for each shipment processed in the business network. 
It acts as the primary key and is used to track shipment details.

Datatype: String

Asset type: This is the type of the product or asset that is being shipped between 
the exporter and the importer.

Datatype: Asset type

Shipment status: This is the status of the shipment


Datatype: Shipment status

Unit count: This is the total number of units of the assets that are shipped.

Datatype: Long

Contract: This is the contract against which the shipment is processed.

Datatype: Contract

Temperature readings: This is an array of transactions that record the temperature of 
the asset at various intervals.

Datatype: Array of temperature reading transactions or function calls

Acceleration readings: This is an array of transactions that record the acceleration of 
the asset at various intervals.

Datatype: Array of acceleration reading transactions or function calls

GPS readings: This is an array of transactions that record the GPS coordinates of 
the asset at various intervals.

Datatype: Array of GPS reading transactions or function calls

Contract

Contract ID: This is a unique ID for each contract initiated in the business network. 
It acts as the primary key and is used to track the contract details.

Datatype: String

Exporter: This refers to the participant who is exporting the goods.

Datatype: Exporter

Importer: This refers to the participant who is importing the goods.

Datatype: Importer

Shipper: This refers to the participant who is shipping the goods.

Datatype: Shipper

Arrival datetime: This is the date and time of the arrival of the shipment; 
it is updated once the shipment is delivered.

Datatype: Datetime

Unit price: This is the price of the asset agreed upon by the parties involved.

Datatype: Double

Minimum temperature: This is the minimum temperature allowed for the asset or product.

Datatype: Double

Maximum temperature: This is the maximum temperature allowed for the asset or product.

Datatype: Double

Minimum penalty factor: This is the factor by which the total amount to be paid is 
multiplied if the temperature goes below the desired range.

Datatype: Double

Maximum penalty factor: This is the factor by which the total amount to be paid is multiplied if 
the temperature goes above the desired range.

Datatype: Double

Maximum acceleration: This is the maximum acceleration allowed for the asset or product.

Datatype: Double


Events
There are three events in the system, namely, temperature threshold, acceleration threshold 
and shipment in a port. The properties of all the events are defined as follows:

 
Temperature threshold event: 
This event is triggered by the 'Temperature Reading' transaction when the temperature
of the shipment recorded at a particular timing exceeds the decided range.

Temperature: This is the value of the temperature on which this event is triggered.

Datatype: Double

Message: This is an additional message detailing the event.

Datatype: String

Latitude: This is the location of latitude when the temperature is recorded for the asset.

Datatype: String

Longitude: This is the location of longitude when the temperature is recorded for the asset.

Datatype: String

Reading time: This is the time value when the temperature is recorded for the asset.

Datatype: String

Shipment: This refers to the shipment asset described above.

Datatype: Shipment

 

Acceleration threshold event: 
This event is triggered by the 'Acceleration Reading' transaction when
the acceleration of the shipment recorded at a particular timing exceeds the decided range.

Acceleration X: This is the value of the x parameter of acceleration on which this event is triggered.

Datatype: Double

Acceleration Y: This is the value of the y parameter of acceleration on which this event is triggered.

Datatype: Double

Acceleration Z: This is the value of the z parameter of acceleration on which this event is triggered.

Datatype: Double

Message: This is an additional message detailing the event.

Datatype: String

Latitude: This is the location of latitude when the acceleration is recorded for the asset.

Datatype: String

Longitude: This is the location of longitude when the acceleration is recorded for the asset.

Datatype: String

Reading time: This is the time value when the acceleration is recorded for the asset.

Datatype: String

Shipment: This refers to the shipment asset described above.

Datatype: Shipment

 

Shipment in a port event: This event is triggered by the 'GPS Reading' transaction 
when the shipment reaches a particular location.

Message: This is an additional message detailing the event.

Datatype: String

Shipment: This refers to the shipment asset described above.

Datatype: Shipment


Transactions
There are four transactions in the system. Out of the four, 
three are related to and are part of the shipment asset. 
Thus an abstract shipment transaction is required for the 
three transactions - Acceleration Reading, Temperature Reading, and GPS reading. 
Following are the details of all the transactions.

 

(Abstract transaction) shipment transaction:

Shipment: This refers to the shipment asset described above.

Datatype: Shipment

Acceleration reading extended from a shipment transaction: By invoking this transaction, 
the shipper will update the acceleration reading for the shipment.

 

Structure: The structure of the transaction will be as follows:

Acceleration X: This is the x-coordinate of the recorded acceleration for the asset.

Datatype: Double

Acceleration Y: This is the y-coordinate of the recorded acceleration for the asset.

Datatype: Double

Acceleration Z: This is the z-coordinate of the recorded acceleration for the asset.

Datatype: Double

Latitude: This is the location of latitude when the acceleration is recorded for the asset.

Datatype: String

Longitude: This is the location of longitude when the acceleration is recorded for the asset.

Datatype: String

Reading time (optional): This is the time value when the acceleration is recorded for the asset.

Datatype: String

Transaction Flow: The transaction flow is as follows:

Fetch the contract and the shipment for which this transaction is being called upon.

Get the acceleration data that is input in the transaction and map it to the acceleration threshold in the contract.

Trigger the 'Acceleration Threshold' event if the acceleration data is not in the required range.

Add the acceleration data to the acceleration array with the shipment.

Save the shipment asset registry with the newly added acceleration.

 

Temperature reading extended from a shipment transaction:  

By invoking this transaction, the shipper will update the temperature reading for the shipment.

 

Structure: The structure of the transaction will be as follows:

Celsius: This is the temperature recorded for the asset.

Datatype: Double

Latitude: This is the location of latitude when the temperature is recorded for the asset.

Datatype: String

Longitude: This is the location of longitude when the temperature is recorded for the asset.

Datatype: String

Reading Time (optional): This is the time value when the temperature is recorded for the asset.

Datatype: String

Transaction Flow: The transaction flow is as follows:

Fetch the contract and shipment for which this transaction is being called upon.

Get the temperature data that is input in the transaction and map it to the temperature 
threshold in the contract.

Trigger the 'Temperature Threshold' event if the temperature data is not in the required range.

Add the temperature data to the temperature array with the shipment.

Save the shipment asset registry with the newly added temperature.

 

GPS reading extended from a shipment transaction: By invoking this transaction, the shipper will 
update the GPS reading for the shipment.

 

Structure: The structure of the transaction will be as follows:

Latitude: This is the location of latitude when the GPS data is recorded for the asset.

Datatype: String

Latitude direction: This is the direction of latitude when the GPS data is recorded for the asset.

Datatype: Compass direction

Longitude: This is the location of longitude when the GPS data is recorded for the asset.

Datatype: String

Longitude direction: This is the direction of longitude when the GPS data is recorded for the asset.

Datatype: Compass direction

Reading time (optional): This is the time value when the GPS data is recorded for the asset.

Datatype: String

Reading date (optional): This is the date value when the GPS data is recorded for the asset.

Datatype: String

Transaction Flow: The transaction flow is as follows:

Fetch the contract and the shipment for which this transaction is being called upon.

Get the GPS data that is input in the transaction.

Trigger the 'Shipment In a Port' event if the GPS data matches the location of the importer.

Add the GPS data to the GPS array with the shipment.

Save the shipment asset registry with the newly added location details.

 

Shipment received: 
This transaction will notify whether the shipment has been successfully received 
by the importer. It will also run the calculations for updating the balances of the exporter,
the importer, and the shipper.

 

Structure: The structure of the transaction will be as follows:

Shipment: This refers to the shipment asset described above.

Datatype: Shipment