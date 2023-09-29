# ASSIGNMENT 

# TASK 1 CALCULATE AREA WITH CONDITIONS 


```python
def Calculate_area(l,w):
    if l==w:
        return "This is a square!"
    else:
        return l*w
def Input_values():
    length=int(input("Enter the length :"))
    width=int(input("Enter the width :"))
    return Calculate_area(length,width)
    
```


```python
Input_values()
```

    Enter the length :2
    Enter the width :4
    




    8



# TASK 2 FIBONNACI SERIES 

Problem Statement:
Write a Python program that generates the Fibonacci sequence up to a specified number of 
terms, n. The Fibonacci sequence starts with 0 and 1, and each subsequent number in the 
sequence is the sum of the two preceding numbers (e.g., 0, 1, 1, 2, 3, 5, 8, ...). Prompt the 
user to enter the number of terms (n) they want in the sequence and then display the 
Fibonacci sequence up to that number of terms


```python
def fab_print_series(n):
    a=0
    b=1
    print(a,b,end=" ")
    for i in range(3,n+1):
        c=a+b
        print(c,end=" ")
        a=b
        b=c
    
        
```


```python
n=int(input("Enter the Number till to print the fibonacci :"))
fab_print_series(n)
```

    Enter the Number till to print the fibonacci :10
    0 1 1 2 3 5 8 13 21 34 


```python
# time complexity is O(2**n) and space complexity O(n) 
# Method 1 Recursive approach with the output(1,1,2,3,5,8,........)
def fab(n):
    if n==0 or n==1:
        return n
    return fab(n-1)+fab(n-2)
```


```python
# Time complexity is O(n) and space complexity O(n) 
# Method 2 Recursion with Dynamic Programming approach 
def fab_rec_dp(n,dp):
    if n==0 or n==1:
        return n 
    if dp[n-1]==-1:
        ans1=fab_rec_dp(n-1,dp)
        dp[n-1]=ans1
    else:
        ans1=dp[n-1]
    if dp[n-2]==-1:
        ans2=fab_rec_dp(n-2,dp)
        dp[n-2]=ans2
    else:
        ans2=dp[n-2]
    return ans1+ans2
    
```


```python
# Time complexity is O(n) and space complexity O(n) (And there is no point of oversatck flow as in the reccursive approach may be)
# Method 3 Dynamic Programming  with itterative approach 
def fab_dp_itr(n):
    dp[0]=0
    dp[1]=1
    for i in range(2,n+1):
        dp[i]=dp[i-1]+dp[i-2]
    return dp[n]

```

# BEST SOLUTION TC=O(N) AND SC=O(1)


```python
# Time complexity is O(n) and space complexity O(1)
# Best solution
def fab_best(n):
    a=0
    b=1
    c=a+b
    for i in range(3,n+1):
        a=b
        b=c
        c=a+b
    return c
```


```python
n=int(input("Enter the number to get the n fibo no : 1 1 2 3 ........"))
dp=[-1]*(n+1)
print(fab_best(n))
print(fab_rec_dp(n,dp))
print(fab_dp_itr(n))
print(fab(n))
```

    Enter the number to get the n fibo no : 1 1 2 3 ........6
    8
    8
    8
    8
    

# TASK 3 MySQL Database Operations with Python

Your task is to write a Python program that accomplishes the following:
First create a database , table and add these column ‘student_id’, ‘first_name’, ‘last_name’,
‘age’, ‘grade’.
Connects to your MySQL database with python.
Inserts a new student record into the "students" table with the following details:
First Name: "Alice"
Last Name: "Smith"
Age: 18
Grade: 95.5
Updates the grade of the student with the first name "Alice" to 97.0.
Deletes the student with the last name "Smith."
Fetches and displays all student records from the "students" table

# CREATING THE TABLE  AND CONNECTING WITH THE DATABASE DB1


```python
import mysql.connector
mydb=mysql.connector.connect(host="localhost",port="3306",user="root",password="admin")
cur=mydb.Cursor()
#CREATING DATABASE AS DB1
cur.execute("CREATE DATABASE db1")
```


```python
mydb=mysql.connector.connect(host="localhost",user="root",password="root",database="db1")
cur=mydb.Cursor()
s="CREATE TABLE students(student_id int(4), first_name varchar(20), last_name varchar(20), age int(4), grade float(5,2))"
cur.execute(s)
```

# INSERTING A NEW STUDENT RECORD


```python
cur=mydb.Cursor()
s="INSERT INTO students(student_id,first_name,last_name,age,grade) VALUES (1,'Alice','Smith',18,95.5)"
cur.execute(s)
mybd.commit()
```

# UPDATING


```python
cur=mydb.Cursor()
s="UPDATE students SET grade=97.0 WHERE first_name='Alice'"
cur.execute(s)
mydb.commit()
```

# DELETING 


```python
cur=mydb.Cursor()
s="DELETE from students WHERE last_name='Smith'"
cur.execute=(s)
mydb.commit()
```

# FETCHING AND DISPLAYING THE TABLE 


```python
s="SELECT * from students"
cur.execute(s)
data=cur.fetchall()
for d in data:
    print(d)
```
