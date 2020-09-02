# PythonNote
notes， questions and others

功能：字符串转浮点
源代码段：

from functools import reduce

CHAR_TO_FLOAT = {
    '0': 0,
    '1': 1,
    '2': 2,
    '3': 3,
    '4': 4,
    '5': 5,
    '6': 6,
    '7': 7,
    '8': 8,
    '9': 9,
    '.': -1
}

def str2float(s):


    nums = map(lambda ch: CHAR_TO_FLOAT[ch], s)
    point = 0

    
    def to_float(f, n):

        
        

        nonlocal point
        if n == -1:
            point = 1
            return f
        if point == 0:
            return f * 10 + n
        else:
            point = point * 10
            return f + n / point
    return reduce(to_float, nums, 0.0)

print(str2float('0'))
print(str2float('123.456'))
print(str2float('123.45600'))
print(str2float('0.1234'))
print(str2float('.1234'))
print(str2float('120.0034'))

问题1：f n 的值怎么来的？

https://github.com/muiz-lee/PythonNote/blob/master/Image%201.png

问题2：以下代码哪里不对？

from functools import reduce

DIGITS = {'0':0,'1':1, '2':2,'3':3,'4':4,'5':5,'6':6,'7':7,'8':8,'9':9 }

def str2float(s):

	def char2num(s):
		return DIGITS[s]

	def char2float(s):
		x = list(s).index('.')
		print("hello")
		print(x)
		return reduce(lambda x,y:10*x+y,map(char2num,s[:x]))+reduce(lambda x,y:0.1*x+0.01*y,map(char2num,s[x+1:]))

print('str2float(\'123.456\') =', str2float('123.456'))
