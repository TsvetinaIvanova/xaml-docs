---
title: Configuration
meta_title: Configuration
meta_description: description.
slug: configuration
tags:configuration
publish:True
---
Common properties for all views

RadScheduleView's four predefined ViewDefinitions have various properties, which can be set in order the views to be configured 
      best. Some of them are common for all views, others are specific for each view. In the following section we will
      go through all common properties.
      >For more information about the view specific properties, check <link xlink:href="ba38cb94-0cf5-43e4-95a9-39a3d3536d5b" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5">here</link>.



* [Title](#Title)

* [LargeChangeInterval](#LargeChangeInterval)

* [SmallChangeInterval](#SmallChangeInterval)

* [DayStartTime](#DayStartTime)

* [DayEndTime](#DayEndTime)

* [VisibleDays](#VisibleDays)

* [FirstDayOfWeek](#FirstDayOfWeek)

* [StretchGroupHeaders](#StretchGroupHeaders)

* [Orientation](#Orientation)

# TitleTitle

Gets or sets the title of the view.

# LargeChangeIntervalLargeChangeInterval

Gets or sets the date time interval with which the current will be increased
      or decreased when clicking on the navigation buttons in the header of the ScheduleView. The default values 
      of the __LargeChangeInterval__ property are:



* 1d (1 day) for DayView

* 7d (7 days) for WeekView

* 1m (1 month) for MonthView

* 7d (7 days) for TimelineViewThe property is of type __DateTimeInterval__. In the following example the __LargeChangeInterval__ property of DayView is set to 2 
      days and of MonthView is set of 2 months and 4 days.
      


 __XAML__
    


	        <telerik:RadScheduleView x:Name="scheduleView" AppointmentsSource="{Binding Appointments}">
	            <telerik:RadScheduleView.ViewDefinitions>
	                <telerik:DayViewDefinition LargeChangeInterval="2d"/>
	                <telerik:MonthViewDefinition LargeChangeInterval="2m 4d"/>
	            </telerik:RadScheduleView.ViewDefinitions>
	        </telerik:RadScheduleView>




 __C#__
    


		dayDefintion.LargeChangeInterval = new Telerik.Windows.Controls.ScheduleView.
		DateTimeInterval(2, 0);
		monthDefinition.LargeChangeInterval = new Telerik.Windows.Controls.ScheduleView.
		DateTimeInterval(4, 2);



# SmallChangeIntervalSmallChangeIntervalGets or sets the small change interval of the ScheduleView. It indicates the date time interval with which the current will be increased or decreased 
      when moving the scrollbar. The default values of the __SmallChangeInterval__ are:
      

* 7d (7 days) for MonthView

* 1d (1 day) for TimelineViewSetting the SmallChangeInterval property of a DayViewDefiniton and WeekViewDefinition won’t change the behavior of the 
      view. That is due to that using the vertical scrollbar will not navigate to the next set of days, but will scroll the current view.
      The following example shows how to set the __SmallChangeInterval__ property of a MonthViewDefinition 
      to 11 days and of a TimelineViewDefinition to 3 days:
      


 __XAML__
    


	        <telerik:RadScheduleView x:Name="scheduleView" AppointmentsSource="{Binding Appointments}">
	            <telerik:RadScheduleView.ViewDefinitions>
	                <telerik:MonthViewDefinition SmallChangeInterval="11d"/>
	                <telerik:TimelineViewDefinition SmallChangeInterval="3d"/>
	            </telerik:RadScheduleView.ViewDefinitions>
	        </telerik:RadScheduleView>




 __C#__
    


		monthDefintion.SmallChangeInterval = new Telerik.Windows.Controls.ScheduleView.
		DateTimeInterval(11, 0);
		timelineDefinition.SmallChangeInterval = new Telerik.Windows.Controls.ScheduleView.
		DateTimeInterval(3, 0);



# DayStartTimeDayStartTimeGets or sets the time used to indicate the start of the TimeRuler. The default value of the DayStartTime for all views is 00:00:00 or 12:00 AM.
      The DayStartTime is of type TimeSpan. It will not affect the look of the MonthView, since MonthView does not display time.
      The following example illustrates how to set the DayStartTime for DayView, WeekView and TimelineView:
      


 __XAML__
    


	        <telerik:RadScheduleView x:Name="scheduleView" AppointmentsSource="{Binding Appointments}">
	            <telerik:RadScheduleView.ViewDefinitions>
	                <telerik:DayViewDefinition DayStartTime="07:30:00"/>
	                <telerik:WeekViewDefinition DayStartTime="08:00:00"/>
	                <telerik:TimelineViewDefinition DayStartTime="11:30:00"/>
	            </telerik:RadScheduleView.ViewDefinitions>
	        </telerik:RadScheduleView>




 __C#__
    


		dayDefintion.DayStartTime = new TimeSpan(7, 30, 00);
		weekDefinition.DayStartTime = new TimeSpan(8, 0, 0);
		timelineDefinition.DayStartTime = new TimeSpan(11, 30, 0);



# DayEndTimeDayEndTimeGets or sets the time used to indicate the end of the view. The default values of the DayStartTime for the view are:
      

* 1.00:00:00 (1 day) for DayView

* 1.00:00:00 (1 day) for WeekView

* 1.00:00:00 (1 day) for TimelineViewThe DayEndTime property is of type TimeSpan. The MonthView will be affected in the following manner – if there are appointments out of the displayed time range, they won’t be displayed in the MonthView also.
      The following example illustrates how to set the DayStartTime for DayView, WeekView and TimelineView:
      


 __XAML__
    


	        <telerik:RadScheduleView x:Name="scheduleView" AppointmentsSource="{Binding Appointments}">
	            <telerik:RadScheduleView.ViewDefinitions>
	                <telerik:DayViewDefinition DayEndTime="17:30:00"/>
	                <telerik:WeekViewDefinition DayEndTime="18:00:00"/>
	                <telerik:TimelineViewDefinition DayEndTime="21:30:00"/>
	            </telerik:RadScheduleView.ViewDefinitions>
	        </telerik:RadScheduleView>




 __C#__
    


		dayDefintion.DayStartTime = new TimeSpan(17, 30, 00);
		weekDefinition.DayStartTime = new TimeSpan(18, 0, 0);
		timelineDefinition.DayStartTime = new TimeSpan(21, 30, 0);



# VisibleDaysVisibleDaysGets or sets the visible dates in the view. It indicates the count of the dates that will be shown in the view. The default values of the VisibleDays property are:
      

* 1 day for DayView

* 7 days for WeekView

* 42 days for MonthView

* 7 days for TimelineViewThe following code-snippet illustrates how to set the VisibleDays property in XAML and in code-behind for all predefined views:
      


 __XAML__
    


	        <telerik:RadScheduleView x:Name="scheduleView" AppointmentsSource="{Binding Appointments}">
	            <telerik:RadScheduleView.ViewDefinitions>
	                <telerik:DayViewDefinition VisibleDays="4"/>
	                <telerik:WeekViewDefinition VisibleDays="11"/>
	                <telerik:MonthViewDefinition VisibleDays="21" />
	                <telerik:TimelineViewDefinition VisibleDays="9"/>
	            </telerik:RadScheduleView.ViewDefinitions>
	        </telerik:RadScheduleView>




 __C#__
    


		dayDefintion.VisibleDays = 4;
		weekDefinition.VisibleDays = 11;
		monthDefintion.VisibleDays = 21;
		timelineDefinition.VisibleDays = 9;

And the result is shown on the next figure for DayView and TimelineView:
               
      		![radschedule View viewdefinitions configuration 01](images/radscheduleView_viewdefinitions_configuration_01.png)

# FirstDayOfWeekFirstDayOfWeekGets or sets the first weekday with which the week will start according to the view. It affects only the WeekView and MonthView. Once set, it will override the FirstDayOfWeek property of the ScheduleView and the one that is default for the culture.
      

# StretchGroupHeadersStretchGroupHeadersIf set to True, it will stretch the GroupHeader if there is more available space.
      

# OrientationOrientationGets or sets the orientation of the view. When the orientation is horizontal the TimeRuler is also horizontally oriented, but the GroupHeaders are oriented vertically and vice versa.
      Values can be Vertical or Horizontal. __Not present in MonthView.__ This is measured according to the position of the TimeRuler. The default values of Orientation property are:
      

* Vertical for DayView

* Vertical for WeekView

* Horizontal for TimelineViewThe following code-snippets show how to set the Orientation property in XAML and code-behind:
      


 __XAML__
    


	        <telerik:RadScheduleView x:Name="scheduleView" AppointmentsSource="{Binding Appointments}">
	            <telerik:RadScheduleView.ViewDefinitions>
	                <telerik:DayViewDefinition Orientation="Horizontal" />
	                <telerik:WeekViewDefinition Orientation="Horizontal"/>
	                <telerik:TimelineViewDefinition Orientation="Vertical"/>
	            </telerik:RadScheduleView.ViewDefinitions>
	        </telerik:RadScheduleView>




 __C#__
    


		dayDefintion.Orientation = Orientation.Horizontal;
		weekDefinition.Orientation = Orientation.Horizontal;
		timelineDefinition.Orientation = Orientation.Vertical;

This is how the views look like after setting the Orientation property:
               
      		![radschedule View viewdefinitions configuration 05](images/radscheduleView_viewdefinitions_configuration_05.png)DayView with Orientation property set to Horizontal.
               
      		![radschedule View viewdefinitions configuration 06](images/radscheduleView_viewdefinitions_configuration_06.png)WeekView with Orientation property set to Horizontal.
      
               
            ![radschedule View viewdefinitions configuration 07](images/radscheduleView_viewdefinitions_configuration_07.png)TimelineView with Orientation property set to Horizontal.
      
