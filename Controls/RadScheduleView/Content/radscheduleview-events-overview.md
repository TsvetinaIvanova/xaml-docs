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
      
        All __event arguments__ of the before operation events (ending with -ing) derive from the __CancelRoutedEventArgs__ class. That's why all of the before operation events (ending with -__ing__) can be canceled by setting event arguments' __Cancel__ property to __True__.
      
        All event arguments of the after operation events (ending with -ed) derive directly from the __RadRoutedEventArgs__ class.
      

# Data Events

__RadScheduleView__ exposes the following events regarding the data manipulation:
        

* __AppointmentCreating__ - occurs when an appointment is going to be created. The __AppointmentCreating__ event handler receives two arguments:
              

* 
                  The sender argument contains the __RadScheduleView__. This argument is of type object, but can be cast to the __RadScheduleView__ type.
                

* 
                  An __AppointmentCreatingEventArgs__ object. Via the __AppointmentCreatingEventArgs__ you can access the following properties:
                  

* __Appointment__ - gets the newly created appointment. This property is read-only and you can use it to initialize the appointment.
                    

* __Cancel__ - set this boolean property to True, when you want to cancel the event.
                    

* __AppointmentCreated__ - occurs when the new appointment is created and the edit appointment dialog window is about to be shown. The __AppointmentCreated__ event handler receives two arguments:
              

* 
                  The __sender__ argument contains the __RadScheduleView__. This argument is of type object, but can be cast to the __RadScheduleView__ type.
                

* 
                  An __AppointmentCreatedEventArgs__ object. Via the AppointmentCreatedEventArgs you can access the following properties:
                  

* __CreatedAppointment__ - this is the newly created appointment, initialized with its default values. The property is read-only.
                    

* __AppointmentEditing__ - occurs when the appointment edit command is initialized and the edit appointment dialog window is about to be shown. The __AppointmentEditing__ event handler receives two arguments:
              

* 
                  The __sender__ argument contains the __RadRadScheduleView__. This argument is of type object, but can be cast to the __RadScheduleView__ type.
                

* 
                  An __AppointmentEditingEventArgs__ object. Via the __AppointmentEditingEventArgs__ you can access the following properties:
                  

* __Appointment__ - gets the appointment that is going to be edited. This property is read-only.
                    

* __Occurrence -__ gets the occurrence that is going to be edited. If the appointment is not recurrent, the value is null.
                    

* __IsDeleted -__ true when an occurrence of a recurrent appointment is about to be deleted, false in all other cases.
                    

* __Cancel -__ set this boolean property to __True__, when you want to cancel the event.
                    

* __AppointmentEdited__ - occurs when the appointment edit has finished and the appointment changes are applied. The __AppointmentEdited__ event handler receives two arguments:
              

* 
                  The __sender__ argument contains the __RadScheduleView__. This argument is of type object, but can be cast to the __RadScheduleView__ type.
                

* 
                  An __AppointmentEditedEventArgs__ object. Via the __AppointmentEditedEventArgs__ you can access the following properties:
                  

* __Appointment__ - gets the appointment that is edited. This property is read-only.
                    

* __AppointmentDeleting__ - occurs when the appointment is going to be removed from the data source. The __AppointmentDeleting__ event handler receives two arguments:
              

* 
                  The __sender__ argument contains the __RadScheduleView__. This argument is of type object, but can be cast to the __RadScheduleView__ type.
                

* 
                  An __AppointmentDeletingEventArgs __object. Via the __AppointmentDeletingEventArgs__ you can access the following properties:
                  

* __Appointment__ - gets the appointment that is going to be deleted. This property is read-only.
                    

* __Cancel -__ set this boolean property to __True__, when you want to cancel the event.
                    

* __AppointmentDeleted__ - occurs when the appointment has been removed from the data source. The __AppointmentDeleted__ event handler receives two arguments:
              

* 
                  The __sender__ argument contains the __RadScheduleView__. This argument is of type object, but can be cast to the __RadScheduleView__ type.
                

* 
                  An __AppointmentDeletedEventArgs__ object. Via the AppointmentDeletedEventArgs you can access the following properties:
                  

* __Appointment__ - gets the appointment that is deleted. This property is read-only.
                    

