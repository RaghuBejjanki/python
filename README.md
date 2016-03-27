https://pypi.python.org/pypi/?
https://wiki.python.org/moin/PythonTestingToolsTaxonomy
https://www.edx.org/course/introduction-computer-science-mitx-6-00-1x-0
http://www.pythontutor.com/visualize.html#mode=edit

telnetlib: telnet client functionality is implemented using the telnetlib.
datetime: we can set, modify and update the current date and time.
logging: To log the messages.Instead of print we can use this module. debug, info, warning, error, critical messages we can display.
paramiko: for ssh and sftp get, put operations we can use paramiko.
2to3: for converting from python 2.7 to 3.4 we can use this. For linux and windows this procedure is different.
IPy: To validate the ipv4 and ipv6 addresses
sys: To get python version and command line arguments
os: To get current working directory.
inspect : To get the filename, line number and number of arguments in a function.

Python is interpreted at run time, interactive, object-oriented programming.
Python is procedural programming language. Procedures are also called subroutines or functions. A procedural program consists of 1 or more units of modules

Source code is first compiles to byte code which is different from binary code. This is called compilation process. Then the PVM(python virtual machine) will run this code at run time.

.py - input source code you write.
.pyc - compiled byte code file. If a module is imported, python will build *.pyc file that contains bytecode to make import easier(and faster) at later point time by checking the time stamps of py and pyc files.
python can run with pyc files even if py files are not present. They speedup the start time as well.
.pyo - this is *.pyc file when created with optimizations. without line numbers, assertions and possibly doc strings. python interpreter invoked with -O flag will generate this file.
.pyd - windows dll file.

.pyc files have more size than .py files.

Every directory will contain __init__.py, .py and .pyc files(if something is imported). This will indicate that the directory is a python directory.

installation success and import error:
1)PYTHONPATH may be wrong
2)Having modules with the same name.

Performance: Since byte code is not binary set instructions, it requires more work than CPU instructions.
but unlike other interpreters, python does not need to reanalyse and reparse each source statement repeatedly. This speeds up, so python sits in between traditional compiled languages and interpreted languages.

magic methods:  + will call internally __add__(). __init__, __new__, __str__, __len__

magic methods are surrounded by double underscore. when __init__() constructor is called, actually __new__ is called and this creates the object and passes the arguments.
__del__ method is called when the object is destroyed.

x = 2
x.__add__(3)
5

a = 'ram'
a.__add__('kri')
ramkri

a.__len__() --> 3

Flavours of python:
The default python, which is cpython is used by us. There are other flavours like jython, ironpython, Pypy etc.

PYCHARM can be used to get reports in html and xml format.
Using pycharm we can run unit test scripts(each test script and test method should start with test) at project level and at script level, not at module level.

To check which version of python is running in ubuntu or windows:
$python -V

To check whether the module is present or not:
$python -c "import telnetlib"
$echo $?   ----> if telnetlib is present then 0, else error and 1.
0


broiler plate: The code which is used at many places without change.
if __name__ == '__main__':
    main()

here main() is only executed only when the module is run directly, but it is not run when the module is imported by some other module.

If lib is not present, to download use below command:
$sudo apt-get install python-scipy

also:
$pip install numpy          : Highly recommanded not to use this as its not from ubuntu repository, may break the system.

also:
#easy_install pip
or if we download zip file from internet like paramiko.zip then, extract it and go to that directory using the command prompt and execute

from the source
>python setup.py install

Also from wheel
>pip install c:/python_wheel.whl

to uninstall the modules:
>pip uninstall kivy

to get which version of interpreter in code
import sys
print sys.version  ----> 2.7

To get the line number and file name
from inspect import currentframe, getframeinfo
frameinfo = getframeinfo(currentframe())
print frameinfo.filename, frameinfo.lineno

import os
os.getcwd() #to get the current working directory like c:\python27>

Pyunit is the unit test framework.
It supports test automation, sharing of setup, combining of test scripts, script reports.
oneoffsetup: database creation, connecting, directories, starting server process.
setup for initialization and teardown for cleanup.

python does not need compilation.python converts source code into intermediate byte code and this into native language for computer to understand. Interpretors have low performance when compared to compiled languages. but code-caching and persistance interpretors can make interpretors fast.

For importing the function from another file of another folder.
parentdir = os.path.abspath(os.path.join('../'))  ---> for main path ../ is appended to get back parent folder.
sys.path.append(parentdir)   ---> module search path
from Modules import nvtl_logger  ---> Modules is the folder name and nvtl_logger is the file name
__file__ ----> will give the filename
nvtl_logger.logging_function()  ---> from file we are using logging_function

Exceptions
raise Exception("Exception: The element is not found") --> explicitly want to raise exception.
try: condition checked : example time start
except: if condition fails
else: if condition passes
finally: at the end : time end

To validate the ipv4 and ipv6 address using python: download IPy using 'pip install IPy'
from IPy import IP
IP('127.0.0.1')  ---> valid, if any exception is thrown, then its not a valid ip address
IP('255.25.255.256')  ---> invalid
IP('2001::2')   ---> valid
IP('FEC80::2')  ---> invalid

or

To validate the ip address in python.
import socket
a = "127.0.0.1"
socket.inet_aton(a)
'\x7f\x00\x00\x01'
a = "327.0.0.1"
socket.inet_aton(a)

Traceback (most recent call last):
  File "<pyshell#4>", line 1, in <module>
    socket.inet_aton(a)
error: illegal IP address string passed to inet_aton


TO GET THE LIST OF MODULES DOWNLOADED AND INSTALLED: :
site packages
import pip
pip.get_installed_distributions()

TO GET ALL PACKAGES INSTALLED:
>>help('modules') 

help(os)  --> to get information of that module or function etc in python interpretor..
#pydoc os --> to get information of that module or function  in linux commmand line

Global variable:

x = 50
def f():
    x = 10
    global x
    print x
print x --------------------> 50
f() -------------------------> 10
print x ----------------------> 10

membership operator(in): for lists, strings, tuples and dict
str1 = "I have lazy dog"
"dog" in str1 --> True
"lion" in str1 --> False

mylist = [1,3, 19, 48, 77]
48 in mylist --> True
23 in mylist --> False

OR

'rama'.__contains__('ma') --> True
'rama'.__contains__('rma') --> False
[1,2,3,4].__contains__(1) --> True
[1,2,3,4].__contains__(5) --> False

Identity operator(is): compare memory location. The value and datatype are same, then is can be used.
a=42
c=42
id(a) --> 100
id(c) --> 100
a is c --> True
e = [1,2,3]
f = [1,2,3]
id(e) --> 200
id(f) --> 300
e is f --> False

id : returns the identity of object. It will be unique and it is integer value.

hence memory are considered in identity operator.

Python memory management:
Python manages memory in private heaps. Objects and data structures are in heaps.
Programmer does not have to access to memory, interpreter will take care of it.
Garbage collector recycles the unused memory and makes it available again in heap space.
objects are garbage-collected when the reference count goes to 0.
Even when python exits, some memory is not freed because of c libraries used, 'atexit' module can be used to delete it.
@atexit can be used as decorator

@atexit.register
def shutdown():
    print "python is closing down."

a = 2
id(a)     19781380
id(2)     19781380
a = b = 2  
id(a)     19781380
id(b)     19781380
id(2)     19781380
id(10)   19781284

a = 10 
id(10)    19781284
id(a)      19781284
b = a
id(b)     19781284

== is used for value equality
'is' is used for reference equality

python caches in the range -5 to 256 as singleton instances for performance reasons.
a=200, b=200
a==b --> True , 
a is b -> True

a=500, b=500
a==b --> True
a is b -> False

For binary 
a = 1.7
b = 0.8 + 0.9
a == b -> False  --> binary level comparison must not be done
a is b --> False

str(a) == str(b) --> True

similarly, memory is considered.
x ='a'
'aa'==2*x -->True
'aa' is 2*x -->False
'aa' is intern(2*x)  -->True

To get the size of the object in bytes:
import sys
sys.getsizeof('c')
sys.getsizeof(1)

Default arguments: you can make some parameters optional and can pass default value to them with assignment operator.
def say(message, times=1):
     print message * times
say('Hello')    -------------------> 'Hello'
say('World', 5) -------------------> 'HelloHelloHelloHelloHello'

Default parameters should contain only immutable datatypes(numbers, strings and tuples). We should not use mutable(lists, sets and dicts) as every time, the function will create a new value when function is called and old value is never retained.

Keyword arguments:
If you have some funs which take many parameters, and you want to specify only some of them, then you can give values to such parameters by naming them.
def func(a, b=5, c=10):
 print 'a is', a, 'and b is', b, 'and c is', c
func(25, c=24)
func(c=50, a=100)

NOTE:we cannot use the non-keyword argument after the keyword argument like
#f(a=1,b=2,c) #this will be an error
#f(c,a=1,b=2) #this is legal

Variable argument parameters: sometimes you might want to define a function that can take any number of parameters. If *param is declared means, then all positional arguments till the end are taken in to a tuple called param. **param: keyword argument from that point till the end are collected in dictionary called param. **param will always be placed after *param in the parameter list.

def fun(ina=5,*tup,**dict1):
    sum = ina
    for num in tup:
        sum = sum + num
    print sum # 90 = 10+ 20+30+40
    for n in dict1:
        sum = sum + dict1[n]
    print sum  #90 + 10 + 20
fun(10,20,30,40, veg=10,non=20)

dir(): It lists the identifiers that object defines. for a module  identifiers include functions, classes, variables. when dir() is sent, it lists the names defined in the module.

