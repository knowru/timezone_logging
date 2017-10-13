timezone_logging
================
Logging with timezone in Python 2.7

Problem
--------
* The standard `logging` package in Python 2.7 does not support timezone.
```
# In a system whose timezone is set to America/Chicago
import logging
logging.basicConfig(format='%(asctime)s %(message)s', datefmt='%Y-%m-%d %H:%M:%S%z')
logger = logging.getLogger('demo')
logger.info('hello')
# 2017-10-12 23:29:00+0000 hello
# Note the '+0000' (not recognizing local timezone even when %z is provided to the datefmt argument in logging.basicConfig)
# The time itself was in the local timezone
```
* This is usually not a big problem but our platform runs in multiple sites across the world that we needed to know the exact time of logs from sites in different timezones

Solution
--------
* Install this package
```
pip install timezone_logging
```
* Use it like below
```
from timezone_logging.timezone_logging import get_timezone_logger
logger = get_timezone_logger('demo')
logger.info('hello')
# 2017-10-12T23:29:00Z-0500 demo                     INFO     hello
```

Source
------
* This package is based on jfs' answer on StackOverflow [https://stackoverflow.com/questions/27858539/python-logging-module-emits-wrong-timezone-information](https://stackoverflow.com/questions/27858539/python-logging-module-emits-wrong-timezone-information)

Contact
-------
* Knowru, LLC (hello@knowru.com / [https://www.knowru.com](https://www.knowru.com))