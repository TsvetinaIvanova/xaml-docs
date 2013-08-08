---
title: Load on demand with RadScheduleView
meta_title: Load on demand with RadScheduleView
meta_description: description.
slug: load-on-demand-with-radscheduleview
tags:load,on,demand,with,radscheduleview
publish:True
---


This tutorial demonstrates how you can load the appointments depending on the visible range of the RadScheduleView. This can be very useful in one real-time scenario when the number of appointments it's very large.

There are two approaches to accomplish this. You can choose one of them according to your scenario:

* 
          Using the 

* 
          Using the 



# 
        Using the __VisibleRangeChanged __event.
      

* 
            Handle the VisibleRangeChanged event:
            

* 
            Get the VisibleRange from the sender:
            

* 
            Load the appointments:
            

# 
        Using the __VisibleRangeChangedCommand__

* Create a RadScheduleViewViewModel class.

* 
            Add VisibleRangeChanged property of type ICommand:
            

* 
            Initialize the VisibleRangeChanged property in the constructor of the RadScheduleViewViewModel and load the appointments in the VisibleRangeExecuted method.
            

* 
            Bind the 
