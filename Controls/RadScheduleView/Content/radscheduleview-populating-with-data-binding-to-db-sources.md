___
title: RadScheduleView Types and Sources
meta_title: RadScheduleView Types and Sources
meta_description: 
slug :radscheduleview types and sources
tags :radscheduleview,types,and,sources
publish :True
___


# 

The ScheduleView control exposes several Sources that enable data binding:__AppointmentsSource__ - gets or sets the data source (__IEnumerable__) used to generate  the Appointments__ResourceTypesSource__ - gets or sets the data source (__IEnumerable__) used to generate the ResourceTypes__CategoriesSource__ - gets or sets the data source (__IEnumerable__) used to generate the Categories__TimeMarkersSource__ - gets or sets the data source (__IEnumerable__) used to generate the TimeMarkers



With its current version RadScheduleView exposes several important interfaces: __ITimeMarker, IResourceType, IResource, IRecurrenceRule, IExceptionOccurrence, IAppointment, IExtendedAppointment, ICategory__. Implementing these interfaces allows the developer to plug custom objects and to not work with the default ones (Appointment, Resource, RecurrenceRule, ExceptionOccurrence, Category, TimeMarker). We are going to use these interfaces to plug the entities from the Entity Framework.

Here you could refer to the class diagram for more detailed information about the interfaces:

[](067f5317-3365-4f80-8a02-05be6b1fb1ec)