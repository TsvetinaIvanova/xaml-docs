---
title: Edit Appointment
meta_title: Edit Appointment
meta_description: description.
slug: edit-appointment
tags:edit,appointment
publish:True
---


This topic describes the work flow for editing an appointment in __RadScheduleView__ control.
      

# Using UI

__RadScheduleView__ uses one and the same dialog to create and edit appointments. This topic describes the end-user's work flow for editing an existing appointment.
        


               
            ![RadScheduleView Edit Appointment](images/radscheduleview_end_user_capabilities_edit_appointment_01.png)

* 
            In order to edit an appointment just double click it in the 

* If the appointment is not a recurrent one, the edit appointment dialog appears immediately. 

* After the edit appointment dialog is opened, you can change the Subject, Description, Start and End time of the appointment.

* You can also change or assign category, time marker or importance by using the tool bar controls.

* You can also change the appointment recurrent.

* 
            If you have completed the appointment edit, click the 'Save & Close' button or press the 

* 
            If you want to cancel the appointment creation, click the X button or press the 

# Using code

You can edit an appointment using the code. Here are the steps to accomplish this:

* 
            Call 

* BeginEdit()

* BeginEdit( IAppointment

* BeginEdit( Occurrence

* 
            If 

* 
            Call 


 __C#__
    


	if (this.radScheduleView.BeginEdit(appointment))
	{
	    appointment.Subject = "New Subject";
	    this.radScheduleView.Commit();
	}




 __VB.NET__
    


	If Me.radScheduleView.BeginEdit(appointment) Then
	 appointment.Subject = "New Subject"
	 Me.radScheduleView.Commit()
	End If

[Understanding Appointments]({{slug:understanding-appointments}})[Create Appointment]({{slug:create-appointment}})[Delete Appointment]({{slug:delete-appointment}})