n = [1,2,3,4]
n2 = n[:]
n2[0] = 6
n  --> [1,2,3,4]
n2 --> [6,2,3,4]

using bit wise operators in python we can check whether number is even or odd:
32 & 1 : 00100000  & 00000001 = 0000000
if 1 is returned then it is odd, 0 then it is even.

what are slots in python ?
For managing the memory we use slots. When lots of objects are created we can use __slots__

default dictionary and normal dict:
a = {}
print a[2] --> error

from collections import defaultdict
a = defaultdict(int)
a[3] --> no error and 0 is assigned
a --> success
-------------------------------------------------------------------------------------------------------------------------

install the pylint seperately.

#pylint file1.py ---------------> gives report of number of lines analysed, number of modules, classes, methods, functions,  docstrings present or not, comments, duplicate lines, etc and gives values out of 10.
#pylint -j 2 file1.py file2.py     ----> to call 2 files in 2 subprocesses.
-------------------------------------------------------------------------------------------------------------------------

General:

Both double and single quotes can be used for string representation.
''' and """ can be used for multi-line comments and doc strings.

To identify the datatype we can use:
import sys
print type(1)  ---------> int
print type(5.0) -------> float
print type([]) ---------> list
print type(()) -----------> tuple
print type({}) -----------> dict
print type(sys) -------------> module
class first():
 pass
fr = first()
type(fr)  -- >  <type 'instance'>
type(first) --> <type 'classobj'>

or
print isinstance(5, int) ---------> True
print isinstance(5.0, float) -----> True
print isinstance(object, class) ---> True

issubclass(subclass,parentclass)

To find sizeof a variable in python:
x = 4
from sys import getsizeof
getsizeof(x)  --> 12

print round(23.23) #23.0
print round(64.324, 2)  #63.32

if we have print 'does\nt' then
does
t
if we want to have \ present, then we can have print r'doesn\t' or print 'does\\nt'

print tuple([1,2,3]) ---------> (1,2,3)
print "abc" + str([1,2,3]) ----> abc[1, 2, 3]

print([1,2,3]+['str','ram'])  #[1,2,3,'str','ram']
print((1,2,3)+('str','ram'))  #(1,2,3,'str','ram')
print({'a':1,'b':2} + {'c':1,'d':2}) #error will be thrown
print(([1,2,3])+(['str','ram'])) #[1,2,3,'str','ram']
print((1,2,3)+['str','ram']) # eror will be trhown

k = 23
print('the value of k:{0}'.format(k))
print('the value of k:%d'%k)
print('the value of k: ',k) all 3 will yield same result

we can split only string:
print('my name is ramakrishna'.split('am')) #['my n' ,'e is r','akrishna']

we can join tuple, set, 2 strings or list to form string
print 'abc'.join(['1', '2', '3']) --------> 1abc2abc3

s = 'ramakrishna'
s.find('k') -->4
s.replace('a', 'b') --> 'rbmbkrishnb'

for i in range(5):  -------> 0,1,2,3,4
for i in range(1, 5):  -------> 1,2,3,4
for i in range(1, 5, 2):  -------> 1,3

range(-3,3) --> [-3,-2,-1,0,1,2]

list(x*3 for x in range(1, 4)) ------> [3, 6, 9]
tuple(x*3 for x in range(1, 4)) ------> (3, 6, 9)

a = [1, 2, 3,4,5,6]
print a[0] --------> 1
print a[1:3] -------> [2,3]
print a[::2] --------> [1,3,5]  -----------> multiples of 2 will be selected
print a[::3] --------> [1,4]  -----------> multiples of 3 will be selected
print a[:-1] --------> [1,2,3,4,5]  --------> [:len(a)-1] ---> [:5]
print a[::-1] --------> [6,5,4,3,2,1]  --------> reverse the string
OR
reverse the string:
b = len(a)
empty = ''
while b > 0 :
 empty +=a[b-1]
 b -=1
print empty

or
s = 'rama'
k = reversed(s)
x = ''
for i in k:
    x += i ---> amar

reverse the list:
empty = []
while b > 0 :
 empty.append(a[b-1])
 b -=1
print empty

or
l = [1,2,3,4]
k = reversed(l)
m = []
for i in k:
 m.append(i)
m -->[4,3,2,1]

print sorted(a)  -------> [1,2,3,4,5,6]  ----------- sort the list.
sorted(a, reverse=True) -->[6,5,4,3,2,1]  --------> sort in reverse order

print methodname.__doc__        # print docstring for a method.
print classname.__doc__       #print docstring for a classname

Frozen libraries: programs written in python are executable anywhere. we can run these programs where the pc does not contain python. These are true executables.

set : It is mutable and frozenset is immutable.
cities = set(["Frankfurt", "Basel","Freiburg"])
cities.add("Strasbourg")
cities
set(['Freiburg', 'Basel', 'Frankfurt', 'Strasbourg'])

cities = frozenset(["Frankfurt", "Basel","Freiburg"])
cities.add("Strasbourg")

Traceback (most recent call last):
  File "<pyshell#23>", line 1, in <module>
    cities.add("Strasbourg")
AttributeError: 'frozenset' object has no attribute 'add'

Variables declared outside function are implicitly global varables, and inside functions are implicitly local.
pass is used if the statement does not require any action or if we want to do something else in future.
Python does not have switch case statement. multiple if else statements can be used and dictionary can be used.

def pri():
 print('ramakrishna')
def out():
 print('reddy')
a = {10:pri, 20:out}
a[10]() -->'ramakrishna'
a[20]() -->'reddy'

#python does not have switch case statement. multiple if else statements can be used and dictionary can be used.

Module: It allows to organise the python code.
reload(module_name) : when there are changes done to the module_name, to see the effect in module which imported this module, we use this.

__init__.py : This file will indicate the directory as python package module. This file is usually empty.
Eg: /mydir/spam/__init__.py
      /mydir/spam/abc.py    -------> if we try to import abc.py to another, if __init__.py is not there, import will fail. Python will no longer consider this directory as python package module.

Generally this file is empty, but also execute initialization code for package or set the __all__.

What is __all__ ?
It is list of strings defining what symbols in a module will exported when "from <module> import *" is used.

foo.py

__all__ = ['bar', 'baz']

waz = 5
bar = 10
def baz(): return 'baz'

if from other module we use

from foo import *

print baz()
print bar 

print waz --> this will give error as __all__ will not contain waz symbol.

continue statement will skip the code in for loop.
re test the code.
; is used to combine 2 statements in 1 line. a=2;b=3

++ and -- operators are not present in python. Python does not deal with indices, instead objects.
swap 2 variables using a, b = b, a
file.readline().rstrip() ---------> strips so that no white spaces at the end of lines

s.rstrip() --> strips are white spaces(spaces, newlines, tabs etc)
s.rstrip(' ') --> strips only spaces.

similarly 
'a\tb c'.split() --> ['a','b', 'c'] --> split based on whitespaces (spaces, newlines, tabs etc).
'a\tb c'.split(' ') --> ['a\tb', 'c'] , splits only spaces.

None: It is returned to calling function when there is no return in the function definition.
eg: def f(x,y):
          z = x+ y

    a = f(3, 4)
   print a ----> None

Booleans: We can add or subtract booleans with numbers.
eg : 2 + True = 3
       2 - False = 2

Module: In python, Every file that ends with .py is called module. from 1 module we will be importing another module. So, import is done only once per session as it is costly. If you have made changes to the imported module and after importing is done, then we can reload() it to see the changes

from imp import reload
reload(ram)

To generate a pyc file:
import py_compile
py_compile.compile('file.py')

exec: This will execute python files in interpretor
>>exec(open('ram.py').read())

dictionary creation using lists:
keys = ['a', 'b', 'c']
values = [1, 2, 3]
d = {}
for (k,v) in zip(keys, values):
 d[k] = v

MRO in python:
http://makina-corpus.com/blog/metier/2014/python-tutorial-understanding-python-mro-class-search-path

Ruby and Python differences:
ruby and python both are interpreted languages with huge community.
missing blocks in python
compulsory indentation in python.
No interfaces in python.
strings are immutable in python but mutable in ruby.
""" triple quotes are not present.
similarities:
1)Both are object oriented, high level languages.
2)both provide standard libraries.
-------------------------------------------------------------------------------------------------------------------------

Regular Expressions:

import re
. = any character
^ = begin of string, or if used like [^]  then except that character in the brackets.
$ = end of string
* = zero or more repititions
+ = 1 or more repititions
\d = digit
\w = word[0-9A-Za-z]
\s = space

match:
s = "rama : krishna - 1909"
match=re.match(r'(\w+) : (\w+) - (\d+)',s)
print match.group() -----> rama : krishna - 1909
print match.group(1)----->rama
print match.group(2)----->krishna
print match.group(3)----->1909

sub:
a = 'rama is a bad boy'
b = re.sub(r'[ai]', 'o', a) --> any character found is replaced by 'o'
b -->'romo os o bod boy'

x=re.findall(r"\d+.\d+.\d+.\d+.","I have ip address 192.168.10.12 and 10.12.12.13")
print(x[0]) # 192.168.10.12
print(x[1]) # 10.12.12.13
print(re.findall(r'\d+.\d+.\d+.\d+',"This is the ip address 10.11.12.13")) #10.11.12.13
print(re.findall(r'[\d+].',"This is my ip-address 10.11.12.13")) #['10','11','12','13']
print(re.findall(r'\d+.\d+.',"This is my ip-address 10.11.12.13")) #['10.11','12.13']

print "i am ramakrishna".count('a')  #4
print "i am ramakrishna".count('a',10,30)  # 1 from 10th character to 30 character
print "i am ramakrishna".startswith(('i', 'r')) #True
print "i am ramakrishna".startswith(('r')) #False
print "i am ramakrishna".startswith(('r', 'i')) #True
print "i am ramakrishna".endswith(('r', 'i')) #False
print "i am ramakrishna".endswith(('r', 'a')) #True
print "i am ramakrishna".endswith(('a', 'a')) #True
print "i am ramakrishna".endswith(('a', '\n')) #True
print len("i am aramakrishna")

Datatypes of python:
mutable: list, set and dictionary
immutable: numbers, strings, and tuples.

List : [] and its mutable.
lang = ['tel', 'hin' , 'eng']
print lang  ---------------- >['tel', 'hin', 'eng']
print len(lang) -------------> 3
del lang[2]
print lang -------------------->['tel', 'hin']
lang.append('sci')
print lang --------------------->['tel', 'hin', 'sci']
print lang.index('sci')-------->2
lang.insert(2,'sco')
lang.insert(2,'sco')
print lang -----------------------> ['tel', 'hin', 'sco', 'sco', 'sci']
lang.pop(1) --------------------->'hin'
print lang------------------------>['tel', 'sco', 'sco', 'sci']
lang.remove('sco')
print lang----------------------->['tel', 'sco', 'sci']
lang[0] ='sans'
print lang    ---------------------> ['sans', 'sco', 'sci']
print lang.index('sco')  ----------> 1

n = [3, 4, 1, 2, 5]
print sorted(n) ------------------>[1, 2, 3, 4, 5]
print sorted(n, reverse=True) --> [5, 4, 3, 2, 1]

Tuple: () and its immutable and readonly. Tuple can be hashed for e.g it can be used as key for dictionaries. They can be used in geographical coordinates and ssh command input, output, error.
tup1 = (1,2,3,4)
print tup1[0]  --------------------> 1
tup1[0] = 100 -------------------> assignment is not supported.

String: ' '," " and its immutable and readonly.

Dictionary: {}, unordered
dict = {'name': 'rama', 'middlename': 'reddy' ,'lastname': 'pappula'}
del dict['lastname']
print dict ------------------------>{'middlename': 'reddy', 'name': 'rama'}
print dict.keys()-----------------> ['middlename', 'name']
print dict.values()---------------> ['reddy', 'rama']
d = {1: 'a' ,2: 'b', 3: 'c'}
for (key, value) in d.items():
    print key, value

def a(x):
    print "in funcation a %d"%x
    return
def b():
    print "in funcation b"
k={'i':a(1),'j':b()}
print k['i']
print k['j']

-------------------------------------------------------------------------------------------------------------------------

Lambda function:

Anonymous function: means name-less.
They are entirely optional.
If we want to embed small bits of executable code we can use this.
lambda can be used directly inside a list.
syntax: function = lambda arguments : logic with arguments

#lambda and def difference:
#multiple expression in def, single expression in lambda
#def creates a function and assigns a name
#lambda can be used inside list, dictionary.
#def has return statement but lambda has not.

f= lambda x,y,z : x+y+z
print f(10,20,30)
f = lambda driver : driver.get('http://www.google.com')
f(driver)
driver.find_element_by_xpath("//input[@class='gsfi']").send_keys('ram')

action = (lambda x: (lambda y:(lambda z:x + y + z)))
act = action(99)
a = act(4)
a(5)  --> 108

from __future__ import print_function
f = lambda x: print(x)
f('hi')

hi

Comprehension:Generating a list or dictionary from an expression or iteration.

list comprehension
l=[x**2 for x in range(5)]
print l  #[0, 1, 4, 9, 16]

convert a list of strings to list of integers.
n= ['1', '2', '3', '4']
[int(i) for i in n]

Dictionary comprehension:
d = {x:x**2 for x in range(1,5)} --> {1: 1, 2: 4, 3: 9, 4: 16}

Decorator: A function that takes another function and extends the behaviour of latter function without explicitly modifying it.
decorator: decorator is special kind function which takes a function or class and returns or class
@classmethod, @staticmethod, @property are the examples of decorators.

def fun(x):
    print("before wrapper")
    x()
    print("after wrapper")

def y():
    print("in wrapper")
fun(y)
-------------------------------------------------------------------------------------------------------------------------

Files:
f = open('D:\\google.txt', 'r+')
print f.name    ---------------------------------> D:\google.txt
print f.mode   ----------------------------------> r+

f.write('python is language.\n scripting language')
f.read() -----------------> read all the lines. read(20), 20 chars will be read.
f.readline() -------------> only 1 line
f.readlines() --------------> Keeps each line as the element of the list.
f.close()

for line in open("C:\\cygwin\\home\\ram_duplicate.pl","r+").readlines():
     print line.upper()

with open('ram.txt', 'wb') as f:
    x=f.readlines()

f.seek(0,0) --> will move the cursor to initial position
f.tell() --> tells where the position of cursor is.
--------------------------------------------------------------------------------------------------------------------------
python telnet client program:

#!/usr/bin/python
import telnetlib
username = 'abcd'
password = '1234'

tclient = telnetlib.Telnet('localhost','1023')
tclient.read_until('login:')
tclient.write(username + '\n')

tclient.read_until('password:')
tclient.write(password + '\n')

tclient.write('ls\n')
tclient.write('exit\n')

print tclient.read_all()

print(t.read_all())

We can use netcat as the telnetserver to listen of 1023 using the command "netcat -l 1023"  in 1 terminal.
-l = listen

--------------------------------------------------------------------------------------------------------------------------
Datetime:

import datetime
x = datetime.time(1,2,3,4)    ---  01:02:03.000004
x.hour  ---1
x.minute --2
x.second  -- 3

current date and time
a = datetime.datetime.now()
2015-03-30 18:29:15.573000
a.hour --- 18
a.minute -- 29
a.second -- 15
a.day -- 30
a.month --- 3
a.year --- 2015
c = a + datetime.timedelta(minutes=10)  ----------> to add 10 minutes to current time
print c --- 2015-03-30 18:49:15.573000
c.strftime("%H:%M")  ---18:49

-------------------------------------------------------------------------------------------------------------------------

logger module: Reports status, error and informational messages.
we can send the logs to a file.

import logging
logger = logging.getLogger('ramakrishna')
formatter = logging.Formatter('%(asctime)s - %(name)s - %(message)s')
sh = logging.StreamHandler()
logger.setLevel(logging.DEBUG)
sh.setFormatter(formatter)
logger.addHandler(sh)
logger.debug("All is well")
logger.debug("debug message")  -- If setlevel is debug, then debug, info, warn, error and critical will be displayed
logger.info("info message") -- If setlevel is info, then info, warn, error and critical will be displayed
logger.warn("warn message") -- If setlevel is warn, then warn, error and critical will be displayed
logger.error("error message")-- If setlevel is error, then error and critical will be displayed
logger.critical("critical message") -- If setlevel is critical, then only critical will be displayed

--------------------------------------------------------------------------------------------------------------------------

paramiko: for ssh and sftp

SSH: paramiko, pxssh, pexpect modules are there . paramiko uses pycrypto at low level.

import paramiko
'''paramiko provides ssh-key authentication, ssh shell access and sftp'''

ssh = paramiko.SSHClient()
ssh.set_missing_host_key_policy(paramiko.AutoAddPolicy())

'''host key is automatically stored in /home#more .ssh/known_hosts if ever connected to a new server. If key is ever changed, then client will refuse to connect to server. By default ("paramiko.RejectPolicy") which will not store any key in known_hosts file. To auto accept we can use "paramiko.AutoAddPolicy()". But this needs to be done on trusted hosts.'''

