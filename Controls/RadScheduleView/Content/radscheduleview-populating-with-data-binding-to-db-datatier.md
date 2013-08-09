---
title: Table Definitions and Relationships
meta_title: Table Definitions and Relationships
meta_description: description.
slug: table-definitions-and-relationships
tags:table,definitions,and,relationships
publish:True
---


The database diagram is very common to the class diagram of the RadScheduleView interfaces:

![radscheduleview populating with data schedule View Data Base Diagram](images/radscheduleview_populating_with_data_scheduleViewDataBaseDiagram.png)

# Table Definitions

We have table definitions in the database according for the following types in the RadScheduleView:

IAppointment & IExtendedAppointment![radscheduleview populating with data IAppointment](images/radscheduleview_populating_with_data_IAppointment.png)![radscheduleview populating with data IExtended Appointment](images/radscheduleview_populating_with_data_IExtendedAppointment.png)SqlAppointments![radscheduleview populating with data Sql Appointments](images/radscheduleview_populating_with_data_SqlAppointments.png)IResource![radscheduleview populating with data IResource](images/radscheduleview_populating_with_data_IResource.png)SqlResources![radscheduleview populating with data Sql Resources](images/radscheduleview_populating_with_data_SqlResources.png)IExceptionOccurrence![radscheduleview populating with data IException Occurence](images/radscheduleview_populating_with_data_IExceptionOccurence.png)SqlExceptionOccurrences![radscheduleview populating with data Sql Exception Occurrences](images/radscheduleview_populating_with_data_SqlExceptionOccurrences.png)IResourceType![radscheduleview populating with data IResource Type](images/radscheduleview_populating_with_data_IResourceType.png)SqlResourceTypes![radscheduleview populating with data Sql Resource Types](images/radscheduleview_populating_with_data_SqlResourceTypes.png)ICategory![radscheduleview populating with data ICategory](images/radscheduleview_populating_with_data_ICategory.png)Categories![radscheduleview populating with data Categories](images/radscheduleview_populating_with_data_Categories.png)ITimeMarker![radscheduleview populating with data ITime Marker](images/radscheduleview_populating_with_data_ITimeMarker.png)TimeMarkers![radscheduleview populating with data Time Markers](images/radscheduleview_populating_with_data_TimeMarkers.png)

# Relationships

Here are some explanations about the keys and the relationships in the data tables:NameBetweenTypeUpdate/delete ruleFK_SqlResources_SqlResourceTypesSqlResourceTypes  - SqlResourcesOne-to-manyNo ActionFK_SqlAppointmentResources_SqlResourceSqlResources - SqlAppointmentResourcesOne-to-manyCascadeFK_SqlExceptionResources_SqlResourceSqlResources -  SqlExceptionResourcesOne-to-manyCascadeFK_SqlExceptionOccurrences_SqlAppointmentsSqlAppointments -  SqlExceptionOccurrencesOne-to-manyCascadeFK_SqlExceptionAppointments_SqlExceptionOccurrencesSqlExceptionOccurrences -  SqlExceptionAppointmentsOne-to-manyCascadeFK_SqlAppointments_TimeMarkersTimeMarkers -  SqlAppointmentsOne-to-manyNo ActionFK_SqlExceptionAppointments_TimeMarkersTimeMarkers -  SqlExceptionAppointmentsOne-to-manyNo ActionFK_SqlAppointments_CategoriesCategories -   SqlAppointmentsOne-to-manyNo ActionFK_SqlExceptionAppointments_CategoriesCategories -  SqlExceptionAppointmentsOne-to-manyNo ActionFK_SqlExceptionResources_SqlExceptionAppointmentCategories -  SqlExceptionAppointmentsOne-to-manyCascadeFK_SqlAppointmentResources_SqlAppointmentSqlAppointment -  SqlAppointmentResourcesOne-to-manyCascade

* 
							There is no table definition for the __IRecurrenceRule__ type because we don’t need it. Storing the __RecurrencePattern__ is enough to generate the recurrence rules at run-time.
						

* 
							We cannot save the Brush type into the database directly, that’s why we can save a string that represents the color and convert the string to __SolidColerBrush__ object when the TimeMarkers & Categories are loaded.
						

* 
							The __SqlAppointmentResource__ and __SqlExceptionResources__ are cross-tables between:
							

* SqlAppointments & SqlResources

* SqlExceptionAppointments & SqlResources

# See Also

# Other Resources[](8a08ec3e-82bb-428f-b234-8b0cb6b79467)

# See Also

# Other Resources[](166f61dd-1051-4a41-8546-a054773902c1)
