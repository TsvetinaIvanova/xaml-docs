

# Telerik RadScheduleView for WPF Q1 2011

# Breaking changes:The IAppointment .Resources property is now IListThe RadScheduleView.CategoriesSource is now IEnumerableThe RadScheduleView.ResourceTypesSource is now IEnumerableThe RadScheduleView.TimeMarkersSource collections is now IEnumerableThe RadScheduleView.VisibleRangeStart/End properties are removed and they are changed with RadScheduleView.VisibleRange.Start/EndIn order to inherit the Slot class, you should implement Copy and CopyFrom methodsSchedulerDragDropPayload is now obsolete – use ScheduleViewDragDropPayload insteadISchedulerDragDropBehavior is now obsolete – use IDragDropBehavior instead