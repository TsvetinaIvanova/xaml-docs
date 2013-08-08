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
    

```XAML


<telerik:RadScheduleView SnapAppointments="True">
...
</telerik:RadScheduleView>

```



This way during drag/resize operation the Start/End times of the appointment will be rounded according to the TimeSlots’ length:![radscheduleview snapappointments 1](images/radscheduleview_snapappointments_1.png)

You could set MinorTickLength property of the ViewDefinition in order to snap the appointments to different duration:
     


 __XAML__
    

```XAML


<telerik:RadScheduleView SnapAppointments="True">		
	<telerik:RadScheduleView.ViewDefinitions>
		<telerik:DayViewDefinition MinorTickLength = "15min" />		
	</telerik:RadScheduleView.ViewDefinitions>	
</telerik:RadScheduleView>

```



And the result is:![radscheduleview snapappointments 2](images/radscheduleview_snapappointments_2.png)
    ![tip](tip.jpg)
    	

You can check [Configuring the TimeRuler ticks]({{slug:configuring-the-timeruler-ticks}}) article for more details about MinorTickLength property.

# Section1Customizing the SnapBehavior

For more advanced scenarios when snapping of the appointments is not directly connected with the time slots, the RadScheduleView control provides a way to customize the snapping of the appointments in a more detailed manner. 
        You just need to create a class which inherits from __Telerik.Windows.Controls.ScheduleView.SnapBehavior__ and to override its SnapStart and SnapEnd methods.
        Then an instance of this class should be set to the __SnapBehavior__ property of RaddScheduleView.

In the next example it is demonstrated how to set the snapping to 5 minutes regardless of the TimeSlots length.

* First, create CustomSnapBehavior class:

* Override the needed methods:

* Attach the newly created custom behavior to the ScheduleView control:

So now the appointments are snapped to 5 minutes:![radscheduleview snapappointments 3](images/radscheduleview_snapappointments_3.png)
