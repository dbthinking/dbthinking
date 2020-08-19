### Python查询从出生起活过了多少天

简化数据处理过程，所以指定了输入格式，默认是我儿子的出生日期。

```python
#!usr/bin/env python3
# -*- coding: utf-8 -*-
import datetime


def live_days():
    day1 = input('your date of birth(eg:2018-3-18):')
    if not day1:
        day1 = '2018-3-18'
    day2 = datetime.datetime.strptime(day1, '%Y-%m-%d')
    day3 = datetime.datetime.now()

    return (day3 - day2).days


if __name__ == '__main__':
    print('You have already lived {} days!'.format(live_days()))

```
