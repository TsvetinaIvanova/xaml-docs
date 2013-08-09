---
title: Overview
meta_title: Overview
meta_description: description.
slug: overview
tags:overview
publish:True
---


The ScheduleView provides the functionality of displaying the data in different views. There are four predefined views 
      from which you can choose to easily navigate through the appointments. These views ensure better flexibility and save time 
      to write or modify the logic behind all different controls to make them work as one. You can customize each view – you can 
      modify its orientation, the number of days displayed, customize the time ruler, etc.
      

* 

__Day View__ – this view displays the appointments for a single day. It is always grouped by date and 
  			additionally can be grouped by resource. It can be oriented horizontally or vertically. If there is more than 1 day displayed 
  			in this view, the listing starts from value of the __CurrentDate__ property set to the ScheduleView control.
  			

* 

__Week View__ – this view contains the same properties as the DayView with the only difference 
  			that the displayed period is not just a single day but the days of a whole week. It is always grouped by date 
  			and additionally can be grouped by resource. The difference between the DayView and the WeekView is that the first 
  			displayed date in WeekView is the first day of the week of the __CurrentDate__ property.
  			

* 

__Month View__ – the Month View displays by default the appointments in one month and allows you to browse 
  			through long-term periods. It is always grouped by week and additionally can be grouped by resource. The MonthView can be 
  			oriented only horizontally.
  			

* 

__Timeline View__ – the TimeLine view displays the days and the hours in a 
  			timeline like matter. It cannot be grouped by date, but only by resource. The TimelineView can be oriented horizontally 
  			or vertically. The first day in this view is the value of the __CurrentDate__ property of the ScheduleView control.
      

Also, through defining different properties you can create your own custom view.>More information about the common for all views properties can be found 
      	<link xlink:href="0973c9f2-dad2-400b-be85-93bdef8c4de0" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5">here</link> and for view specific properties - 
      	<link xlink:href="ba38cb94-0cf5-43e4-95a9-39a3d3536d5b" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5">here</link>.

# How to set the views

RadScheduleView has different definitions for each view. It has four types of predefined view definitions, as
          mentioned earlier:
        

* 

DayViewDefiniton

* 

MonthViewDefinition

* 

TimelineViewDefinition

* 

WeekViewDefinition

In order to include each one of the views in the RadScheduleView, they have to be defined as follows:
        


 __XAML__
    


	        <telerik:RadScheduleView AppointmentsSource="{Binding Appointments}" x:Name="scheduleView">
	            <telerik:RadScheduleView.ViewDefinitions>
	                <telerik:DayViewDefinition/>
	                <telerik:MonthViewDefinition/>
	                <telerik:WeekViewDefinition/>
	                <telerik:TimelineViewDefinition/>
	            </telerik:RadScheduleView.ViewDefinitions>
	        </telerik:RadScheduleView>




 __C#__
    


	            MonthViewDefinition monthDefintion = new MonthViewDefinition();
	            DayViewDefinition dayDefintion = new DayViewDefinition();
	            WeekViewDefinition weekDefinition = new WeekViewDefinition();
	            TimelineViewDefinition timelineDefinition = new TimelineViewDefinition();
	            this.scheduleView.ViewDefinitions.Add(monthDefintion);
	            this.scheduleView.ViewDefinitions.Add(dayDefintion);
	            this.scheduleView.ViewDefinitions.Add(timelineDefinition);
	            this.scheduleView.ViewDefinitions.Add(weekDefinition);
	

[Configuration]({{slug:configuration}})[View specific properties]({{slug:view-specific-properties}})[How to configure the VisibleRange]({{slug:how-to-configure-the-visiblerange}})
