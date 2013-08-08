---
title: Overview
meta_title: Overview
meta_description: description.
slug: overview
tags:overview
publish:True
---


This topic covers the specific events exposed by the __RadScheduleView__ control and its sub element __Appointment__. The events are first grouped by control and then by their general purpose.
      

__RadScheduleView__ provides a couple of useful events that can be used for customization purposes. Events can be used for: persisting appointment changes, creating new appointments or canceling various operations.
      

Event naming convention is the standard naming convention for data manipulation events similar to web and windows programming. Every operation has a before event (ending with -__ing__) and after event (ending with -__ed__). An example of these are __AppointmentDeleting__ and __AppointmentDeleted__ event of __RadScheduleView__.
      
    ![tip](tip.jpg)
    	
        All __event arguments__ of the before operation events (ending with -ing) derive from the __CancelRoutedEventArgs__ class. That's why all of the before operation events (ending with -__ing__) can be canceled by setting event arguments' __Cancel__ property to __True__.
      
    ![tip](tip.jpg)
    	
        All event arguments of the after operation events (ending with -ed) derive directly from the __RadRoutedEventArgs__ class.
      

# Data Events

__RadScheduleView__ exposes the following events regarding the data manipulation:
        

* AppointmentCreating

* AppointmentCreated

* AppointmentEditing

* AppointmentEdited

* AppointmentDeleting

* AppointmentDeleted

* AppointmentSaving
    ![tip](tip.jpg)
    	

When a new __appointment__ is __created__ the lifecycle of the raised events is:
          

* AppointmentCreating

* AppointmentSaving

* AppointmentCreated
    ![tip](tip.jpg)
    	

When an existing __appointment__ is __edited__ the lifecycle of the raised events is:
          

* AppointmentEditing

* AppointmentSaving

* AppointmentEdited
    ![tip](tip.jpg)
    	

When an existing __appointment__ is __deleted__ the lifecycle of the raised events is:
          

* AppointmentDeleting

* AppointmentDeleted

Note that when deleting an appointment, the __AppointmentSaving__ event is not raised.
          
    ![tip](tip.jpg)
    	

When an existing __occurrence__ is __deleted__ the lifecycle of the raised events is:
          

* AppointmentEditing

* AppointmentSaving

* AppointmentEdited

# Other Events

* AppointmentSelectionChanged

* ShowDialog

* VisibleRangeChanged

* DialogClosing - occurs when a ScheduleView dialog is about to be closed. The DialogClosing event handler receives two arguments:


 __C#__
    

```C#


private void ScheduleView_DialogClosing(object sender, CancelRoutedEventArgs e)
{
    // cast to CloseDialogEventArgs
    var eventArgs = e as CloseDialogEventArgs;

    // you can get the DialogViewModel
    var currentDialogViewModel = eventArgs.DialogViewModel;

    // you can also cancel the event
    eventArgs.Cancel = true;
}

```

[Understanding Appointments]({{slug:understanding-appointments}})
