

# Telerik RadScheduleView for WPF Q1 2011

# Breaking changes:

* The IAppointment .Resources property is now IList

* The RadScheduleView.CategoriesSource is now IEnumerable

* The RadScheduleView.ResourceTypesSource is now IEnumerable

* The RadScheduleView.TimeMarkersSource collections is now IEnumerable

* The RadScheduleView.VisibleRangeStart/End properties are removed and they are changed with RadScheduleView.VisibleRange.Start/End

* In order to inherit the Slot class, you should implement Copy and CopyFrom methods

* SchedulerDragDropPayload is now obsolete – use ScheduleViewDragDropPayload instead

* ISchedulerDragDropBehavior is now obsolete – use IDragDropBehavior instead