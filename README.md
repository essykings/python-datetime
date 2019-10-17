## Introduction to the python datetime module
A very important aspect of any program in python is datetime. Python provides the datetime module that helps manipulate date and time and represent it in a way users can understand. When you talk about datetime,there are various components to it.
The datetime module consists of the following object types: 

- date -holds the date
- time -holds the time
- datetime -holds both date and time


### How to get the current date and time

As we have seen above, the datetime module is available to do this. We will start by importing the datetime class form the datetime module then use it to create a datetime object as shown below. Python provides the now() method from the datetime class which gives us the local date and time.

```python
import datetime
dt_object = datetime.datetime.now()
print(dt_object)
```



The result is:

```sh
2019-10-17 16:13:43.300953
```



### Components of datetime

The datetime module can be used to obtain different versions of time. Lets look at the attributes in the datetime module. To do that we will use the dir() function

```sh
import datetime
attr = dir(datetime)
attr
['MAXYEAR', 'MINYEAR', '__doc__', '__name__', '__package__', 'date', 'datetime', 'datetime_CAPI', 'time', 'timedelta', 'tzinfo']
```


In this tutorial, we  will only cover the following attributes:

- 'date' - These are  date objects
- datetime', - these are both date and  time  objects
- 'time',  - these are time objects
- 'Timedelta', this attribute covers intervals in time and is used to determine past and future dates
- 'Tzinfo - this attribute deals with timezones

### Get the current date in Python
We use the date module to create or modify date objects. For example, if we want to get the local date we will go about it as follows:

```python
from datetime import date
current_date = date.today()
print(current_date)
```



The result is:
```sh
2019-10-17
```

The current date is represented is  2019, 10, 17 in the format( year, month day)respectively.


### Get the current/local time in Python

To get the current/local time, we first obtain the current date and time and then break it in to time by calling the time() method 

```python
import datetime
local_date_time = datetime.datetime.now()
local_time = local_date_time.time()
print(local_time)
```

The result is :

```sh
16:19:48.809945
```



Time delta
Tme delta represents a  duration of time i.e a duration of date or time.  The datetime module contains the timedelta() attribute which is primarily used to perform date manipulations in python. Lets say you want to know the number of days in a certain time interval, we will first import the timedelta from the datetime modules as follows:

A timedelta object is represented as follows:

>>> td_object =timedelta(days=0, seconds=0, microseconds=0, milliseconds=0, minutes=0, hours=0, weeks=0)
>>> td_object
datetime.timedelta(0)

NB All arguments are optional and default to 0  and can be floats, integers, positives or negatives.. You can be able to perform  mathematical operations such as addition, substraction and multiplication with the timedelta class.

Attributes of timedelta
The timedelta class has 3 attributes namely:
Max
Min
resolution


How to calculate the time difference between two dates
Let’s look at some examples of how to get time difference. Lets say you have two datetime.date objects as shown below

first_date = date(2019, 10, 2)
second_date = date(2014, 10, 30)

To obtain the difference, we will subtract the two dates as follows

>>> from datetime import date
>>> first_date = date(2019, 10, 2)
>>> second_date = date(2019, 10, 30)
>>> delta = second_date - first_date
>>> delta
datetime.timedelta(28)
Therefor the number of days between 2nd october 2019 and 30th October 2019 is 28 days.


How to calculate the time difference between two datetime.time objects

Lets say you have two datetime.time objects as shown below

time_1 = time(2019, 10, 2)
time_2 = time(2014, 10, 30)

To obtain the difference, we will subtract the two objects as follows


How to get past and future dates with timedelta

Since timedelta reprsents a duration, to get any future or past date , we will add or subtract timedelta to the current date respectively. A simple equation to represent this is shown below.

import datetime
current_date = datetime.datetime.today()
past_date =  datetime.datetime.today() – datetime.timedelta(days=n)

future_date =  datetime.datetime.today() – datetime.timedelta(days=n)

where n represents the number of days in integers

If we want to get the date for the past 2 weeks ie. 14 days, we will substract 14 from the current date

past_date =  datetime.datetime.today() – datetime.timedelta(days=14)

