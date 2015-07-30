# UTime.jl
Universal Time using local system timezone 


#####*Experimental, Changeable, *Robustly Untested**

This module lets you have whatever it is that your local system believes is Universal Time relative to the local time zone, present, past and future. And it lets you use the things that come with Base.Dates (for the most part .. not exaustively).  If you find errors, omissions, better ways, raise an issue.

Caveats:

1. This may be of transitional use -- please do not expect this to match the eventual handling of Universal Time.
2. *Do Not* store these as typed values in a jld file -- store the string forms; the strings will be redigestable later, that jld not.
3. Some sysadmins set up the network to live on Universal Time, and adjust that to give local time.  If you are working in that enivronment (a) thank your sysadmin for caring (b) that may mislead the C library.
4. This uses a lesser visted few lines of ISO and ANSI Standard C.  If your supplier let something slide in their implementation of mktime_r, that would be unhelpful.
5. Try UTime.ok() (not exported), if it is false is module should not be used.

|function|action|
---------|-------
|ut()| get the current date&time as it is in UT|
|ut(dtm::DateTime)|convert the local date&time dtm to UT|
|localtime()| get the current date&time as it is in local time|
|localtime(utm::UT)|convert the UT date&time to local time|
|UT(...)|like DateTime(...)|
|year(utm::UT)..|like year,month...|
|Year(utm::UT)..|like Year,Month...|
|format(utm,string) | postpends " UT" |
|format(utm,string,false) | does not postpend |
|format(utm,DateFormat)   | does not postpend |
|much other stuff|used as with DateTime|

```julia
exports
ut, localtime, UT,

exports (imported from Base.Dates)
Year, Month, Week, Day, Hour, Minute, Second, Millisecond,
year, month, week, day, hour, minute, second, millisecond, 
dayofyear, dayofmonth, dayofweek, yearmonthday, yearmonth, monthday, 
dayofweekofmonth, daysofweekinmonth, quarterofyear, dayofquarter,
firstdayofyear, lastdayofyear, firstdayofquarter, lastdayofquarter,
firstdayofmonth, lastdayofmonth, firstdayofweek, lastdayofweek, 
daysinmonth, daysinyear, monthname, monthabbr, dayname, dayabbr,
isleapyear, format, ISOUniversalTimeFormat, 
adjust, tonext, toprev, tofirst, tolast, recur,
(+), (-), (.+), (.-)
```
