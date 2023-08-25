# Fix my code


Fix my code is a new type of project, where we’ll jump into an existing code base and fix it!


# FizzBuzz


**Initial**

$ ./0-fizzbuzz.py 50
1 2 Fizz 4 Buzz Fizz 7 8 Fizz Buzz 11 Fizz 13 14 Fizz 16 17 Fizz 19 Buzz Fizz 22 23 Fizz Buzz 26 Fizz 28 29 Fizz 31 32 Fizz 34 Buzz Fizz 37 38 Fizz Buzz 41 Fizz 43 44 Fizz 46 47 Fizz 49 Buzz
$

**Problem**


The condition (i % 3) == 0 that checks for "Fizz" is placed before the combined condition (i % 3) == 0 and (i % 5) == 0 that checks for "FizzBuzz." As a result, any number that is divisible by both 3 and 5 will first match the (i % 3) == 0 condition and be labeled as "Fizz," causing "FizzBuzz" numbers like 15 to be displayed as "Fizz."


**fixed**


─$ ./0-fizzbuzz.py 50
1 2 Fizz 4 Buzz Fizz 7 8 Fizz Buzz 11 Fizz 13 14 FizzBuzz 16 17 Fizz 19 Buzz Fizz 22 23 Fizz Buzz 26 Fizz 28 29 FizzBuzz 31 32 Fizz 34 Buzz Fizz 37 38 Fizz Buzz 41 Fizz 43 44 FizzBuzz 46 47 Fizz 49 Buzz


**solution**


In this corrected version, the combined condition (i % 3) == 0 and (i % 5) == 0 is checked first for "FizzBuzz," followed by (i % 3) == 0 for "Fizz," and finally (i % 5) == 0 for "Buzz." This ensures that numbers divisible by both 3 and 5 will correctly result in "FizzBuzz."


# Print Square


**initial**


$ ./1-print_square.js 10
################
################
################
################
################
################
################
################
################
################
################
################
################
################
################
################
$


There's an issue in your code related to parsing the size argument. You're using parseInt(process.argv[2], 16) to parse the size, which is not correct for your use case. You should use parseInt(process.argv[2]) instead.


**fixed**


└─$ ./1-print_square.js 10
##########
##########
##########
##########
##########
##########
##########
##########
##########
##########


**solution**


I've replaced parseInt(process.argv[2], 16) with parseInt(process.argv[2]) to correctly parse the size argument as a decimal number. With this correction, the code should now generate the expected square output for different sizes.


# sort


**initial**


$ ruby 2-sort.rb 12 41 2 C 9 -9 31 fun -1 32
31
32
12
41
2
9
-9
-1
$


**problem**


In the loop where you're trying to insert the sorted integer into the result array, you are checking if result[i] < i_arg to determine the correct position.

**fixed**


─$  ruby 2-sort.rb 12 41 2 C 9 -9 31 fun -1 32
-9
-1
2
9
12
31
32
41


**solution**


This condition should be the opposite (if result[i] > i_arg) for ascending sorting.


# User


**initial**


$./3-user.py    
Test User
is_valid_password should return True if it's the right password


**problem**


The issue lies in the password setter method. You are using an incorrect attribute name (self._password) when assigning the hashed password value. Also, you need to convert the hashed password to lowercase for comparison in the is_valid_password method.


**fixed**


─$ ./3-user.py       
Test User
         

**solution**


Change 'self._password' to 'self.__password' and Also, you need to convert the hashed password to lowercase for comparison in the is_valid_password method.


# delete_dnodeint

**initial**

$ ./delete_dnodeint 
0
1
2
3
4
98
402
1024
-----------------
0
1
2
3
4
0
402
1024
-----------------
1
2
3
4
0
402
1024
-----------------
2
3
4
0
402
1024
-----------------
3
4
0
402
1024
-----------------
4
0
402
1024
-----------------
0
402
1024
-----------------
402
1024
-----------------
-----------------
-----------------
-----------------
-----------------
-----------------
-----------------
-----------------
-----------------
-----------------


**problem**


it seems that there is an issue with updating the prev pointers of the nodes when deleting a node from a doubly linked list.

`(*head)->prev->prev = (*head)->prev;`


This line seems incorrect, as it's assigning the prev pointer of the node before the one being deleted to the prev pointer of the node being deleted. This can break the consistency of the linked list structure.


**fixed**


0
1
2
3
4
98
402
1024
-----------------
0
1
2
3
4
402
1024
-----------------
1
2
3
4
402
1024
-----------------
2
3
4
402
1024
-----------------
3
4
402
1024
-----------------
4
402
1024
-----------------
402
1024
-----------------
1024
-----------------
-----------------
-----------------
-----------------
-----------------
-----------------
-----------------
-----------------
-----------------
-----------------
                                                                        

**solution**


Instead, when deleting a node in a doubly linked list, you should update the next and prev pointers of the adjacent nodes to correctly maintain the links in the list. 


else
{
    tmp = (*head)->next; // Save the next node before freeing the current node
    (*head)->prev->next = tmp; // Update the next pointer of the previous node
    if (tmp != NULL)
        tmp->prev = (*head)->prev; // Update the prev pointer of the next node
    free(*head); // Free the current node
    *head = saved_head; // Restore the head pointer
}


This way, you ensure that the prev and next pointers of the adjacent nodes are correctly updated to maintain the integrity of the doubly linked list.
