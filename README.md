class Man(object):
    def __init__(self, name, age):
        self.name = name
        self.age = age 
        print(' Man __init__ ')

    def __del__(self):
        print(' Man __del__ ')

    def __str__(self):
        return '{}님은 {}살'.format(self.name, self.age)

    def __eq__(self, other):
        if self.name == other.name  and self.age == other.age:
            return True
        else:
            return False

    def __add__(self, num):
        self.age = self.age + num 

    def __sub__(self, num):
        self.age -= num 
        
    def disp_Man(self):
        print('{}님은 {}살'.format(self.name, self.age))

    def get_name(self):
        return self.name

    def get_age(self):
        return self.age
    
    def set_name(self, name):
        self.name = name

    def set_age(self, age):
        self.age = age

m1 = Man('손흥민', 30)
m2 = Man('이강인', 21)
m3 = Man('손흥민', 30)

print(m1)
print(m2)
# print(m1.__str__())
# print(m2.__str__())
print(m1 == m3)
m1 + 2 
m2 - 4
m1.disp_Man()
m2.disp_Man()
class Man(object):
    cnt = 0

    @staticmethod  # 장식자
    def get_cnt1():
        return Man.cnt 

    @classmethod
    def get_cnt2(cls):
        return Man.cnt        

    def __init__(self, name, age):
        self.name = name
        self.age = age 
        Man.cnt += 1
        print(' Man __init__ ')

    def __del__(self):
        Man.cnt -= 1
        print(' Man __del__ ')

    def __str__(self):
        return '{}님은 {}살'.format(self.name, self.age)

    def __eq__(self, other):
        if self.name == other.name  and self.age == other.age:
            return True
        else:
            return False

    def __add__(self, num):
        self.age = self.age + num 
        #self.age += num 
    def __sub__(self, num):
        self.age -= num 
        
    def disp_Man(self):
        print('{}님은 {}살'.format(self.name, self.age))

    def get_name(self):
        return self.name

    def get_age(self):
        return self.age
    
    def set_name(self, name):
        self.name = name

    def set_age(self, age):
        self.age = age

print('현재 객체생성수는 : {}'.format(Man.cnt))
print('현재 객체생성수는 : {}'.format(Man.get_cnt1()))

m1 = Man('손흥민', 30)
m2 = Man('이강인', 21)
m3 = Man('손흥민', 30)

print('현재 객체생성수는 : {}'.format(Man.cnt))
print('현재 객체생성수는 : {}'.format(m1.get_cnt2()))

print(m1)
print(m2)
# print(m1.__str__())
# print(m2.__str__())
print(m1 == m3)
m1 + 2 
m2 - 4
m1.disp_Man()
m2.disp_Man()
CUR_YEAR = 2021  ## 전역변수 

class Date(object):
    def __init__(self, year, month):
        self.year = year
        self.month = month    
        print('Date __init__ ')
  
    def disp_Date(self):
        print('{}년{}월'.format(self.year, self.month))

    def __del__(self):
        print('Date __del__ ')

    def disp_Date(self):
        print('{}년{}월'.format(self.year, self.month))

    def __del__(self):
        print('Date __del__ ')


class Man(Date):  ## Date class를 상속 받는다.
    cnt = 0 ## class변수 

    @staticmethod  # 장식자
    def get_cnt1():
        return Man.cnt 

    @classmethod
    def get_cnt2(cls):
        return Man.cnt        

    ## 객체 생성시 자동 호출(constructor)되는 함수, 생성자
    def __init__(self, name, year, month):
        super().__init__(year, month)
        self.name = name       
        Man.cnt += 1
        self.age = CUR_YEAR - year + 1
     

    ## 객체 소멸시 자동 호출(destructor)되는 함수, 소멸자
    def __del__(self):
        Man.cnt -= 1
        super().__del__()
        print(' Man __del__ ')

    ## 객체 출력시 자동으로 호출되는 함수, 기본값은 객체의 id값 리턴 
    def __str__(self):
        return '{}님은 {}살'.format(self.name, self.age)        

    def disp_Man(self):
        print('{}님은 {}살'.format(self.name, self.age))
        ## Date.disp_Date(self) ## Date class의 메서드 호출 
        super().disp_Date() ## Date class의 메서드 호출 
       
    
m1 = Man('손흥민', 1992, 7)
m2 = Man('이강인', 2001, 2)

m1.disp_Man()
>>> y = 20
>>> import  sys
>>> sys.getsizeof(y)
28
>>> a = [i for i in range(1, 11)]
>>> sys.getsizeof(a)
184
>>> a = [i for i in range(1, 101)]
>>> sys.getsizeof(a)
920
>>> a = [i for i in range(1, 1001)]
>>> sys.getsizeof(a)
8856
>>> b = (i for i in range(1, 11))
>>> sys.getsizeof(b)
112
>>> b = (i for i in range(1, 101))
>>> sys.getsizeof(b)
112
>>> b = (i for i in range(1, 1001))
>>> sys.getsizeof(b)

>>> sys.getsizeof(a)
8856
>>> a = [i for i in range(1, 101, 2)]
>>> len(a)
50
>>> sys.getsizeof(a)
472
>>> a2 = iter(a)
>>> sys.getsizeof(a)
472
>>> sys.getsizeof(a2)
48
>>> len(a2)
Traceback (most recent call last):
  File "<pyshell#117>", line 1, in <module>
    len(a2)
TypeError: object of type 'list_iterator' has no len()
>>> type(a2)
<class 'list_iterator'>
>>> a[3]
7
>>> a2[3]
Traceback (most recent call last):
  File "<pyshell#120>", line 1, in <module>
    a2[3]
TypeError: 'list_iterator' object is not subscriptable
>>> a2.__next__()
1
>>> next(a2)
3
>>> next(a2)
5
