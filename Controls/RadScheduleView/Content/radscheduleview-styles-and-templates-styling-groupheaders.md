---
title: Styling the GroupHeaders
meta_title: Styling the GroupHeaders
meta_description: description.
slug: styling-the-groupheaders
tags:styling,the,groupheaders
publish:True
---


It is a common scenario to use resources in RadScheduleView and group the appointments according to the resource they are assigned to. 
        This article discussed how the GroupHeaders can be customized. Also it explains the use of GroupHeaderStyleSelector in order to apply separate styles to the GroupHeaders.
      

Let's have the following RadScheduleView grouped by  Date, "Calendar" and “Room” Resources:


 __XAML__
    	


<telerik:RadScheduleView x:Name="scheduleView" AppointmentsSource="{Binding Appointments}" >         
    <telerik:RadScheduleView.ResourceTypesSource>
        <telerik:ResourceTypeCollection>
            <telerik:ResourceType Name="Calendar">
                <telerik:Resource ResourceName="MyCalendar" DisplayName="My Calendar"  />
                <telerik:Resource ResourceName="TeamCalendar" DisplayName="Team Calendar"  />
            </telerik:ResourceType>
            <telerik:ResourceType Name="Room">
                <telerik:Resource ResourceName="Room1" DisplayName="Room 1" />
                <telerik:Resource ResourceName="Room2" DisplayName="Room 2" />
            </telerik:ResourceType>
        </telerik:ResourceTypeCollection>
    </telerik:RadScheduleView.ResourceTypesSource>
    <telerik:RadScheduleView.GroupDescriptionsSource>
        <telerik:GroupDescriptionCollection>
            <telerik:DateGroupDescription />
            <telerik:ResourceGroupDescription ResourceType="Calendar" />
            <telerik:ResourceGroupDescription ResourceType="Room" />
        </telerik:GroupDescriptionCollection>
    </telerik:RadScheduleView.GroupDescriptionsSource>
    <telerik:RadScheduleView.ViewDefinitions>                
        <telerik:DayViewDefinition />
        <telerik:WeekViewDefinition />
        <telerik:MonthViewDefinition />
        <telerik:TimelineViewDefinition />
    </telerik:RadScheduleView.ViewDefinitions>
</telerik:RadScheduleView>



This article will cover the following topics:

* How to generate and use the GroupHeaderStyleSelector;#generate-and-use-groupheaderstyleselector

* How to create a custom GroupHeaderStyleSelector.#create-custom-groupheaderstyleselector

# generate-and-use-groupheaderstyleselectorGenerate and use the GroupHeaderStyleSelector

Any change on the appearance of a GroupHeader depends on the GroupHeaderStyleSelector and the containing styles. The selector is oriented, meaning it contains orientation dependant styles – horizontal and vertical.
        

The GroupHeaderStyleSelector contains the following styles:

* HorizontalGroupHeaderStyle, HorizontalBottomLevelGroupHeaderStyle


         
      ![](images/radscheduleview_horizontalgroupheaderstyle.png)

* HorizontalTodayGroupHeaderStyle, HorizontalBottomLevelTodayGroupHeaderStyle


         
      ![](images/radscheduleview_horizontaltodaygroupheaderstyle.png)

* VerticalGroupHeaderStyle, VerticalBottomLevelGroupHeaderStyle


         
      ![](images/radscheduleview_verticalgroupheaderstyle.png)

* VerticalTodayGroupHeaderStyle,  VerticalBottomLevelTodayGroupHeaderStyle


         
      ![](images/radscheduleview_verticaltodaygroupheaderstyle.png)

* MonthViewWeekGroupStyle, MonthViewBottomLevelWeekGroupStyle


         
      ![](images/radscheduleview_monthviewweekgroupstyle.png)



Choose one of the following approaches to obtain the source code of GroupHeaderStyleSelector:

* Generate GroupHeaderStyleSelector from installation folder

In the RadControls installation folder on your computer, go to Themes folder and select the theme that you use in your application. Drill down to find the ScheduleView.xaml file in that directory. From this resource dictionary you can extract the GroupHeaderStyleSelector and any needed resources that it uses. 

* Generate GroupHeaderStyleSelector from RadScheduleView template

Generate first the RadScheduleView template from Expression Blend ( Edit Template > Edit a Copy). Search for the GroupHeaderStyleSelector and copy the style together with all needed resources that it uses.

The end result should include the following:


 __XAML__
    	