ssh.connect('127.0.0.1', username='ibx', password='chinna')

Only if the key needs to be taken from file then below line are add
#ssh.connect('127.0.0.1', username='ibx', password='chinna', key_filename='~/.ssh/known_hosts')

stdin, stdout, stderr = ssh.exec_command('uptime')

'''Each command returns 3 items in a tuple, (stdin,stdout,stderr).Actually "paramiko.Channel" will open a channel and sends command and output is returned as "paramiko.ChannelFile" which is read.We can use read(), readlines() and readline() to read the data. If output is enough to fill the buffer then instead of read() readlines() can be used.'''

#stdin.write('if the command executed will give prompt like ask for password then we can this')
#stdin.flush()
print(stdout.readlines())
ssh.close()

SFTP :paramiko, pysftp modules are there

import paramiko

ssh = paramiko.SSHClient()
ssh.set_missing_host_key_policy(paramiko.AutoAddPolicy())
ssh.connect('127.0.0.1', username='ibx', password='chinna')
sftp = ssh.open_sftp()
print('get operation success')
sftp.get('/home/ibx/Desktop/log.zip', 'log.zip')
'''From remote directory to local directory. sftp does not support *.py, this will give error'''
sftp.close()

sftp = ssh.open_sftp()
print('put operation success')
sftp.put('log.zip','/home/ibx/Desktop/log.zip')
sftp.close()

ssh.exec_command('rm -rf log.zip')
ssh.close()
--------------------------------------------------------------------------------------------------------------------------

Pexpect is for unix like operating system, below error will be thrown when tried to import:

import pexpect
Pexpect is intended for UNIX-like operating systems.

pxssh module which is based on pexpect is also intended for only unix-like operating systems.
--------------------------------------------------------------------------------------------------------------------------

Python 2to3 conversion:

for converting the python file from 2.x version to 3.x version we should use this.
for windows and linux, its different. Both python 2.x and 3.x libraries should be existing in the device.

In Windows:

>python c:/python34/tools/scripts/2to3.py pyfilename.py  --------> this will display the converted output

>python c:/python34/tools/scripts/2to3.py -w pyfilename.py ---> this will be written to a file with same name and folder and old 2.x version file will be in .py.bak


