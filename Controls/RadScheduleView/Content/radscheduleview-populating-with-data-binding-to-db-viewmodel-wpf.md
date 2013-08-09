---
title: View and ViewModel
meta_title: View and ViewModel
meta_description: description.
slug: view-and-viewmodel
tags:view,and,viewmodel
publish:True
---


# Presentation tier (xaml)

When the models are defined, we need to create the __ViewModel__ (refer to __ScheduleViewViewModel__ class) and bind the ScheduleView control in the xaml:




 __XAML__
    


	<Grid x:Name="LayoutRoot" Background="White">
		<Grid.RowDefinitions>
			<RowDefinition Height="*"/>
			<RowDefinition Height="Auto"/>
		</Grid.RowDefinitions>
		<telerik:RadBusyIndicator IsBusy="{Binding IsLoading}">
			<telerik:RadScheduleView Grid.Row="0"	 
				AppointmentsSource="{Binding Appointments}"
				ResourceTypesSource="{Binding ResourceTypes}"
				TimeMarkersSource="{Binding TimeMarkers}"
				CategoriesSource="{Binding Categories}"
				VisibleRangeChangedCommand="{Binding VisibleRangeChanged}"
				VisibleRangeChangedCommandParameter="{Binding VisibleRange, RelativeSource={RelativeSource Self}}">
				<telerik:RadScheduleView.ViewDefinitions>
					<telerik:WeekViewDefinition />
					<telerik:MonthViewDefinition  />
					<telerik:TimelineViewDefinition />
				</telerik:RadScheduleView.ViewDefinitions>
				<telerik:RadScheduleView.GroupDescriptionsSource>
					<telerik:GroupDescriptionCollection>
						<telerik:DateGroupDescription />
						<telerik:ResourceGroupDescription ResourceType="Level" ShowNullGroup="True" />
						<telerik:ResourceGroupDescription ResourceType="Speaker" ShowNullGroup="True" />
					</telerik:GroupDescriptionCollection>
				</telerik:RadScheduleView.GroupDescriptionsSource>
			</telerik:RadScheduleView>
		</telerik:RadBusyIndicator>
		<Button Grid.Row="1" Content="Save data" HorizontalAlignment="Center" Command="{Binding SaveCommand}" VerticalAlignment="Center"/>
	</Grid>

>The appointments are loaded from the database when the VisibleRangeChanged command is executed.

When "Save data" button is clicked, we save the data to the server.




 __C#__
    


	private void OnSaveExecuted(object param) 
	{
		ScheduleViewRepository.SaveData();
	}
	
	...
	
	public static bool SaveData()
	{
		return ScheduleViewRepository.Context.SaveChanges() > 0;
	}



# ViewModel

In the constructor we load the data for the ScheduleView control (without appointments, they are loaded later).
					First, we need to load the SqlResource and SqlResourceTypes. When both are loaded, we can added the resources to the ResourceTypes collection.
				

Load the SqlTimeMarkers and the SqlCategories and add them to the TimeMarkers and Categories collections.
				

Here is the code:




 __C#__
    


	private void LoadData()
	{
		this.ResourceTypes.AddRange(ScheduleViewRepository.Context.SqlResourceTypes);
	
		this.TimeMarkers.AddRange(ScheduleViewRepository.Context.TimeMarkers);
	
		this.Categories.AddRange(ScheduleViewRepository.Context.Categories);
	}



Also, we need to handle the Appointments.CollectionChanged event and in the handler we add or remove the items from the ObjectSets:
        




 __C#__
    


	private void OnAppointmentsCollectionChanged(object sender, NotifyCollectionChangedEventArgs e)
	{
		if (e.Action == NotifyCollectionChangedAction.Add)
		{
			var app = e.NewItems == null ? null : e.NewItems[0] as SqlAppointment;
			if (app != null && app.EntityState == EntityState.Added)
			{
				ScheduleViewRepository.Context.AddToSqlAppointments(app);
			}
		}
		else if (e.Action == NotifyCollectionChangedAction.Remove)
		{
			var app = e.OldItems == null ? null : e.OldItems[0] as SqlAppointment;
			if (app != null && ScheduleViewRepository.Context.SqlAppointments.Any(a => a.SqlAppointmentId == app.SqlAppointmentId))
			{
				if (app.RecurrenceRule != null)
				{
					var tempList = app.RecurrenceRule.Exceptions.ToList();
	
					foreach (SqlExceptionOccurrence item in tempList)
					{
						ScheduleViewRepository.Context.SqlExceptionOccurrences.DeleteObject(item);
					}
				}
	
				var tempAppList = ScheduleViewRepository.Context.SqlAppointmentResources.ToList();
	
				foreach (var item in tempAppList)
				{
					ScheduleViewRepository.Context.SqlAppointmentResources.DeleteObject(item);
				}
	
				ScheduleViewRepository.Context.SqlAppointments.DeleteObject(app);
			}
		}
	}

>
        You can download the complete project from 
        <externalLink xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5"><linkText>here</linkText><linkUri>http://www.telerik.com/community/code-library/wpf/scheduleview/binding-to-database-example.aspx</linkUri></externalLink>.
        
