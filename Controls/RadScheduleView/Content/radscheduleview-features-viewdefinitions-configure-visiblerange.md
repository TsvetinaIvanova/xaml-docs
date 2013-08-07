___
title: How to configure the VisibleRange
meta_title: How to configure the VisibleRange
meta_description:description
slug:how_to_configure_the_visiblerange
tags:how,to,configure,the,visiblerange
publish:True
___



				The built-in __RadScheduleView__ ViewDefinitions have specific ways to determine what the visible range will be when the CurrentDate property is set:
			TypeVisibleRangeStartVisibleDaysDayViewDefinitionCurrentDate1WeekViewDefinitionThe first day of the week, containing CurrentDate7MonthViewDefinitionThe first day of the first week of the month, containing CurrentDate42TimelineViewDefinitionCurrentDate7


    ![note](note.jpg)
    	

The VisibleRangeEnd is VisibleRangeStart+VisibleDays for all view definitions.


    ![tip](tip.jpg)
    	

The easiest way to create a WeekViewDefinition that behaves like the DayViewDefinition is to use a DayViewDefinition and set its VisibleDays=7.

# 


					For advanced customization of the VisibleRange the ViewDefinitionBase class provides two virtual methods:
				
protected virtual DateTime GetVisibleRangeStart (DateTime currentDate, CultureInfo culture, DayOfWeek? firstDayOfWeek);

protected virtual DateTime GetVisibleRangeEnd(DateTime currentDate, CultureInfo culture, DayOfWeek? firstDayOfWeek);




For example, the following class represents a MonthViewDefinition that starts from the first week of CurrentDate:
   				
public class CustomMonthViewDefinition : MonthViewDefinition
{
	protected override DateTime GetVisibleRangeStart(DateTime currentDate, CultureInfo culture, DayOfWeek? firstDayOfWeek)
	{
		return CalendarHelper.GetFirstDayOfWeek(currentDate, firstDayOfWeek.Value);
	}
}



Since VisibleDays is 42 by default, this CustomMonthViewDefinition will display 6 weeks, as the standard MonthViewDefinition does.

Here is how to use the CustomMonthViewDefinition:
<telerik:RadScheduleView>
	<telerik:RadScheduleView.ViewDefinitions>
		<local:CustomMonthViewDefinition />
	</telerik:RadScheduleView.ViewDefinitions>
</telerik:RadScheduleView>
