---
title: Prevent Dialogs from Opening
meta_title: Prevent Dialogs from Opening
meta_description: description.
slug: prevent-dialogs-from-opening
tags:prevent,dialogs,from,opening
publish:True
---


This article covers the following topics:

* [How to hide a RadScheduleView dialog](#hidedialog)

* [How to skip ConfirmDeleteDialog.](#skipconfirmdeletedialog)

* [How to preselect a certain option in RecurrenceChoiceDialog.](#preselectrecurrencechoicedialog)



# hidedialogHow to hide a RadScheduleView dialog

In order to prevent a specific dialog from appearing , the ShowDialog event of the __RadScheduleView__ should be cancelled. The event args contain a property called __DialogViewModel__ which can be used to determine which dialog is going to be opened.

For example the view model for the __EditAppointmentDialog__ is __AppointmentDialogViewModel__. The following code snippet shows how it can be cancelled:


 __XAML__
    


	<telerik:RadScheduleView AppointmentsSource="{Binding Appointments}" ShowDialog="RadScheduleView_ShowDialog">
	…
	</telerik:RadScheduleView>




 __C#__
    


	private void RadScheduleView_ShowDialog(object sender, ShowDialogEventArgs e)
	{
	    if (e.DialogViewModel is AppointmentDialogViewModel)
	        e.Cancel = true;
	}




 __VB.NET__
    


	Private Sub RadScheduleView_ShowDialog(sender As System.Object, e As ShowDialogEventArgs)
	    If TypeOf e.DialogViewModel Is AppointmentDialogViewModel Then
	       e.Cancel = True
	    End If
	End Sub

>To learn more about <legacyBold xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5">RadScheduleView</legacyBold> events, check <link xlink:href="DA2E2C18-FE43-486A-B8E2-055460967DE8" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5">here</link>.

# skipconfirmdeletedialogHow to skip ConfirmDeleteDialog

In this case __DefaultDialogResult __ property of the event args should be set in order to stimulate pressing OK/Cancel in the dialog. If __DefaultDialogResult__ is set to “true”, the appointment will be directly deleted:


 __C#__
    


	private void RadScheduleView_ShowDialog(object sender, ShowDialogEventArgs e)
	{
	    if (e.DialogViewModel is ConfirmDialogViewModel)
	    {
	        e.DefaultDialogResult = true;
	        e.Cancel = true;
	    }
	}




 __VB.NET__
    


	Private Sub RadScheduleView_ShowDialog(sender As System.Object, e As ShowDialogEventArgs)
	    If TypeOf e.DialogViewModel Is ConfirmDialogViewModel Then
	        e.DefaultDialogResult = True
	        e.Cancel = True
	    End If
	End Sub





# preselectrecurrencechoicedialogHow to preselect  a certain option in RecurrenceChoiceDialog

By default  “Open/Delete the occurrence” option is selected in RecurrenceChoiceDialog.  This can be changed in ShowDialog event by setting __IsSeriesModeSelected__ property of the RecurrenceChoiceDialogViewModel:


 __C#__
    


	private void RadScheduleView_ShowDialog(object sender, ShowDialogEventArgs e)
	{
	    var dialogViewModel = e.DialogViewModel as RecurrenceChoiceDialogViewModel;
	    if (dialogViewModel != null)
	    {
	        dialogViewModel.IsSeriesModeSelected = true;
	    }
	}




 __VB.NET__
    


	Private Sub RadScheduleView_ShowDialog(sender As System.Object, e As ShowDialogEventArgs)
	   Dim dialogViewModel = TryCast(e.DialogViewModel, RecurrenceChoiceDialogViewModel)
	   If dialogViewModel IsNot Nothing Then
	       dialogViewModel.IsSeriesModeSelected = True
	   End If
	End Sub

Check [here](85B3264C-F847-4860-95E8-45BD51423977) for more information about RadScheduleView dialogs.
