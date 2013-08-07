---
title: Overview
meta_title: Overview
meta_description: description.
slug: overview
tags:overview
publish:True
---


# Prerequisites

The walkthrough in this section is intended for users who are familiar with developing applications for SilverlightWPF by using Visual Studio and know how to work with Telerik RadControls for SilverlightWPF. You need the following components to complete this walkthrough:Visual Studio 2010[ADO.NET Entity Framework 4.1](http://www.microsoft.com/download/en/details.aspx?displaylang=en&id=26825)[RIA Services for Visual Studio 2010](http://www.microsoft.com/en-us/download/details.aspx?id=28357)



With the current version __(v1.0 SP2)__ WCF RIA Services __doesn’t support Many-To-Many__  relationships between the Entities, but we have such ones in the Database. To work around this limitation, we use an additional property which forces EF to create 
Many-To-Many table.
      	

Prior knowledge of the following concepts is also helpful, but not required to complete the walkthrough:[WCF RIA Services](http://msdn.microsoft.com/en-us/library/ee707344%28v=VS.91%29.aspx)Entity Data Models and the ADO.NET Entity Framework. For more information, see 
      		[Entity Data Model](http://msdn.microsoft.com/en-us/library/ee382825.aspx)
      		and [Entity Framework](http://msdn.microsoft.com/en-us/library/aa697427%28VS.80%29.aspx).
      		

# Creating Silverlight Application

Start this walkthrough by creating a Silverlight application in the Visual Studio 2010.
	
    ![note](note.jpg)
    	

In the New Silverlight Application dialog box, check the Enable .NET RIA Services option.

Add the following references to the Silverlight project:Telerik.Windows.Controls.dllTelerik.Windows.Controls.Input.dllTelerik.Windows.Controls.Navigation.dllTelerik.Windows.Controls.ScheduleView.dllTelerik.Windows.Data.dll
    ![note](note.jpg)
    	

Check [Getting Started]({{slug:getting-started}}) for more details about adding the RadScheduleView to the page.


        You can download the complete project from 
        [here](http://www.telerik.com/community/code-library/silverlight/scheduleview/binding-to-database-example.aspx).
        

# Creating WPF Application

Start this walkthrough by creating a WPF application in the Visual Studio 2010.
	

Add the following references to the project:Telerik.Windows.Controls.dllTelerik.Windows.Controls.Input.dllTelerik.Windows.Controls.Navigation.dllTelerik.Windows.Controls.ScheduleView.dllTelerik.Windows.Data.dll
    ![note](note.jpg)
    	

Check [Getting Started]({{slug:getting-started}}) for more details about adding the RadScheduleView to the project.


        You can download the complete project from 
        [here](http://www.telerik.com/community/code-library/wpf/scheduleview/binding-to-database-example.aspx).
        [RadScheduleView Types and Sources]({{slug:radscheduleview-types-and-sources}})
