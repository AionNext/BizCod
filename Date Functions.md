# Date Functions

Function|Example
-|-
.addDays(n)|
.addBusinessDays(n,country)|
.addMonths(n)|deliveryDate=person.conceptionDate.addMonths(9)
.addYears(n)|
.day|
.dayOfWeek|Sunday=1
.dayOfYear|
.daysBetween|
.in|
.IsLeapYear|
.isHoliday(country)|`'2021/11/4'.isHoliday('india')` would return true since is Diwali
.holiday(country)|`'2021/11/4'.holiday('india')` would return 'Diwali'
.isWeekend
.milliseconds|
.month|
.monthsBetween
.nextDay|
.toDateTime|
.toString|
.weekOfMonth|
.year|
.yearsBetween|

Is there value to accommodating other calendar systems by providing an optional <calendar> parameter for those functions that might need it.
  
Function|Result  
-|- 
`'2021/9/13'.toCalendar('Chinese')` |would return 'Eighth Month 7, 2021 (xin-chou), year of the Ox'
`'2021/9/13'.toCalendar('Hebrew')` |would return '7 Tishri 5782'
`'2021/9/13'.toCalendar('Islamic')` |would return 'Safar 6, 1443 AH'
`'Safar 6, 1443 AH'.toCalendar('Gregorian')` |would return '2021/9/13'
  
The function would return null if the conversion cannot be made
