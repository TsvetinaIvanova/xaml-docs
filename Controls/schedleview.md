This article describes how you can create a custom SpecialSlot, add custom properties to it and bind the properties in the Slot template.

    
    
    ![note](note.jpg)Please check here for more details about SpecialSlots.

   #Let's for example have the following RadScheduleView grouped by "Calendar" ResourceType:
We will define a custom Slot class, create a collection of custom Slot objects which then will be set to the SpecialSlotsSource property.Also in this tutorial we will crete custom ScheduleViewStyleSelector class and define the needed Styles.

  * First, create a class which inherits 
   __Telerik.Windows.Controls.ScheduleView.Slot__
   class:

    
    
    ![note](note.jpg)Note how 
   __Copy__
   and 
   __CopyFrom__
   methods in the custom slot class are overriden!

  * Then you should create the collection of 
   __BreakSlot__
   objects and set their additional properties:

  * The next step is to create the 
   __ScheduleViewStyleSelector__
   class:

  * and to define the Style:

  * Finally, bind them to 
   __SpecialSlotsSource__
   and 
   __SpecialSlotsStyleSelector__
   properties:
Here is the result:

    ![alt text](images/radscheduleview_custom_slots.png)
  
