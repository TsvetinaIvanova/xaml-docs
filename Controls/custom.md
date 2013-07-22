A very common scenario when using RadScheduleView is the usage of custom appointments. When you create a **Custom Appointment** class you gain the ability to append additional properties to the base Appointment class, to add them to your custom AppointmentItem and optionally to its ToolTip, display them in the EditAppointment dialog while supporting the cancelation of editing. 

In this article we will explore the process of using custom appointments in RadScheduleView. We will go through the following steps:


[Create a custom appointment class and populate the RadScheduleView control with custom appointments](#Creating-a-Custom-Appointment-class)

[Modify the EditAppointment dialog to display the custom data of the newly created custom appointment class](#Creating-a-Custom-Appointment-dialog)

[Customize the AppointmentItem and its ToolTip to display the new data](#Changing-the-Style-of-the-AppointmentItem)

## Creating a Custom Appointment class
To create a custom appointment class you can start off with either of the following approaches : you can implement the **IAppointment**  interface or you can inherit from one of the classes that already implement this interface – AppointmentBase (the base implementation of the interface) or Appointment (an extended implementation). It is very important to provide your own implementations for the **Copy** and **CopyFrom** methods as they are used intensively in the editing process of the ScheduleView control. If you choose to implement the interface, the Copy and CopyFrom methods will be automatically implemented for you, but if you take the second approach and inherit from one of the base classes, you should keep this in mind. 

Let's create a simple task tracking system. For our Custom Appointment class we will inherit from Appointment. Out tracking system will need to show an additional field for the task progress – an indication of whether the task has finished or not. In order to enable editing in transactions of the new property we need to use the Storage method of the AppointmentBase class to access the instance which owns the fields. We will name our custom appointment class Task. Here is the creation of the Custom Appointment class: 

## Creating a custom Appointment Dialog
## Changing the Style of the AppointmentItem
