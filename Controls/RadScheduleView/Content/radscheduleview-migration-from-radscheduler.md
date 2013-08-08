---
title: Migration from RadScheduler
meta_title: Migration from RadScheduler
meta_description: description.
slug: migration-from-radscheduler
tags:migration,from,radscheduler
publish:True
---


The following article describes the migration process from the RadScheduler to the RadScheduleView control.

# 

RadScheduler properties

Corresponding way for ScheduleView__IsReadOnly__IsReadOnly property – you have to set it to SpecialSlotsSource collection. If you want to set ReadOnly for the whole ScheduleView (not specific days) just make the special slot covers all days.__Appointments____AppointmentsSource__

__AppointmentTemplate__/
              

__AppointmentTemplateSelector__

__AppointmentItemContentTemplate__/__AppointmentItemContentTemplateSelector__

__AppointmentStyleSelector__ -> [http://demos.telerik.com/wpf?ScheduleView/CustomStyles/AppointmentStyle](http://demos.telerik.com/wpf?ScheduleView/CustomStyles/AppointmentStyle)__AllDayAreaHeight__
              Not supported with the current version. All-day appointments are now displayed as regular appointments and they are stretched across the timeruler for the whole day.
            __DisplayEmptyGroup__

You could use the __ResourceGroupDescription.ShowNullGroup__ property. For example:
              


 __XAML__
    	


<telerik:RadScheduleView.GroupDescriptionsSource>
    <telerik:GroupDescriptionCollection>
     <telerik:ResourceGroupDescription ResourceType="Room" ShowNullGroup="True" />
     <telerik:ResourceGroupDescription ResourceType="User"  />
    </telerik:GroupDescriptionCollection>
</telerik:RadScheduleView.GroupDescriptionsSource>

__TimeRulerStyle____TimeRulerItemStyleSelector__, __TimeRulerItemTemplateSelector__ (to make it work the __TimeRulerItemTemplateSelector__ and __TimeRulerItemTemplate__ must be set to __{x:Null}__)
              

[http://demos.telerik.com/wpf/?ScheduleView/CustomStyles/TimeRulerStyle](http://demos.telerik.com/wpf/?ScheduleView/CustomStyles/TimeRulerStyle)[http://demos.telerik.com/silverlight/#ScheduleView/CustomStyles/TimeRulerStyle](http://demos.telerik.com/silverlight/#ScheduleView/CustomStyles/TimeRulerStyle)__EditAppointmentStyle____EditAppointmentDialogStyle____IsBackAndForwardNavigationEnabled____IsViewModeNavigationEnabled____NavigationHeaderVisibility____ViewMode____ActiveViewDefinition__, __ActiveViewDefinitionIndex____GroupBy__

Add __GroupDescription__ and to the __GroupDescriptionSource__. For example:
              


 __XAML__
    	


<telerik:RadScheduleView.GroupDescriptionsSource>
<telerik:GroupDescriptionCollection>     <telerik:ResourceGroupDescription ResourceType="Category" />
<telerik:ResourceGroupDescription ResourceType="Level" />
</telerik:GroupDescriptionCollection>
</telerik:RadScheduleView.GroupDescriptionsSource>



[http://demos.telerik.com/wpf/?ScheduleView/Grouping/Basics](http://demos.telerik.com/wpf/?ScheduleView/Grouping/Basics)__View definitions__ and properties
            


 __XAML__
    	


<telerik:RadScheduleView.ViewDefinitions>
 <telerik:DayViewDefinition VisibleDays="" FirstDayOfWeek=" " LargeChangeInterval="" MinorTickLength="" MinTimeRulerExtent="" Orientation=" " />
 <telerik:WeekViewDefinition/>
 <telerik:MonthViewDefinition/>
 <telerik:TimelineViewDefinition/>
</telerik:RadScheduleView.ViewDefinitions>

__TimeSlotTemplateSelector____SpecialSlotStyleSelector__, __SpecialSlotsSource__

Please refer to [Special and ReadOnly slots]({{slug:special-and-readonly-slots}}).
              __AppointmentAdded__, __AppointmentAdding__ events
            
              Not supported. There is new event mechanism for the RadScheduleView control. Please, refer to [Overview]({{slug:overview}}) article.
            __ActiveViewDefinitionChanged__, __SelectedViewStartDateChanged__ events
            __VisibleRangeChanged__ event, __VisibleRangeChangedCommand__ and __VisibleRangeChangedCommandParameter____AvailableViewModes__

Depends on which __ViewDefinitions__ are defined:
              


 __XAML__
    	


<telerik:RadScheduleView.ViewDefinitions>
 <telerik:DayViewDefinition  />
 <telerik:WeekViewDefinition />
 …
 <telerik:TimelineViewDefinition />
</telerik:RadScheduleView.ViewDefinitions>

__Culture__There is no such property. Use LocalizationManager.DefaultCulture instead.__TimeFormatString__, __DayHeaderFormat__, __MonthViewDayHeaderDayFormat__, __MonthViewDayHeaderMonthFormat__, __TimelineHeaderFormat____TimerulerMajorTickStringFormat__, __GroupHeaderDateStringFormat__, __TimerulerMinorTickStringFormat__ properties on the view definitions
            __ResourceStyleMapping____GroupHeaderStyleSelector__ and __GroupHeaderContentTemplateSelector____Edit____Appointment__ using code
              



Using the __BeginEdit()__ method of the __RadScheduleView__, which returns whether or not the appointment or the occurrence can be edited. If __BeginEdit()__ is True the appointment or occurrence can be edited. Call __Commit()__ to commit the changes:
              


 __C#__
    	


if (this.radScheduleView.BeginEdit(appointment))
{   
    appointment.Subject = "New Subject";
    this.radScheduleView.Commit();
}




 __VB.NET__
    	


If Me.radScheduleView.BeginEdit(appointment) Then
 appointment.Subject = "New Subject"
 Me.radScheduleView.Commit()
End If

__Delete Appointment__ using code:
            

Using the Remove() method of the RadScheduleView(), which returns whether or not the appointment or occurrence can be removed.


 __C#__
    	


this.radScheduleView.Remove(appointment);




 __VB.NET__
    	


Me.radScheduleView.Remove(appointment)





__TimeRuler__ configuration:
              

- MaxTimeRulerExtent/ MinTimeRulerExtent - gets or sets the extend (the size) of the TimeRuler – width/height depending on the orientation of the view in pxl.
                - MinorTickLength – gets or sets the minimum time between the TimeSlots
                - MajorTickLength – sets the maximum time between the TimeSlots (usually the hours)
              __TimeSlotItemTemplateSelector__

__SpecialSlotStyleSelector:____-__ Create NonWorkingSlots and WorkingSlots classes, which inherit the Slot. To be used in the ViewModel, which will be set as a source of the SpecialSlotSource and  in which will be defined the conditions for the special slots.
              - Create StyleSelector class which inherits ScheduleViewStyleSelector
              - Define the XAML for the styles

              

__Horizontal grouping__:
              - Set the Orientation property to Horizontal of the ViewDefinition in order to achieve horizontal grouping.
            __Change size of Appointment__:
              - MinAppointmentHeight – gets or sets the minimum heights of the Appointments in RadScheduleView when the orientation of the active ViewDefinition is set to Horizontal.
              - MinAppointmentWidth - gets or sets the minimum width of the Appointments in RadScheduleView when the orientation of the active ViewDefinition is set to Vertical.
            __SelectedAppointment__ property – Gets or sets the selected appointment. This is the first appointment from __SelectedAppointments__. When set it removes all other selected appointments.
            __SelectedTimeSlot____SelectedSlot__. There is a difference between RadScheduler.SelectedTimeSlot and RadScheduleView.SelectedSlot properties. Please, note that the second one cannot be null. Also, the SelectedSlot is not responsible for the navigation throughout the ScheduleView's views, but the SelectedTimeSLot is.
            

 

RadScheduler events

RadScheduleView events

__AppointmentCreating__ – occurs when an appointment is going to be created. Via the __AppointmentCreatingEventArgs__ the following properties can be accessed:
              

* NewAppointment

* Cancel

__AppointmentCreating__ – occurs when an appointment is going to be created. Via the AppointmentCreatingEventArgs you can access the following properties:
              

* Appointment

* Cancel

__AppointmentCreated__ - occurs when the new appointment is created and the edit appointment dialog window is about to be shown.
              

Via the __AppointmentCreatedEventArgs__ you can access the following properties:
              

* CreatedAppointment

__AppointmentCreated__ - occurs when the new appointment is created and the edit appointment dialog window is about to be shown.
              

Via the __AppointmentCreatedEventArgs__ you can access the following properties:
              

* CreatedAppointment__AppointmentAdding__, __AppointmentAdded__Not supported.

__AppointmentEditing__ - occurs when the appointment edit command is initialized and the edit appointment dialog window is about to be shown.
              

Via the __AppointmentEditingEventArgs__ you can access the following properties:
              

* Appointment

* AppointmentEditAction

* ExceptionAction

* ExceptionOccurrence

* Cancel

__AppointmentEditing__ - occurs when the appointment edit command is initialized and the edit appointment dialog window is about to be shown.
              

Via the __AppointmentEditingEventArgs__ you can access the following properties:
              

* Appointment

* Occurrence

* Cancel

__AppointmentDeleting__ - occurs when the appointment is going to be removed from the data source.
              

Via the __AppointmentDeletingEventArgs__ you can access the following properties:
              

* Appointment

* Cancel

__AppointmentDeleting__ - occurs when the appointment is going to be removed from the data source.
              

Via the AppointmentDeletedEventArgs you can access the following properties:

* 
                  Appointment - gets the appointment that is deleted. This property is read-only.
                

__AppointmentSaving__ - occurs before the appointment is saved.
              

Via the __AppointmentSavingEventArgs__ you can access the following property:
                • __Appointment__ - the appointment that is going to be saved. The property is read-only.
              

__AppointmentSaving__ - occurs before the appointment is saved.
              

Via the __AppointmentSavingEventArgs__ you can access the following property:
              

* 
                  Appointment - gets the appointment that is going to be saved. This property is read-only.
                

* 
                  Cancel - set this boolean property to True, when you want to cancel the event.
                

* ActiveViewDefinitionChanged

* SchedulerPerformedGrouping

* SelectedViewStartDateChanged

* AppointmentSelectionChanged

* VisibleRangeChanged

* ShowDialog

 

Lifecycle of appointment in RadScheduler

Lifecycle of appointment in RadScheduleView

__New Appointment:__



* AppointmentCreating 

* 
                    AppointmentCreated
                  

* 
                    AppointmentSaving
                  

* 
                    AppointmentAdding
                  

* 
                    AppointmentAdded
                  

__New Appointment:__



* AppointmentCreating

* AppointmentSaving

* AppointmentCreated

__Editing Appointment:__



* AppointmentEditing

* AppointmentSaving

* AppointmentEdited

__Editing Appointment:__

* AppointmentEditing

* AppointmentSaving

* AppointmentEdited

__Deleting Appointment:__



* AppointmentDeleting

* AppointmentDeleted

__Deleting Appointment:__



* AppointmentDeleting

* AppointmentDeleted__
                Deleting an occurrence:
              __



* AppointmentEditing

* AppointmentSaving

* AppointmentEdited