<!-- Brushes -->
...
<!-- Styles-->
		<ControlTemplate x:Key="GroupHeaderButtonControlTemplate" TargetType="local:GroupHeaderButton">
			...
		</ControlTemplate>

		<Style x:Key="GroupHeaderButtonStyle" TargetType="local:GroupHeaderButton">
			...
		</Style>

		<local:NullToBooleanConverter x:Key="NullToBooleanConverter" />
		<ControlTemplate x:Key="GroupHeaderTemplate"  TargetType="local:GroupHeader">
			...
		</ControlTemplate>

		<Style x:Key="GroupHeaderBaseStyle" TargetType="local:GroupHeader">
			...
		</Style>
		<Style TargetType="local:GroupHeader" BasedOn="{StaticResource GroupHeaderBaseStyle}" />

		<Style x:Key="HorizontalGroupHeaderStyle" TargetType="local:GroupHeader" BasedOn="{StaticResource GroupHeaderBaseStyle}">
			...
		</Style>
		<Style x:Key="HorizontalTodayGroupHeaderStyle" TargetType="local:GroupHeader" BasedOn="{StaticResource GroupHeaderBaseStyle}">
			...
		</Style>
		<Style x:Key="HorizontalBottomLevelGroupHeaderStyle" TargetType="local:GroupHeader" BasedOn="{StaticResource GroupHeaderBaseStyle}">
			...
		</Style>
		<Style x:Key="HorizontalBottomLevelTodayGroupHeaderStyle" TargetType="local:GroupHeader" BasedOn="{StaticResource GroupHeaderBaseStyle}">
			...
		</Style>
		<Style x:Key="VerticalGroupHeaderStyle" TargetType="local:GroupHeader" BasedOn="{StaticResource GroupHeaderBaseStyle}">
			...
		</Style>
		<Style x:Key="VerticalTodayGroupHeaderStyle" TargetType="local:GroupHeader" BasedOn="{StaticResource GroupHeaderBaseStyle}">
			...
		</Style>
		<Style x:Key="VerticalBottomLevelGroupHeaderStyle" TargetType="local:GroupHeader" BasedOn="{StaticResource GroupHeaderBaseStyle}">
			...
		</Style>
		<Style x:Key="VerticalBottomLevelTodayGroupHeaderStyle" TargetType="local:GroupHeader" BasedOn="{StaticResource GroupHeaderBaseStyle}">
			...
		</Style>
		<Style x:Key="MonthViewWeekGroupStyle" TargetType="local:GroupHeader" BasedOn="{StaticResource GroupHeaderBaseStyle}">
			...
		</Style>
		<Style x:Key="MonthViewBottomLevelWeekGroupStyle" TargetType="local:GroupHeader" BasedOn="{StaticResource GroupHeaderBaseStyle}">
			...
		</Style>
		<!-- GroupHeaderStyleSelector -->
		<local:OrientedGroupHeaderStyleSelector x:Key="GroupHeaderStyleSelector"
			HorizontalStyle="{StaticResource HorizontalGroupHeaderStyle}"
			HorizontalTodayStyle="{StaticResource HorizontalTodayGroupHeaderStyle}"
			HorizontalBottomLevelStyle="{StaticResource HorizontalBottomLevelGroupHeaderStyle}"
			HorizontalTodayBottomLevelStyle="{StaticResource HorizontalBottomLevelTodayGroupHeaderStyle}"
			
			VerticalStyle="{StaticResource VerticalGroupHeaderStyle}"
			VerticalTodayStyle="{StaticResource VerticalTodayGroupHeaderStyle}"
			VerticalBottomLevelStyle="{StaticResource VerticalBottomLevelGroupHeaderStyle}"
			VerticalTodayBottomLevelStyle="{StaticResource VerticalBottomLevelTodayGroupHeaderStyle}"
			
			MonthViewWeekGroupStyle="{StaticResource MonthViewWeekGroupStyle}"
			MonthViewBottomLevelWeekGroupStyle="{StaticResource MonthViewBottomLevelWeekGroupStyle}">
		</local:OrientedGroupHeaderStyleSelector>



Note the use of the local namespace from the raw source:


 __XAML__
    	


xmlns:local="clr-namespace:Telerik.Windows.Controls;assembly=Telerik.Windows.Controls.ScheduleView"



The selector is applied to our instance of RadScheduleView:


 __XAML__
    	


<telerik:RadScheduleView x:Name="scheduleView" AppointmentsSource="{Binding Appointments}" GroupHeaderStyleSelector="{StaticResource GroupHeaderStyleSelector}">



