

This article describes how you can create a custom SpecialSlot, add custom properties to it and bind the properties in the Slot template.
    ![note](note.jpg)
      

Please check here for more details about SpecialSlots.

# 

Let's for example have the following RadScheduleView grouped by "Calendar" ResourceType:

We will define a custom Slot class, create a collection of custom Slot objects which then will be set to the SpecialSlotsSource property.Also in this tutorial we will crete custom ScheduleViewStyleSelector class and define the needed Styles.

* First, create a class which inherits Telerik.Windows.Controls.ScheduleView.Slot class:

* Then you should create the collection of BreakSlot objects and set their additional properties:

* The next step is to create the ScheduleViewStyleSelector class:

* and to define the Style:

* Finally, bind them to SpecialSlotsSource and SpecialSlotsStyleSelector properties:

Here is the result:![alt text](images/radscheduleview_custom_slots.png)
  
