# Lab-7_202001195

## IT314: Software Engineering
## Name: Vidhi Ahir
### Section A:
1) Consider a program for determining the previous date. Its input is triple of day, month and year with the
following ranges 1 <= month <= 12, 1 <= day <= 31, 1900 <= year <= 2015.The possible output dates would be
previous date or invalid date. Design the equivalence class test cases?

### Test Cases:

| Test Case Id  | Day | Month | Year | Expected Output (DD/MM/YY) |
|-|-|-|-|-|
|1|5|5|2010|4/5/2010|
|2|19|12|2002|18/12/2002|
|3|1|6|1999|31/5/1999|
|4|24|7|2013|23/7/2013|
|5|1|5|2005|30/4/2005|
|6|1|3|2009|28/2/2009|
|7|1|1|2001|31/12/2000|
|8|29|2|2003|Invalid Date|
|9|31|4|2008|Invalid Date|


### Equivalence Class Testing:

#### Input Classes:

Day
D1: Day between 1 to 28
D2: 29
D3: 30 
D4: 31

Month
M1: Month has 30 days
M2: Month has 31 days
M3: Month is February

Year
Y1: Year is a leap year
Y2: Year is a normal year 


#### Output Classes:

Decrement Day
Reset Day and Decrement Month
Decrement Year
Invalid Date

### Conditions for input classes to be valid:

Day:
| Partition ID | Range | Status |
|----------------------|-------|--------|
| E1 | Between 1 and 28 | Valid |
| E2 | Less than 1 | Invalid |
| E3 | Greater than 31 | Invalid |
| E4 | Equals 30 | Valid |
| E5 | Equals 29 | Valid for leap year |
| E6 | Equals 31 | Valid |

Month:
| Partition ID | Range | Status |
|----------------------|-------|--------|
| E7 | Between 1 and 12 | Valid |
| E8 | Less than 1 | Invalid |
| E9 | Greater than 12 | Invalid |

Year: 
| Partition ID | Range | Status |
|----------------------|-------|--------|
| E10 | Between 1900 and 2015 | Valid |
| E11 | Less than 1 | Invalid |
| E12 | Greater than 2015 | Invalid |
## Program 1
The function linearSearch searches for a value v in an array of integers a. <br>
If v appears in the array a, then the function returns the first index i, such that a[i] == v; otherwise, -1 is returned.<br>
int linearSearch(int v, int a[])<br>
{
int i = 0;<br>
while (i < a.length)<br>
{<br>
if (a[i] == v)<br>
return(i);<br>
i++;<br>
}<br>
return (-1);<br>
}
*Equivalence partition for linear search*
| Tester Action and Input Data | Expected Outcome |
|------------------------------|------------------|
| [2, 4, 6, 8, 10],v = 2 | 0 |
| [1, 3, 5, 7, 9],v = 2 | -1 |
| [2, 4, 6, 8, 10],v = 11 | -1 |
| [-100, 100] | 0 |
| [1,2,3,4,5,6],v = 6 | 5 |
| [],v = 10 | -1 |
| NULL,v = 111 | -1 |

*Boundary value analysis*
| Tester Action and Input Data | Expected Outcome |
|------------------------------|------------------|
| NULL | -1 |
| [],v = 5 | -1 |
| [5],v = 5 | 0 |
| [5],v = 60 | -1 |
| [3,5],v = 3 | 0 |
| [3,5],v = 5 | 1 |
| [3,5],v = 14 | -1 |
| [1,3,5],v = 1 | 0 |
| [1,3,5],v = 5 | 2 |
| [1,3,5],v = 10 | -1 |
|[1,2,3,4,5,6,7,8,9,1,0,11,111],v = 1| 0 |
|[1,2,3,4,5,6,7,8,9,1,0,11,111],v = 111| 12 |
|[1,2,3,4,5,6,7,8,9,1,0,11,111],v = 1111| -1 |

## Program 2
The function countItem returns the number of times a value v appears in an array of integers a.<br>
int countItem(int v, int a[])<br>

{<br>
int count = 0;<br>
for (int i = 0; i < a.length; i++)<br>
{<br>
if (a[i] == v)<br>
count++;<br>

}<br>
return (count);<br>
}

*Equivalence Class partitioning for counting occurance*
| Tester Action and Input Data | Expected Outcome |
|------------------------------|------------------|
| [265, 41, 60, 80, 100],v = 100 | 1 |
| [2655, 451, 6560, 1050, 1050],v = 1050 | 2 |
| [[265545, 451, 65460, 1050, 105024]],v = 1 | 0 |
| [[10,10,10,10]],v = 11 | 0 |
| [],v = 100 | 0 |
| NULL,v = 51 | 0 |
| [0],v = 0 | 1 |
| [-89,-89],v = -89 | 2 |

*Boundary value analysis*
| Tester Action and Input Data | Expected Outcome |
|------------------------------|------------------|
| [1, 2, 3, 4],v = 2 | 2 |
| 15, 10, 15, 15],v = 15 | 3 |
| [],v = 100 | 0 |
| NULL,v = 51 | 0 |
|[-100,100,100,100],v = 10000| 0 |
| [-89,89],v = -89 | 1 |
| [-890,890],v = 890 | 1 |

