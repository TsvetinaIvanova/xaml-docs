___
title: Inline Editing
meta_title: Inline Editing
meta_description: 
slug :inline editing
tags :inline,editing
publish :True
___


RadScheduleView supports inline editing of the displayed appointment's subject. The purpose of this tutorial is to show you:
	[How to start, commit and cancel the inline process run-time](#HowTo)[How to enable\disable the inline editing behavior](#HowTo_Enable_Disable)

# HowToHow to start, commit and cancel the inline process run-time.

Inline editing lets you edit the appointment's subject right where you see it in the appointment. Just select the appointment, press F2 and type your changes.Select the target appointment:
          	

![radscheduleview inline editing 01](../Media\radscheduleview_inline_editing_01.png)Press __F12__ and type the changes:
          	

![radscheduleview inline editing 02](../Media\radscheduleview_inline_editing_02.png)Press __Enter__ or click outside the textbox in order to apply the change:
          	

![radscheduleview inline editing 03](../Media\radscheduleview_inline_editing_03.png)
    ![tip](tip.jpg)
    	

Pressing the __Enter__ key will apply your changes, while pressing the __Esc__ key will reject them.


    ![note](note.jpg)
    	

It is important to know that if you edit an appointment which is result of recurrence, then the changes will be applied to the whole series.

# HowTo_Enable_DisableHow to enable\disable the inline editing behavior

The RadScheduleView exposes a property __IsInlineEditingEnabled__ which allows you to enable\disable the inline editing behavior.
    ![tip](tip.jpg)
    	

The default value of the __IsInlineEditingEnabled__ property is True. Which means that the inline editing behavior is allowed by default.
      	If you want to disable the inline editing behavior, you should set the __IsInlineEditingEnabled__ property to False.
      	
<telerik:RadScheduleView x:Name="scheduleView" IsInlineEditingEnabled="False"/>
scheduleView.IsInlineEditingEnabled = false;
