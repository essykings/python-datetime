## Introduction to the python datetime module
An essential aspect of any program in python is datetime. Python provides the datetime module that helps manipulate date and time and represents it in a way users can understand. When you talk about datetime, there are various components to it.
The datetime module consists of the following object types: 

- date -holds the date
- time -holds the time
- datetime -holds both date and time


### How to get the current date and time

As we have seen above, the datetime module is available to do this. We'll start by importing the datetime class form the datetime module then use it to create a datetime object, as shown below. Python provides the now() method from the datetime class, which gives us the local date and time.

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

The datetime module can be used to obtain different versions of time. Let's look at the attributes in the datetime module. To do that we are going to use the dir() function

```sh
import datetime
attr = dir(datetime)
attr
['MAXYEAR', 'MINYEAR', '__doc__', '__name__', '__package__', 'date', 'datetime', 'datetime_CAPI', 'time', 'timedelta', 'tzinfo']
```


In this tutorial, we  are going to cover the following attributes:

- date - These are  date objects
- datetime - these are both date and  time  objects
- time  - these are time objects
- timedelta -this attribute covers intervals in time and is used to determine past and future dates
- 'Tzinfo - this attribute deals with timezones

### Get the current date in Python
We use the date module to create or modify date objects. For example, to get the local date:

```python
from datetime import date
current_date = date.today()
print(current_date)
```



The result is:
```sh
2019-10-17
```

The current date is 2019, 10, 17 in the format( year, month day), respectively.


### Get the current/local time in Python

To get the current/local time, we first obtain the current date and time and then break it into time by calling the time() method 

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



## Time delta
Time delta represents a  duration of time i.e., a duration of date or time.  The datetime module contains the timedelta(a) attribute, which is primarily used to perform date manipulations in python. Let's say you want to know the number of days in a certain time interval, first import the timedelta from the datetime modules as follows:

A timedelta object is represented as follows:

```sh
td_object =timedelta(days=0, seconds=0, microseconds=0, milliseconds=0, minutes=0, hours=0, weeks=0)
td_object
datetime.timedelta(0)
```

NB All arguments are optional and default to 0  and can be floats, integers, positives, or negatives. You can be able to perform mathematical operations such as addition, subtraction, and multiplication with the timedelta class.

### Attributes of timedelta
The timedelta class has 3 attributes, namely:

- Max
- Min
- resolution


### How to calculate the time difference between two dates
Let’s look at some examples of how to get the time difference. Let's say you have two datetime. date objects as shown below

```python
first_date = date(2019, 10, 2)
second_date = date(2014, 10, 30)
```

To obtain the difference, we will subtract the two dates as follows
```python
from datetime import date
first_date = date(2019, 10, 2)
second_date = date(2019, 10, 30)
delta = second_date - first_date
print(delta)
```
The result is:

```sh
28 days,0:00:00
```


Therefore the number of days between 2nd October 2019 and 30th October 2019 is 28 days.


### How to calculate the time difference between two datetime.time objects

Let's say you have two datetime. time objects as shown below

```python
time_1 = time(2019, 10, 2)
time_2 = time(2014, 10, 30)
```

To obtain the difference, subtract the two objects as follows

``python
time_2 - time_1
``


### How to get past and future dates with timedelta

Since timedelta represents a duration, to get any future or past date, you add or subtract timedelta to the current date, respectively. A simple equation to represent this is shown below.

```python
import datetime
current_date = datetime.datetime.today()
past_date =  datetime.datetime.today() – datetime.timedelta(days=n)

future_date =  datetime.datetime.today() – datetime.timedelta(days=n)
```

where n represents the number of days in integers

If we want to get the date for the past 2 weeks, i.e., 14 days, you subtract 14 from the current date

```python
import datetime
past_date =  datetime.datetime.today() - datetime.timedelta(days=14)
print(past_date)
```

The result is:

```sh
2019-10-03 18:38:04.733042
```

Let's say we want to practice a particular skill for 21 days, to get the future date you add 21 days to the current date as shown below.

```python
import datetime
future_date =  datetime.datetime.today() +  datetime.timedelta(days=21)
print(future_date)
```
#### Result
```sh
2019-11-07 18:39:11.019086
```