## Program 3
The function binarySearch searches for a value v in an ordered array of integers a. <br>
If v appears in the array a, then the function returns an index i, such that a[i] == v; otherwise, -1 is returned.<br>
Assumption: the elements in the array a are sorted in non-decreasing order.<br>
int binarySearch(int v, int a[])<br>
{<br>
int lo,mid,hi;<br>
lo = 0;<br>
hi = a.length-1;<br>
while (lo <= hi)<br>
{<br>
mid = (lo+hi)/2;<br>
if (v == a[mid])<br>
return (mid);<br>
else if (v < a[mid])<br>
hi = mid-1;<br>
else<br>
lo = mid+1;<br>
}<br>
return(-1);<br>
}

*Equivalent testcases for binary search:*
| Tester Action and Input Data | Expected Outcome |
|------------------------------|------------------|
| [1, 21, 30, 40, 50],v = 21 | 1 |
| [10, 20, 30, 40, 50, 60],v = 30 | 2 |
| [10,100,1000,10000],v = 100000 | -1 |
| [,11,22,33,44],v = 444 | -1 |
| [11,20,200,300],v=11 | 0 |
| [-100,-90,-80,100,1000],v = 10000 | 4 |
| [],v = 12 | -1 |
| NULL,v = 168 | -1 |
| [1,2],v = 3 | -1 |
| [1,3],v=3 | 1 |

*Boundary value analysis*
| Tester Action and Input Data | Expected Outcome |
|------------------------------|------------------|
| [1, 2, 3, 4, 5],v = 2 | 1 |
| [1, 2, 2, 351, 551],v = 2 | 2 |
| [1,22,33,44,55],v = 66 | -1 |
| [2, 4, 6, 8, 10],v = 51 | -1 |
| [-100, 0, 1000],v = -100 | 0 |
| [-100, 0, 1000],v = 1000 | 2 |
| [],v=0 | -1 |
| NULL,v = 4 | -1 |

## Program 4
 The following problem has been adapted from The Art of Software Testing, by G. Myers (1979). <br>
The function triangle takes three integer parameters that are interpreted as the lengths of the sides of a triangle. <br>
It returns whether the triangle is equilateral (three lengths equal), isosceles (two lengths equal), scalene (no lengths equal), or invalid (impossible lengths).<br>

final int EQUILATERAL = 0;<br>
final int ISOSCELES = 1;<br>
final int SCALENE = 2;<br>
final int INVALID = 3;<br>
int triangle(int a, int b, int c)<br>
{<br>
if (a >= b+c || b >= a+c || c >= a+b)<br>
return(INVALID);<br>
if (a == b && b == c)<br>
return(EQUILATERAL);<br>
if (a == b || a == c || b == c)<br>
return(ISOSCELES);<br>
return(SCALENE);<br>
}

*Equivalent class test cases of checking the type of triangle*
| Tester Action and Input Data | Expected Outcome |
|------------------------------|------------------|
| a=2,b=2,c=2 | EQUILATERAL |
| a=1,b=1,c=1 | EQUILATERAL |
| a=0,b=0,c=0 | INVALID |
| a=-1,b=-1,c=-1 | INVALID |
| a=10,b=10,c=0 | INVALID |
| a=17,b=17,c=5 | ISOCELES |
| a=15,b=2,c=15 | ISOCELES |
| a=6,b=11,c=5 | SCALENE |
| a=16,b=21,c=25 | SCALENE |
| a=-1,b=21,c=25 | INVALID |
| a=2,b=3,c=4 | SCALENE |

*Boundary value analysis*
| Tester Action and Input Data | Expected Outcome |
|------------------------------|------------------|
| a=2,b=2,c=2 | EQUILATERAL |
| a=0,b=0,c=0 | INVALID |
| a=INT_MAX,b = INT_MAX,c = INT_MAX | EQUILATERAL |
| a=INT_MIN,b=INT_MIN,c=INT_MIN | INVALID |
| a=1,b=1,c=2 | ISOCELES |
| a=15,b=12,c=15 | ISOCELES |
| a = INT_MAX,b = 1,c = INT_MAX | ISOCELES |
| a=1,b=2,c=3 | SCALENE |
| a = INT_MAX,b = 1,c = INT_MAX - 1 | SCALENE |

## Program 5
The function prefix (String s1, String s2) returns whether or not the string s1 is a prefix of string s2 (you may assume that neither s1 nor s2 is null).<br>
public static boolean prefix(String s1, String s2)<br>
{<br>
if (s1.length() > s2.length())<br>
{<br>
return false;<br>
}<br>
for (int i = 0; i < s1.length(); i++)<br>
{<br>
if (s1.charAt(i) != s2.charAt(i))<br>
{<br>
return false;<br>
}<br>
}<br>
return true;<br>
}
*Equivalent test cases for prefix searching are as follows:*
| Tester Action and Input Data | Expected Outcome |
|------------------------------|------------------|
| s1= "abcd",s2 = "abcd" | true |
| s1 = "",s2 = "" | true |
| s1 = "po",s2 = "poojan" | true |
| s1 = "poo",s2 = "po" | false |
| s1 = "abc",s2 = "" | false |
| s1 = "",s2 = "abc" | true |
| s1 = "o",s2 = "ott" | true |
| s1 = "abc",s2 = "def" | false |
| s1 = "deg",s2 = "def" | false |

