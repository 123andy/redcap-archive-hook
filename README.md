# redcap-archive-hook
@ARCHIVE is a Hook that allows the users hide (not delete) options for a checkbox, drop-down and/or radio button field.  It is intended for cases when you no longer want to present an option but do not want to change/remove records with these options. 
So, for analysis, all options will remain as they originally were selected, but new records will be unable to select the retired options.

## When to use 
In some cases, you want to prevent new records from selecting some checkbox, dropdown, or radio options that no longer apply.  However, you want to keep those old records with the no-longer-active selections.
How to Use
Say you are using the drop-down list -Month- to register subjects over time and you just want to show from the current month until December to avoid confusion: 
```
1, January
2, February
3, March
4, April
5, May
6, June
7, July
8, August
9, September
10, October
11, November
12, December
```

### Say the current month is now July and you want to prevent new users from selecting Jan-July in the dropdown.
Simply add the custom action tag @ARCHIVE=1,2,3,4,5,6 where 1..6 correspond to the choice values you wish to hide from the dropdown list. 

For a record that didn't have a previous value for this option, you can now see that the drop-down list no longer contains Jan-June and starts with July. 

If you open a previously saved record, any options which are retired and NOT selected will be hidden.  Any options which are retired AND selected will remain selected but will be marked as 'retired'.

When you export the data, you will not see the '*Archived' message - it is simply a label change on the user-interface.

It is important to keep in mind that to the extent the selection of an option is something you are measuring, you should track the dates you make changes to the question. Or, you could go through the production change logs to determine the change after-the-fact.

###Other Uses
This feature could also come in handy where you are tracking names of people who performed actions, for example the fellow who performed a surgery.  If someone leaves the group or graduates, you can retire their option so no new records are confused by seeing an option which cannot apply any longer while preserving your historical data.
If, for some reason, you must create a NEW record with a retired option, you choices are to remove the custom action tag, create the record, and re-add it. Or, alternately, you can use the data-import tool to import in a value which is retired.
