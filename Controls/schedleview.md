This article describes the release history of the control.
For the complete Release History of RadControls for SilverlightWPF go to 
		
  [What's New Section](http://www.telerik.com/products/silverlight/whats-new.aspx)

  [What's New Section](http://www.telerik.com/products/wpf/whats-new.aspx)

 #What's New
* Add OccurrenceFilter property

* Add ToolTipStyle property

* Provide a way to make the row expand automatically in MonthViewDefinition when there are more appointments 

 #What's Fixed
* ScheduleView should not use the Local time zone for its internal calculations

* When adding an appointment with Start = End, the appointment is added to the appointment source, but it is not displayed on the ScheduleView

* When importing all day recurring appointments they are not displayed in DayView and WeekView

* The ICal importer throws DateTimeParse exception for recurrent all day appointments exported by Google Calendar 

* When the FirstVisibleGroup property is set to a group with no TimeZone set, an exception is thrown 

* VisibleRangeChanged event is triggered more times when initially loading the control and have ActiveViewDefinitionIndex set

* When changing Start/End time of an appointment in EditRecurrenceDialog, these properties are not updated in EditAppointmentDialog 

* Inconsistency between DAILY and BYDAY attributes when importing ICal appointments 

* Dragging 2 appointments from different resources adds both resources to one of the appointments 

* Appointments are not displayed when changing the theme runtime in TimelineViewDefinition

* CustomAppointmentItemTemplate is not applied when changing from DayView to other Views 

* When the start time of the day in DayView is bigger than the start time of the all day appointment, the appointment is missing 

* When increasing the start time of an appointment in the EditAppointmentDialog, the end time should be automatically increased

* RadScheduleView raises ArgumentException in TimelineViewDefinition when VisibleDays="1" and the day duration is shorter than the DayStartTime

* When the Focus in the control clicking on a Hyperlink causes InvalidOperationException 

* ScrollTimeRuler method does not behave as expected when changing from MonthView to Day/WeekView 

* Delete obsoleted InvertedBooleanConverter from ScheduleView 

* Error when recurrence appointment start is equal to start time of view