*Boundary value analysis*
| Tester Action and Input Data | Expected Outcome |
|------------------------------|------------------|
| s1= "abcd",s2 = "abcd" | true |
| s1= "",s2 = "" | true |
| s1= "abcd",s2 = "" | false |
| s1= "",s2 = "abcd" | true |
| s1 = "aef",s2 = "def" | false |
| s1 = "def",s2 = "deg" | false |
| s1 = "a",s2 = "att" | true |
| s1 = "poojan",s2 = "patel" | false |

## Program 6
Consider again the triangle classification program (P4) with a slightly different specification: <br>
The program reads floating values from the standard input. The three values A, B, and C are interpreted as representing the lengths of the sides of a triangle. <br>
The program then prints a message to the standard output that states whether the triangle, if it can be formed, is scalene, isosceles, equilateral, or right angled.<br>
Determine the following for the above program:<br>
<br>
*(a) All equivalent classes*
| Class ID | Class |
|----------|-------|
| E1 | All sides are positive |
| E2 | two of its sides are zero |
| E3 | One of its sides are negative |
| E4 | Sum of two sides is less than third side |
| E5 | Any of the side/sides is negative |

*(b) Identify test cases to cover the identified equivalence classes. Also, explicitly mention which test case would cover which equivalence class.*
| Test Case ID | Class ID | Test Case |
|--------------|----------|-----------|
| T1 | E1 | A = 1,B = 1,C = 1 |
| T2 | E1 | A = 3, B = 4, C= 5 |
| T3 | E2 | A = 0,B = 0,C = 1 |
| T4 | E3 | A = 0,B = 1,C = 2 |
| T5 | E4 | A = 1, B = 3, C = 8 |
| T6 | E5 | A = -1,C = 1,D = 5 |

*(c) For the boundary condition A + B > C case (scalene triangle), identify test cases to verify the boundary.* <br/>
A = 1, B = 3, C = 2
*(d) For the boundary condition A = C case (isosceles triangle), identify test cases to verify the boundary.* <br/>
A = 3,B = 2, C = 3
*(e) For the boundary condition A = B = C case (equilateral triangle), identify test cases to verify the boundary.*<br/>
A = 30,B = 30,C = 30
*(f) For the boundary condition A2 + B2 = C2 case (right-angle triangle), identify test cases to verify the boundary.* <br/>
A = 6,B = 8,C = 10
*(g)  For the non-triangle case, identify test cases to explore the boundary.*
A = 20, B = 10,C = 5
*(h) For non-positive input, identify test points.*
A = 0, B = 10, C = 0 <br/>
A = 0,B = 0,C = 0 <br/>
A = 0, B = -1, C = 10<br/>

### Section B:

#### 1. Convert the Java code comprising the beginning of the doGraham method into a control flow graph (CFG).

**i. Below is the control flow graph of converted Java code**<br>

![control-flow-diagram drawio](https://user-images.githubusercontent.com/84441910/231426230-4f73e587-ef87-4d39-83df-3722a17df30d.png)

#### 2. Test sets

Statement coverage test sets: To achieve statement coverage, we need to make sure that every statement in the code is executed at least once.<br>
Test 1: p = empty vector<br>
Test 2: p = vector with one point<br>
Test 3: p = vector with two points with the same y component<br>
Test 4: p = vector with two points with different y components<br>
Test 5: p = vector with three or more points with different y components<br>
Test 6: p = vector with three or more points with the same y component<br>


Branch coverage test sets: To achieve branch coverage, we need to make sure that every possible branch in the code is taken at least once<br>
Test 1: p = empty vector<br>
Test 2: p = vector with one point<br>
Test 3: p = vector with two points with the same y component<br>
Test 4: p = vector with two points with different y components<br>
Test 5: p = vector with three or more points with different y components, and none of them have the same x component<br>
Test 6: p = vector with three or more points with the same y component, and some of them have the same x component<br>
Test 7: p = vector with three or more points with the same y component, and all of them have the same x component<br>


Basic condition coverage test sets: To achieve basic condition coverage, we need to make sure that every basic condition in the code (i.e., every Boolean subexpression) is evaluated as both true and false at least once<br>
Test 1: p = empty vector<br>
Test 2: p = vector with one point<br>
Test 3: p = vector with two points with the same y component, and the first point has a smaller x component<br>
Test 4: p = vector with two points with the same y component, and the second point has a smaller x component<br>
Test 5: p = vector with two points with different y components<br>
Test 6: p = vector with three or more points with different y components, and none of them have the same x component<br>
Test 7: p = vector with three or more points with the same y component, and some of them have the same x component<br>
Test 8: p = vector with three or more points with the same y component, and all of them have the same x component.<br>
