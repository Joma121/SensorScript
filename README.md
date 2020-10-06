# SensorScript
Javascript plugin for RPGMaker MV. Allows events to detect player and each other using ranged and shaped detection areas.

-----------------------------------------------------------------------------
What does it do?
-----------------------------------------------------------------------------

This plugin activates a self switch when a player is in a certain proximity
of an event. It uses a notetag in the note of the event to set the proximity.

-----------------------------------------------------------------------------
Usage
-----------------------------------------------------------------------------

In the plugin parameters, set the self switch to be triggered on the event
when a player enters the range. Options are A, B, C, and D. Default is D.

Event tags provide 2 way functionality, they will turn off the switch when
the player leaves the event tag sensor zone.

Comment tags only provide 1 way switching, they will NOT turn off the Self
Switch when the player leaves the comment tag sensor zone.

The value of Blackout Region is the number of the region where you want the
sensor to be ineffectual.
When Blackout Variable is true, Blackout Region is the variable number whose
value contains the desired region number, anything other than a number set 
to the variable will most likely cause errors.

When Blackout Switch is true and the switch (set in Blackout Switch Number)
is off, the region established for Blackout Region will not alter the
funcitons of the sensor. When it is ON the established region will prevent
triggering the self switch.
 

-----------------------------------------------------------------------------
Notetags
-----------------------------------------------------------------------------

These notetags go in the note box for the event or in a comment on an event
page. All commas are optional.
    
Placing an exclamation mark "!" in front of any number in the following tags
will use the value of the variable with the ID of that number.
Ex: <Sensor: !3> will use the value of variable 3.

   <Sensor: x>

Where x is the number of tiles away that the selfswitch will be triggered.

   <SensorLV: x>

This makes it so that the selfswitch will only be triggered in a straight
line in the direction the event is facing.
Where x is the number of tiles away that the selfswitch will be triggered.

   <SensorCV: x>

This makes it so that the selfswitch will be triggered in a cone, the
direction the event is looking.
Where x is the number of tiles away the cone extends.

   <SensorRV: x, y>

This makes it so that the selfswitch will only be triggered in a 
rectangular line in the direction the event is facing.
Where x is the number of tiles to both sides of the event's looking 
direction, and y is the number of tiles away that the selfswitch will be 
triggered.
 
  <SensorCV: x L>
  <SensorRV: x y left>
  <SensorLV: x left up>

Sensor direction can be set using d, l, r, u, down, left, right, up. This is
not case sensitive. The direction set is in relation to the event the tag is
on. x and/or y are defined as established in above tags. This works for any 
sensor type, except the basic sensor.
You may put any combinations of directions in the tag. They may be separated
by spaces, but this is not required


-----------------------------------------------------------------------------
Plugin Commands
-----------------------------------------------------------------------------

Change your sensors on the fly! Use Plugin Commands to alter any aspect of 
sensors on your event. You could even ADD or REMOVE sensors to/from an event.

LSensor event property value
LSensor page property value

Okay, this is the Plugin command LSensor is required, as is either event or
page. If you don't have at least one property and value after these, why are
you using the plugin command??

You can have any number of properties and values in the Plugin command, but
only 1 event or page identifier.
The event identifier is equivilant to using/modifying the event note tag.
The page identifier is equivilant to using/modifying a comment tag.

LSensor off
LSensor event off
LSensor page off

On/Off commands turn all, event level, or comment level sensors on or off
respectively

Here is the list and limits of the properties:

Id       x
Type     b, cv, lv, rv, null
Range    x (any number)
RangeVar x (any number)
Width    x (any number)
WidthVar x (any number)
Dir      d, l, r, u, down, left, right, up
ThisDir  true

Id x
   The Id of the event to be affected, this is not needed if the change is 
   to happen on the current event. Do NOT include preceding 0's.
Type b, cv, lv, rv, null
  These are basic, coneview, lineview, rectangleview, the shorthand MUST be
   used. Width/WidthVar will be ignored on b, cv, and lv types. The command
   null will prevent the sensor from working.
Range x (any number)
    Know that if you set this and then RangeVar, Range will be overwritten.
RangeVar x (any number)
    This is the variable number whose value will be used for the sensor Range.
Width x (any number)
   Know that if you set this and then WidthVar, Width will be overwritten.
WidthVar x (any number)
   This is the variable number whose value will be used for the sensor Width.
Dir d, l, r, u, down, left, right, up
   Shorthand or full word can be used with Dir. This will set the direction
   that the sensor will use. Multiple directions can be used, a space is
   required between each direction.
ThisDir true
   This will set the sensor to use the direction of the event itself.
   Do NOT use both this and the Dir commands. This could easily lead to 
   errors.

## A note about page sensor changes. The changes will only occur for the 
   current page, and will not persist through page changes, even if the page
   that was changed comes back up. The plugin will use the original tag, if
   there was one, to make a sensor on page changes.

-----------------------------------------------------------------------------
Special Thanks to Gilles, Estriole and YOU!
-----------------------------------------------------------------------------
