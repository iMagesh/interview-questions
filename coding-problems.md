## Coding problems for training purpose

---

### Find the matching Brackets

Solution:

```ruby
class Brackets
  def self.paired?(s)
    stack = []
    brackets = { '{' => '}', '[' => ']', '(' => ')' }

    s.each_char do |char|
      if brackets.key?(char)
        stack.push(char)
      elsif brackets.values.include?(char)
        return false if brackets.key(char) != stack.pop
      end
    end
    stack.empty?
  end
end


Brackets.paired?("[ ] } ]") # => false
Brackets.paired?("[ ]") # => true
Brackets.paired?("[  ") # => false
Brackets.paired?("[ (] {}") # => false
Brackets.paired?("[ ( ) ") # => false
Brackets.paired?("[ ( text { ) } ]") # => false
Brackets.paired?("[ ( text ) {} ]") # => true
```

### User input string contain 5 occurrence of a replace it with '%' sign

Example: aaaaasdddsdsfgfd
Output: %%%%%sdddsdsfgfd

### Create 5 methods: add, subtract, multiply, divide and reminder pass 2 integer value and calculate add, subtract, multiply, divide and reminder

add(4,5) => 9
subtract(5,4) => 1

### Pattern print

```
*****
****
***
**
*
**
***
****
*****
```

### From 1 to 100 print no which are divisible by 3 or 5

### From 11 to 99 multiply all no to 11..99 range and print if no is palindrome

1991 = reverse 1991 palindrome no

### Print product of 1 to 55 no

### Search element in an array

a = [1,4,8,9,0]
elementSearch = 0
Output: 4 is an index of 0 element
elementSearch: 10
Output: Element not found

### Find unique element length of array

[2,3,4,5,6,3,4,5]
Output: 2 because 2,6 are unique element

### Array will have string sort array be length of string

["Hi","a","Hello","How"]
Output: ["a","Hi","How","Hello"]

### Find minimum difference between any two elements

Input : {1, 5, 3, 19, 18, 25};
Output : 1
Minimum difference is between 18 and 19
Minimum delete operations to make all elements of array same
Given an array of n elements such that elements may repeat. We can delete any number of elements from the array. The task is to find the minimum number of elements to be deleted from the array to make it equal.

Examples:

Input : arr[] = {4, 3, 4, 4, 2, 4}
Output : 2
After deleting 2 and 3 from array, array becomes
arr[] = {4, 4, 4, 4}

### Count maximum points on same line

Given a N point on a 2D plane as a pair of (x, y) co-ordinates, we need to find the maximum number of points which lie on the same line.

Examples:

Input : points[] = {-1, 1}, {0, 0}, {1, 1},
{2, 2}, {3, 3}, {3, 4}
Output : 4
Then maximum number of point which lie on same
line are 4, those point are {0, 0}, {1, 1}, {2, 2},
{3, 3}

### Find top three repeated in array

Given an array of size N with repeated numbers, You Have to Find the top three repeated numbers.
Note : If Number comes same number of times then our output is one who comes first in array
Examples:

Input : arr[] = {3, 4, 2, 3, 16, 3, 15, 16, 15, 15, 16, 2, 3}
Output : Three largest elements are 3 16 15
Explanation :Here, 3 comes 4 times, 16 comes 3 times, 15 comes 3 times.

### Find the smallest positive number missing from an unsorted array | Set 1

You are given an unsorted array with both positive and negative elements. You have to find the smallest positive number missing from the array

Input: {2, 3, 7, 6, 8, -1, -10, 15}
Output: 1

### Count all distinct pairs with difference equal to k

Given an integer array and a positive integer k, count all distinct pairs with difference equal to k.
Examples:

Input: arr[] = {1, 5, 3, 4, 2}, k = 3
Output: 2
There are 2 pairs with difference 3, the pairs are {1, 4} and {5, 2}

Input: arr[] = {8, 12, 16, 4, 0, 20}, k = 4
Output: 5
There are 5 pairs with difference 4, the pairs are {0, 4}, {4, 8},
{8, 12}, {12, 16} and {16, 20}

Count equal pairs from given string arrays
Given two string arrays s1[] and s2[]. The task is to find the count of pairs (s1[i], s2[j]) such that s1[i] = s2[j]. Note that an element s1[i] can only participate in a single pair.

Examples:

Input: s1[] = {“abc”, “def”}, s2[] = {“abc”, “abc”}
Output: 1
Only valid pair is (s1[0], s2[0]) or (s1[0], s2[1])
Note that even though “abc” appears twice in the
array s2[] but it can only make a single pair
as “abc” only appears once in the array s1[]

### Create class Student

Define below attributes:
name,age,m1,m2,m3
Create method:
print_details: print details of object
avg: calculate avg of m1,m2,m3
total: calculate total
no_of_students: calculate no of students
User input name, age, m1,m2,m3

### Class Math

Methods:
add
multiply
division
subtraction
power: 2*3 => 8
modulo: 3%2 => 1
convert_to_binary: input => 6 => 110
convert_binary_to_num: input => 110 => 6
Class Math
Methods:
add
multiply
division
subtraction
power: 2*3 => 8
modulo: 3%2 => 1
convert_to_binary: input => 6 => 110
convert_binary_to_num: input => 110 => 6

### Create class Shape and create child classes as Circle, Rectangle, Square,Triangle and create method in child class to define area

### Find the diagonal difference of a matrix

11 2 4
4 5 6
10 8 -12

11+5+(-12) = 4
4+5+10=19

Difference: 19-4 = 15

### Perform left rotation on array:

Input:
Left rotation = 2
Array: [1,2,3,4,5]
Output: [3,4,5,1,2]

### Write the code to implement the concept of inheritance forVehicles. You are required to implement inheritance between classes. You have to write four classes in java i.e. one superclass, two sub classes and one driver class.

Vehicle is the super class whereas Bus and Truck are sub of Vehicle class.
Transport is a driver class which contains the main method.

Detailed description:

Detailed description of Vehicle (Super class):

The class Vehicle must have following attributes:
Vehicle model
Registration number
Vehicle speed (km/hour)
Fuel capacity (liters)
Fuel consumption (kilometers/liter)

The Vehicle class must have following methods:

- Parameterized constructor that will initialize all the data members with the given values.
- Getters and Setters for each data member that will get and set the values of data members of class.
- A method fuelNeeded() that will take distance (in kilometer) as an argument.It will calculate the amount of fuel needed for the given distance and will return the value of fuel needed for a given distance. You Can use the attributes ‘Fuel consumption defined within the above Vehicle class to determine the fuel needed for the given distance. You are required to implement this functionality by yourself.

- A method distanceCovered() that will take time (in hours) as an argument. It Will calculate the distance for the given time and speed and returns the value of distance. The formula to calculate speed is given as speed = distance/time. You can use this formula to calculate the distance.
- A display() method that will display all the information of a vehicle.

Detailed description of Truck (Sub class):

The class Truck must have following attributes:

Cargo weight limit (Kilograms)
The above class must have the following methods:

- Parameterized constructor that will initialize all data members with the given values.
- Getters and setters for each data member that will get and set the values of data members of class.
- It must also override the display()method of Vehicle class and must call display() method of superclass within overridden method.

Detailed description of Bus (Sub class):

The class Bus must have following attributes:

No of passengers
The above class must have the following methods:

- Parameterized constructor that will initialize all the data members with given values.
- Getters and setters that will get and set the value of each data member of the class.
- It must also override the display()method of Vehicle class and must call display method of super class within overridden method.

Create a class Transport which contains the main method. Perform the following within main method:

- Create an instance of class Truck and initialize all the data members with proper values.
