---
title: Delete Appointment
meta_title: Delete Appointment
meta_description: description.
slug: delete-appointment
tags:delete,appointment
publish:True
---


This topic describes the work flow for deleting an appointment in __RadScheduleView__ control.
      

# Using UI

* 
            In order to delete an appointment in the 

* If the appointment you are trying to delete is single one and is not part of any recurrence, a simple confirmation dialog appears asking you to confirm the deletion. Click 'OK' to confirm the deletion or 'Cancel' to stop it.


               
            ![RadScheduleView Delete Appointment](images/radscheduleview_end_user_capabilities_delete_appointment_01.png)

* If the appointment is part of a recurrence series, a more complex confirmation dialog appears asking you what do you want to delete.

* You can choose between two options:

* 'Delete this occurrence'

* 'Delete the series'

Select the option you wish and click 'OK' to confirm the deletion or 'Cancel' to stop it.



# Using code

You can delete an appointment using the code. Just Call __Remove()__ method of the __RadScheduleView__ control. It returns whether or not  the appointment or the occurrence can be removed. This method has 2 overloads:
          

* Remove(IAppointment appointment)

* Remove(Occurrence occurrence)


 __C#__
    	


this.radScheduleView.Remove(appointment);




 __XAML__
    	


Me.radScheduleView.Remove(appointment)

[Understanding Appointments]({{slug:understanding-appointments}})[Create Appointment]({{slug:create-appointment}})[Edit Appointment]({{slug:edit-appointment}})
