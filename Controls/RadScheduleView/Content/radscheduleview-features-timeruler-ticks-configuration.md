---
title: Configuring the TimeRuler ticks
meta_title: Configuring the TimeRuler ticks
meta_description: description.
slug: configuring-the-timeruler-ticks
tags:configuring,the,timeruler,ticks
publish:True
---


# Overview

The __MajorTickLength__ and __MinorTicklength__ properties of the RadScheduleView ViewDefinitions are used to determine the density of the time ruler items. You can play with different combinations to find the one that best suits your needs. The appointments will snap with regards to the minor ticks.  Also TimelineViewDefinition has an additional __GroupTickLength__ property used to set the length of the group. 
        

Let’s have the RadScheduleView defined like this:




 __XAML__
    


	<telerik:RadScheduleView AppointmentsSource="{Binding Appointments}" >
		<telerik:RadScheduleView.ViewDefinitions>
			<telerik:DayViewDefinition MinorTickLength="30min" MajorTickLength="2h"  />
			<telerik:WeekViewDefinition MinorTickLength="1h" MajorTickLength="2h" />
			<telerik:TimelineViewDefinition MinorTickLength="6h" MajorTickLength="1d" GroupTickLength="2d" />
		</telerik:RadScheduleView.ViewDefinitions>
	</telerik:RadScheduleView>



This will lead to the following results:

* In DayViewDefinition:
    	

* In WeekViewDefinition:
    	

* In TimelineViewDefinition:>

You can check [Formatting]({{slug:formatting}}) where it is explained how the dates and times on the time ruler can be formatted.
    	

# Setting the properties

The ticklength properties can be set in the XAML and in code-behind:

* In XAML:
       

* In Code-Behind:
       

You can check the ScheduleView Configurator example at 
      	[RadControls for Silverlight demos](http://demos.telerik.com/silverlight/#ScheduleView/ScheduleViewConfigurator)[RadControls for WPF demos](http://demos.telerik.com/wpf/) to see the tick length properties in action.
      