### More arithmetic operations with timedelta


## Time Zones
So far, we have been dealing with datetime without any consideration of factors such as timezones or daylight savings. Before we dive in further, let’s get to understand the difference between naive and aware dates. Naive dates and times usually don’t have any information that can determine things like timezones or daylight savings; They are, however, easier to work with because they are less complicated. Aware dates and times, on the other hand, have enough information to determine their timezones and keep track of daylight savings

Let's look at how you write a simple aware datetime


```python
import datetime
dt_now = datetime.datetime.utcnow()
print(dt_now)
```

The simple program shows a naive datetime object. If you wish to make it an aware datetime, you have to explicitly factor in a timezone.
So how can we add information about timezones in our datetime objects? The Python datetime library does not have any module available to work with timezones; we can still use other libraries to add timezone information. One such library is the pytz library.

Suppose you want to get the current time in Nairobi city, you will need to use the specific timezone in our program explicitly. To get the timezone in Nairobi, you can use pytz to get all the possible timezones.

```sh
import pytz
pytz.all_timezones
['Africa/Abidjan', 'Africa/Accra', 'Africa/Addis_Ababa', 'Africa/Algiers', 'Africa/Asmara', 'Africa/Asmera', 'Africa/Bamako', 'Africa/Bangui', 'Africa/Banjul', 'Africa/Bissau', 'Africa/Blantyre', 'Africa/Brazzaville', 'Africa/Bujumbura', 'Africa/Cairo', 'Africa/Casablanca', 'Africa/Ceuta', 'Africa/Conakry', 'Africa/Dakar', 'Africa/Dar_es_Salaam', 'Africa/Djibouti', 'Africa/Douala', 'Africa/El_Aaiun', 'Africa/Freetown', 'Africa/Gaborone', 'Africa/Harare', 'Africa/Johannesburg', 'Africa/Juba', 'Africa/Kampala', 'Africa/Khartoum', 'Africa/Kigali', 'Africa/Kinshasa', 'Africa/Lagos', 'Africa/Libreville', 'Africa/Lome', 'Africa/Luanda', 'Africa/Lubumbashi', 'Africa/Lusaka', 'Africa/Malabo', 'Africa/Maputo', 'Africa/Maseru', 'Africa/Mbabane', 'Africa/Mogadishu', 'Africa/Monrovia', 'Africa/Nairobi']

```

To get the time in Nairobi in timezone will be:

```python
import pytz
import datetime
tz_nairobi = pytz.timezone("Africa/Nairobi")
dt_nairobi =datetime.datetime.now(tz_nairobi)
print(dt_nairobi)
```


The result is:
```sh
2019-10-17 10:40:33.592608+03:00
``

What about the city of Berlin

```python
import pytz
import datetime
tz_berlin = pytz.timezone("Europe/Berlin")
dt_berlin =datetime.datetime.now(tz_berlin)
print(dt_berlin)
```

The result is:
```sh
2019-10-17 09:40:33.614581+02:00
```

As you can see, different cities have different timezones even though the dates may be the same.


### Difference between DST, GMT, and UTC

GMT is the official timezone used in some countries in Europe and Africa. Time is displayed in 24-hour 0r 12-hour format or both. GMT is used to set the local time. For example, in our case above the local time in Berlin is 2019-10-17 09:40:33.614581+02:00 GMT while in Nairobi it is 2019-10-17 10:40:33.592608+03:00 GMT

DST(day light saving )- Countries that have summer change from daylight saving to summer time to make evening daylight to last longer. During DST,  these countries turn their clocks forward an hour and revert to standard time during the fall.

. 
UTC (Coordinated Universal Time ) is a time standard for timezones worldwide. UTC is used to keep time synchronized across the world and acts as a reference point for all timezones.

### How to work with timezones
Working with timezones can be a very tedious task

### Converting timezones
The first thing to keep in mind when making timezone conversions is to ensure all the time attributes you intend to work with are in UTC. Suppose you want to convert the following timezone to America/New_York timezone

```python
import datetime 
import pytz

timezone_berlin = '2018-06-29 17:08:00'
timezone_berlin_obj = datetime.datetime.strptime(timezone_berlin, '%Y-%m-%d %H:%M:%S')

