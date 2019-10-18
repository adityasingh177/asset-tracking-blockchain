Smart contract

Smart contract is the heart of Asset Tracking solution. 
It will provide the logic to the system for tracking the assets. 

There are three participants - Importer, Exporter, and Shipper. 
There are two assets, namely, Contract and Shipment. 
There are four transactions -  Acceleration Reading, Temperature Reading, GPS Reading, 
and Shipment Received along with an Abstract Shipment transaction.

The Asset Tracking system also consists of 
three events- Temperature Threshold, Acceleration Threshold and Shipment in a port. 



There are three participants-

Importer- It is representative of a company who initiates the smart contract for the shipment of assets.
Exporter- It is representative of another company who ships the assets across to the Importer.
Shipper- It is an identity who ships the assets from the provider (Exporter) to the orderer (Importer). 
The shipper is responsible for tracking the assets using GPS, acceleration, and temperature 
throughout the course of the shipment. This tracking data will be stored with the shipped assets so 
that the participants can have visibility on the assets.


Let's imagine two organizations in a blockchain. One organization XYZ, which is a book store, 
has to order a certain number of books from another organization ABC, who is a publisher.  
Now before any transaction happens between the two organizations some kind of contract should be in place. 
This contract should contain values such as details of the orderer (Importer), details of the shipper, 
details of the provider (Exporter) along with some other details such as arrival date and time of the asset 
(in this case books), etc. Once such a contract is in place, there is also a need to maintain the details 
of the asset (in this case books) being shipped such as the asset type, the count of the asset (books), 
the status of the asset along with the contract. When the contract and the details of the asset (here books) 
to be shipped are recorded on the blockchain, a transaction can take place between both the organizations.


Thus in the Asset Tracking System, the asset 'Contract' stores the details of the importer, exporter, and 
shipper along with other details. The asset 'Shipment' stores the details of the asset being shipped.




The objective of invoking the transaction. For example-

Acceleration Reading Transaction- It is initiated by the Shipper of the network to update the acceleration reading of the shipment.
Temperature Reading Transaction- It is initiated by the Shipper of the network to update the temperature reading of the shipment.
GPS Reading Transaction- It is initiated by the Shipper of the network to update the location of the shipment.
Shipment Received Transaction- It is initiated by the Importer of the network to update the final status of the shipment.



Finally, are the events of the system.

Events are the triggers that are used to indicate if something (such as a transaction) has happened in the network. 
Transactions like 'Temperature Reading' are associated with its corresponding event. 
These events are triggered by the transactions if a triggering condition is satisfied. 
For example, in Asset Tracking system, we need to make sure that the temperature of the Asset varies between 
a stipulated range. The temperature of the asset for a particular time duration is recorded by the Shipper.
Now, if the temperature for the time duration exceeds the decided Max and Min range, the event linked 
to the 'Temperature Reading' transaction, which is 'Temperature Threshold' event, 
can be called to trigger a set of actions like notifying the shipper of the exceeded temperature range.


Similarly, the 'Acceleration Reading' event is associated with the 'Acceleration Threshold' event 
which gets triggered when the acceleration of the asset recorded by the shipper exceeds the decided 
max and min range.

 

The 'GPS Reading' transaction is associated with the 'Shipment In a Port' event, which is triggered when 
the shipment arrives at a certain location. Suppose the shipment has to be shipped from a location A to a location E 
via locations B, C and D. Thus the shipper will be invoking the 'GPS Reading' transaction, 
which in turn will invoke the 'Shipment In a Port' event when the shipment will reach the intermediate locations.