>>> past_date =  datetime.datetime.today() - datetime.timedelta(days=14)
>>> past_date 
datetime.datetime(2019, 10, 1, 16, 37, 41, 222060)

Lets say we want to practice a certain skill for 21 days, to get our future date we will add 21 days to the current date as shown below.

>>> future_date =  datetime.datetime.today() +  datetime.timedelta(days=21)
>>> future_date
datetime.datetime(2019, 11, 5, 16, 39, 50, 366742)

More arithmetic operations with timedelta


## Time Zones
So far, we have been dealing with datetime without any consideration of factors such as timezones or daylight savings. Before we dive in further, let’s get to understand the difference between naive and aware dates. Naive dates and times usually don’t have any information that can determine things like timezones or daylight savings, They are however easier to work with because they are less complex. Aware dates and times, on the other hand, have enough information to determine their timezones and keep track of daylight savings

Lets look at how you write a simple aware datetime


>>> import datetime
>>> dt_now = datetime.datetime.utcnow()
>>> dt_now
datetime.datetime(2019, 10, 17, 7, 3, 21, 271240)
>>> 

The simple program shows a naive datetime object. If you wish to make it an ware datetime you have to explicitly factor in a timezone.
So how can we add information about timezones in our datetime objects. The python datetime library does not have any module available for that but we can still use other libararies to add timezone information. One such library is the pytz library.

Suppose we want to get the current time in Nairobi city, we will need to explicitly use the specific timezone in our program. In order to get the timezone in Nairobi, we can use pytz to get all the possible timezones.

