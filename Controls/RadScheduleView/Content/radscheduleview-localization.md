---
title: Localization
meta_title: Localization
meta_description: description.
slug: localization
tags:localization
publish:True
---



        The built-in localization mechanism in Silverlight and WPF allows you to localize any string resource used by the standard __RadScheduleView__ control. Once translated you might use your resources in Silverlight and WPF projects without changing anything.
      ![RadScheduleView Localization 01](../Media/radscheduleview_localization01.png)

# LocalizationManager


          The __Telerik.Windows.Controls.LocalizationManager__ allows you to easily localize any of the Telerik controls.
        


          To apply custom localization to your controls just instantiate your custom __LocalizationManager__ and set it to the static property __LocalizationManager.Manager__, before the creation of the UI.
        


 __C#__
    

```C#


LocalizationManager.Manager = new CustomLocalizationManager();

```




 __VB.NET__
    

```VB.NET


LocalizationManager.Manager = New CustomLocalizationManager()

```




    ![note](note.jpg)
    	

__Note that you have to set the localization manager before the creation of the UI, otherwise some parts might remain not-localized.__

# Resource Keys

__RadScheduleView__ is a complex user interface control and its strings for localization are numerous. In order to be able to distinguish these resources, a unique identifier, called__resource key__, is assigned to each localizable string.
        


          On the picture below you can see some of the resource keys and the strings they are associated with. A complete list of the __RadScheduleView__ resource keys can be found 
          [here](#RadScheduler_Resource_Keys).
        ![RadScheduleView Localization 01](../Media/radscheduleview_localization06.png)

# Localization Using ResourceManager


          You can base your localization on the standard resource files provided by the .NET framework. For that purpose you will have to create a separate __.ResX file__ for each one of the languages that your application will support.
        

Imagine that you want to translate your schedule control into English, German and Dutch. For that purpose you will have to add three new resource files to your project:__ScheduleViewResources.resx__ - this resource file will store the __English(default)__ resources for the ScheduleView control. Set the __AccessModifier__ property to __Public__.
          __ScheduleViewResources.de.resx__ - this resource file will store the __German__ resources for the ScheduleView control. Set the __AccessModifier__ property to __No code generation__.
          __ScheduleViewResources.nl.resx__ - this resource file will store the __Dutch__ resources for the ScheduleView control. Set the __AccessModifier__ property to __No code generation__.
          ![RadScheduleView Localization04](../Media/radscheduleview_localization04.png)

Now, having the needed files, it's time to illustrate the idea and localize for example the text for the Day, Week, Month and Timeline navigation strings. For that purpose you need to create four resource strings in each one of the three resource files and translate them to the appropriate language.
    ![note](note.jpg)
    	

         
              Note that the name of the resource string should be the same as the resource key for the string you are localizing i.e. the resource key for the Day is __Day__, for the Week is __Week__, for Month is __Month__ and for the Timeline is __Timeline__.
          

The snapshot below shows the content of the __ScheduleViewResources.de.resx__ file. The resource name of the other two files should be the same. The Value column will contain the translation for the appropriate language.
        ![RadScheduleView Localization3](../Media/radscheduleview_localization03.png)


          The last step is to instantiate the __LocalizationManager__ class and set its __ResourceManager__ to the resources that have been just created.
        


 __C#__
    

```C#


LocalizationManager.Manager = new LocalizationManager()
{
   ResourceManager = ScheduleViewResources.ResourceManager
};

```




 __VB.NET__
    

```VB.NET


LocalizationManager.Manager = New LocalizationManager()
LocalizationManager.Manager.ResourceManager = ScheduleViewResources.ResourceManager

```


    ![note](note.jpg)
    	


                If you rely on culture settings to load the right resources automatically, you have to write some code inside your application's project file. For example, if you have to support English and Dutch languages, you can store the localized strings in __Resources.resx__ and __Resources.nl.resx __files. For the __Resources.resx__ file you can set __ResXFileCodeGenerator__ to __Internal __or __Public __and for others - to __No code generation__. Then, open the project file in a text-mode and insert the code below into the __<PropertyGroup>__ section. In this way you notify the framework about the supported cultures.
              


                <SupportedCultures>en;nl</SupportedCultures>
              


          Here is how the localized __RadScheduleView__ looks like:
        ![RadScheduleView Localization 06](../Media/radscheduleview_localization05.png)

#  Localization Using Custom Localization Manager


          The other way to localize your __RadScheduleView__ control is to create a class that derives from the __LocalizationManager__ object and to override its method __GetStringOverride()__. The logic is pretty simple, you just have to create a switch statement and return the correct translation for each resource key,____as it is shown below:
        


 __C#__
    

```C#


public class CustomLocalizationManager : LocalizationManager
{
   public override string GetStringOverride( string key )
   {
       switch( key )
       {
           case "Timeline":
               return "Zeitline";
           case "Day":
               return "Tag";
           case "Week":
               return "Woche";
           case "Month":
               return "Monat";
           case "SaveAndCloseCommandText":
               return "Speichern & Sliessen";
           case "EditRecurrence":
               return "Serie bearbeithen";
           case "Categories":
               return "Kategrisieren";
       }
       return base.GetStringOverride( key );
   }
}

```




 __VB.NET__
    

```VB.NET


Public Class CustomLocalizationManager
    Inherits LocalizationManager
    Public Overloads Overrides Function GetStringOverride(ByVal key As String) As String
        Select Case key
            Case "Timeline"
                Return "Zeitline"
            Case "Day"
                Return "Tag"
            Case "Week"
                Return "Woche"
            Case "Month"
                Return "Monat"
            Case "SaveAndCloseCommandText"
                Return "Speichern & Sliessen"
            Case "EditRecurrence"
                Return "Serie bearbeithen"
            Case "Categories"
                Return "Kategrisieren"
        End Select
        Return MyBase.GetStringOverride(key)
    End Function
End Class

```





Of course, if you don't want to hard-code your translation inside your source code, you can always use resource files:




 __C#__
    

```C#


public override string GetStringOverride( string key )
{
   switch( key )
   {
       //----------------------
       case "Timeline":
           return ScheduleViewResources.Timeline;
       //----------------------
   }
   return base.GetStringOverride( key );
}

```




 __VB.NET__
    

```VB.NET


Public Overloads Overrides Function GetStringOverride(ByVal key As String) As String
    Select Case key
        '----------------------
        Case "Timeline"
            Return ScheduleViewResources.Timeline
        '----------------------
    End Select
    Return MyBase.GetStringOverride(key)
End Function

```



# RadScheduler_Resource_KeysRadScheduleView Resource Keys


          The following __Resource Keys__ are available:
        __AllDayEvent____Appointment____AppointmentRecurrence____AppointmentTime____Body____Busy____Cancel____Categorize____CreateAppointment____Daily____Day____Days____DeleteAppointment____DeleteItem____DeleteItemQuestion____DeleteOccurrence____DeleteRecurringItem____DeleteRecurringItemQuestion____DeleteSeries____DurationColon____DurationDay____DurationDays____DurationHour____DurationHours____DurationMinute____DurationMinutes____DurationWeek____DurationWeeks____EditAppointment____EditParentAppointment____EditRecurrence____EditRecurrenceCommandText____EditRecurrenceRule____EndAfter____EndBy____EndColon____EndDateBeforeStart____EndTime____Event____Every____EveryDay____EveryWeekday____First____Fourth____Free____HighImportance____InvalidRecurrenceRuleMessage____InvalidRecurrenceRuleTitle____Last____LowImportance____Month____Monthly____Months____NoEndDate____Occurrences____Of____OfEvery____Ok____OpenOccurrence____OpenRecurringItem____OpenRecurringItemQuestion____OpenSeries____OutOfOffice____RangeOfRecurrence____RecurEvery____RecurrencePattern____RemoveRecurrence____SaveAndClose____SaveAndCloseCommandText____SaveAppointment____SaveRecurrence____Second____SetDayViewMode____SetMonthViewMode____SetTimelineViewMode____SetWeekViewMode____ShowAs____Start____StartColon____StartTime____Subject____Tentative____The____Third____Timeline____Untitled____Week____WeekDays____WeekendDays____Weekly____WeeksOn____Yearly__

# Using Built-In Resources

__RadScheduleView__ provides you with built-in resources for several cultures:  __Spanish, German, Italian, Turkish, Dutch__.
        


          To change the default culture, you should set the __CurrentCulture__ and the __CurrentUICulture __of the __CurrentThread__. Note that this must happen in the code-behind of your__Application__ (__App.xaml.cs__) file, right before the UI initialization. The next code-snippet shows you how to change the __CurrentCulture __to __Dutch__.
        




 __C#__
    

```C#


public partial class App : Application
{
   public App()
   {
       System.Threading.Thread.CurrentThread.CurrentCulture = new System.Globalization.CultureInfo( "nl" );
       System.Threading.Thread.CurrentThread.CurrentUICulture = new System.Globalization.CultureInfo( "nl" );
       this.Startup += this.Application_Startup;
       this.Exit += this.Application_Exit;
       this.UnhandledException += this.Application_UnhandledException;
       InitializeComponent();
   }
}

```


