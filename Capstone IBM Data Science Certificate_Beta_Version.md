Previsions of the Number Rescue Units to be Deployed by Traffic Acccidents.

Initially we are ask to built and develop a prediction model through ML which would allow to predict the severity of a road accident based on the weather conditions experienced locally.

The question put forward is very interesting but not of great use for the emergency services. In this sense that usually the severity of road accident also determined of the location, the hour day and if we are dealing with a vehicule, a bicycle or a pedestrian.
We will have to study the relation of location, hour of the day and weather conditons to predict possible accidents.

But just having the probality of accidents is not good enough since it's very difficult or impossible to determine in advance on an alert how much resources to mobilise for the intervention,being ambulance crews, specialist emergency teams (Physicist Traumatologue, Driver Paramedic, Paramedic Traumatologue (In Belgium : MUG or Delta's) and the number Operation Quarters and Chirugical teams, intensive care units to prepare and the number of beds to foreseen in the hospitals.

So we will have to study within an accident the relation between the kind of accident , the number of victims to be expected and the fort coming severity of injuries.
To built and develop our model we have the short hand registration of the Collisions in Seattle over the time span of a year.

We are also handed the MetaData of the various attibutes of the file to unable us to determinec which elements will be needed.

The needed elements:
OBJECTID:ESRI unique identifier, which can be used as index key 
ADDRTYPE: Collision address type: • Alley • Block • Intersection S
EVERITYCODE: A code that corresponds to the severity of the collision: 
    • 3—fatality 
    • 2b—serious injury 
    • 2—injury 
    • 1—prop damage 
    • 0—unknown
COLLISIONTYPE:Collision type 
PERSONCOUNT:The total number of people involved in the collision 
PEDCOUNT: The number of pedestrians involved in the collision. 
PEDCYLCOUNT: The number of bicycles involved in the collision. 
VEHCOUNT:The number of vehicles involved in the collision. 
INJURIES:The number of total injuries in the collision. 
SERIOUSINJURIES:The number of serious injuries in the collision. 
FATALITIES: The number of fatalities in the collision. 
WEATHER: A description of the weather conditions during the time of the collision. ROADCOND: The condition of the road during the collision.

Let us load the datafile to check if we can find back all needed attributes and how the incidents are incoded in the various fields.

Grazing through the datafile we noticed that some attribes are missing (INJURIES, SERIOUSINJURIES,FATALITIES)(lines 1 up to 7) 

By analizing the 'SEVERITYCODE' we notice that it has been limited to a minimum compared to  the Metadata description.(line 5)

This makes that we unforntunately have to reduce our scope of our initial project.

We will limit ourselves to the first part of our project being predicting the possibility of a road accident based on weather- , road conditions and location for Seattle.

The attributes we will be using:

OBJECTID:ESRI unique identifier, which can be used as index key
ADDRTYPE: Collision address type:
                        • Alley
                        • Block
                        • Intersection
SEVERITYCODE: A code that corresponds to the severity of the collision:
                                    • 3—fatality
                                    • 2b—serious injury
                                    • 2—injury
                                    • 1—prop damage
                                    • 0—unknown
LOCATION: Description of the general location of the collision.
WEATHER: A description of the weather conditions during the time of the collision.
ROADCOND: The condition of the road during the collision.


Lets us built a reduce dataframe which we will be using to built up our ML model.(lines 8 & 9)



We notice that for ROADCOND and WEATHER some data fields are missing and replaced by 'Unknown'.
Let's replace 'Unknown' by 'nan' which will allows us to discard the rows with 'Unknown'.( lines 11 to 16)

We set 'OBJECTID' as index field.(lines 16 - 17)
