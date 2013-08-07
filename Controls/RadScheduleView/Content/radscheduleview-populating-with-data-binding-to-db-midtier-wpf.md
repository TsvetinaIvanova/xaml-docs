---
title: Entity Model
meta_title: Entity Model
meta_description: description.
slug: entity-model
tags:entity,model
publish:True
---


# 

Now, when we have the table definitions that match the types in the RadScheduleView control in a very common way, we can continue with generating the Entity Model:Select the project and select Add -> New item -> ADO.NET Entity Data ModelEnter a name and select AddFrom the __Entity Data Model Wizard__ select __Generate from database**__ model and click nextSet a connection string to the database and click nextSelect the tables from the database that will be used.
      		

![radscheduleview populating with data Entity Data Model Wizard](images/radscheduleview_populating_with_data_EntityDataModelWizard.png)Click Finish. The generated model looks like the following diagram:

![radscheduleview populating with data EFModel](images/radscheduleview_populating_with_data_EFModel.png)[Models]({{slug:models}})
