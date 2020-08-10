Help on class Qualean in module builtins:

class Qualean(object)
=========================
The Qualean class that is inspired by Boolean+Quantum concepts. 
We can assign it only 3 possible real states. True, False, and Maybe (1, 0, -1) but it internally picks an imaginary state. 
The moment you assign it a real number, it immediately finds an imaginary number random.uniform(-1, 1) and 
multiplies with it and stores that number internally after using Bankers rounding to 10th decimal place. 
It implements these functions (with exactly the same names)
__and__,  __or__, __repr__, __str__, __add__, __eq__, __float__, __ge__, __gt__, __invertsign__, __le__, __lt__, __mul__, __sqrt__, __bool__


#and 
----

Checks first value is false then it does not check the second one and returns false
        def  __and__(self, value):
            return self._real if not bool(self._real) else value._real
    
# or
------  
Checks the first value is True then it does not check the second one and returns True
       
    def __or__(self,value):
        return self._real if bool(self._real) else value._real
    
#repr
-------

returns instance of class
    def __repr__(self):
        return f'Value of the Qualean object is : {self.real}'
#str
------
returns string value of object
   
    def __str__(self):
        return f'Qualean object value is : {self.real}'
#add
-------
takes real part of the numbers and adds two objects

    def __add__(self,other):
        return Qualean(other._real + self._real,1)
    
#eq
-------
checks quality of two two numbers 
   
    def __eq__(self,other):
        return (self.__class__ == other.__class__) and (self._real == other._real)
    
    
#float
--------

returns the float value of the given object

    def __float__(self):
        return float(self._real)
#ge
-----
returns if the numbers are either greater than or equal to each other 
    
    def __ge__(self,other):
        return (self.__class__ == other.__class__) and (self.real >= other.real)
#gt
------
returns if the numbers are either greater than or not
 
    def __gt__(self,other):
        return (self.__class__ == other.__class__) and (self.real > other.real)
    
#le
-----
returns if the numbers are either less than or equal to each other 
    def __le__(self,other):
        return (self.__class__ == other.__class__) and (self._real <= other._real)
 
 # lt
------
returns if the numbers are either less than or not
    
    def __lt__(self,other):
        return (self.__class__ == other.__class__) and (self._real < other._real)
    
#mul
-----
 multiplies two objects and returns the result

    def __mul__(self,other):
        return Qualean(other._real * self._real,1)
 
#bool
-------
Provides the bool value. It returns true for everything except 0
 
    def __bool__(self):
        return self.real != 0
 
 # invertsign
 ----------------
 
 It just alters the sign of the real part of the object negative to positive vice varse
 
    def __invertsign__(self):
        return (-1) * self.real

# sqrt
--------

It returns the square root of the given imaginary number 

    def __sqrt__(self):
        if self.real >=0:
            return math.sqrt(self.real)
        else:
            return cmath.sqrt(self.real)
        
        
