A very common scenario when using RadScheduleView is the usage of custom appointments. When you create a **Custom Appointment** class you gain the ability to append additional properties to the base Appointment class, to add them to your custom AppointmentItem and optionally to its ToolTip, display them in the EditAppointment dialog while supporting the cancelation of editing. 

In this article we will explore the process of using custom appointments in RadScheduleView. We will go through the following steps:


[Create a custom appointment class and populate the RadScheduleView control with custom appointments](#Creating-a-Custom-Appointment-class)

[Modify the EditAppointment dialog to display the custom data of the newly created custom appointment class](#Creating-a-Custom-Appointment-dialog)

[Customize the AppointmentItem and its ToolTip to display the new data](#Changing-the-Style-of-the-AppointmentItem)

## Creating a Custom Appointment class
To create a custom appointment class you can start off with either of the following approaches : you can implement the **IAppointment**  interface or you can inherit from one of the classes that already implement this interface – AppointmentBase (the base implementation of the interface) or Appointment (an extended implementation). It is very important to provide your own implementations for the **Copy** and **CopyFrom** methods as they are used intensively in the editing process of the ScheduleView control. If you choose to implement the interface, the Copy and CopyFrom methods will be automatically implemented for you, but if you take the second approach and inherit from one of the base classes, you should keep this in mind. 

Let's create a simple task tracking system. For our Custom Appointment class we will inherit from Appointment. Out tracking system will need to show an additional field for the task progress – an indication of whether the task has finished or not. In order to enable editing in transactions of the new property we need to use the Storage method of the AppointmentBase class to access the instance which owns the fields. We will name our custom appointment class Task. Here is the creation of the Custom Appointment class: 
```C#
public class Task:Appointment
{
    private bool isDone;
    public bool IsDone
    {
        get
        {
             return this.Storage<Task>().isDone;
        }
        set
        {
             var storage = this.Storage<Task>();
             if (storage.isDone != value)
             {
                  storage.isDone = value;
                  this.OnPropertyChanged(() => this.IsDone);
             }
        }
    }
    public override IAppointment Copy()
    {
        var newAppointment = new Task();
        newAppointment.CopyFrom(this);
        return newAppointment;
    }
    public override void CopyFrom(IAppointment other)
    {
        var task = other as Task;
        if (task != null)
        {
                this.IsDone = task.IsDone;
        }
        base.CopyFrom(other);
    }
}
```

```Vb.NET
Public Class Task
 Inherits Appointment
 Private m_isDone As Boolean
 Public Property IsDone() As Boolean
  Get
   Return Me.Storage(Of Task)().m_isDone
  End Get
  Set
   Dim storage = Me.Storage(Of Task)()
   If storage.m_isDone <> value Then
    storage.m_isDone = value
    Me.OnPropertyChanged("IsDone")
   End If
  End Set
 End Property
 Public Overrides Function Copy() As IAppointment
  Dim newAppointment = New Task()
  newAppointment.CopyFrom(Me)
  Return newAppointment
 End Function
 Public Overrides Sub CopyFrom(other As IAppointment)
  Dim task = TryCast(other, Task)
  If task IsNot Nothing Then
   Me.IsDone = task.IsDone
  End If
  MyBase.CopyFrom(other)
 End Sub
End Class
```
For the next step, it is important to set the AppointmentsSource of RadScheduleView to be of type `IList<Task>`, because this way the ScheduleView knows that our custom appointments should be of type Task. Let's create an **ObservableCollection\<Task\>** using the following approach: 
## Creating a custom Appointment Dialog
## Changing the Style of the AppointmentItem


And here is the result so far:
![Alt text](../images/custom_appointment1.png "Optional title")

