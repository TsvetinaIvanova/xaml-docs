---
title: Snapping Appointments
meta_title: Snapping Appointments
meta_description: description.
slug: snapping-appointments
tags:snapping,appointments
publish:True
---


RadScheduleView provides the option to automatically snap the appointments while resizing/dragging them. This behavior is enabled through the __SnapAppointments__ Boolean property:


 __XAML__
    


	<telerik:RadScheduleView SnapAppointments="True">
	...
	</telerik:RadScheduleView>



This way during drag/resize operation the Start/End times of the appointment will be rounded according to the TimeSlots’ length:![radscheduleview snapappointments 1](images/radscheduleview_snapappointments_1.png)

You could set MinorTickLength property of the ViewDefinition in order to snap the appointments to different duration:
     


 __XAML__
    


	<telerik:RadScheduleView SnapAppointments="True">		
		<telerik:RadScheduleView.ViewDefinitions>
			<telerik:DayViewDefinition MinorTickLength = "15min" />		
		</telerik:RadScheduleView.ViewDefinitions>	
	</telerik:RadScheduleView>



And the result is:![radscheduleview snapappointments 2](images/radscheduleview_snapappointments_2.png)>You can check <link xlink:href="8e7ade44-944f-4507-8555-95a35fe0abd5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" /> article for more details about MinorTickLength property.

# Section1Customizing the SnapBehavior

For more advanced scenarios when snapping of the appointments is not directly connected with the time slots, the RadScheduleView control provides a way to customize the snapping of the appointments in a more detailed manner. 
        You just need to create a class which inherits from __Telerik.Windows.Controls.ScheduleView.SnapBehavior__ and to override its SnapStart and SnapEnd methods.
        Then an instance of this class should be set to the __SnapBehavior__ property of RaddScheduleView.

In the next example it is demonstrated how to set the snapping to 5 minutes regardless of the TimeSlots length.

* 

First, create CustomSnapBehavior class:


 __C#__
    


	public class CustomSnapBehavior : Telerik.Windows.Controls.ScheduleView.SnapBehavior
	{
	}



* 

Override the needed methods:


 __C#__
    


	public class CustomSnapBehavior : Telerik.Windows.Controls.ScheduleView.SnapBehavior
	{
	
		public override DateTime SnapEnd(SnapData snapData, DateTime timeToSnap)
		{
			if (timeToSnap >= snapData.OriginalData.End)
			{
				return SnapToTimeSpan(TimeSpan.FromMinutes(5), timeToSnap, true);
			}
			else
			{
				return SnapToTimeSpan(TimeSpan.FromMinutes(5), timeToSnap, false);
			}
		}
	
		public override DateTime SnapStart(SnapData snapData, DateTime timeToSnap)
		{
			if (timeToSnap >= snapData.OriginalData.End)
			{
				return SnapToTimeSpan(TimeSpan.FromMinutes(5), timeToSnap, true);
			}
			else
			{
				return SnapToTimeSpan(TimeSpan.FromMinutes(5), timeToSnap, false);
			}
		}
	
		public static DateTime SnapToTimeSpan(TimeSpan timeSpan, DateTime timeToSnap, bool roundToBiggestNumber)
		{
			var difference = timeToSnap.Ticks % timeSpan.Ticks;
			if (roundToBiggestNumber)
			{
				return timeToSnap.AddTicks(timeSpan.Ticks - difference);
			}
	
			return timeToSnap.AddTicks(-difference);
		}
	}



* 

Attach the newly created custom behavior to the ScheduleView control:


 __XAML__
    


	<telerik:RadScheduleView SnapAppointments="True">
		...
		<telerik:RadScheduleView.SnapBehavior>
			<local:CustomSnapBehavior />
		</telerik:RadScheduleView.SnapBehavior>
	</telerik:RadScheduleView>



So now the appointments are snapped to 5 minutes:![radscheduleview snapappointments 3](images/radscheduleview_snapappointments_3.png)
