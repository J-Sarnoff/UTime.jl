# UTime.jl
Universal Time using local system timezone 


#####*Experimental:  passes initial tests*

This module lets you have whatever it is that your local system believes is Universal Time relative to the local time zone, present, past and future. And it lets you use the things that come with Base.Dates (for the most part .. not exaustively).

If you find errors, omissions, better ways, please raise an issue here.

####Asks:

1. **Do Not** store UT typed values in a jld file
    -- store their strings, they will be rereadable.

2. This is transitional -- working in multiple timezones is different.
3. The module requires the local system provides a Standard C compliant maketm_r().
4. Try UTime.ok() (not exported), if it is false is module should not be used.
5. This is transitional -- working in multiple timezones is different.


####Offers:

|function|action|
---------|-------
|ut()| get the current date&time as it is in UT|
|ut(dtm::DateTime)|convert the local date&time dtm to UT|
|localtime()| get the current date&time as it is in local time|
|localtime(utm::UT)|convert the UT date&time to local time|
|UT(...)|like DateTime(...)|
|year(utm::UT)..|like year,month...|
|Year(utm::UT)..|like Year,Month...|
|format(utm,DateFormat)   | like format(dt::DateTime, DateFormat) |
|much other stuff|used as with DateTime|

```importall UTime```
```julia
exports
gmt, ut, localtime, UT # gmt is an alias for ut

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