>>> import pytz
>>> print(pytz.all_timezones)
['Africa/Abidjan', 'Africa/Accra', 'Africa/Addis_Ababa', 'Africa/Algiers', 'Africa/Asmara', 'Africa/Asmera', 'Africa/Bamako', 'Africa/Bangui', 'Africa/Banjul', 'Africa/Bissau', 'Africa/Blantyre', 'Africa/Brazzaville', 'Africa/Bujumbura', 'Africa/Cairo', 'Africa/Casablanca', 'Africa/Ceuta', 'Africa/Conakry', 'Africa/Dakar', 'Africa/Dar_es_Salaam', 'Africa/Djibouti', 'Africa/Douala', 'Africa/El_Aaiun', 'Africa/Freetown', 'Africa/Gaborone', 'Africa/Harare', 'Africa/Johannesburg', 'Africa/Juba', 'Africa/Kampala', 'Africa/Khartoum', 'Africa/Kigali', 'Africa/Kinshasa', 'Africa/Lagos', 'Africa/Libreville', 'Africa/Lome', 'Africa/Luanda', 'Africa/Lubumbashi', 'Africa/Lusaka', 'Africa/Malabo', 'Africa/Maputo', 'Africa/Maseru', 'Africa/Mbabane', 'Africa/Mogadishu', 'Africa/Monrovia', 'Africa/Nairobi'

To get the time in Nairobi in timezone will be:

import pytz
import datetime
tz_nairobi = pytz.timezone("Africa/Nairobi")
dt_nairobi =datetime.datetime.now(tz_nairobi)
print(dt_nairobi)


The result will be:
2019-10-17 10:40:33.592608+03:00

What about the city of Berlin

import pytz
import datetime
tz_berlin = pytz.timezone("Europe/Berlin")
dt_berlin =datetime.datetime.now(tz_berlin)
print(dt_berlin)

The result will be:
2019-10-17 09:40:33.614581+02:00

As you can see, different cities have different timezones even though the dates may be the same.


Difference between DST, GMT, and UTC

GMT is the official timezone used in some countries in Europe and Africa. Time is displayed in 24-hour 0r 12-hour format or both. GMT is used to set the local time. For example, in our case above the local time in Berlin is 2019-10-17 09:40:33.614581+02:00 GMT while in Nairobi it is 2019-10-17 10:40:33.592608+03:00 GMT

DST(day light saving ) Countries which have summer  change from daylight saving to summer time to make evening daylight to  last longer. During DST,  these countries turn their clocks forward an hour and revert to standard time during the fall.

. 
UTC (Coordinated Universal Time ) is a time standard for timezones worldwide. UTC is used to keep time synchronized across the world and acts as a reference point for all timezones.

How to work with timezones
Working with timezones can be a very tedious task

Converting timezones
The first thing to keep  in mind when making tomezone conversions is to ensure all the time attributes you intend to work with are in UTC. Suppose you want to convert the following timezone to America/New_York timezone

import datetime 
import pytz

timezone_berlin = '2018-06-29 17:08:00'
timezone_berlin_obj = datetime.datetime.strptime(timezone_berlin, '%Y-%m-%d %H:%M:%S')

timezone_newyork = pytz.timezone('America/New_York')
timezone_newyork_obj = timezone_newyork.localize(timezone_berlin_obj)

print(timezone_newyork_obj)
print(timezone_newyork_obj.tzinfo)

The result will be:

2018-06-29 17:08:00-04:00
America/New_York






Other Practical examples

How to convert strings into datetime
Python strptime() is a method in the datetime module, and its syntax is:

dateobj =datetime.strptime(date_string,format) where the arguments should be strings and are not optional.

The datetime module has a number of methods such as the strptime()  method, which can be used to manipulate dates. Suppose we want to represent today's date (10/17/2019) into a date object. 

import datetime
date_string = '10/17/19'
date_obj = datetime.datetime.strptime(date_string, '%m/%d/%y')
print(date_obj)

The result will be:
2019-10-17 00:00:00

Examples of string to datetime object with strptime
Suppose we have a datetime string represented as ‘10/17/19 15:02:34’ and we woud like to convert in to a datetime object.

from datetime import datetime
datetime_string = '10/17/19 13:08:45'
datetime_obj = datetime.strptime(datetime_string, '%m/%d/%y %H:%M:%S')
print(datetime_obj)

The result will be:
2019-10-17 13:08:45

The format() function
There are different ways in which to format 




How to convert Python datetime to string
The datetime module also has the strftime() method that does the opposite (ie. converts datetime nd time objects into strings. The syntax for the datetime and time module are:

datetime_string = datetime_object.strftime(format_string)
time_string = datetime_object.strftime(format_string[,time_object])

Examples of datetime to string with strftime()
Suppose we wish to convert the current datetime in to a string?. How do we go about it?. We fist get the datetime object representation of the current datetime and call the strftime() method on the object.

import datetime
current_date = datetime.datetime.now()
current_date_string = current_date.strftime('%m/%d/%y %H:%M:%S')
print(current_date_string)

The result will be:
10/17/19 16:35:49

Other python datetime libraries

Python has other libaries that make manipulation of datetimes much easier. Some of them have timezones hence reducing the complexity associated with timezones. Lets look at them below.

Arrow
Arrow is also another powerful python module that makes it easy to create, manipulate, and format dates and times. It is available via pip, and you can  install it as follows:

sudo pip3 install arrow

For example, you can use Arrow to get the current time just like the datetime module.

import arrow
current_time = arrow.now()
print(current_time)
print(current_time.to('UTC'))

The result is:
import arrow
current_time = arrow.now()
print(current_time)
print(current_time.to('UTC'))





Maya
Maya makes it very easy to parse strings and convert timezones.

For example

import maya
 
dt = maya.parse('2018-04-29T17:45:25Z').datetime()
print(dt.date())
print(dt)
print(dt.time())

The result is:
import maya
 
dt = maya.parse('2018-04-29T17:45:25Z').datetime()
print(dt.date())
print(dt)
print(dt.time())


Dateutil
dateutil is a powerful library that can be used to parse dates and times in python in a variety of formats. See the examples below.

from dateutil import parser
dt_obj = parser.parse('Thu Oct 17 17:10:28 2019')
print(dt_obj)
 
dt_obj1=parser.parse('Thursday, 17. October 2019 5:10PM')
print(dt_obj1)
 
dt_obj2=parser.parse('10/17/2019 17:10:28')
print(dt_obj2)
 
t_obj=parser.parse('10/17/2019')
print(t_obj)

The result will be:

2019-10-17 17:10:28
2019-10-17 17:10:00
2019-10-17 17:10:28
2010-10-17 00:00:00

As you can see, you dont need any regular expression to determine the format; the parser will look for recognizable tokens and then guess where it belongs. If it doent, then it will throw an error.


























































