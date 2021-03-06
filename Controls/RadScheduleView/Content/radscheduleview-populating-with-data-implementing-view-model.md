---
title: Implementing View-ViewModel 
meta_title: Implementing View-ViewModel 
meta_description: description.
slug: implementing-view-viewmodel-
tags:implementing,view-viewmodel,
publish:True
---


# 

The purpose of this tutorial is to show you how to bind a __RadScheduleView__ with a ViewModel.
        >
            Before reading this tutorial you should get familiar with the <link xlink:href="2268BE7E-A271-4468-B0CC-9958C1357EF0" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5">Data Binding</link> support of the <legacyBold xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5">RadScheduleView</legacyBold> control.
          

* 
            Add a new __RadScheduleView__ declaration in your XAML
            


 __XAML__
    


	<telerik:RadScheduleView />



* 
            Create a new class named __MyViewModel__.
            


 __C#__
    


	public class MyViewModel
	{
	}






 __VB.NET__
    


	Public Class MyViewModel
	End Class



* 
            In the __MyViewModel __class add two properties:
            

* __Appointments__ - we will bind the __AppointmentsSource__ property of the __RadScheduleView__ to this property.
              

* __ResourcesTypes __- we will bind the __ResourceTypesSource __property of the __RadScheduleView__ to this property.
              


 __C#__
    


	private ObservableCollection<Appointment> appointments;
	private ObservableCollection<ResourceType> resourceTypes;
	public ObservableCollection<Appointment> Appointments
	{
	    get
	    {
	        return this.appointments;
	    }
	    set
	    {
	        this.appointments = value;
	    }
	}
	public ObservableCollection<ResourceType> ResourcesTypes
	{
	    get
	    {
	        return this.resourceTypes;
	    }
	    set
	    {
	        this.resourceTypes= value;
	    }
	}






 __VB.NET__
    


	Private m_Appointments As ObservableCollection(Of Appointment)
	Private m_ResourceTypes As ObservableCollection(Of ResourceType)
	
	Public Property Appointments() As ObservableCollection(Of Appointment)
		Get
			Return Me.m_Appointments
		End Get
		Private Set(value As ObservableCollection(Of Appointment))
			Me.m_Appointments = value
		End Set
	End Property
	
	Public Property ResourceTypes() As ObservableCollection(Of ResourceType)
		Get
			Return Me.m_ResourceTypes
		End Get
		Private Set(value As ObservableCollection(Of ResourceType))
			Me.m_ResourceTypes = value
		End Set
	End Property



* 
            Let's create a method in the ViewModel that generates some Resources:
            


 __C#__
    


	private ObservableCollection<ResourceType> GenerateResourceTypes()
	{
	    ObservableCollection<ResourceType> result = new ObservableCollection<ResourceType>();
	
	    ResourceType roomType = new ResourceType("Room");
	    Resource room102 = new Resource("Room 102");
	    Resource room203 = new Resource("Room 203");
	    Resource room406 = new Resource("Room 406");
	    roomType.Resources.Add(room102);
	    roomType.Resources.Add(room203);
	    roomType.Resources.Add(room406);
	
	    ResourceType speakerType = new ResourceType("Speaker");
	    Resource tomSpeaker = new Resource("Tom");
	    Resource peterSpeaker = new Resource("Peter");
	    speakerType.Resources.Add(tomSpeaker);
	    speakerType.Resources.Add(peterSpeaker);
	
	    result.Add(roomType);
	    result.Add(speakerType);
	    return result;
	}






 __VB.NET__
    


	Private Function GenerateResourceTypes() As ObservableCollection(Of ResourceType)
	 Dim result As New ObservableCollection(Of ResourceType)()
	 Dim roomType As New ResourceType("Room")
	 Dim room102 As New Resource("Room 102")
	 Dim room203 As New Resource("Room 203")
	 Dim room406 As New Resource("Room 406")
	 roomType.Resources.Add(room102)
	 roomType.Resources.Add(room203)
	 roomType.Resources.Add(room406)
	 Dim speakerType As New ResourceType("Speaker")
	 Dim tomSpeaker As New Resource("Tom")
	 Dim peterSpeaker As New Resource("Peter")
	 speakerType.Resources.Add(tomSpeaker)
	 speakerType.Resources.Add(peterSpeaker)
	 result.Add(roomType)
	 result.Add(speakerType)
	 Return result
	End Function



* 
            All we have to do is to initialize the __resourceTypes__ and __appointments__ fields:
            


 __C#__
    


	public MyViewModel()
	{
	    this.resourceTypes = this.GenerateResourceTypes();
	    this.appointments = new ObservableCollection<Appointment>();
	}




 __VB.NET__
    


	Public Sub New()
	 Me.resourceTypes = Me.GenerateResourceTypes()
	 Me.appointments = New ObservableCollection(Of Appointment)()
	End Sub



* 
            The ViewModel is complete. Now, let's return to the View. Add some __ViewDefinitions__, __GroupDescriptionsSource__ and bind the __AppointmentsSource__ and __ResourceTypes__


 __XAML__
    


	<telerik:RadScheduleView AppointmentsSource="{Binding Appointments}" 
	                         ResourceTypesSource="{Binding ResourcesTypes}" >
	    <telerik:RadScheduleView.ViewDefinitions>
	        <telerik:DayViewDefinition />
	        <telerik:WeekViewDefinition />
	        <telerik:TimelineViewDefinition />
	    </telerik:RadScheduleView.ViewDefinitions>
	    <telerik:RadScheduleView.GroupDescriptionsSource>
	        <telerik:GroupDescriptionCollection>
	            <telerik:DateGroupDescription />
	            <telerik:ResourceGroupDescription ResourceType="Speaker" />
	            <telerik:ResourceGroupDescription ResourceType="Room" />
	        </telerik:GroupDescriptionCollection>
	    </telerik:RadScheduleView.GroupDescriptionsSource>
	</telerik:RadScheduleView>



* 
            Finally, set the DataContext:
            


 __C#__
    


	this.DataContext = new MyViewModel();




 __VB.NET__
    


	Me.DataContext = New MyViewModel()



 * [Implementing View-ViewModel ]({{slug:implementing-view-viewmodel-}})