In Linux:

#python filename.py  ---> this gives python 2.x version.
#python3 filename.py--> this gives python 3.x version.

#2to3 filename.py  -----> to display the converted output
#2to3 -w filename.py -> to write to a file and old file will be named as .py.bak

--------------------------------------------------------------------------------------------------------------------------
Configparser:

from ConfigParser import SafeConfigParser
parser = SafeConfigParser()
parser.read('config.ini')
section = parser.sections()

print(section)

option = parser.options('masthan_reddy_family')

print(option)

value = parser.get('masthan_reddy_family','father')

print(value)

parser.set('sanjeeva_reddy_family', 'daughter1', 'punnamma')

print(parser.options('sanjeeva_reddy_family'))

print(parser.get('sanjeeva_reddy_family','daughter1'))

parser.add_section('shekar_reddy_family')

parser.set('shekar_reddy_family', 'father', 'shekar reddy')
parser.set('shekar_reddy_family', 'daughter1', 'swarna priya')
parser.set('shekar_reddy_family', 'daughter2', 'sneha priya')


section1 = parser.sections()

print(section1)

Reading all keys and value from ini file:
for section in config.sections():
    print section
    for (key, value) in config.items(section):
        print(key, value) ------------------------------------------------------------------------------------------------------------------------

 import shutil
shutil.copyfile('config.ini', 'config_copy.ini')

# shutil.rmtree('C:\Users\Ramakrishna\PycharmProjects\Sample1\problems\config_copy.ini') to remove whole of the# directory
shutil.move('config_copy.ini', 'config_move.ini')
--------------------------------------------------------------------
FTP library

from ftplib import FTP
ftp = FTP('127.0.0.1')
ftp.login(user='ibx', passwd='Kernel@123')
ftp.cwd('/home/ibx/Desktop') # set current working directory in server side
ftp.pwd()  # to get the present working directory of server
ftp.dir()  # to list the files in the directory of server

# to get the file from the remote directory('/home/ibx/Desktop')
filename = 'log.zip'
localfile = open(filename, 'wb')
ftp.retrbinary('RETR ' + filename, localfile.write, 1024)
#ftp.retrlines("RETR " + filename, localfile.write, 1024)  to read in ascii mode
#ftp.abort() to abort the file
#ftp.delete(filename) to delete the file
ftp.quit()
localfile.close()

# to put the file to the remote directory
filename = 'log.zip'
# Also we can have like x = filename.split('.') , if x[1] == 'txt'
# or ftp.storlines("STOR " + file, open(file)) for ascii write
ftp.storbinary('STOR ' + filename, open(filename, 'rb'))

ftp.quit()

-------------------------------------------------------------------------------------------------------------------------

Inspect module:

How to know the parameters of a module method when we know the module:
using inspect we will get to know

import inspect
import paramiko
ssh = paramiko.SSHClient()
inspect.getargspec(ssh.connect)

inspect.getargspec(pydoc.Helper.__init__)

class Class1(object):
 def __init__(self,name):
  self.name = name
 def method1(self, rollno, sub, marks):
  self.rollno = rollno
  self.sub = sub
  self.marks = marks
 def method2(self, tab=3, mas=6):
  pass

inspect.getargspec(Class1.__init__)   ----> ArgSpec(args=['self', 'name'], varargs=None, keywords=None, defaults=None)

inspect.getargspec(Class1.method1)  -----> ArgSpec(args=['self', 'rollno', 'sub', 'marks'], varargs=None, keywords=None, defaults=None)

inspect.getargspec(Class1.method2)   -----> ArgSpec(args=['self', 'tab', 'mas'], varargs=None, keywords=None, defaults=(3, 6))
----------------------------------------------------------------------------------------------------------------------

for wait, we can have:

import time
time.sleep(5)

--------------------------------------------------------------------------------------------------------------------------
Ip address regular expression:

a = "this is my ip address 10.101.10.1"

theIP = re.findall(r"\d{1,3}\.\d{1,3}\.\d{1,3}\.\d{1,3}", a)

print(theIP)

password generator:

import string
from random import *
char = string.ascii_letters + string.punctuation + string.digits
password = "".join(choice(char) for x in range(randint(8,16)))
print password

Check for files that end with .exe in a given directory:

import os
newlist = []
for names in os.listdir('.'):
      if names.endswith('.exe'):
            newlist.append(names)

print newlist

import glob
glob.glob('*') ---------------> to print the list of files in the directory.

-------------------------------------------------------------------------------------------------------------------------

 Serial:

from serial.tools import list_ports

Device_port = list(serial.tools.list_ports.grep('Console'))[0][0]  --> we can have console, status ports.
#ser = serial.Serial('/dev/ttyUSB0') # open serial port in linux
 ser = serial.Serial(port=Device_port, baudrate=9600, parity=serial.PARITY_ODD,stopbits=serial.STOPBITS_TWO, bytesize=serial.SEVENBITS)
ser.write('commands')
ser.read()
ser.close()

Console port: Direct physical access to the device we can get using console port. We cannot do telnet or ssh to the console port.

--------------------------------------------------------------------------------------------------------------------------

Xmlrpc Client and Server:

SimpleXMLRPCServer: Server side library for xml-rpc implementation. Using this we can define methods and classes in server, register these class_instances and functions, listen forever.

xmlrpcserver.py

from SimpleXMLRPCServer import SimpleXMLRPCServer
import os
server = SimpleXMLRPCServer(('localhost', 9000)) #create instance and tell where to listen
def list_the_files(directory):  #what server can serve are defined in functions
    return os.listdir(directory)

server.register_function(list_the_files)
server.serve_forever()  #put in infinite loop to handle the requests at any time.

or we can use class and register it:
class ServerClass(object):
 def list_of_files(self, dir):
  return os.listdir(dir)
 def time_of_server(self):
  return datetime.datetime.now()
 def server_name(self):
  return 'ramakrishna'

server.register_instance(ServerClass())
server.serve_forever()

We can know the methods of a class and functions that are present in Server using:
server.register_introspection_functions() ---- this should be done after register_function
server.serve_forever()

then in client side client.system.listMethods()  --------> This will give all method names in a list.


xmlrpclib: Client side library for xml-rpc implementation. Using this we can connect to server and retrieve the values.

xmlrpcclient.py

import xmlrpclib
import sys
client = xmlrpclib.ServerProxy('http://127.0.0.1:9000')
print client.list_the_files('/home/')
print client.list_the_files('/')
print client.list_the_files('/home/ibx')
print client.list_the_files(sys.argv[1])

server side

import socket
hostname = socket.gethostbyname(socket.gethostname())
from SimpleXMLRPCServer import SimpleXMLRPCServer
server = SimpleXMLRPCServer((hostname, 8000), allow_none=True)
class get_google():
 def open_browser(self,url):
  self.driver = webdriver.Firefox()
  self.driver.get(url)
 def close_browser(self):
  self.driver.close()

server.register_instance(get_google())
server.serve_forever()

client:

import xmlrpclib
client = xmlrpclib.ServerProxy("http://"+serverip+":8000/")
client.open_browser("http://www.google.com/")
client.close_browser()

Python HTTP server:

SimpleHTTPServer module can be used in python to create  HTTP server that provides standard GET and HEAD request handlers.

In linux or windows, it can be used.

$python -m SimpleHTTPServer 8080

The directory where you used this command will become server directory and then we can access this server using http client like web browser and type: http://127.0.0.1:8080

logs can be seen in server will files are accessed from server.

--------------------------------------------------------------------------------------------------------------------------

OOPS PYTHON:

What is OOPs:
Objects are kept at center and more important then the logic to manipulate those objects.

class: It is blue print,  behavior or set of properties.
object : Its the instance of the class.

class Basic():
 def __init__(self):
  print('Object created')
 def method(self):
  print('This is in method')
 def __del__(self):

   print('Object destroyed')

obj = Basic()  --> Object created
del obj  --> Object destroyed.

class Base(str):
 pass
obj = Base()
type(obj)  --> <class '__main__.Base'>
isinstance(obj, Base)  -->True
isinstance(obj, str)  -->True

method overloading:
Its a OOP feature, where a class can have 2 or more methods with same name, if the argument lists are different.
If that method is constructor, then it is constructor overloading.
Method overloading is not supported in python. Below way we can use instead of method overloading.

class baseClass():
  def area(self, d, e=None):
    if e == None:
      area = d * d
      return area
    else:
      area = d * e
      return area

obj_base = baseClass()
k = obj_base.area(10)
print k

Method Overriding:
Its a concept where subclass or child class provides a specific implementation of method that is already provided by one of its superclasses or parent classes.

class Parent(object):
    def area(self,a):
      area = a*a
      print area

class Child(Parent):
    def area(self, a):
      area = a**a
#      area = super(Child, self).area(20) , we can use this if we want to call parent class instead of child class.
      print area

obj_b = Child()

obj_b.area(10)

Class variable:
class First():
 rama = 4
     def met1(self):
         return 2 * First.rama

fr = First()
fr.__class__.rama  -->4
First.rama --> 4
First.rama = 5
fr.__class__.rama  --> 5
fr.met1() --> 10  # This is bound method call , called with the object
First.met1(fr) --> 10 # This is unbound method call, called with the class and object as first parameter.


Functions that are defined inside the classes are called methods.
3 types are methods are there:
1)Instance method: These methods require instance of a class in order to be used.
self is always the first parameter. Python passes the object to the method using self.

2)static method: some variables are accessed by all the instances of the class commonly and they are not restricted to a single object. without creating the object we can call these methods using classname.
Class and  instances can be used to access the static variable or method using classname.methodname or instancename.methodname.
They do not take self as the first argument and @staticmethod decorator is used.