timezone_newyork = pytz.timezone('America/New_York')
timezone_newyork_obj = timezone_newyork.localize(timezone_berlin_obj)

print(timezone_newyork_obj)
print(timezone_newyork_obj.tzinfo)

```

The result is:

```sh
2018-06-29 17:08:00-04:00
America/New_York
```

### Other Practical examples

## How to convert strings into datetime
Python ```strptime()```is a method in the datetime module, and its syntax is:

```python
dateobj =datetime.strptime(date_string,format) 
```

date_string, format arguments are strings and mandatory.

The datetime module has several methods, such as the ```strptime()```  method, which can be used to manipulate dates. Suppose we want to represent today's date (10/17/2019) into a date object. 

```python
import datetime
date_string = '10/17/19'
date_obj = datetime.datetime.strptime(date_string, '%m/%d/%y')
print(date_obj)
```

The result is:
```sh
2019-10-17 00:00:00
```

### Examples of string to datetime object with strptime
Suppose you have a datetime string represented as ‘10/17/19 15:02:34’, and you would like to convert into a datetime object.

```python
from datetime import datetime
datetime_string = '10/17/19 13:08:45'
datetime_obj = datetime.strptime(datetime_string, '%m/%d/%y %H:%M:%S')
print(datetime_obj)
```

The result is:

```sh
2019-10-17 13:08:45
```

### The format() function
There are different ways in which to format 




## How to convert Python datetime to string
The datetime module also has the strftime() method that does the opposite (ie. converts datetime nd time objects into strings. The syntax for the datetime and time module are:

```python
datetime_string = datetime_object.strftime(format_string)
time_string = datetime_object.strftime(format_string[,time_object])
```

### Examples of datetime to string with strftime()
Suppose we wish to convert the current datetime into a string?. How do we go about it?. We fist get the datetime object representation of the current datetime and call the strftime() method on the object.

```python
import datetime
current_date = datetime.datetime.now()
current_date_string = current_date.strftime('%m/%d/%y %H:%M:%S')
print(current_date_string)
```

The result is:

```sh
10/17/19 16:35:49
```

## Other python datetime libraries

Python has other libraries that make manipulation of date-times much easier. Some of them have timezones hence reducing the complexity associated with timezones. Let's look at them below.

### Arrow
Arrow is also another powerful python module that makes it easy to create, manipulate, and format dates and times. It is available via pip, and you can  install it as follows:

```sh
sudo pip3 install arrow
```

For example, you can use Arrow to get the current time just like the datetime module.

```python
import arrow
current_time = arrow.now()
print(current_time)
print(current_time.to('UTC'))
```

The result is:
```sh
2019-10-17T15:52:58.921198+00:00
2019-10-17T15:52:58.921198+00:00
```

### Maya
Maya makes it very easy to parse strings and convert timezones.

For example
```python
import maya
dt = maya.parse('2018-04-29T17:45:25Z').datetime()
print(dt.date())
print(dt)
print(dt.time())
```

The result is:
```python
import maya
 
dt = maya.parse('2018-04-29T17:45:25Z').datetime()
print(dt.date())
print(dt)
print(dt.time())
```


### Dateutil
dateutil is a powerful library that can be used to parse dates and times in python in a variety of formats. See the examples below.

```python

from dateutil import parser
dt_obj = parser.parse('Thu Oct 17 17:10:28 2019')
print(dt_obj)
 
dt_obj1=parser.parse('Thursday, 17. October 2019 5:10PM')
print(dt_obj1)
 
dt_obj2=parser.parse('10/17/2019 17:10:28')
print(dt_obj2)
 
t_obj=parser.parse('10/17/2019')
print(t_obj)
```

The result will be:

```sh
2019-10-17 17:10:28
2019-10-17 17:10:00
2019-10-17 17:10:28
2010-10-17 00:00:00
```

As you can see, you dont need any regular expression to determine the format; the parser looks for recognizable tokens and then guess where it belongs. If it doesn't, then it throws an error.

## Important points to keep in mind
Let's look at some of the best practices to keep in mind when working with timezones in python.

- It is recommended to always work with UTC s this eliminates the need for timezones, which can make the process very complicated.

## Conclusion


























































