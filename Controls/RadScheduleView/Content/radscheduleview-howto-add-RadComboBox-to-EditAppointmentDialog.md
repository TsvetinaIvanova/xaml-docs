___
title: Add RadComboBox to a custom EditAppointmentDialog
meta_title: Add RadComboBox to a custom EditAppointmentDialog
meta_description: 
slug :add radcombobox to a custom editappointmentdialog
tags :add,radcombobox,to,a,custom,editappointmentdialog
publish :True
___



        This tutorial explains how to bind additional controls in a custom EditAppointmentDialog to properties in the ViewModel of the __RadScheduleView__.
      

Before we proceed, check these topics:[Implementing View-ViewModel](16E2654A-2813-4277-999A-6B510F045C43)[Custom Dialogs](85B3264C-F847-4860-95E8-45BD51423977)[Custom Appointment](401E5B97-3FC0-47ED-9C4A-2DDE80D769A3)


        Let’s have the following __RadScheduleView__ with EditAppointmentDialogStyle set to the generated Style:
      
<telerik:RadScheduleView x:Name="ScheduleView"
    AppointmentsSource="{Binding Appointments}"
    EditAppointmentDialogStyle="{StaticResource EditAppointmentDialogStyle}">
   <telerik:RadScheduleView.ViewDefinitions>
       <telerik:DayViewDefinition />
 …
   </telerik:RadScheduleView.ViewDefinitions>
</telerik:RadScheduleView>

RadComboBox is added to the ControlTemplate of the EditAppointmentDialog:
<ControlTemplate x:Key="EditAppointmentTemplate" TargetType="local:SchedulerDialog">
  ... 
    <telerik:RadComboBox  />
  ...    
</ControlTemplate>


        The ViewModel of the __ScheduleView__ has an additional property called “ComboBoxItems” which will be used to populate it:
      
public class MyViewModel:ViewModelBase
{
    public ObservableCollection<Appointment> Appointments
    {
        get;
        private set;
    }
    public ObservableCollection<string> ComboBoxItems
    {
        get;
        private set;
    }
    public MyViewModel()
    {
        Appointments = new ObservableCollection<Appointment>() {
            new Appointment() {
                Subject="test app",
                Start = DateTime.Now,
                End = DateTime.Now.AddHours(2)
            }
        };
        ComboBoxItems = new ObservableCollection<string>() {
            "item1", "item2", "item3"
        };
    }
}
Public Class MyViewModel
    Public Property Appointments() As ObservableCollection(Of Appointment)
        Get
            Return m_Appointments
        End Get
        Private Set(value As ObservableCollection(Of Appointment))
            m_Appointments = value
        End Set
    End Property
    Private m_Appointments As ObservableCollection(Of Appointment)
    Public Property ComboBoxItems() As ObservableCollection(Of String)
        Get
            Return m_ComboBoxItems
        End Get
        Private Set(value As ObservableCollection(Of String))
            m_ComboBoxItems = value
        End Set
    End Property
    Private m_ComboBoxItems As ObservableCollection(Of String)

    Public Sub New()
        Appointments = New ObservableCollection(Of Appointment)() From {
         New Appointment() With {
          .Subject = "test app",
          .Start = DateTime.Now,
         .[End] = DateTime.Now.AddHours(2)
        }
        }
        ComboBoxItems = New ObservableCollection(Of String)() From {
         "item1",
         "item2",
         "item3"
        }
    End Sub
End Class

# bindingtodatacontext

If the DataContext is set in XAML:
<UserControl.Resources>
    <my:MyViewModel x:Key="MyViewModel" />
    ...
</UserControl.Resources>

The ItemsSource can be bound like this:
<telerik:RadComboBox ItemsSource="{Binding Source={StaticResource MyViewModel}, Path=ComboBoxItems, Mode=TwoWay}" />

Here is the result:


               
            


    ![tip](tip.jpg)
    	


            In order to preselect a certain item in the RadComboBox,  bind __SelectedItem__  to a  property in your [custom appointment](401E5B97-3FC0-47ED-9C4A-2DDE80D769A3) class:
          


<telerik:RadComboBox SelectedItem="{Binding Occurrence.Appointment.ComboBoxItem, Mode=TwoWay}"
            ItemsSource="{Binding Source={StaticResource MyViewModel}, Path=ComboBoxItems, Mode=TwoWay}" />