@staticmethod
def staticmethod1():
    pass


3)class method: It takes cls as the first parameter and @classmethod decorator is used. It is accessed by all instances of the class.

@classmethod
def classmethod1(cls):
    pass

Inheritance: Its a process by which a child class derives the data and behavior of parent class. Its mainly for not repeating the code.

class Animal:
   def __init__(self):
      print "Animal created"

   def whoAmI(self):
      print "Animal"

   def eat(self):
      print "Eating"

class Dog(Animal):
   def __init__(self):
      Animal.__init__(self) #must explicitly call base class __init__method
      print "Dog created"

   def whoAmI(self):
      print "Dog"

   def bark(self):
      print "Woof!"

d = Dog() -->  Animal created,Dog created #object created.
d.whoAmI() --> Dog  # overwiring is done
d.eat()  ----> Eating # inherits base class
d.bark()  ---> Woof!  # extends its behavior.

polymorphism: Ability to process objects differently depending on their data type or class.
x = 'string'
len(x) --> 6
x = [1,2,3]
len(x) --> 3
x = {1:'a', 2:'b'}
len(x) --> 2
x = 5
len(5) --> error.

Here string, list, dict are no error and int will show error for same len method. len is behaving different for different data types.

Abstract method: Its a method that is declared but does not contain implementation.
Abstract Class: Abstract classes cannot be instantiated means objects cannot be created for abstract classes.

from abc import ABCMeta, abstractmethod

#interface/abstract class:
class Shape(object):
    __metaclass__ = ABCMeta
    @abstractmethod
    def area(self): pass  #methods are just declared.

    @abstractmethod
     def perimeter(self): pass

sp = Shape() --> This will give error, as objects cannot be created for abstract class.

class Rectangle(Shape):  #---> abstract class is inherited.
    def __init__(self, leng, wid):
        self.leng = leng
        self.wid = wid
        super(Rectangle, self).__init__()  #If base class has init method, they we dont write this.
    def area(self):                  # Method overriding
        return self.leng * self.wid
    def perimeter(self):
        return  2*self.leng + 2*self.wid

rec = Rectangle(2,3)
rec.area()
rec.perimeter()

class Square(Rectangle):
    def __init__(self, side_len):
        self.side_len = side_len
        super(Square, self).__init__(side_len, side_len)

s = Square(5)
s.area()
s.perimeter()

class Circle(Shape):
 def __init__(self, rad):
     self.rad = rad
     super(Circle, self).__init__()
 def area(self):
  return 3.14 * self.rad * self.rad
 def perimeter(self):
  return 2 * 3.14 * self.rad

c = Circle(3)
c.perimeter()
c.area()

class Triangle(Shape):
 def __init__(self, side_a=1, side_b=1, side_c=1, hyt=1):
  self.side_a = side_a
  self.side_b = side_b
  self.side_c = side_c
  self.hyt = hyt
  super(Triangle, self).__init__()
 def area(self):
  return (self.side_b * self.hyt)/2
 def perimeter(self):
  return self.side_a + self.side_b + self.side_c

t = Triangle(1,2,3)
t.perimeter()
t.area()

-----------------------------------------------------------------------------------------------------------------------
subprocess:

process: A program in execution is called process. It contains its state, includes memory, program counter to keep track of instructions executed, etc. Process executes statements one after the other in a sequence called the main thread of process. At any given point of time, program is doing only 1 thing.

Subprocess executes concurrently with main process. Subprocess allows to create new process, connect to io pipes and obtain return codes.

To run unix commands, we need to create subprocess.
os.system('echo $HOME') ---> /home-stdout  0-result of executing this command.

os.system('ls > output.txt') --to only get the output and not the result.

os.popen() and os.system() are same except popen gives a file stream

subprocess replaces the older modules like os.system, os.popen

subprocess.call(['ls', '-l']) ----to avoid escaping quotes.

subprocess.call('ls -l', shell=True) ---this will call the intermediate process to run the command.

return_0_1 = subprocess.check_call('ls') --- checks the exit code

return_value = subprocess.check_output('ls') ---- returns the output of ls.

To run a process and read all its output, set stdout to PIPE and call communicate()

reading is done by Popen().

pr = subprocess.Popen('ifconfig', stdout=subprocess.PIPE, shell=True)
output, error = pr.communicate()
print(output)


if we dont include stdout=subprocess.PIPE and stderr=subprocess.PIPE, then we will get none in pr.communicate() 

Its not mandatory to have shell=True argument

to send message to stdin, we can argument to communicate method

pr = subprocess.Popen('ls', stdin=subprocess.PIPE)
pr.communicate('hello')
--------------------------------------------------------------------------------------------------------------------------

MRO in python: Method Resolution Order.
class A(object): pass
A.__mro__     -- >(<class '__main__.A'>, <type 'object'>)
class B(A): pass
B.__mro__  -->  (<class '__main__.B'>, <class '__main__.A'>, <type 'object'>)
class C(B): pass
class D(C,B,A): pass    ---> If (A,B,C) is used instead, then error is shown indicating MRO.
D.__mro__
(<class '__main__.D'>, <class '__main__.C'>, <class '__main__.B'>, <class '__main__.A'>, <type 'object'>)

MRO will explain about in which order the classes are evaluated. It returns the order how the methods of classes are evaluated.
--------------------------------------------------------------------------------------------------------------------------

CSV file using python

import csv
f = open("test.csv", "wb")
writer = csv.writer(f)
writer.writerow(("name", "age", "phone"))
writer.writerow(("ramakrishna", 27, 9052310828))
writer.writerow(("abcd", 24, 902126815))
f.close()


import csv
fr = open("test.csv", "rb")
reader = csv.reader(fr)
reader.next() --- ['name', 'age', 'phone']
reader.next() --- ['ramakrishna', '27', '9052310828']
reader.next() --- ['abcd', '24', '902126815']
fr.close
--------------------------------------------------------------------------------------------------------------------------
                                     smtp mail sending

smtp mail sending:
import smtplib
server = smtplib.SMTP('smtp.gmail.com', 587)
server.starttls()
server.login('ramakrishna.pappula@innobox.com', 'Reddy05841a0434')
server.sendmail('ramakrishna.pappula@innobox.com', 'ramakrishna.pappula@innobox.com', 'Hello World!')
server.close()

------------------------------------------------------------------------------------------------------------------------
                                                      elementtree module

Xml parsing and xml file creation in python is done using elementtree module. It needs to be downloaded.

<head>
 <title>My Podcasts</title>
 <dateCreated>Sun, 07 Mar 2010 15:53:26 GMT</dateCreated>
 <dateModified>Sun, 07 Mar 2010 15:53:26 GMT</dateModified>
 <to>Tove</to>
    <from>Jani</from>
    <heading>Reminder</heading>
    <body name='ramakrishna'>Don't forget me this weekend!</body>
</head>

from elementtree import ElementTree
root = ElementTree.parse('D:\\sqlite3\\samplexml.xml').getroot()
print root.getchildren()
[<Element title at 1fe8648>, <Element dateCreated at 1fe85f8>, <Element dateModified at 1fe8670>, <Element outline at 1fe86e8>]
print root.findtext('title')
My Podcasts
print root.findtext('dateCreated')
Sun, 07 Mar 2010 15:53:26 GMT

node=root.find('./body')
print node.tag
body
print node.attrib.keys()
['name']
print node.attrib.values()
['ramakrishna']
for name, value in node.attrib.items():
 print '%s = %s'%(name, value)
name = ramakrishna

-------------------------------------------------------------------------------------------------------------
XML parsing using xmltodict module:                                         

x = "<mydocument has='an attribute'>
        <and>
          <many>elements</many>
          <many>more elements</many>
        </and>
         <plus a='complex'>element as well</plus>
         </mydocument>"

import xmltodict   -----------> download it
# from file
with open('file.txt') as f1:
    doc = xmltodict.parse(f1.read())
or
doc = xmltodict.parse(x)
doc['mydocument']['@has'] ---> u'an attribute'
doc['mydocument']['and']['many'] ---> [u'elements', u'more elements']
doc['mydocument']['plus']   ---> OrderedDict([(u'@a', u'complex'), ('#text', u'element as well')])
doc['mydocument']['plus']['#text']   -----> u'element as well'

to convert from unicode to string:

x = u'an attribute'
type(x)  -----> unicode
a = str(x)
print a --------> 'an attribute'
-------------------------------------------------------------------------------------------------------------
                                          PYTHON TO EXE conversion:
py2exe conversion: with this we dont require python to be there on the pc where you are running. no libraries and external modules are required.

download : py2exe-0.6.9.win32-py2.7.exe and pyinstaller-2.0(DONT execute using python setup.py install)

go to the command prompt and execute: pyinstaller.py --onefile c:\abcd.py

after execution go to pyinstaller2.0 folder and check folder will be created with file name. Under this /dist will give you .exe file of your program.

-------------------------------------------------------------------------------------------------------------------------
                              PYTHON WINDOWS APP TESTING:
pywinauto

from pywinauto import application
app = application.Application()
app.start_('notepad.exe')

app.notepad.edit.TypeKeys('Hello')

app.notepad.edit.TypeKeys('World')

app.notepad.edit.TypeKeys ('World')

app.Notepad.MenuSelect('help->aboutnotepad')
app.aboutnotepad.OK.Click()

--------------------------------------------------------------------------------------------------------------------------
HTTPlib2 :

http methods:

Get operation:

import httplib2
h = httplib2.Http(".cache")      ---. creates an object with ".cache" directory, which can be used in                                                                future to get result from here, instead of asking the server.
resp, content = h.request("http://example.org", "GET")
print resp.status -----> 200

