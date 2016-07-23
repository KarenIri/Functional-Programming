# Functional-Programming
Higher-order function; map/reduce; filter; sorted; Return Function; lambda; Decorator; Partial function
#函数式编程

变量指向函数
>>> x = abs()
>>> x(-10)
10

函数名是变量
>>> abs(-10)
10

#高阶函数
变量可指向函数，函数的参数可为变量，则一个函数可接受另一个函数作为参数，即高阶函数
def add(x, y, f):
	return f(x) + f(y)
add(-5, 6, abs)
11




# map/reduce

# map
map(f, [1, 2, 3, 4, 5, 6, 7, 8, 9]):两个参数，一个是函数，一个是序列
map将传入的函数依次作用到序列的每个元素，并把结果作为新的list返回。
map(str, [1, 2, 3, 4, 5, 6, 7, 8, 9])
['1', '2', '3', '4', '5', '6', '7', '8', '9']

# reduce
必须有2个参数，把结果继续和序列的下一个元素做累积计算
reduce(f, [x1, x2, x3, x4]) = f(f(f(x1, x2), x3), x4) 
def add(x, y):
	return x + y
reduce(add, [1, 3, 5, 7, 9])

把'13579'变成13579
def fn(x, y):
	return x * 10 + y
def char2num(s):
	return {'0': 0, '1': 1, '2': 2, '3': 3, '4': 4, '5': 5, '6': 6, '7': 7, '8': 8, '9': 9}[s]
reduce(fn, map(char2num, '13579'))
13579
char2num作用：通过定义dict，把字符变成整数



['adam', 'LISA', 'barT']
['Adam', 'Lisa', 'Bart']

def change(s):


Python提供的sum()函数可以接受一个list并求和，
请编写一个prod()函数，可以接受一个list并利用reduce()求积。
def multi(x, y):
	return x * y
def prod():
	return reduce(multi, [1, 3, 5, 7, 9])




# fileter
filter用于过滤序列，2个参数：函数+序列 。
filter()把传入的函数依次作用于每个元素，然后根据返回值是True还是False决定保留还是丢弃该元素。             
def is_odd(n):
	return n % 2 == 1
filter(is_odd, [1, 2, 3, 4, 5, 6, 7, 8, 9])

def not_empty(n):
	return n and n.strip()
filter(not_empty, ['A', '', 'B', None, 'C', '  '])
['A', 'B', 'C']

>>> 'www.example.com'.strip('cmowz.')
'example'
>>> '   spacious   '.strip()
'spacious'
strip():删除括号中出现的字符，若为空括号，则删除字符串中空格

def zhis(a):
	for x in range(2:a):
		if a % x ==0:
			return 1
		else:
			return 0
filter(zhis, range(1:101))
