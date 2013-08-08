---
title: Drag and Drop with RadScheduleView
meta_title: Drag and Drop with RadScheduleView
meta_description: description.
slug: drag-and-drop-with-radscheduleview
tags:drag,and,drop,with,radscheduleview
publish:True
---


# 


                 
              ![RadScheduleView - Drag And Drop](images/scheduleview_features_draganddrop.png)

__RadScheduleView__ uses __DragDropManager__ to implement drag and drop of appointments. In order to add some custom logic for drag and drop, you can inherit __Telerik.Windows.Controls.ScheduleViewDragDropBehavior__ class. There are several method you can override:
        

* CanDrop

* CanStartDrag

* Drop

* CanResize

* CanStartResize

* Resize

* DragDropCompleted

* ConvertDraggedData

* CoerceDraggedItems

	>

The __state__ parameter of each method identifies the current drag operation.
          

After the CustomDragDropBehavior is implemented, all you need is to set it as RadScheduleView.DragDropBehavior:




 __XAML__
    

```XAML


<telerik:RadScheduleView.DragDropBehavior>
  <local:CustomDragDropBehavior />
</telerik:RadScheduleView.DragDropBehavior>

```



Check out the 
          
          Drag and Drop Example at 
          [WPF online demos](http://demos.telerik.com/wpf/)[online demo](http://demos.telerik.com/silverlight/#ScheduleView/DragDrop)
          to see the __RadScheduleView__'s Drag and Drop functionality in action.
        
