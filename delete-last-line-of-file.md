To delete last line on file can using sed command.

Example we have file test.txt with contain:
a

b

c

d

We will delete last line of that file, we can use command below

`````sed -i '$ d' test.txt`````

Result test.txt:

a

b

c
