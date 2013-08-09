---
title: Commands
meta_title: Commands
meta_description: description.
slug: commands
tags:commands
publish:True
---


__RadScheduleView__ exposes its functionality through various commands that can be executed on its behalf. All commands are placed in the static class __RadScheduleViewCommands__. 
      The purpose of this tutorial is to show you all of the commands exposed by the __RadScheduleViewCommands__ class and how to execute them.

* [CreateAppointment / CreateAppointmentWithDialog Commands](#Create_Appointment)

* [CreateInlineAppointment Command](#Create_Inline_Appointment)

* [EditAppointment Command](#Edit_Appointment)

* [DeleteAppointment Command](#Delete_Appointment)

* [EditRecurrenceRule Command](#Edit_RecurrenceRule)

* [DeleteRecurrenceRule Command](#Delete_RecurrenceRule)

* [EditParentAppointment Command](#Edit_ParentAppointment)

* [SetDayViewMode Command](#SetDayViewMode)

* [SetWeekViewMode Command](#SetWeekViewMode)

* [SetMonthViewMode Command](#SetMonthViewMode)

* [SetTimelineViewMode Command](#SetTimelineViewMode)

* [IncreaseVisibleDateLarge /  DecreaseVisibleDateLarge Commands](#IncreaseVisibleDateLarge)

* [SetAppointmentImportance Command](#SetAppointmentImportance)

* [GoToPreviousAppointment / GoToNextAppointment Commands](#GoToPreviousAppointment)

# Create_AppointmentCreateAppointment / CreateAppointmentWithDialog Commands

When you want to create a new appointment and show the EditAppointmentDialog, then you need to use the __CreateAppointment__ or __CreateAppointmentWithDialog__ commands. 
        If no parameter is passed, the __SelectedSlot__ of __RadScheduleView__ will be used for the new appointment start and end dates. 
        If you want to explicitly specify which will be the start and end date you should pass a parameter of type __IDateSpan__ (for example Slot is an __IDateSpan__).



The difference between both commands is when neither the parameter nor the __SelectedSlot__ is set. In this case only the __CreateAppointmentWithDialog__ command will show EditAppointmentDialog for the first visible slot, while __CreateAppointment__ command won’t be executed.




 __C#__
    


	RadScheduleViewCommands.CreateAppointment.Execute(null, ScheduleView);
	RadScheduleViewCommands.CreateAppointmentWithDialog.Execute(null, ScheduleView);



# Create_Inline_AppointmentCreateInlineAppointment Command

Use it when you want to create a new appointment via the inline editing. If no parameter is passed, the __SelectedSlot__ of __RadScheduleView__ will be used for the new appointment start and end dates. If you want to explicitly specify which will be the start and end date you should pass a parameter of type __IDateSpan__ (for example __Slot__ is an __IDateSpan__):




 __C#__
    


	RadScheduleViewCommands.CreateInlineAppointment.Execute(null, ScheduleView);

>IsInlineEditingEnabled property of the RadScheduleView should be set in order to use the command.
      		

# Edit_AppointmentEditAppointment Command

Use it when you want to show the edit dialog for an appointment. If no parameters are passed it uses the __SelectedAppointment__ of __RadScheduleView__. By default this command is bound to double click on appointment.




 __C#__
    


	RadScheduleViewCommands.EditAppointment.Execute(null, ScheduleView);



# Delete_AppointmentDeleteAppointment Command

When you want to remove an appointment from __AppointmentsSource__ collection, then you need to use the __DeleteAppointment__ command. If no parameter is passed the __SelectedAppointment__ will be used.




 __C#__
    


	RadScheduleViewCommands.DeleteAppointment.Execute(null, ScheduleView);



# Edit_RecurrenceRuleEditRecurrenceRule Command

When you want to open EditRecurrenceDialog, then you need to use the __EditRecurrenceRule__ command. 
        This command is used mainly in EditAppointmentDialog. 

# Delete_RecurrenceRuleDeleteRecurrenceRule Command

When you want to remove the recurrence, then you need to use __DeleteRecurrenceRule__ Command. 
        The command is used mainly in EditRecurrenceDialo

# Edit_ParentAppointmentEditParentAppointment Command

If you want to edit the master appointment, when the user has initiated editing of an occurrence or exception from appointment's RecurrenceRule, you need to use the __EditParentAppointment__ command. 
        This command is used mainly in EditAppointmentDialog.

# SetDayViewModeSetDayViewMode Command

Executing this command will result in setting the RadScheduleView’s __ActiveViewDefinition__ property to __DayViewDefinition__.




 __C#__
    


	RadScheduleViewCommands.SetDayViewMode.Execute(null, ScheduleView);



# SetWeekViewModeSetWeekViewMode Command

Executing this command will result in setting the RadScheduleView's __ActiveViewDefinition__ property to __WeekViewDefinition__.




 __C#__
    


	RadScheduleViewCommands.SetWeekViewMode.Execute(null, ScheduleView);



# SetMonthViewModeSetMonthViewMode Command

Executing this command will result in setting the RadScheduleView's __ActiveViewDefinition__ property to __MonthViewDefinition__.




 __C#__
    


	RadScheduleViewCommands.SetMonthViewMode.Execute(null, ScheduleView);



# SetTimelineViewModeSetTimelineViewMode Command

Executing this command will result in setting the RadScheduleView's __ActiveViewDefinition__ property to __TimelineViewDefinition__.




 __C#__
    


	RadScheduleViewCommands.SetTimelineViewMode.Execute(null, ScheduleView);



# IncreaseVisibleDateLargeIncreaseVisibleDateLarge /  DecreaseVisibleDateLarge Commands

Increases/decreases the first visible date with n months or days, where n is the value of the __LargeChangeInterval__ property of the ActiveViewDefinition. Executing this command is equivalent to changing the displayed days using the navigation buttons.




 __C#__
    


	RadScheduleViewCommands.IncreaseVisibleDateLarge.Execute(null, ScheduleView);
	RadScheduleViewCommands.DecreaseVisibleDateLarge.Execute(null, ScheduleView);



# SetAppointmentImportanceSetAppointmentImportance Command

When you want to set the Appointment's Importance property, then you need to execute the __SetAppointmentImportance__ command. 
        This command is used primely in EditAppointmentDialog.

# GoToPreviousAppointmentGoToPreviousAppointment / GoToNextAppointment Commands

Use these commands when you want to navigate to the previous/next appointment outside the visible range:




 __C#__
    


	RadScheduleViewCommands.GoToPreviousAppointment.Execute(null, ScheduleView);
	RadScheduleViewCommands.GoToNextAppointment.Execute(null, ScheduleView);


