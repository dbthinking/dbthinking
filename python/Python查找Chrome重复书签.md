### Python查找Chrome重复书签

从Chrome导出书签文件，改名为bookmarks.html与脚本放在同一目录后执行脚本。

```python
#!/usr/bin/env python3
# encoding: utf-8
import re


def read_bookmarks(file_name):
    with open(file_name) as f:
        return f.readlines()


def process(lst):
    dic = {}
    dir_name = ['chrome']
    for line in lst:
        if '<DT><H3' in line:
            name = re.findall(r'">(.*?)</H3>', line)[0]
            dir_name.append(name)
        elif '</DL><p>' in line:
            del dir_name[-1]
        elif '<DT><A HREF' in line:
            url, title = re.findall(r'HREF="(.*?)".*?">(.*?)</A>', line)[0]
            value = '  >>  '.join(dir_name) + '  >>  ' + title
            dic.setdefault(url, []).append(value)

    for i, j in dic.items():
        if len(j) > 1:
            print(i)
            for marks in j:
                print('    ' + marks)
            print()


if __name__ == '__main__':
    process(read_bookmarks('bookmarks.html'))

```
