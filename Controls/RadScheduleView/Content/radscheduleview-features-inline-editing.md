---
title: Inline Editing
meta_title: Inline Editing
meta_description: description.
slug: inline-editing
tags:inline,editing
publish:True
---


RadScheduleView supports inline editing of the displayed appointment's subject. The purpose of this tutorial is to show you:
	

* [How to start, commit and cancel the inline process run-time](#HowTo)

* [How to enable\disable the inline editing behavior](#HowTo_Enable_Disable)

# HowToHow to start, commit and cancel the inline process run-time.

Inline editing lets you edit the appointment's subject right where you see it in the appointment. Just select the appointment, press F2 and type your changes.

* Select the target appointment:
          	

![radscheduleview inline editing 01](images/radscheduleview_inline_editing_01.png)

* Press __F12__ and type the changes:
          	

![radscheduleview inline editing 02](images/radscheduleview_inline_editing_02.png)

* Press __Enter__ or click outside the textbox in order to apply the change:
          	

![radscheduleview inline editing 03](images/radscheduleview_inline_editing_03.png)>Pressing the <legacyBold xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5">Enter</legacyBold> key will apply your changes, while pressing the <legacyBold xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5">Esc</legacyBold> key will reject them.

>It is important to know that if you edit an appointment which is result of recurrence, then the changes will be applied to the whole series.

# HowTo_Enable_DisableHow to enable\disable the inline editing behavior

The RadScheduleView exposes a property __IsInlineEditingEnabled__ which allows you to enable\disable the inline editing behavior.>The default value of the <legacyBold xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5">IsInlineEditingEnabled</legacyBold> property is True. Which means that the inline editing behavior is allowed by default.
      	If you want to disable the inline editing behavior, you should set the __IsInlineEditingEnabled__ property to False.
      	


 __XAML__
    


	<telerik:RadScheduleView x:Name="scheduleView" IsInlineEditingEnabled="False"/>




 __C#__
    


	scheduleView.IsInlineEditingEnabled = false;


