___
title: Data Binding Support Overview
meta_title: Data Binding Support Overview
meta_description: 
slug :data binding support overview
tags :data,binding,support,overview
publish :True
___


# 


          Data binding allows you to establish a link between the UI and the underlying business logic and keep them synchronized. It means that when a value is changed in the business layer, that change is automatically populated to the UI and vice versa. Of course, in order to work, you have to implement the proper notification or to use objects that have already implemented it.
        


          Binding to __RadScheduleView__ involves the following property:
        __AppointmentsSource__ - gets or sets the data source (__IEnumerable__) used to generate the Appointments in the __RadScheduleView__ control. It can be bound to data from a variety of data sources in the form of common language runtime (CLR) objects and XML.
            
    ![note](note.jpg)
    	




                  Note that the data source passed to the property __AppointmentsSource__ should contain only objects that implement the __IAppointment__ interface.
                __ResourceTypesSource__ -  gets or sets the data source (__IEnumerable__) used to generate the ResourceTypes of the __RadScheduleView__ control. It can be bound to data from a variety of data sources in the form of common language runtime (CLR) objects and XML.
            
    ![note](note.jpg)
    	




                  Note that the data source passed to the property __ResourceTypesSource__ should contain only objects of type __ResourceType__.
                __CategoriesSource__ - gets or sets the data source (__IEnumerable)__ used to generate the Categories in the __RadScheduleView__ control. It can be bound to data from a variety of data sources in the form of common language runtime (CLR) objects and XML.
            
    ![note](note.jpg)
    	




                  Note that the data source passed to the property __CategoriesSource__ should contain only objects of type __Category__.
                __TimeMarkersSource__ - gets or sets the data source (__IEnumerable__) used to generate the TimeMarkers in the __RadScheduleView__ control. It can be bound to data from a variety of data sources in the form of common language runtime (CLR) objects and XML.
            
    ![note](note.jpg)
    	




                  Note that the data source passed to the property __TimeMarkersSource__ should contain only objects of type __TimeMarker__.
                __GroupDescriptionsSource__ - gets or sets the data source (__IEnumerable<GroupDescription>)__ used to generate the GroupDescriptions in the __RadScheduleView__ control. It can be bound to data from a variety of data sources in the form of common language runtime (CLR) objects and XML.
            
    ![note](note.jpg)
    	




                  Note that the data source passed to the property __GroupDescriptionsSource__ should contain only objects of type __GroupDescription__.
                [](16E2654A-2813-4277-999A-6B510F045C43)