Put operation:

import httplib2
h = httplib2.Http(".cache")
h.add_credentials('name', 'password')
resp, content = h.request("https://example.org/chap/2", "PUT", body="This is text", headers={'content-type': 'text/plain'})
print resp

Post operation:
import httplib2
from urllib import urlencode
data = dict(name="ram", comment="a statement")
resp, content = h.request("http://bitworking.org/news/223/Meet-Ares", "POST", urlencode(data))
resp

-------------------------------------------------------------------------------------------------------------------------

                                                PYTHON PROGRAMS:

:program to find whether entered number is prime or not.
prime numbers are greater than 1
num = int(raw_input("enter number:"))
if num>1:
    for x in range(2,num):
        if(num%x==0):
            print("number is not prime")
            print(x,"times",num//x,"is",num)
            break
    else:
     print("number is prime")

:print all primes number within interval
for i in range(enter_num1, enter_num2):
    for x in range(2,i):
        if(i%x ==0):
            print(i,"is not prime")
            print(x,"times",i//x,"is",i)
            break
    else:
        print(i,"is prime")

:Factorial of a number
x = int(raw_input("Enter a number:"))
if x <=0:
    print("invalid")
if x == 1:
    fact = 1
else:
    for i in range(1,x+1):
        fact = fact*i
print "factorial of ",x,"is",fact

:Factorial using recursion
def fact(n):
    if n==1:
        return 1
    else:
        return(n*fact(n-1))
x=fact(5)
print x

:fibonacci series
x = int(raw_input("Enter a number:"))
n1=0;n2=1;count=2
if x <=0:
    print "enter a valid number"
elif x == 1:
    print 0
else:
    print n1
    print n2
    while count < x:
        n3=n1+n2
        print n3
        n1=n2
        n2=n3
        count += 1

:fibonacci series using recursion
def feb(x):
    if x<=1:
     return x
    else:
     return(feb(x-1)+feb(x-2))  
x = int(raw_input("Enter the terms:"))
for i in range(x):
    print(feb(i))

#palindrome or not
a=raw_input("Enter a string:")
b = a[::-1]
if b == a:
    print("Enter string is palindrome")
else:
    print("Not a palindrome")

:Amstrong number with in given range = 371 = 3*3*3 + 7*7*7 +1*1*1
x = int(raw_input("Enter the lower range:"))
y = int(raw_input("Enter the upper range:"))
for i in range(x,y+1):
    sum=0
    temp = i
    while temp > 0:
        k = temp%10
        sum = (k**3) + sum
        temp = temp/10
    if i ==sum:
        print i,"is amstrong number"

:Decimal to binary conversion
def bin(x):
    if x>1:
        bin(x//2)
    print(x % 2)
dec=int(raw_input("enter the number:"))
bin(dec)

a=['ram', 'kri', 'red', 'pap']
for x, y, z in a:
 print x+y
ra
kr
re
pa

-------------------------------------------------------------------------------------------------------------------------
PYUNIT testing:

setUp has an error, then tests will not run.
If setUp is run, teardown will be run even if there is error in tests.
setting setUp, tests and teardown is called fixture(need to perform 1 or more methods with initializations and cleanups).



__author__ = 'ramakrishna.pappula'
__date__ = '1/1/2015'
__copyright__ = "google"

import unittest

def setUpModule():
    print("setUpModule")
   #Create Connection
def tearDownModule():
    print("tearDownModule")
   #Close Connection

class Multiplication(unittest.TestCase):
    @classmethod
    def setUpClass(cls):
        print("setUpClass")
        pass

    def setUp(self):
        print("setUp")
        self.a = 50
        self.b = 0

    @unittest.skip("Demonstrate skip ")
    @unittest.skipIf(mylib.__version__ < (1,3))
    @unittest.skipUnless(sys.platform.startswith("win"), "windows only")
    def test_multiplication_value(self):
        result = self.a / 10
        print(result)

    def test_Divisin_value(self):
        result = self.a / 10
        print(result)

    def tearDown(self):
        print("tearDown")
        self.a = 0
        self.b = 0

    @classmethod
    def tearDownClass(cls):
        print("tearDownClass")
        pass

if __name__ == '__main__':
    unittest.main()

Asserts: assertTrue, assertFalse, assertEqual, assertNotEqual, assertIn, assertNotIn(), assertRaises --> To check specific exception raises.
#setUp and tearDown are instance methods
# setupclass and teardownclass are class methods

We can run test scripts at module, class and even at method level.
python -m unitest  test_module.test_class.test_method


--------------------------------------------------------------------------------------------------------------------------
str = 'abcxyz.xml'
for strings we can use str.startswith('abc') or str.endswith(('.html', '.xml'))

using #!/usr/bin/env python at the top of the can make script portable. In linux, mac, Freebsd. In windows this is ignored.
If there are multiple versions of python installed. Then based environment settings priority value this is used.

Dont compare boolean values to True or False:

1)
if google:  ---> good
if google == True:  ----> bad
if google is True:  -------> worse

2)
if cond:
    return True
else:
    return False

instead use
return bool(cond)

3)In python we can do swapping like below without a temp variable:
   a,b = b,a

Also a=1
a,b = a+1, a+1
print a --> 2  
print b --> 2  --> new value of a will not be used. 

a = 'asd'
print "The list is empty" if len(a)==0 else "The list is not empty"

5) Instead of 
for line in f.readlines():       use
for line in f:   ----> It saves memory

6)print 'print in 2.7 is a statement' 
from __future__ import print_function
print 'print in 2.7 is a statement' --------> This will give error as print is function in future
print('print in 2.7 is a statement') ----> This is not error.

7) huge Python libraries are found http://www.lfd.uci.edu/~gohlke/pythonlibs/

8) dictionaries are unordered by default. pprint module will sort dictionary based on keys
a = {3:'a', 9:'z', 5:'v', 1:'d', 7:'x'}
import pprint
pprint.pprint(a)
{1: 'd', 3: 'a', 5: 'v', 7: 'x', 9: 'z'}

9) __new__ is a class method which will create instance.
   __init__ will initialize the object.

10) For matplotlib : http://matplotlib.org/examples/index.html
11) finally should be used after try: and except:

12) "python -m compileall *py" for pyc and  "python -Om compileall *py" for pyo files generation

13)  x = (3 + 7) ------> type(x)  ----------> int
     x = (3 + 7, ) ----> type(x)  ----------> tuple

14) trailing ',' in the list is ignored, hence [1,2,3,4,] is perfectly fine.

15) with statement guarantees that file object is closed at block exit.

16) 4 spaces are not prescribed by python language. Indentation needs to be consistent is prescribed.

17) the keys of the dictionaries must be only immutable(numbers, strings, tuples)

18) when ever possible try to avoid : 'from module import *'
import module and from module import difference is that, module itself is imported, but namespace is retained. That is why we need to use module.function() to access a function. But using from module import, You are actually importing specific functions and attributes from other module into your own module, that is why you are directly using without referencing.

os module has open() method, Also file is opened using open(), so we will not know which will be used.
if exit() is used in many places, we will not know which module is used. But if os.exit(), we will directly know which module is used.

19) if x in dict.keys():

20) Avoid using '+' for string concatenation. instead use str.join()

http://www.mypythonquiz.com/question.php?qid=257

getting index of each element in list:
l = [3, 10, 5, 6, 4, 9, 7]
x = sorted(l)
for i in x:
    print(str(i) +" is present at index "+ str(l.index(i)))

combining 2 lists so that 3 list contains ordered list:
l1 = [1,3,5,7,9]
l2 = [2,4,6,8,10]
i = 0
while i < len(l1):
 l.append(l1[i])
 l.append(l2[i])
 i +=1

Get number of times an element if list is present:
l = [1, 2, 2, 4, 1, 2, 4, 2, 1, 4, 3]
for j in list(set(l)):
 print(l.count(j))

output: 3, 4, 1, 3
list(set(l)) = [1, 2, 3, 4] ------> 1 is repeated 3 times, 2 is repeated 4 times etc

subprocess.Popen([sys.executable, script_name])
os._exit(1) ---> to come out of the program.

THREADING MODULE: It helps python program to run multiple operations concurrently in the same process space. Python has contruct called Global Interpreter Lock(GIL), Which makes sure that only 1 thread at any point of time. Thread acquires the GIl does little work and then passes GIL to next thread.

threading with lock: If there is a variable shared between 2 threads. while accessing, first 1 thread will lock it, modify it, then releases it, so that other thread can use it.

import threading
import time

count = 0
def inc():
 global count
 with threading.Lock():
     print 'lock acquired'
     count += 1
     print count
     time.sleep(2)

def method1(m):
  for i in range(m):
      print "I am printing method1 \n"
      inc()

def method2(n):
  for i in range(n):
      print "I am printing method2 \n"
      inc()

m1 = threading.Thread(name='method1', target=method1, args=(5,))
m2 = threading.Thread(name='method2', target=method2, args=(6,))

m2.setdaemon(True) --> by setting this, we are explicitly killing once all the non-daemon threads are killed without interuppting the main program.

m1.start()
m2.start()

m2.isAlive() --> to check whether the thread is alive or not.

m1._Thread__stop()

m2._Thread__stop()

compare 2 lists and get the difference:
script = list(set(scripts_after) - set(scripts_before))

collections module is used for counting the elements in string, tuple, list.

import collections
x = collections.Counter(['a', 'b', 'c', 'a', 'c'])
x
Counter({'a': 2, 'c': 2, 'b': 1})

