___
title: Load on demand with RadScheduleView
meta_title: Load on demand with RadScheduleView
meta_description:description
slug:load_on_demand_with_radscheduleview
tags:load,on,demand,with,radscheduleview
publish:True
___


This tutorial demonstrates how you can load the appointments depending on the visible range of the RadScheduleView. This can be very useful in one real-time scenario when the number of appointments it's very large.

There are two approaches to accomplish this. You can choose one of them according to your scenario:
          Using the __RadScheduleView.VisibleRangeChanged__ event. The __VisibleRangeChanged__ event handler receives two arguments:
          
              The __sender__ argument contains the RadScheduleView. This argument is of type object, but can be cast to the __RadScheduleView__ type.
            The System.EventArgs object.
          Using the __RadScheduleView.VisibleRangeChangedCommandProperty__ and the __RadScheduleView.VisibleRangeChangedCommandParameterProperty__. This approach is effective if you wish to load the visible appointments using the MVVM pattern.
        



# 
        Using the __VisibleRangeChanged __event.
      
            Handle the VisibleRangeChanged event:
            


<telerik:RadScheduleView VisibleRangeChanged="scheduleView_VisibleRangeChanged">
...
</telerik:RadScheduleView>
            Get the VisibleRange from the sender:
            


private void scheduleView_VisibleRangeChanged(object sender, System.EventArgs e)
{
 var range = (sender as RadScheduleView).VisibleRange;
 }
Private Sub scheduleView_VisibleRangeChanged(sender As Object, e As System.EventArgs)

 Dim range = TryCast(sender, RadScheduleView).VisibleRange
 End Sub
            Load the appointments:
            


private void scheduleView_VisibleRangeChanged(object sender, System.EventArgs e)
{
   var range = (sender as RadScheduleView).VisibleRange;
   this.LoadAppointmentsByRange(range);
}
Private Sub scheduleView_VisibleRangeChanged(sender As Object, e As System.EventArgs)

 Dim range = TryCast(sender, RadScheduleView).VisibleRange
 Me.LoadAppointmentsByRange(range)
End Sub

# 
        Using the __VisibleRangeChangedCommand__Create a RadScheduleViewViewModel class.
            Add VisibleRangeChanged property of type ICommand:
            


private ICommand visibleRangeChanged;
  public ICommand VisibleRangeChanged
  {
   get
   {
    return this.visibleRangeChanged;
   }
   set
   {
    this.visibleRangeChanged = value;
   }
  }
            Initialize the VisibleRangeChanged property in the constructor of the RadScheduleViewViewModel and load the appointments in the VisibleRangeExecuted method.
            


private ICommand visibleRangeChanged;
  public ICommand VisibleRangeChanged
  {
   get
   {
    return this.visibleRangeChanged;
   }
   set
   {
    this.visibleRangeChanged = value;
   }
  }
public RadScheduleViewViewModel ()
  {
   this.VisibleRangeChanged = new DelegateCommand(this.VisibleRangeExecuted, this.CanVisibleRangeCanExecuted);
  }
private void VisibleRangeExecuted(object param)
  {
   // param is the value of the VisibleRange property. It is used to get the appointments only for the visual range.
   this.LoadAppointmentsByRange(param as DateSpan);
  }
private bool CanVisibleRangeCanExecuted(object param)
  {
   return param != null;
  }
Private visibleRangeChanged As ICommand
Public Property VisibleRangeChanged() As ICommand
 Get
  Return Me.visibleRangeChanged
 End Get
 Set
  Me.visibleRangeChanged = value
 End Set
End Property
Public Sub New()
 Me.VisibleRangeChanged = New DelegateCommand(Me.VisibleRangeExecuted, Me.CanVisibleRangeCanExecuted)
End Sub
Private Sub VisibleRangeExecuted(param As Object)
 ' param is the value of the VisibleRange property. It is used to get the appointments only for the visual range.
 Me.LoadAppointmentsByRange(TryCast(param, DateSpan))
End Sub
Private Function CanVisibleRangeCanExecuted(param As Object) As Boolean
 Return param IsNot Nothing
End Function
            Bind the __VisibleRangeChangedCommand__ and __VisibleRangeChangedCommandParameter__


<scheduleView:RadScheduleView AppointmentsSource="{Binding Appointments}" 
         VisibleRangeChangedCommand="{Binding VisibleRangeChanged}" 
         VisibleRangeChangedCommandParameter="{Binding VisibleRange, RelativeSource={RelativeSource Self}}">
...
</scheduleView:RadScheduleView>
