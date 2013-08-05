___
title: Time Markers
meta_title: Time Markers
meta_description: 
slug :time markers
tags :time,markers
publish :True
___


__RadScheduleView__ provides you with a built-in time markers support. You can assign a time marker to each one of your appointments, thus making them easily distinguishable.
		

This chapter will cover the following topics:[Assign Time Marker to an Appointment run-time](#Assign_TimeMarker_Runtime)[Adding TimeMarkers to the RadScheduleView](#Adding_TimeMarkers)

# Assign_TimeMarker_RuntimeAssign Time Marker to an Appointment run-time

Run-time you can define the time marker of your appointment via the drop down menu in the EditAppointmentDialog.

![radscheduleview timemarkers 01](../Media/radscheduleview_timemarkers_01.png)

On the snapshot below you can see four appointments where three of them have time markers set, while the fourth does not have. Notice the color markers in the left part of the appointments.

![radscheduleview timemarkers 02](../Media/radscheduleview_timemarkers_02.png)

# Adding_TimeMarkersAdding TimeMarkers to the RadScheduleView

By default the RadScheduleView has predefined list of time markers i.e. "Busy", "Free", etc. 
		

However, there are cases when new time markers are needed and you have to create them on your own, as it is shown below. 
		

Each time marker has three important characteristics:__TimeMarkerName__ - each time marker has a name assigned. It is used to distinguish that time marker amongst the others in your application.__TimeMarkerBrush__ - each category has a color brush assigned.

The time markers available in the RadScheduleView are defined in the TimeMarkersSource property (IEnumarable). Just add or remove time markers to that collection in order to add or remove time markers to the RadScheduleView itself.
		
<telerik:RadScheduleView x:Name="scheduleView" AppointmentsSource="{Binding Appointments}">
		<telerik:RadScheduleView.TimeMarkersSource>
			<telerik:TimeMarkerCollection>
				<telerik:TimeMarker TimeMarkerName="Busy" TimeMarkerBrush="Red"  />
				<telerik:TimeMarker TimeMarkerName="Free" TimeMarkerBrush="Green" />
			</telerik:TimeMarkerCollection>
		</telerik:RadScheduleView.TimeMarkersSource>
			<telerik:RadScheduleView.ViewDefinitions>
		<telerik:DayViewDefinition />
	</telerik:RadScheduleView.ViewDefinitions>		
</telerik:RadScheduleView>

or
public class MyViewModel : ViewModelBase
{
	public ObservableCollection<Appointment> Appointments { get; set; }
	public ObservableCollection<TimeMarker> TimeMarkers { get; set; }

	public MyViewModel()
	{
		this.Appointments = new ObservableCollection<Appointment>();
		this.TimeMarkers = new ObservableCollection<TimeMarker>() {
			new TimeMarker("Busy", new SolidColorBrush( Colors.Red ) ),
			new TimeMarker("Free", new SolidColorBrush( Colors.Green ) )
		};
	}
}
<telerik:RadScheduleView x:Name="scheduleView" 
			AppointmentsSource="{Binding Appointments}"
			TimeMarkersSource="{Binding TimeMarkers}">		
			<telerik:RadScheduleView.ViewDefinitions>
		<telerik:DayViewDefinition />
	</telerik:RadScheduleView.ViewDefinitions>		
</telerik:RadScheduleView>

Finally, set the DataContext:
this.DataContext = new MyViewModel();

Here is the result:

![radscheduleview timemarkers 03](../Media/radscheduleview_timemarkers_03.png)[Implementing View-ViewModel ](http://radscheduleview-populating-with-data-implementing-view-model.md)
