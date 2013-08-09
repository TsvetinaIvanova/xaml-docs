---
title: Data Binding Support Overview
meta_title: Data Binding Support Overview
meta_description: description.
slug: data-binding-support-overview
tags:data,binding,support,overview
publish:True
---


# 

Data binding allows you to establish a link between the UI and the underlying business logic and keep them synchronized. It means that when a value is changed in the business layer, that change is automatically populated to the UI and vice versa. Of course, in order to work, you have to implement the proper notification or to use objects that have already implemented it.
        

Binding to __RadScheduleView__ involves the following property:
        

* __AppointmentsSource__ - gets or sets the data source (__IEnumerable__) used to generate the Appointments in the __RadScheduleView__ control. It can be bound to data from a variety of data sources in the form of common language runtime (CLR) objects and XML.
            ><para xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5">
                  Note that the data source passed to the property <legacyBold>AppointmentsSource</legacyBold> should contain only objects that implement the <legacyBold>IAppointment</legacyBold> interface.
                </para>

* __ResourceTypesSource__ -  gets or sets the data source (__IEnumerable__) used to generate the ResourceTypes of the __RadScheduleView__ control. It can be bound to data from a variety of data sources in the form of common language runtime (CLR) objects and XML.
            ><para xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5">
                  Note that the data source passed to the property <legacyBold>ResourceTypesSource</legacyBold> should contain only objects of type <legacyBold>ResourceType</legacyBold>.
                </para>

* __CategoriesSource__ - gets or sets the data source (__IEnumerable)__ used to generate the Categories in the __RadScheduleView__ control. It can be bound to data from a variety of data sources in the form of common language runtime (CLR) objects and XML.
            ><para xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5">
                  Note that the data source passed to the property <legacyBold>CategoriesSource</legacyBold> should contain only objects of type <legacyBold>Category</legacyBold>.
                </para>

* __TimeMarkersSource__ - gets or sets the data source (__IEnumerable__) used to generate the TimeMarkers in the __RadScheduleView__ control. It can be bound to data from a variety of data sources in the form of common language runtime (CLR) objects and XML.
            ><para xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5">
                  Note that the data source passed to the property <legacyBold>TimeMarkersSource</legacyBold> should contain only objects of type <legacyBold>TimeMarker</legacyBold>.
                </para>

* __GroupDescriptionsSource__ - gets or sets the data source (__IEnumerable<GroupDescription>)__ used to generate the GroupDescriptions in the __RadScheduleView__ control. It can be bound to data from a variety of data sources in the form of common language runtime (CLR) objects and XML.
            ><para xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5">
                  Note that the data source passed to the property <legacyBold>GroupDescriptionsSource</legacyBold> should contain only objects of type <legacyBold>GroupDescription</legacyBold>.
                </para>[Implementing View-ViewModel ]({{slug:implementing-view-viewmodel-}})
