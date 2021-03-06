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
	
	public static void SaveData()
	{
		if (ScheduleViewRepository.Context.HasChanges && !ScheduleViewRepository.Context.IsSubmitting)
		{
			try
			{
				ScheduleViewRepository.Context.SubmitChanges(OnSubmitChangesCompleted, null);
			}
			catch (System.Exception)
			{
				throw;
			}
		}
	}



# ViewModel

In the constructor we load the data for the ScheduleView control (without appointments, they are loaded later). 
      First, we need to load the SqlResource and SqlResourceTypes. When both are loaded, we can added the resources to the ResourceTypes collection.
	  

Load the SqlTimeMarkers and the SqlCategories and add them to the TimeMarkers and Categories collections.
		

Here is the code:




 __C#__
    


	private void LoadData()
	{
		ScheduleViewRepository.Context.Load(ScheduleViewRepository.Context.GetSqlResourcesQuery()).Completed += (o, e) =>
		{
			ScheduleViewRepository.Context.Load(ScheduleViewRepository.Context.GetSqlResourceTypesQuery()).Completed += (s, a) =>
			{
				this.ResourceTypes.AddRange((s as LoadOperation).Entities);
			};
	
			this.OnPropertyChanged(() => this.ResourceTypes);
		};
	
		ScheduleViewRepository.Context.Load(ScheduleViewRepository.Context.GetTimeMarkersQuery()).Completed += (o, e) =>
		{
			this.TimeMarkers.AddRange((o as LoadOperation).Entities);
		};
	
		ScheduleViewRepository.Context.Load(ScheduleViewRepository.Context.GetCategoriesQuery()).Completed += (o, e) =>
		{
			this.Categories.AddRange((o as LoadOperation).Entities);
		};
	}



Also, we need to handle the Appointments.CollectionChanged event and in the handler we add or remove the items from the EntitySets:
        




 __C#__
    


	private void OnAppointmentsCollectionChanged(object sender, NotifyCollectionChangedEventArgs e)
	{
		if (e.Action == NotifyCollectionChangedAction.Add)
		{
			var app = e.NewItems == null ? null : e.NewItems[0] as SqlAppointment;
			if (app != null && app.EntityState != EntityState.Unmodified)
			{
				ScheduleViewRepository.Context.SqlAppointments.Add(app);
			}
		}
		else if (e.Action == NotifyCollectionChangedAction.Remove)
		{
			var app = e.OldItems == null ? null : e.OldItems[0] as SqlAppointment;
			if (app != null && ScheduleViewRepository.Context.SqlAppointments.Contains(app))
			{
				if (app.RecurrenceRule != null)
				{
					foreach (SqlExceptionOccurrence item in app.RecurrenceRule.Exceptions)
					{
						ScheduleViewRepository.Context.SqlExceptionOccurrences.Remove(item);
					}
				}
	
				foreach (var resource in app.SqlAppointmentResources)
				{
					ScheduleViewRepository.Context.SqlAppointmentResources.Remove(resource);
				}
				ScheduleViewRepository.Context.SqlAppointments.Remove(app);
			}
		}
	}

>
        You can download the complete project from 
        <externalLink xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5"><linkText>here</linkText><linkUri>http://www.telerik.com/community/code-library/silverlight/scheduleview/binding-to-database-example.aspx</linkUri></externalLink>.
        