* __AppointmentSaving__ - occurs before the appointment is saved. The __AppointmentCreating__ event handler receives two arguments:
              

* 
                  The __sender__ argument contains the __RadScheduleView__. This argument is of type object, but can be cast to the __RadScheduleView__ type.
                

* 
                  An __AppointmentSavingEventArgs__ object. Via the __AppointmentSavingEventArgs__ you can access the following property:
                  

* __Appointment__ -  gets the appointment that is going to be saved. This property is read-only.
                    

* __Cancel__ - set this boolean property to __True__, when you want to cancel the event.
                    >
            When a new <legacyBold xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5">appointment</legacyBold> is <legacyBold xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5">created</legacyBold> the lifecycle of the raised events is:
          

* __AppointmentCreating__

* __AppointmentSaving__

* __AppointmentCreated__>
            When an existing <legacyBold xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5">appointment</legacyBold> is <legacyBold xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5">edited</legacyBold> the lifecycle of the raised events is:
          

* __AppointmentEditing__

* __AppointmentSaving__

* __AppointmentEdited__>
            When an existing <legacyBold xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5">appointment</legacyBold> is <legacyBold xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5">deleted</legacyBold> the lifecycle of the raised events is:
          

* __AppointmentDeleting__

* __AppointmentDeleted__>
            Note that when deleting an appointment, the <legacyBold xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5">AppointmentSaving</legacyBold> event is not raised.
          >
            When an existing <legacyBold xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5">occurrence</legacyBold> is <legacyBold xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5">deleted</legacyBold> the lifecycle of the raised events is:
          

* __AppointmentEditing__

* __AppointmentSaving__

* __AppointmentEdited__

# Other Events

* __AppointmentSelectionChanged__ - occurs when an appointments is selected.
          

* __ShowDialog__ - occurs when a ScheduleView dialog is about to be shown. The __ShowDialog__ event handler receives two arguments:
            

* 
                The __sender__ argument contains the __RadScheduleView__. This argument is of type object, but can be cast to the __RadScheduleView__ type.
              

* 
                An __ShowDialogEventArgs__ object. Via the __ShowDialogEventArgs__ you can access the following properties:
                

* __DialogViewModel__ -  gets the scheduler dialog. The property can be cast to the following types:
                    

* AppointmentDialogViewModel

* RecurrenceChoiceDialogViewModel

* RecurrenceDialogViewModel

* ConfirmDialogViewModel

* __Cancel__ - set this boolean property to __True__, when you want to cancel the event.
                  

* __DefaultDialogResult -__ set this property to __True__ when you want to simulate pressing OK in the corresponding window, or __False__ if you want to simulate pressing Cancel.
                  

* __VisibleRangeChanged__ - occurs when the view or the Start/End date is changed. The VisibleRangeChanged event handler receives two arguments:



* 
                The __sender__ argument contains the __RadScheduleView__. This argument is of type object, but can be cast to the __RadScheduleView__ type.
              

* 
                An __EventArgs__ object.
              



* 

__DialogClosing__ - occurs when a ScheduleView dialog is about to be closed. The DialogClosing event handler receives two arguments:

* 
                The __sender__ argument contains the __RadScheduleView__. This argument is of type object, but can be cast to the __RadScheduleView__ type.
              

* 
                An __CancelRoutedEventArgs__ object. After casting the __CancelRoutedEventArgs__ to __CloseDialogEventArgs__ you can access the following properties:
                

* __DialogViewModel__ -  gets the scheduler dialog. The property can be cast to the following types:
                    

* AppointmentDialogViewModel

* RecurrenceChoiceDialogViewModel

* RecurrenceDialogViewModel

* ConfirmDialogViewModel

* __Cancel__ - set this boolean property to __True__, when you want to cancel the event.
                  


 __C#__
    


	private void ScheduleView_DialogClosing(object sender, CancelRoutedEventArgs e)
	{
	    // cast to CloseDialogEventArgs
	    var eventArgs = e as CloseDialogEventArgs;
	
	    // you can get the DialogViewModel
	    var currentDialogViewModel = eventArgs.DialogViewModel;
	
	    // you can also cancel the event
	    eventArgs.Cancel = true;
	}



 * [Understanding Appointments]({{slug:understanding-appointments}})
