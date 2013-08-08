---
title: Getting Started
meta_title: Getting Started
meta_description: description.
slug: getting-started
tags:getting,started
publish:True
---


This tutorial will walk you through the creation of a sample application that contains __RadScheduleView__ and will show you how to:
      

* Add RadScheduleView in your projects#Adding_RadScheduleView_to_the_project

* Add a ViewDefinition to the RadScheduleView control#Adding_a_ViewDefinition_to_the_RadScheduleView_control

* Bind your RadScheduleView control to a collection of appointments#Bind_your_RadScheduleView_control_to_a_collection_of_appointments



# Adding_RadScheduleView_to_the_projectAdding RadScheduleView to the project

For the purpose of this example, you will need to create an empty WPFSilverlight Application project and open it in Visual Studio.	>

In order to add RadScheduleView control in your projects you have to add references to the following assemblies:

* Telerik.Windows.Controls

* Telerik.Windows.Controls.Input

* Telerik.Windows.Controls.Navigation 

* Telerik.Windows.Controls.ScheduleView

* Telerik.Windows.Data

* 
            Now add a 


 __XAML__
    


	<Window x:Class="GettingStarted.MainWindow"         
	 xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"         
	 xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"         
	 xmlns:telerik="http://schemas.telerik.com/2008/xaml/presentation"         
	 Title="MainWindow" Height="350" Width="790">     
	 <Grid>           
	  <telerik:RadScheduleView />     
	 </Grid>
	</Window>

Two lines of code are important here:

* First is the import of the Telerik URL namespace:
          

* 
            And second is the declaration of the 
          There are two things you should do in order to use __RadScheduleView__ control:
        

* 
            First is to set a 

* 
            Second is to set a collection of Appointments for 

# Adding_a_ViewDefinition_to_the_RadScheduleView_controlAdding a ViewDefinition to the RadScheduleView control
          The following lines will add a DayViewDefinition to the __RadScheduleView__ control:
        	>You can add more than only one ViewDefinition. There are four view definitions available:

* DayViewDefinition

* WeekViewDefinition

* TimelineViewDefinition

* MonthViewDefinition

* CustomViewDefinition

# Bind_your_RadScheduleView_control_to_a_collection_of_appointmentsBind your RadScheduleView control to a collection of appointments
          Now, lets bind the __AppointmentsSource__ to a collection of appointments in our ViewModel, named Appointments:
        


 __XAML__
    


	<telerik:RadScheduleView AppointmentsSource="{Binding Appointments}">             
	 <telerik:RadScheduleView.ViewDefinitions>                  
	  <telerik:DayViewDefinition />                  
	  <telerik:MonthViewDefinition />             
	 </telerik:RadScheduleView.ViewDefinitions>
	</telerik:RadScheduleView>


          To learn more about the Appointments of the RadScheduleView take a look at the [Understanding Appointments]({{slug:understanding-appointments}}) topic.
        [Understanding Appointments]({{slug:understanding-appointments}})