y = collections.Counter('abcd12a')
y
Counter({'a': 2, 'c': 1, 'b': 1, 'd': 1, '1': 1, '2': 1})

y.update('12')
y
Counter({'a': 2, '1': 2, '2': 2, 'c': 1, 'b': 1, 'd': 1})

y['1']
2

y.update('1')
y
Counter({'1': 3, 'a': 2, '2': 2, 'c': 1, 'b': 1, 'd': 1})
y.most_common(1)
[('1', 3)]

for name, value in y.most_common(1):
 i = name
 j = value

i = 1
j = 3

global variable : If a = 2 is a global variable, then if we want to use it in every function, then 'global a' must be given in every function.

Set : It is collection of unique(no duplicates), un ordered, immutable objects, so list and dictionary cannot be elements in the set. Set by itself is mutable, so we can add or remove items.
{1,2,3} -- correct
{1,2,3, [1,3]} -- incorrect
a = {}
type(a) --> dict
a = set() 
type(a) --> set

a = {1,12,3}
type(a)   <type 'set'>
a.pop()    1
a         set([3, 12])

a.add(1)
a         set([1, 3, 12])


a = {1,2,4}
b = {4,5,6}
a | b  -->      set([1, 2, 4, 5, 6])
a & b -->      set([4])

all({1,2,3}) --> True
all({1,2,0}) --> False
any({1,2,3}) --> True
any({0,0,0}) --> False

Game development:

https://www.youtube.com/watch?v=mTmJfWdZzbo

In version 2 and 3, print(5//2) will return 2.(floor division or integer division)

range: returns a list. It creates lists in memory. like for range(0,20), entire list of 20 elements will be created in memory.
xrange: returns an object. It creates object in memory. like for xrange(0,20), only 1 element will be created at any time in memory. For memory efficiency we can use this. It resolves the number lazily.

map: map returns a list by applying function to the items a sequence. mostly we can use lambda function as argument.

map(lambda x: 5/9(x-32), [1,2,3,4])

filter: Returns a list containing the items by applying if function(items)  is true. mostly we can use lambda function as argument. The function will return only True or False based on the condition.

res = filter(lambda x : x % 2, [1,2,3,4,5])
res = [1,3,5]

reduce:  Applies function to 2 consecutive arguments cumulatively to a sequence.

res = reduce(lambda x,y : x+y, [1,2,3])
res = 6

zip(): Returns the list of tuples where each tuple contains i-th element from each of sequences.
a = [1,2,3]
b = [7,8,9]
c = [4,5]
zip(a, b)
[(1, 7), (2, 8), (3, 9)]
zip(a,c)
[(1, 4), (2, 5)]

Enumerate: It will return the index and value of the items in pair.
y = [1,2,3]
list(enumerate(y))
[(0, 1), (1, 2), (2, 3)]

2.x and 3.x python differences:
1. xrange is removed as range() functions acts similar like xrange in 3.x

2. In try, except scenarios, as is present.
In 2.x
try:

except Nameerror, x:

In 3.x
try:

except Nameerror as x:

3. re.fullmatch() is present in python 3.x, but not present 2.x
4. Exec is a statement in python 2.x, but a built-in function in python 3.x
5. print is statement in python 2.x, but a function in python 3.x

6)  In version 2 print(5/2) will return 2 and in version 3 it will return 2.5(floating point division).

7) raw_input('Its in python 2'), input('Its in python 3')

-------------------------------------------------------------------------------------------------------------------------

REGULAR EXPRESSIONS:
\d : any number
\D : anything but a number
\s : space
\S : anything but a space
\w : any character
\W : anything but a character
.    : any character, except for new line
\b  : whitespace around words
\.  : period

{1, 3} --> are expecting, eg: 0-99 is given by {1,2} length
+ :1 or more
? : matches 0 or 1 occurence of pattern to its left.
* : 0 or more
$ : match the end of the string
? : match the beginging of the string
| : either or
[] : range in varience, eg: [a-zA-Z0-9]

\n : new line
\s : space
\t  : tab

re.split() : splits the string to list.
eg : re.split(r'asd', 'kjhsdfkjKUJHYasdJHWEasdjh') --------> ['kjhsdfkjKUJHY', 'JHWE', 'jh']
re.match() : this will check the pattern at the very start of the string.
eg: y = re.match('ram', 'ramakrishna is good boy') --> found
     y = re.match('good', 'ramakrishna is good boy')  --> NOT found
re.search(): this will check the pattern throughout the string
eg: y = re.search('ram', 'ramakrishna') --> found
     y = re.search('am', 'ramakrishna')  --> found
re.findall():  This will check the pattern and returns the matches in a list.
re.sub(): To substitute a string in place of another string. re.sub(regex, substitute, string)
re.fullmatch: this is present from 3.4, this will check the pattern for entire match in string

re.I  or re.IGNORECASE: ignore case sensitivity
re.M or re.MULTILINE : 
re.I | re.M

module:
Its simply a python source file. 

package:
group of python files in a directory is package.

lists are evaluated from left to right
l = ['ram',18,'uppal']
name, age, addr = l
name --> 'ram'
age -->18
addr -->'uppal'

Difference between repr and str:
str prints human readable format , 
repr prints string to avoid unambiquity. Its mainly for developers for debugging, what we are actually sending we can see using repr.
a = 'A is for America'
str(a) --> 'A is for America'
repr(a) --> "'A is for America'" --> we can send this to interpreter and there will be no error

import datetime
a = datetime.datetime.now()
str(a)
'2016-02-04 10:56:54.995000'
repr(a)
'datetime.datetime(2016, 2, 4, 10, 56, 54, 995000)'   --> we can send this to interpreter and there will be no error

while else loop:
i = 0
while i<5:
 if i > 7:
     print(i)
     break
 i += 1
else:
 print('i is not more than 7')

for i in range(0,5):
 if i> 7:
     break
else:
        print('i is not in the range')   ---> i is not in the range

x = ([1,2,3]) or x = [(1,2,3)] both are lists.

x= [(1,2,3), 4, 5]
we can access x and append x as it is list, but cannot append to x[0] as it is tuple.
x=([1,2,3], 4, 5)
we cannot access x as it is tuple, but we can access x[0] as it is list and modify it.

Eval function: Eval function takes the string representation of python expression and evaluates it. Eval function will help python program to run python code within itself.
import os
eval("os.getcwd()")
'C:\\Python27'
x =1
y = eval('x+1') 
print y --> 2
Exec : It compiles and immediately executes python statement or set of statements in a string.
exec("if 'ram' == 'ram': print('ramakrishna')")
exec() is similar to eval(), but it does not return any value.

difference between eval and exec:
eval: It will return the value
exec: It does not return the value.
In python 2.x, exec is a statement while in 3.x its a built-in function

febinoci series:

a, b = 0,1
for i in xrange(0,10): or range(0, 10)
 print a
 a,b = b, a+b

tuple vs list:
Once created, tuple cannot be changed(fixed size). It is immutable, we cannot append and delete the values. Tuples are faster than lists.

collections module:
datatypes
MRO in python:
private and protected methods:

MY NOTES:

''' this is a multi-line
comment string which consists of \n \t
which are also neglected'''

print('does\not') #does  newline ot
print('does\\not') #does\not
print(r'does\not') #does\not

# only string can be split to list.
# string,list, set and tuple can be used to join as a string.

print('my name is ramakrishna'.split()) #['my' ,'name' ,'is','ramakrishna']
print('my name is ramakrishna'.split('am')) #['my n' ,'e is r','akrishna']

l1 = ['a','b','c']
print ''.join(l1) #abc
''.join(('a','b','c')) #'abc'
'xyz'.join('abc') ->'axyzbxyzc'
'xyz'.join('1') ->'1'
 'xyz'.join('a') ->'a'
'xyz'.join('ab') ->'axyzb'

print('1111'.isdigit())
print('abc'.isdigit())
print('acb'.isalpha())
print('acb'.islower())

a = [123,'wea',2.32,'a2ww1']
print(a[1:4]) --> ['wea',2.32,'a2ww1']

list append will be done at the end
list insert will be done at a particular index
list[0]=1, replace at 0 index with 1.

del(a): deletion of list is done

#dictionary
a = {'name':'rama', 'rollno':34, 'coll':'kask'}
print(a['name'])
print(a['rollno'])
print(a.values())
print(a.keys())
print(a.keys()[0])
print(a.values()[0])
print(a.values()[1][2])
del a['name']
del a

s = "rama : krishna - 1909"
match=re.search(r'(\w+) : (\w+) - (\d+)',s)
print match.group(1)
print match.group(2)

print match.group(3)

#self is always replaced by instance object when the method is called.

print [6,7,3,4] + list({'a':1,'b':2}) + [8,9] #[6,7,3,4,'a','b',8,9]
print (1,2,3,4) + tuple({'a':1,'b':2}) + (8,9) #(1,2,3,4,'a','b',8,9)

List comprehension: Its used to construct list in a very easy and natural way.

Generator:
It is similar to a function that returns an array. However instead of building an array and returning them all at once, the generator yields value one at a time, which requires less memory.

There are generator functions and generator expressions:
Generator functions: def is used, yield to return results one at a time, suspending and resuming.

Generator expressions: similar to list comprehensions, but return an object instead of building a list.

Both does not return result list all at once, which saves memory.

Difference between function and generator is that generator yields a value, rather than returns a value.

To get next item in iterator we use __next__(),  and termination is done by Stopiteration exception.

fibonacci series using generator function:

def fib(n):
 count = 0
 a,b = 0,1
 while True:
  yield a
  a,b = b, a+b
  if count == n:
   break
  count += 1

   
for i in fib(10):
    print(i) --> 0, 1, 1, 2, 3, 5, 8, 13, 21, 34, 55