Now we can apply any customization to the GroupHeaders and watch the change. Let’s for example modify __HorizontalBottomLevelStyle__ – change the color and style of the headers:


 __XAML__
    	


<Style x:Key="HorizontalBottomLevelGroupHeaderStyle" TargetType="telerik:GroupHeader" BasedOn="{StaticResource GroupHeaderBaseStyle}">
	<Setter Property="Margin" Value="0 0 -1 0" />
	<Setter Property="Padding" Value="0 0 5 0" />
	<Setter Property="Canvas.ZIndex" Value="-2" />
	<Setter Property="Foreground" Value="Red"/>
	<Setter Property="FontStyle" Value="Italic"/>
</Style>



Here is the result:


         
      ![](images/radscheduleview_horizontalgroupheaderstyleexample.png)

# create-custom-groupheaderstyleselectorCreate a custom GroupHeaderStyleSelector

In order to set different styles to the different Resource GroupHeaders , we should create a custom class which inherits OrientedGroupHeaderStyleSelector class and overrides its SelectStyle method.  Also we need to add Style properties for Date and "Calendar" Resource headers and return the corresponding Style:


 __C#__
    	


public class CustomGroupHeaderStyleSelector : OrientedGroupHeaderStyleSelector 
{
    public Style CalendarStyle { get; set; }
    public Style DateStyle { get; set; }
    public override Style SelectStyle(object item, DependencyObject container, ViewDefinitionBase activeViewDeifinition)
    {
        var groupHeader = container as GroupHeader;
        if (groupHeader != null)
        {
            var groupKey = groupHeader.GroupKey as Resource;
            if (groupKey != null && groupKey.ResourceType == "Calendar")
            {
                return this.CalendarStyle;
            }
            else if (groupHeader.GroupKey is DateTime)
            {
                return this.DateStyle;
            }
        }
        return base.SelectStyle(item, container, activeViewDeifinition);
    }
}






 __VB.NET__
    	


Public Class CustomGroupHeaderStyleSelector
    Inherits OrientedGroupHeaderStyleSelector
    Public Property CalendarStyle() As Style
        Get
            Return m_CalendarStyle
        End Get
        Set(value As Style)
            m_CalendarStyle = value
        End Set
    End Property
    Private m_CalendarStyle As Style
    Public Property DateStyle() As Style
        Get
            Return m_DateStyle
        End Get
        Set(value As Style)
            m_DateStyle = value
        End Set
    End Property
    Private m_DateStyle As Style
    Public Overrides Function SelectStyle(item As Object, container As DependencyObject, activeViewDeifinition As ViewDefinitionBase) As Style
        Dim groupHeader = TryCast(container, GroupHeader)
        If groupHeader IsNot Nothing Then
            Dim groupKey = TryCast(groupHeader.GroupKey, Resource)
            If groupKey IsNot Nothing AndAlso groupKey.ResourceType = "Calendar" Then
                Return Me.CalendarStyle
            ElseIf TypeOf groupHeader.GroupKey Is DateTime Then
                Return Me.DateStyle
            End If
        End If
        Return MyBase.SelectStyle(item, container, activeViewDeifinition)
    End Function
End Class



Add the Styles to the XAML:


 __XAML__
    	


<local:CustomGroupHeaderStyleSelector x:Key="CustomGroupHeaderStyleSelector">
     <local:CustomGroupHeaderStyleSelector.CalendarStyle>
          <Style TargetType="telerik:GroupHeader">
              <Setter Property="BorderThickness" Value="0, 0, 0, 2" />
              <Setter Property="BorderBrush" Value="Red" />
          </Style>
      </local:CustomGroupHeaderStyleSelector.CalendarStyle>
      <local:CustomGroupHeaderStyleSelector.DateStyle>
          <Style TargetType="telerik:GroupHeader">
               <Setter Property="FontWeight" Value="Bold" />
          </Style>
      </local:CustomGroupHeaderStyleSelector.DateStyle>
</local:CustomGroupHeaderStyleSelector>



And finally set the GroupHeaderStyleSelector property of the RadScheduleView:


 __XAML__
    	


<telerik:RadScheduleView x:Name="scheduleView" AppointmentsSource="{Binding Appointments}"   GroupHeaderStyleSelector="{StaticResource CustomGroupHeaderStyleSelector}">






         
      ![](images/radscheduleview_customgroupheaderexample.png)