list(fib(5))
[0, 1, 1, 2, 3, 5]

Generator expression:
list(x**3 for x in range(1, 10, 2)) --> [1, 27, 125, 343, 729]

tuple(x**2 for x in range(1,10)) --> (1, 4, 9, 16, 25, 36, 49, 64, 81)

pylint and pychecker are also there. PEP8: Python Enchancement Proposals.

Pickle module: object serialization.
module that converts objects into string representation and dumps into a file using dump function is called pickling.
Retrieving original objects from stored strings is called unpickling.

import pickle
d = {1: 'a', 2: 'b'}
#For dumping the object into a file
with open('ram.txt', 'wb') as f:  --> compulsory in wb
     pickle.dump(d, f)

#For loading the object from the file
with open('ram.txt', 'rb') as f:
    var = pickle.load(f)

print var  --> {1: 'a', 2: 'b'}

#continue statement skip the remainder of the body and retest the condition
#pass statement do not execute the code.

febinoci using recursion
def feb(x):
    if x<=1:
     return x
    else:
     return(feb(x-1)+feb(x-2))  
x = raw_input("Enter the terms:")
x=int(x)
for i in range(x):
    print(feb(i))

def bin(x):
    if x>1:
        bin(x//2)   
    print(x % 2)
dec=raw_input("enter the number:")
dec=int(dec)
bin(dec)

Python speciality:
compulsory indentation in python.
strings, tuples are immuntable in python
""" triple quotes are present.

singleton class:
Class for which atmost only 1 instance can be created.

_this : Python does not have real private methods, so we use underline to indicate it is private and should not be accessed. They must not be accessed outside class.
__this : This is used to avoid overriding in case of python class. A class has __method, B class has __method, A is inherited by B. If we want to get __method of particular class, then use __ method.
__init__ : These are magic methods. Python calls these methods, we will not be able to call this. __init__(), __new__().

Use reduce function to find the maximum number from an integer list
l = [1,2,3,4,5]    
reduce(lambda x,y: x if x>y else y, l)

DOUBT:
def return_list(a = [1, 2, 3]):
    a.append(len(a)+1)
    return a

return_list([0]) --> [0, 2]
return_list() --> [1, 2, 3, 4]
return_list([1]) -->[1,2]
return_list() --> [1, 2, 3, 4, 5]

divmod(16,4) --> returns a tuple of quotient and reminder

Direct and Indirect calling:
def direct(x):
 print(x)

  
direct("This is direct call") -- >This is direct call
def indirect(fun, value):
 fun(value)

indirect(direct, "This is indirect call")  -->This is indirect call

list(sequence='abc') -> ['a', 'b', 'c']

'.' in regular expression matches everythong except new line.
matching new line as well we use re.DOTALL flag.

str.startswith() and endswith() suports tuple. like url.endswith(('.html', '.xml', '.css'))

PYTHON PROGRAMS:
import os
k=os.walk('.')
for i in k:
print k

OR

def parentdir(path):
 import os
 for child in os.listdir(path):
  childpath = os.path.join(path, child)
  if os.path.isdir(childpath):
   parentdir(childpath)
  else:
   print(childpath)

print 1 to 100 as string
''.join([`x` for x in range(101)])

'xyz'.join('1') -> '1'
'xyz'.join('ab') -> 'axyzb'
''.join(('a','b','c')) -> 'abc'
''.join([`x` for x in range(101)]) --> to get continuous 100 numbers in string.

Monkey patch: modifying the classes or modules is done at runtime so that third party code works as a workaround to a bug.

from somemodule import someclass

def speak(self):
print('speaking')

someclass.speak=speak

unicode('ram') --> u'ram'

Inheritance in python:
classes can derive attributes from other classes via inheritance
class DeriveClass(BaseClass):

If the base class is present in other module
class DeriveClass(module.BaseClass):

python supports multiple inheritance:
class DeriveClass(Baseclass1, Baseclass2,....):
If attribute is not found in DeriveClass then search in BaseClass1 and their parent then Baseclass2 and their parents.
Python avoids common base class from multiple paths by lineraly searching base classes in left to right order. 

copy, shallow copy and deepcopy:
Copy an object: To copy an object we can have copy.copy() or copy.deepcopy(). we cannot copy all the objects but most of them we can copy.
copy :
l = [1,2,3]
l2 =l
l2.pop() -->3
l2 --> [1, 2]
l -->  [1, 2]  -> Problem: copy and original will be modified.

shallow copy:
l = [1,2,3]
import copy
l3 = copy.copy(l)
l.pop() -->3
l --> [1, 2]
l3 --> [1, 2, 3] Fine

l = [[1,2,3], ['a', 'b', 'c']]
l4 = copy.copy(l)
l4[0].pop() --> 3
l4  --> [[1, 2], ['a', 'b', 'c']]
l --> [[1, 2], ['a', 'b', 'c']] #Problem again, original and copy are same.

Deep copy:
l = [[1,2,3], ['a', 'b', 'c']]
l5 = copy.deepcopy(l)
l5[0].pop() --> 3
l5  --> [[1, 2], ['a', 'b', 'c']]
l   --> [[1, 2, 3], ['a', 'b', 'c']] #Problem solved.


command line arguments:  len(sys.agrv)-> total command line arguments, sys.argv[1:]-> to do some operation on command lines, sys.argv[0]-> file name

import sys
try :
       total = sum(int(arg) for arg in sys.argv[1:])
       print('sum:', total)
except Exception as e:
       print(e)

       print('Enter integer values')

Generate random list: a = random.sample(range(100),7), a=[1, 63, 26, 8, 45, 12, 64] -> random list of 7 elements
Generate random int : a = random.randint(10,20), a=12

type() and isinstance() difference ?
class with area and perimeter for square, circle and rectangle using inheritance?

What is namespace ?
In python, every name created has a place in memory where it lives and can be hooked for.

Python uses call by object. In python everything is object. All variables hold references to objects.

we cannot change the value of reference but we can modify the object if it mutable.

There are 3 types of namespaces: 1) local namespace 2) global namespace 3) builtin namespace

locals() and globals() are builtin functions which provide dictionary based access to local and global variables.

locals(): returns dictionary. It is specific to function or class, if the function defines local variable x, then python will use this.
globals(): returns dictionary. It is specific to current module. If a module has variable, class, function, python will use this.
vars(): returns dictionary specific to current module or argument.

a = 1
b = 2
h = locals()
h ---> {'a': 1, 'b': 2, '__builtins__': <module '__builtin__' (built-in)>, 'h': {...}, '__package__': None, '__name__': '__main__', '__doc__': None}

If python does not find in any of these name spaces, then nameError exception is raised.

negative index in python: sequences can have index in positive and negative number. a[1] and a[-1]

sum of elements:
basic way:
sum = 0
for i in range(10) :
    sum += i

another way:
s = sum(range(10))

another way
from operator import add
reduce(add, range(0,10))

multiply:
basic way:
m = 1
for i in range(1,10) :
    s = i

another way
from operator import mul

reduce(mul, range(1,10))

import re;  statement imports all the names defined in module re.  
from statements can be used to import specific names from a module.
With from statement, names can be directly used. module name is not required.

email regular expression:
re.search(r"[0-9a-zA-Z.]+@[a-zA-Z]+\.(com|co\.in)$","micheal.pages@mp.com")

to get all the links in the page:
linkslist = re.findall('<a href=(.*?)>.*?</a>', htmlsource)

similar to readlines there is also writelines to write a sequence of lines at once.

Read the file and get only the integers:
with open('pickle.txt', 'rb') as f:
 i = f.readlines()
 for j in i:
  if re.search(r'^\d+', j):
      print re.search(r'^\d+', j).group()

Write a function that should take two integers as input, divide them and give the output without using an if statement. For cases such as divide by 0(zero), it should return 0

def method1(a, b):
 try:
     return a/b
 except:

  return 0

Write a function that does the following:
print_result(2, 3, multiply=5)
# Outputs (2+3)*5 => 25
print_result(2, 3, 4)
# Outputs (2+3+4) => 9

def p(*x, **y):
 sum1 = 0
 for i in x:
     sum1 = sum1 + i
 for j in y:
     sum1 = sum1*y[j]
 return sum1

Output for the following:
def return_list(a = [1, 2, 3]):
    a.append(len(a)+1)
    return a

return_list([0]) --> [0, 2]
return_list() --> [1, 2, 3, 4]
return_list([1]) -->[1,2]

return_list() --> [1, 2, 3, 4, 5]  --> This is important, as every time, value of a is saved.

Return only the numbers that are greater than 5 from the list:

n = [5,10,1,6,3,15]
filter(lambda x: x> 5, n)

[i for i in n if i >5 ]

n=1
print(n+=1) or print(n=n+1) # error, as assignment will not work.

s = 'aaa bbb ccc ddd eee'
import re
y = re.sub(r' ', '', s)
y  -->'aaabbbcccdddeee'  OR
filter(lambda x: x != ' ', s) 'aaabbbcccdddeee' OR
''.join(s.split())  'aaabbbcccdddeee'

'3\' --> Error.

left to right : order of precedence

variable name should not start with number : 1_str = 1 --> error
variable names can be of any length.

True, False, None keywords are capitalized while all others are lower case.

print 0.1 + 0.2 == 0.3 --> false, decimal values are not represented in memory. 

k = 2 + 3j, k = 2 + 3J, k = complex(2, 3) -> represents complex numbers.

~(x) = -(x+1),  eg : ~4 = -5

for i in rang(0):
    print i ---> nothing is printed.

for i not in x : ---> error, not is not allowed in for loops.

format function returns a string.
