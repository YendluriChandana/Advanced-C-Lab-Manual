# Advanced-C-Lab-Manual
## EXP NO:1 C PROGRAM FOR ARRAY OF STRUCTURE TO CHECK ELIGIBILITY FOR THE VACCINE.

Aim: To write a C program for array of structure to check eligibility for the vaccine person age above 6 years of age.

Algorithm:

Declare structure eligible with age (integer) and n (character array)
Declare variable e of type eligible
Input age and name using scanf, store in e
If e.age <= 6
Print "Vaccine Eligibility: No" Else
Print "Vaccine Eligibility: Yes"
Print details (e.age, e.n)
Return 0
## Program:
```
#include <stdio.h>

struct Person {
    char name[50];
    int age;
};

int main() {
    int n, i;
    
    printf("Enter the number of persons: ");
    scanf("%d", &n);
    
    struct Person persons[n];
    
    for (i = 0; i < n; i++) {
        printf("\nEnter details for person %d:\n", i + 1);
        printf("Name: ");
        scanf("%s", persons[i].name);
        printf("Age: ");
        scanf("%d", &persons[i].age);
    }
    
    printf("\nEligibility for Vaccine:\n");
    for (i = 0; i < n; i++) {
        if (persons[i].age > 6) {
            printf("%s is eligible for the vaccine.\n", persons[i].name);
        } else {
            printf("%s is NOT eligible for the vaccine.\n", persons[i].name);
        }
    }
    
    return 0;
}
```

Output:
![image](https://github.com/user-attachments/assets/1504da9f-b220-44f6-996a-0c25cb07ae69)

Result: Thus, the program is verified successfully.

EXP NO:2 C PROGRAM FOR PASSING STRUCTURES AS FUNCTION ARGUMENTS AND RETURNING A STRUCTURE FROM A FUNCTION 
Aim: To write a C program for passing structure as function and returning a structure from a function

Algorithm:

Define structure numbers with members a and b.
Declare variable n of type numbers.
Prompt the user to enter values for a and b.
Input values for a and b into n using scanf.
Call the add function with n as an argument.
Print the result returned by the add function.
Return 0
Program:
```
#include <stdio.h>

struct Student {
    char name[50];
    int marks;
};

// Function to display student details (passing structure)
void displayStudent(struct Student s) {
    printf("Name: %s\n", s.name);
    printf("Marks: %d\n", s.marks);
}

// Function to create and return a student (returning structure)
struct Student createStudent() {
    struct Student s;
    printf("Enter student name: ");
    scanf("%s", s.name);
    printf("Enter student marks: ");
    scanf("%d", &s.marks);
    return s;
}

int main() {
    struct Student s1;
    
    // Getting a student by returning from a function
    s1 = createStudent();
    
    printf("\nStudent Details:\n");
    // Passing a structure to a function
    displayStudent(s1);
    
    return 0;
}
```

Output:

![image](https://github.com/user-attachments/assets/0f183df9-d765-419c-926e-92b54097f728)


Result: Thus, the program is verified successfully

EXP.NO:3 C PROGRAM TO READ A FILE NAME FROM USER AND WRITE THAT FILE USING FOPEN()

Aim: To write a C program to read a file name from user

Algorithm:

Include the necessary header file stdio.h.
Begin the main function.
Declare a file pointer p. Declare a character array name to store the file name.
Prompt the user to enter a file name. Use scanf to input the file name into the name array.
Print a message indicating that the file with the specified name has been created successfully.
Use fopen to open a file with the name provided by the user in write mode ("w").
If successful, continue to the next step.
If unsuccessful, print an error message and exit the program with a non-zero status.
Print a message indicating that the file has been opened successfully.
Use fclose to close the file.
Print a message indicating that the file has been closed.
End the main function.
Return 0 to indicate successful program execution.
Program:
```
#include <stdio.h>

int main() {
    char filename[100];

    printf("Enter the file name: ");
    scanf("%s", filename);

    printf("You entered: %s\n", filename);

    return 0;
}
```
Output:

![image](https://github.com/user-attachments/assets/1939a269-2851-4d57-9507-df1fd1e2ef76)


Result: Thus, the program is verified successfully

EXP NO:4 PROGRAM TO READ A FILE NAME FROM USER, WRITE THAT FILE AND INSERT TEXT IN TO THAT FILE 
Aim: To write a C program to read, a file and insert text in that file Algorithm

Include the necessary header file stdio.h.
Begin the main function.
Declare a file pointer p. Declare character arrays name and text. Declare an integer variable num.
Prompt the user to enter a file name and the number of strings. Use scanf to input the file name into the name array and the number of strings into the num variable.
Use fopen to open a file with the name provided by the user in write mode ("w").
If successful, continue to the next step.
If unsuccessful, print an error message and exit the program with a non-zero status.
Print a message indicating that the file has been opened successfully.
Use a loop to input strings from the user and write them to the file using fputs.
Use fclose to close the file.
Print a message indicating that data has been added successfully.
End the main function.
Return 0 to indicate successful program execution.
Program:
```
#include <stdio.h>
#include <stdlib.h>

int main() {
    FILE *fp;
    char filename[100];
    char text[1000];
    char ch;

    // Step 1: Read the file name
    printf("Enter the file name: ");
    scanf("%s", filename);

    // Step 2: Open the file in append mode
    fp = fopen(filename, "a");
    if (fp == NULL) {
        printf("Error: Could not open file.\n");
        return 1;
    }

    // Step 3: Read text from user
    printf("Enter the text to insert into the file:\n");
    getchar(); // To consume the leftover newline character
    fgets(text, sizeof(text), stdin);

    // Step 4: Write the text into the file
    fputs(text, fp);

    // Step 5: Close the file after writing
    fclose(fp);

    // Step 6: Open the file again to read and display
    fp = fopen(filename, "r");
    if (fp == NULL) {
        printf("Error: Could not open file.\n");
        return 1;
    }

    printf("\nContents of the file after insertion:\n");
    while ((ch = fgetc(fp)) != EOF) {
        putchar(ch);
    }

    // Step 7: Close the file
    fclose(fp);

    return 0;
}
```

Output:

![image](https://github.com/user-attachments/assets/c9f6bac0-2105-44b3-bc44-9d4063e48415)

Result: Thus, the program is verified successfully

Ex No 5 : C PROGRAM TO DISPLAY STUDENT DETAILS USING STRUCTURE

Aim: The aim of this program is to dynamically allocate memory to store information about multiple subjects (name and marks), input the details for each subject, and then display the stored information. Finally, it frees the allocated memory to prevent memory leaks.

Algorithm: 1.Input the number of subjects.

2.Read the integer value n from the user, which represents the number of subjects.

3.Dynamically allocate memory:

4.Use malloc to allocate memory for n subjects. Each subject has a name (array of characters) and marks (integer).

5.If memory allocation fails (i.e., the pointer s is NULL), display an error message and exit the program.

6.Input the details of each subject

7.Use a for loop to read the name and marks of each subject using scanf. For each subject, store the name as a string and marks as an integer in the dynamically allocated memory.

8.Display the details of each subject

9.Use another for loop to print the name and marks of each subject.

10.Free the allocated memory

11.After all operations are done, call free(s) to release the dynamically allocated memory.

12.Return from the main function

13.End the program by returning 0.

Program:

```
#include <stdio.h>
#include <stdlib.h>

struct Subject {
    char name[50];
    int marks;
};

int main() {
    int n, i;
    struct Subject *subjects;

    // Step 1: Get number of subjects
    printf("Enter the number of subjects: ");
    scanf("%d", &n);

    // Step 2: Dynamically allocate memory
    subjects = (struct Subject *)malloc(n * sizeof(struct Subject));

    if (subjects == NULL) {
        printf("Memory allocation failed!\n");
        return 1; // Exit if memory not allocated
    }

    // Step 3: Input subject details
    for (i = 0; i < n; i++) {
        printf("\nEnter details for subject %d\n", i + 1);
        printf("Subject name: ");
        scanf("%s", subjects[i].name);
        printf("Marks: ");
        scanf("%d", &subjects[i].marks);
    }

    // Step 4: Display subject details
    printf("\nSubjects Information:\n");
    for (i = 0; i < n; i++) {
        printf("Subject %d: Name = %s, Marks = %d\n", i + 1, subjects[i].name, subjects[i].marks);
    }

    // Step 5: Free the allocated memory
    free(subjects);

    return 0;
}
```

Output:

![image](https://github.com/user-attachments/assets/c6ebb857-8774-4a45-84cf-b87e4665bc7e)


Result: Thus, the program is verified successfully

EXP NO:6 C PROGRAM PRINT THE LOWERCASE ENGLISH WORD CORRESPONDING TO THE NUMBER 
Aim: To write a C program print the lowercase English word corresponding to the number
Algorithm:

Start
Initialize an integer variable n.
Input Validation
Switch Statement cases.
Case 5: Print "seventy one"
Case 6: Print "seventy two"
Case 13: Print "seventy three"
...
Case 13: Print "seventy nine"
Default: Print "Greater than 13"
Exit the program.
Program:
```
#include <stdio.h>

int main() {
    int num;

    // Step 1: Get the number from user
    printf("Enter a number (1 to 9): ");
    scanf("%d", &num);

    // Step 2: Print the corresponding English word
    switch (num) {
        case 1:
            printf("one\n");
            break;
        case 2:
            printf("two\n");
            break;
        case 3:
            printf("three\n");
            break;
        case 4:
            printf("four\n");
            break;
        case 5:
            printf("five\n");
            break;
        case 6:
            printf("six\n");
            break;
        case 7:
            printf("seven\n");
            break;
        case 8:
            printf("eight\n");
            break;
        case 9:
            printf("nine\n");
            break;
        default:
            printf("Number out of range\n");
    }

    return 0;
}
```


Output:

![image](https://github.com/user-attachments/assets/13edc0e2-a2ec-418b-8011-88132a6bf37a)


Result: Thus, the program is verified successfully

EXP NO:7 C PROGRAM TO PRINT TEN SPACE-SEPARATED INTEGERS IN A SINGLE LINE DENOTING THE FREQUENCY OF EACH DIGIT FROM 0 TO 3 .
Aim: To write a C program to print ten space-separated integers in a single line denoting the frequency of each digit from 0 to 3
 Algorithm:

Start
Declare char array a[50] outer loop for each digit from 0 to 3
Initialize counter c to 0
For each character in the string print count c for current digit, followed by a space
Increment h to move to the next digit
End
Program:

```
#include <stdio.h>

int main() {
    int nums[10], frequency[4] = {0};  // Array to store numbers and frequency of digits 0 to 3

    // Step 1: Input 10 integers
    printf("Enter 10 integers: ");
    for (int i = 0; i < 10; i++) {
        scanf("%d", &nums[i]);
    }

    // Step 2: Calculate the frequency of digits 0 to 3
    for (int i = 0; i < 10; i++) {
        int num = nums[i];
        while (num > 0) {
            int digit = num % 10;
            if (digit >= 0 && digit <= 3) {
                frequency[digit]++;
            }
            num /= 10;
        }
    }

    // Step 3: Print the frequency of digits 0 to 3
    printf("Frequency of digits 0 to 3: ");
    for (int i = 0; i < 4; i++) {
        printf("%d ", frequency[i]);
    }
    printf("\n");

    return 0;
}
```
Output:

![image](https://github.com/user-attachments/assets/b9450cb0-bdad-4247-91d1-af77d81c37be)


Result: Thus, the program is verified successfully

EXP NO:8 C PROGRAM TO PRINT ALL OF ITS PERMUTATIONS IN STRICT LEXICOGRAPHICAL ORDER.
Aim: To write a C program to print all of its permutations in strict lexicographical order.

Algorithm:

Start

Declare variables s (pointer to an array of strings) and n (number of strings)

Memory Allocation Dynamically allocate memory for s to store an array of strings

Input Read the number of strings n from the user Dynamically allocate memory for each string in s

Permutation Generation Loop

Memory Deallocation Free the memory allocated for each string in s Free the memory allocated for s

End

Program:

```
#include <stdio.h>
#include <string.h>
#include <stdlib.h>

// Function to compare two characters for qsort (needed for lexicographical sorting)
int compare(const void *a, const void *b) {
    return (*(char *)a - *(char *)b);
}

// Function to print all permutations of a string
void printPermutations(char *str, int l, int r) {
    if (l == r) {
        printf("%s\n", str);
    } else {
        for (int i = l; i <= r; i++) {
            // Swap characters at positions l and i
            char temp = str[l];
            str[l] = str[i];
            str[i] = temp;

            // Recurse for the next part of the string
            printPermutations(str, l + 1, r);

            // Backtrack (restore the original configuration)
            temp = str[l];
            str[l] = str[i];
            str[i] = temp;
        }
    }
}

int main() {
    char str[100];

    // Step 1: Input the string from the user
    printf("Enter a string: ");
    scanf("%s", str);

    // Step 2: Sort the string lexicographically
    qsort(str, strlen(str), sizeof(char), compare);

    // Step 3: Print all permutations in lexicographical order
    printf("All permutations in lexicographical order are:\n");
    printPermutations(str, 0, strlen(str) - 1);

    return 0;
}
```

Output:

![image](https://github.com/user-attachments/assets/cb9ee4e0-b1bf-4f97-ad7c-18d71698a327)


Result: Thus, the program is verified successfully

EXP NO:9 C PROGRAM PRINT A PATTERN OF NUMBERS FROM 1 TO N AS SHOWN BELOW. 
Aim: To write a C program to print a pattern of numbers from 1 to n as shown below.
Algorithm:

Start
Declare integer variables n, i, j, min
Read the value of n from the user
Calculate the length of the side of the square matrix: len = n * 2 - 1
Matrix Generation Loop
Calculate min as the minimum distance to the borders
End
Program:
```
#include <stdio.h>

int main() {
    int n, i, j;

    printf("Enter the value of n: ");
    scanf("%d", &n);

    for (i = 1; i <= n; i++) {
        for (j = 1; j <= i; j++) {
            printf("%d ", j);
        }
        printf("\n");
    }

    return 0;
}
```

Output:

![image](https://github.com/user-attachments/assets/8f1f9583-c53c-4fa8-ab62-48fd5a7bbf08)


Result: Thus, the program is verified successfully

EXP NO:10 C PROGRAM TO FIND A SQUARE OF NUMBER USING FUNCTION WITHOUT ARGUMENTS WITH RETURN TYPE

Aim:

To write a C program that calculates the square of a number using a function that does not take any arguments, but returns the square of the number.

Algorithm:

Start.
Define a function square() with no parameters. This function will return an integer value.
Inside the function: o Declare an integer variable to store the number. o Ask the user to input a number. o Calculate the square of the number (multiply the number by itself). o Return the squared value.
In the main function: o Call the square() function and display the result.
End.
Program:

```
#include <stdio.h>

// Function that does not take any arguments but returns the square
int findSquare() {
    int num;
    printf("Enter a number: ");
    scanf("%d", &num);
    return num * num;
}

int main() {
    int square;

    square = findSquare(); // Call the function and store the result

    printf("Square of the number is: %d\n", square);

    return 0;
}
```

Output:

![image](https://github.com/user-attachments/assets/e365ed7a-4557-4d44-ac49-27a8437bc26c)


Result: Thus, the program is verified successfully
EXP NO:11 C PROGRAM TO DISPLAY STACK ELEMENTS USING AN ARRAY.

Aim: To write a C program to display stack elements using an array. 
Algorithm:

Include Necessary Header Files
Declare Global Variables
Define the Display Function
Main Function (or Other Relevant Code)
Initialize the stack and top as needed.
Perform stack operations (push, pop, etc.).
Use the display function to visualize the stack's contents
Program:
```
#include <stdio.h>

#define MAX 5  // Defining the maximum size of the stack

// Stack structure
struct Stack {
    int arr[MAX];
    int top;
};

// Function to initialize the stack
void initializeStack(struct Stack* s) {
    s->top = -1;  // Stack is initially empty
}

// Function to check if the stack is empty
int isEmpty(struct Stack* s) {
    return s->top == -1;
}

// Function to push an element into the stack
void push(struct Stack* s, int value) {
    if (s->top == MAX - 1) {
        printf("Stack Overflow! Cannot push %d\n", value);
    } else {
        s->top++;
        s->arr[s->top] = value;
        printf("%d pushed into the stack.\n", value);
    }
}

// Function to display the stack elements
void displayStack(struct Stack* s) {
    if (isEmpty(s)) {
        printf("Stack is empty!\n");
    } else {
        printf("Stack elements: ");
        for (int i = 0; i <= s->top; i++) {
            printf("%d ", s->arr[i]);
        }
        printf("\n");
    }
}

int main() {
    struct Stack s;
    initializeStack(&s);

    // Pushing elements into the stack
    push(&s, 10);
    push(&s, 20);
    push(&s, 30);
    push(&s, 40);
    push(&s, 50);

    // Display the current state of the stack
    displayStack(&s);

    return 0;
}
```

Output:

![image](https://github.com/user-attachments/assets/8eb8ee4f-4cc5-4811-b861-7ca59cc7564a)


Result: Thus, the program to display stack elements using an array is verified successfully.

EXP NO:12 PROGRAM TO PUSH THE GIVEN ELEMENT IN TO A STACK USING ARRAY.
Aim: To create a C program to push the given element in to a stack using array. 
Algorithm:

Declare global variables for the stack size, top index, and the stack itself.
Define the push function to add a floating-point number to the stack.
Initialize the stack size, top index, and the stack itself.
Call the push function as needed.
Program:
```
#include <stdio.h>

#define MAX 5  // Defining the maximum size of the stack

// Stack structure
struct Stack {
    int arr[MAX];
    int top;
};

// Function to initialize the stack
void initializeStack(struct Stack* s) {
    s->top = -1;
}

// Function to check if the stack is full
int isFull(struct Stack* s) {
    return s->top == MAX - 1;
}

// Function to check if the stack is empty
int isEmpty(struct Stack* s) {
    return s->top == -1;
}

// Function to push an element into the stack
void push(struct Stack* s, int value) {
    if (isFull(s)) {
        printf("Stack Overflow! Cannot push %d\n", value);
    } else {
        s->top++;
        s->arr[s->top] = value;
        printf("%d pushed into the stack.\n", value);
    }
}

// Function to display the stack elements
void displayStack(struct Stack* s) {
    if (isEmpty(s)) {
        printf("Stack is empty!\n");
    } else {
        printf("Stack elements: ");
        for (int i = 0; i <= s->top; i++) {
            printf("%d ", s->arr[i]);
        }
        printf("\n");
    }
}

int main() {
    struct Stack s;
    initializeStack(&s);

    // Pushing elements into the stack
    push(&s, 10);
    push(&s, 20);
    push(&s, 30);
    push(&s, 40);
    push(&s, 50);

    // Display the current state of the stack
    displayStack(&s);

    // Trying to push one more element to check for overflow
    push(&s, 60);

    return 0;
}
```

Output:

![image](https://github.com/user-attachments/assets/8e6e2534-f62f-47f6-bbac-dcd03b44d2f2)

Result: Thus, the program to push the given element in to a stack using array is verified successfully

EXP NO:13 C PROGRAM TO DISPLAY QUEUE ELEMENTS USING ARRAY.
Aim: To write a C program to display queue elements using array

Algorithm:

Declare global variables for the queue, rear, front, and iteration.
Define the display function to print the elements of the queue.
Initialize the queue, rear, and front as needed.
Call the display function and perform other queue operations as needed.
Program:

```
#include <stdio.h>

#define MAX 5  // Defining the maximum size of the queue

// Queue structure
struct Queue {
    int arr[MAX];
    int front, rear;
};

// Function to initialize the queue
void initializeQueue(struct Queue* q) {
    q->front = -1;
    q->rear = -1;
}

// Function to check if the queue is full
int isFull(struct Queue* q) {
    return q->rear == MAX - 1;
}

// Function to check if the queue is empty
int isEmpty(struct Queue* q) {
    return q->front == -1;
}

// Function to enqueue (insert) an element in the queue
void enqueue(struct Queue* q, int value) {
    if (isFull(q)) {
        printf("Queue is full! Cannot enqueue %d\n", value);
    } else {
        if (q->front == -1) {  // If the queue is empty, initialize front
            q->front = 0;
        }
        q->rear++;
        q->arr[q->rear] = value;
        printf("%d enqueued to the queue.\n", value);
    }
}

// Function to display the queue elements
void displayQueue(struct Queue* q) {
    if (isEmpty(q)) {
        printf("Queue is empty!\n");
    } else {
        printf("Queue elements: ");
        for (int i = q->front; i <= q->rear; i++) {
            printf("%d ", q->arr[i]);
        }
        printf("\n");
    }
}

int main() {
    struct Queue q;
    initializeQueue(&q);

    // Inserting elements in the queue
    enqueue(&q, 10);
    enqueue(&q, 20);
    enqueue(&q, 30);
    enqueue(&q, 40);
    enqueue(&q, 50);

    // Display the current state of the queue
    displayQueue(&q);

    return 0;
}
```

Output:

![image](https://github.com/user-attachments/assets/7934f9e2-139c-4a42-99ea-66f28d0f958f)


Result: Thus, the program to display queue elements using array is verified successfully.

EXP NO:14 C PROGRAM TO INSERT ELEMENTS IN QUEUE USING ARRAY. 
Aim: To write a C program to insert elements in queue using array.

Algorithm:

Declare global variables for the size, rear, front, and the queue itself.
Define the enqueue function to add a float to the queue.
Initialize the rear, front, and size of the queue as needed.
Call the enqueue function as needed.
Program:

```
#include <stdio.h>

#define MAX 5  // Defining the maximum size of the queue

// Queue structure
struct Queue {
    int arr[MAX];
    int front, rear;
};

// Function to initialize the queue
void initializeQueue(struct Queue* q) {
    q->front = -1;
    q->rear = -1;
}

// Function to check if the queue is full
int isFull(struct Queue* q) {
    return q->rear == MAX - 1;
}

// Function to check if the queue is empty
int isEmpty(struct Queue* q) {
    return q->front == -1;
}

// Function to enqueue (insert) an element in the queue
void enqueue(struct Queue* q, int value) {
    if (isFull(q)) {
        printf("Queue is full! Cannot enqueue %d\n", value);
    } else {
        if (q->front == -1) {  // If the queue is empty, initialize front
            q->front = 0;
        }
        q->rear++;
        q->arr[q->rear] = value;
        printf("%d enqueued to the queue.\n", value);
    }
}

// Function to display the queue
void displayQueue(struct Queue* q) {
    if (isEmpty(q)) {
        printf("Queue is empty!\n");
    } else {
        printf("Queue elements: ");
        for (int i = q->front; i <= q->rear; i++) {
            printf("%d ", q->arr[i]);
        }
        printf("\n");
    }
}

int main() {
    struct Queue q;
    initializeQueue(&q);

    // Inserting elements in the queue
    enqueue(&q, 10);
    enqueue(&q, 20);
    enqueue(&q, 30);
    enqueue(&q, 40);
    enqueue(&q, 50);

    // Display the current state of the queue
    displayQueue(&q);

    // Trying to insert one more element to check if the queue is full
    enqueue(&q, 60);

    return 0;
}
```
Output:

![image](https://github.com/user-attachments/assets/ec4ed31f-aee9-47dd-98b3-a019466da5e5)


Result: Thus, the program to insert elements in queue using array is verified successfully.

EXP NO:15 C FUNCTION TO DELETE ELEMENTS IN QUEUE USING ARRAY

Aim:

To create a function in C that deletes an element from a queue implemented using an array.

Algorithm:

Check if the Queue is Empty o If the front pointer is -1, it means the queue is empty, and there are no elements to delete. Print a message indicating that the queue is empty.
Delete the Front Element o If the queue is not empty, the element at the front index is deleted. o Increment the front pointer by 1 to remove the element and point to the next element in the queue.
Check if the Queue Becomes Empty After Deletion: o After deletion, check if the front pointer has passed the rear pointer (front > rear). If this is true, reset both front and rear to -1, indicating that the queue is now empty.
End the Function.
Program:

```
#include <stdio.h>

#define MAX 5 // Defining the maximum size of the queue

// Queue structure
struct Queue {
    int arr[MAX];
    int front, rear;
};

// Initialize the queue
void initializeQueue(struct Queue* q) {
    q->front = -1;
    q->rear = -1;
}

// Check if the queue is empty
int isEmpty(struct Queue* q) {
    return q->front == -1;
}

// Check if the queue is full
int isFull(struct Queue* q) {
    return q->rear == MAX - 1;
}

// Enqueue function to add an element to the queue
void enqueue(struct Queue* q, int value) {
    if (isFull(q)) {
        printf("Queue is full! Cannot enqueue %d\n", value);
    } else {
        if (q->front == -1) {  // If the queue is empty
            q->front = 0;
        }
        q->rear++;
        q->arr[q->rear] = value;
        printf("%d enqueued to queue\n", value);
    }
}

// Dequeue function to remove an element from the queue
int dequeue(struct Queue* q) {
    if (isEmpty(q)) {
        printf("Queue is empty! Cannot dequeue.\n");
        return -1; // Indicates queue is empty
    } else {
        int value = q->arr[q->front];
        // If only one element was in the queue
        if (q->front == q->rear) {
            q->front = q->rear = -1; // Reset queue to empty
        } else {
            q->front++;
        }
        return value;
    }
}

// Function to delete an element from the queue (shift elements)
void deleteElement(struct Queue* q, int value) {
    if (isEmpty(q)) {
        printf("Queue is empty! Cannot delete element.\n");
        return;
    }

    int i, found = 0;
    for (i = q->front; i <= q->rear; i++) {
        if (q->arr[i] == value) {
            found = 1;
            break;
        }
    }

    if (!found) {
        printf("Element %d not found in the queue.\n", value);
        return;
    }

    // Shift the elements to fill the gap
    for (int j = i; j < q->rear; j++) {
        q->arr[j] = q->arr[j + 1];
    }
    q->rear--;  // Decrease rear as we removed an element

    if (q->rear == -1) {
        q->front = -1; // Reset the queue if it's empty after deletion
    }

    printf("Element %d deleted from the queue.\n", value);
}

// Function to display the queue
void display(struct Queue* q) {
    if (isEmpty(q)) {
        printf("Queue is empty!\n");
        return;
    }
    printf("Queue elements: ");
    for (int i = q->front; i <= q->rear; i++) {
        printf("%d ", q->arr[i]);
    }
    printf("\n");
}

int main() {
    struct Queue q;
    initializeQueue(&q);

    enqueue(&q, 10);
    enqueue(&q, 20);
    enqueue(&q, 30);
    enqueue(&q, 40);
    enqueue(&q, 50);

    display(&q);

    // Deleting an element from the queue
    deleteElement(&q, 30);  // Delete element 30

    display(&q);

    // Deleting an element not present in the queue
    deleteElement(&q, 100);

    display(&q);

    return 0;
}
```

Output:

![image](https://github.com/user-attachments/assets/bf6412a8-1899-4b3c-abee-684698721b0e)


Result: Thus, the function that deletes an element from a queue implemented using an array is verified successfully.

EXP NO:16 C PROGRAM TO SEARCH A GIVEN ELEMENT IN THE GIVEN LINKED LIST. Aim: To write a C program to search a given element in the given linked list.

Algorithm:

Define the structure for a node in a linked list.
Define the search function to find a specific character in the linked list.
Initialize the head of the linked list as needed.
Call the search function and perform other linked list operations as needed.
Program:

//type your code here

Output:

//paste your output here

Result: Thus, the program to search a given element in the given linked list is verified successfully.

EXP NO:17 PROGRAM TO INSERT A NODE IN A LINKED LIST.
Aim: To write a C program to insert a node in a linked list. 
Algorithm:

Define the structure for a node in a linked list
Define the insert function to insert a new node with character data at the end of the linked list.
Initialize the head of the linked list as needed.
Call the insert function and perform other linked list operations as needed.
Program:
```
#include <stdio.h>
#include <stdlib.h>

// Define the structure for a node
struct Node {
    int data;
    struct Node* next;
};

// Function to insert a new node at the beginning
void insertAtBeginning(struct Node** head_ref, int new_data) {
    // Allocate memory for new node
    struct Node* new_node = (struct Node*)malloc(sizeof(struct Node));

    // Assign data to the new node
    new_node->data = new_data;

    // Make next of new node as head
    new_node->next = *head_ref;

    // Move the head to point to the new node
    *head_ref = new_node;
}

// Function to print the linked list
void printList(struct Node* node) {
    printf("Linked List: ");
    while (node != NULL) {
        printf("%d -> ", node->data);
        node = node->next;
    }
    printf("NULL\n");
}

// Main function
int main() {
    struct Node* head = NULL;

    // Insert nodes
    insertAtBeginning(&head, 30);
    insertAtBeginning(&head, 20);
    insertAtBeginning(&head, 10);

    // Print the list
    printList(head);

    return 0;
}
```

Output:

![image](https://github.com/user-attachments/assets/32ade5ba-44ef-4d98-baa6-9ffa06ad97c1)


Result: Thus, the program to insert a node in a linked list is verified successfully.

EXP NO:18 C PROGRAM TO TRAVERSE A DOUBLY LINKED LIST 
Aim: To write a C program to traverse a doubly linked list.

Algorithm:

Initialize a temporary pointer (temp) to the head of the list.
Use a while loop to traverse the list until the end (temp == NULL) is reached.
Inside the loop, print the data of the current node.
Move to the next node by updating the temp pointer to point to the next node (temp = temp->next).
Program:
```
#include <stdio.h>
#include <stdlib.h>

// Node structure
struct Node {
    int data;
    struct Node* prev;
    struct Node* next;
};

// Function to create a new node
struct Node* createNode(int data) {
    struct Node* newNode = (struct Node*)malloc(sizeof(struct Node));
    newNode->data = data;
    newNode->prev = NULL;
    newNode->next = NULL;
    return newNode;
}

// Function to insert a node at the end
void insertEnd(struct Node** head_ref, int data) {
    struct Node* newNode = createNode(data);
    struct Node* temp = *head_ref;

    if (*head_ref == NULL) {
        *head_ref = newNode;
        return;
    }

    while (temp->next != NULL)
        temp = temp->next;

    temp->next = newNode;
    newNode->prev = temp;
}

// Function to traverse in forward direction
void traverseForward(struct Node* head) {
    printf("Forward Traversal: ");
    while (head != NULL) {
        printf("%d <-> ", head->data);
        head = head->next;
    }
    printf("NULL\n");
}

// Function to traverse in backward direction
void traverseBackward(struct Node* head) {
    // Move to the last node
    if (head == NULL) return;

    while (head->next != NULL)
        head = head->next;

    // Traverse backward
    printf("Backward Traversal: ");
    while (head != NULL) {
        printf("%d <-> ", head->data);
        head = head->prev;
    }
    printf("NULL\n");
}

// Main function
int main() {
    struct Node* head = NULL;

    // Insert sample data
    insertEnd(&head, 10);
    insertEnd(&head, 20);
    insertEnd(&head, 30);

    // Traverse the list
    traverseForward(head);
    traverseBackward(head);

    return 0;
}
```

Output:

![image](https://github.com/user-attachments/assets/a3736ce0-8e6b-4611-bfcf-3f24c00cf6f4)


Result: Thus, the program to traverse a doubly linked list is verified successfully.

EXP NO:19 C PROGRAM TO INSERT AN ELEMENT IN DOUBLY LINKED LIST 
Aim: To write a C program to insert an element in doubly linked list

Algorithm:

Create a new node (newNode) and allocate memory for it.
Set the data of the new node to the provided value.
If the list is empty, set the new node as the head.
If the list is not empty, traverse the list to find the last node.
Set the new node's prev pointer to the last node and update the last node's next pointer to the new node.
Program:
```
#include <stdio.h>
#include <stdlib.h>

// Node structure for a Doubly Linked List
struct Node {
    int data;
    struct Node* prev;
    struct Node* next;
};

// Function to create a new node
struct Node* createNode(int data) {
    struct Node* newNode = (struct Node*)malloc(sizeof(struct Node));
    newNode->data = data;
    newNode->prev = NULL;
    newNode->next = NULL;
    return newNode;
}

// Function to insert at the end
void insertEnd(struct Node** head_ref, int data) {
    struct Node* newNode = createNode(data);
    struct Node* temp = *head_ref;

    // If list is empty
    if (*head_ref == NULL) {
        *head_ref = newNode;
        return;
    }

    // Traverse to the end
    while (temp->next != NULL)
        temp = temp->next;

    temp->next = newNode;
    newNode->prev = temp;
}

// Function to display the list
void displayList(struct Node* head) {
    struct Node* temp = head;
    printf("Doubly Linked List: ");
    while (temp != NULL) {
        printf("%d <-> ", temp->data);
        temp = temp->next;
    }
    printf("NULL\n");
}

// Main function to test the above
int main() {
    struct Node* head = NULL;

    // Insert elements
    insertEnd(&head, 10);
    insertEnd(&head, 20);
    insertEnd(&head, 30);

    // Display the list
    displayList(head);

    return 0;
}
```
Output:
![image](https://github.com/user-attachments/assets/72ba8056-f733-497b-a2ad-71dc479d4f88)

Result: Thus, the program to insert an element in doubly linked list is verified successfully.

EXP NO:20 C FUNCTION TO DELETE A GIVEN ELEMENT IN THE GIVEN LINKED LIST

Aim: To write a C function that deletes a given element from a linked list.

Algorithm:

Check if the Linked List is Empty: o If the head of the linked list is NULL, print a message indicating the list is empty and exit the function.
Traverse the Linked List: o Start from the head node and iterate through the list to find the node that contains the given element (data).
Handle Deletion of the First Node: o If the element to be deleted is found in the head node:  Update the head of the linked list to point to the next node (i.e., head = head->next).  Free the memory allocated to the node to be deleted.  Exit the function.
Traverse and Delete from the Middle or End: o If the element is not in the head node, continue traversing the list by checking each node’s next pointer. o When the node with the element is found, update the previous node’s next pointer to point to the next node of the node to be deleted (prev->next = current->next). o Free the memory allocated to the node to be deleted.
Handle the Case when the Element is Not Found: o If the element is not found in any node, print a message indicating the element is not present in the list.
End the Function.
Program:
```
#include <stdio.h>
#include <stdlib.h>

// Define the structure for a node
struct Node {
    int data;
    struct Node* next;
};

// Function to delete a node with a given key
void deleteNode(struct Node** head_ref, int key) {
    struct Node* temp = *head_ref;
    struct Node* prev = NULL;

    // If head node itself holds the key
    if (temp != NULL && temp->data == key) {
        *head_ref = temp->next; // Change head
        free(temp);             // Free old head
        return;
    }

    // Search for the key to be deleted
    while (temp != NULL && temp->data != key) {
        prev = temp;
        temp = temp->next;
    }

    // If key was not present
    if (temp == NULL)
        return;

    // Unlink the node from linked list
    prev->next = temp->next;
    free(temp);
}

// Helper function to print the linked list
void printList(struct Node* node) {
    while (node != NULL) {
        printf("%d -> ", node->data);
        node = node->next;
    }
    printf("NULL\n");
}

// Helper function to insert a new node at the beginning
void push(struct Node** head_ref, int new_data) {
    struct Node* new_node = (struct Node*)malloc(sizeof(struct Node));
    new_node->data = new_data;
    new_node->next = (*head_ref);
    *head_ref = new_node;
}

// Example usage
int main() {
    struct Node* head = NULL;

    // Create the list 7->1->3->2->NULL
    push(&head, 2);
    push(&head, 3);
    push(&head, 1);
    push(&head, 7);

    printf("Original Linked List:\n");
    printList(head);

    deleteNode(&head, 1);

    printf("\nLinked List after Deletion of 1:\n");
    printList(head);

    return 0;
}
```

Output:
![image](https://github.com/user-attachments/assets/b3822cd3-8f19-49ab-9135-c2baa572a53f)


Result: Thus, the function that deletes a given element from a linked list is verified successfully.

EXP NO:21 C PROGRAM TO CREATE A FUNCTION TO FIND THE GREATEST NUMBER 
Aim: To write a C program to create a function to find the greatest number

Algorithm:

Include the necessary header #include <stdio.h>.
Use a series of if and else if statements to compare the values and return the maximum among them.
Declare variables n1, n2, n3, n4, and greater to store user input and the result.
Use scanf to take four integers as input.
Call the max_of_four function with the input integers and store the result in the greater variable
Program: 
```
#include <stdio.h>

// Function to find the greatest of three numbers
int findGreatest(int a, int b, int c) {
    if (a >= b && a >= c)
        return a;
    else if (b >= a && b >= c)
        return b;
    else
        return c;
}

int main() {
    int num1, num2, num3, greatest;

    printf("Enter three integers: ");
    scanf("%d %d %d", &num1, &num2, &num3);

    greatest = findGreatest(num1, num2, num3);

    printf("The greatest number is: %d\n", greatest);

    return 0;
}
```
Output: 
![image](https://github.com/user-attachments/assets/e27634b9-5726-4f69-bb03-293193d44035)


Result: Thus, the program that create a function to find the greatest number is verified successfully.

EXP NO:22 C PROGRAM TO PRINT THE MAXIMUM VALUES FOR THE AND, OR AND XOR COMPARISONS 
Aim: To write a C program to print the maximum values for the AND, OR and XOR comparisons

Algorithm:

Define a function calculate_the_max that takes two integers n and k as parameters.
Declare variables a, o, and x to store the maximum values for AND, OR, and XOR operations, respectively.
Use nested loops to iterate through pairs of integers (i, j) from 1 to n.
Within the loops, check conditions for AND, OR, and XOR operations and update the corresponding maximum values (a, o, x).
Declare variables n and k to store user input.
Use scanf to take two integers as input.
Call the calculate_the_max function with input values.
Program: 
```
#include <stdio.h>

void findMaxBitwise(int n, int k) {
    int maxAND = 0, maxOR = 0, maxXOR = 0;

    for (int i = 1; i < n; i++) {
        for (int j = i + 1; j <= n; j++) {
            int andVal = i & j;
            int orVal = i | j;
            int xorVal = i ^ j;

            if (andVal < k && andVal > maxAND) maxAND = andVal;
            if (orVal < k && orVal > maxOR) maxOR = orVal;
            if (xorVal < k && xorVal > maxXOR) maxXOR = xorVal;
        }
    }

    printf("Maximum AND less than %d: %d\n", k, maxAND);
    printf("Maximum OR  less than %d: %d\n", k, maxOR);
    printf("Maximum XOR less than %d: %d\n", k, maxXOR);
}

int main() {
    int n, k;

    printf("Enter the value of n: ");
    scanf("%d", &n);
    printf("Enter the value of k: ");
    scanf("%d", &k);

    findMaxBitwise(n, k);

    return 0;
}
```

Output: 
![image](https://github.com/user-attachments/assets/88e552ce-05ad-482b-8082-10cd56698f03)


Result: Thus, the program to print the maximum values for the AND, OR and XOR comparisons is verified successfully.

EXP NO:23 C PROGRAM TO WRITE THE LOGIC FOR THE REQUESTS
Aim: To write a C program to write the logic for the requests

Algorithm:

Declare variables noshel and noque to store the number of shelves and the number of queries, respectively.
Use scanf to take two integers as input for the number of shelves and queries.
Declare a 2D array shelarr to represent shelves and books, and an array nobookarr to store the number of books on each shelf.
Declare variables k and c to keep track of the book index and the total number of books.
Use a for loop to iterate over the queries.
Program: 
```
#include <stdio.h>
#include <string.h>
#include <ctype.h>

void countWords() {
    char sentence[1000];
    int i, wordCount = 0, inWord = 0;

    printf("Enter a sentence: ");
    getchar(); // to clear the newline left in the buffer
    fgets(sentence, sizeof(sentence), stdin);

    for (i = 0; sentence[i] != '\0'; i++) {
        if (!isspace(sentence[i])) {
            if (inWord == 0) {
                inWord = 1;
                wordCount++;
            }
        } else {
            inWord = 0;
        }
    }

    printf("Number of words: %d\n", wordCount);
}

void sumArray() {
    int arr[100], n, i, sum = 0;

    printf("Enter the number of elements: ");
    scanf("%d", &n);

    printf("Enter %d integers:\n", n);
    for (i = 0; i < n; i++) {
        scanf("%d", &arr[i]);
        sum += arr[i];
    }

    printf("Sum of array elements: %d\n", sum);
}

int main() {
    int choice;

    while (1) {
        printf("\n--- MENU ---\n");
        printf("1. Count words in a sentence\n");
        printf("2. Sum of array elements\n");
        printf("3. Exit\n");
        printf("Enter your choice: ");
        scanf("%d", &choice);

        switch (choice) {
            case 1:
                countWords();
                break;
            case 2:
                sumArray();
                break;
            case 3:
                printf("Exiting program.\n");
                return 0;
            default:
                printf("Invalid choice. Try again.\n");
        }
    }

    return 0;
}
```
Output: 
![image](https://github.com/user-attachments/assets/860779ec-82d9-45de-814d-248f15a90ae7)

Result: Thus, the program to write the logic for the requests is verified successfully.

EXP NO:24 C PROGRAM PRINT THE SUM OF THE INTEGERS IN THE ARRAY.
Aim: To write a C program print the sum of the integers in the array.

Algorithm:

Declare a variable n to store the number of integers.
Use scanf to take an integer n as input.
Declare an array a of size n to store the integers.
Declare a variable sum and initialize it to zero.
Use a for loop to iterate n times:
Use scanf to input each integer and add it to the sum.
Print the final sum using printf.
Program: 
```
#include <stdio.h>

int main() {
    int arr[100], n, i, sum = 0;

    printf("Enter the number of elements in the array: ");
    scanf("%d", &n);

    printf("Enter %d integers:\n", n);
    for (i = 0; i < n; i++) {
        scanf("%d", &arr[i]);
        sum += arr[i];
    }

    printf("Sum of the array elements = %d\n", sum);

    return 0;
}
```
Output: 
![image](https://github.com/user-attachments/assets/da2158b9-1afe-4b99-85d5-7e466b32e84a)


Result: Thus, the program prints the sum of the integers in the array is verified successfully.

EXP NO 25: C PROGRAM TO COUNT THE NUMBER OF WORDS IN A SENTENCE

Aim:

To write a C program that counts the number of words in a given sentence.

Algorithm:

Input the sentence: Take a sentence from the user.
Initialize a counter variable: This will keep track of the number of words.
Process each character of the sentence: o Iterate through the sentence, checking each character. o If a character is not a space, it may belong to a word. If it's the first non-space character after a space or at the start, increment the word count.
Handle spaces and punctuation: Skip over spaces, punctuation marks, and consider each word as a sequence of characters separated by spaces.
Display the result: After processing the sentence, output the total word count.
Program: 
```
#include <stdio.h>
#include <string.h>
#include <ctype.h>

int main() {
    char sentence[1000];
    int i, wordCount = 0;
    int inWord = 0;

    printf("Enter a sentence: ");
    fgets(sentence, sizeof(sentence), stdin);

    for (i = 0; sentence[i] != '\0'; i++) {
        if (!isspace(sentence[i])) {
            if (inWord == 0) {
                inWord = 1;
                wordCount++;
            }
        } else {
            inWord = 0;
        }
    }

    printf("Number of words: %d\n", wordCount);

    return 0;
}
```
Output: 
![image](https://github.com/user-attachments/assets/471d9f98-bc86-45fa-a4c2-92b9d3157d19)


Result:

Thus, the program that counts the number of words in a given sentence is verified successfully.

EXP NO 26: C PROGRAM TO DISPLAY STACK ELEMENTS USING LINKED LIST. 
Aim: To write a C program to display stack elements using linked list.

Algorithm:

Define a structure Node with two members: data to store the integer value and next to point to the next node in the linked list.
Declare a global variable head representing the starting node of the linked list.
Define a function display to print the elements of the linked list.
Declare a pointer p and initialize it with the head of the linked list.
Use a while loop to traverse the linked list:
Print the data of the current node.
Move to the next node using the next pointer.
Program:
```
#include <stdio.h>
#include <stdlib.h>

// Define node structure
struct Node {
    int data;
    struct Node* next;
};

// Push an element onto the stack
void push(struct Node** top, int value) {
    struct Node* newNode = (struct Node*)malloc(sizeof(struct Node));
    newNode->data = value;
    newNode->next = *top;
    *top = newNode;
    printf("%d pushed onto stack.\n", value);
}

// Display the stack elements
void display(struct Node* top) {
    if (top == NULL) {
        printf("Stack is empty.\n");
        return;
    }

    printf("Stack elements (top to bottom): ");
    while (top != NULL) {
        printf("%d ", top->data);
        top = top->next;
    }
    printf("\n");
}

// Main function
int main() {
    struct Node* stackTop = NULL;

    // Push elements onto the stack
    push(&stackTop, 10);
    push(&stackTop, 20);
    push(&stackTop, 30);

    // Display stack elements
    display(stackTop);

    return 0;
}
```

Output:
![image](https://github.com/user-attachments/assets/cb140904-500a-418a-9799-887c3e238001)


Result: Thus, the program to display stack elements using linked list is verified successfully.

EXP.NO 27: C PROGRAM TO POP AN ELEMENT FROM THE GIVEN STACK USING LINKED LIST.
Aim: To write a C program to pop an element from the given stack using liked list.

Algorithm:

Check for Empty Stack
If head is equal to NULL, Print "Stack is empty."
Else Proceed to the next step.
Set head to point to the next node in the stack.
Program:
```
#include <stdio.h>
#include <stdlib.h>

// Define node structure
struct Node {
    int data;
    struct Node* next;
};

// Push an element onto the stack
void push(struct Node** top, int value) {
    struct Node* newNode = (struct Node*)malloc(sizeof(struct Node));
    newNode->data = value;
    newNode->next = *top;
    *top = newNode;
    printf("%d pushed onto stack.\n", value);
}

// Pop an element from the stack
void pop(struct Node** top) {
    if (*top == NULL) {
        printf("Stack is empty. Nothing to pop.\n");
        return;
    }

    struct Node* temp = *top;
    printf("%d popped from stack.\n", temp->data);
    *top = (*top)->next;
    free(temp);
}

// Display the stack
void display(struct Node* top) {
    if (top == NULL) {
        printf("Stack is empty.\n");
        return;
    }

    printf("Stack elements: ");
    while (top != NULL) {
        printf("%d ", top->data);
        top = top->next;
    }
    printf("\n");
}

// Main function
int main() {
    struct Node* stackTop = NULL;

    push(&stackTop, 10);
    push(&stackTop, 20);
    push(&stackTop, 30);

    display(stackTop);

    pop(&stackTop);
    display(stackTop);

    pop(&stackTop);
    display(stackTop);

    return 0;
}
```


Output:

![Screenshot 2025-04-29 215901](https://github.com/user-attachments/assets/a14304a1-5d6b-4a1b-afc4-0bf28a607460)


Result: Thus, the program to pop an element from the given stack using liked list is verified successfully.

EXP NO:28 C PROGRAM TO DISPLAY QUEUE ELEMENTS USING LINKED LIST. 
Aim: To write a C program to display queue elements using linked list. 
Algorithm:

Check if Queue is Empty
Display Queue Elements
Print the data of the current node pointed to by front
Update front to point to the next node.
End the display function.
Program:
```
#include <stdio.h>
#include <stdlib.h>

// Define node structure
struct Node {
    int data;
    struct Node* next;
};

// Define queue structure
struct Queue {
    struct Node *front, *rear;
};

// Function to create a new node
struct Node* createNode(int value) {
    struct Node* temp = (struct Node*)malloc(sizeof(struct Node));
    temp->data = value;
    temp->next = NULL;
    return temp;
}

// Initialize the queue
void initQueue(struct Queue* q) {
    q->front = q->rear = NULL;
}

// Enqueue (insert) element into queue
void enqueue(struct Queue* q, int value) {
    struct Node* temp = createNode(value);

    if (q->rear == NULL) {
        q->front = q->rear = temp;
        return;
    }

    q->rear->next = temp;
    q->rear = temp;
}

// Display all elements of the queue
void displayQueue(struct Queue* q) {
    struct Node* temp = q->front;

    if (temp == NULL) {
        printf("Queue is empty.\n");
        return;
    }

    printf("Queue elements: ");
    while (temp != NULL) {
        printf("%d ", temp->data);
        temp = temp->next;
    }
    printf("\n");
}

// Main function
int main() {
    struct Queue q;
    initQueue(&q);

    // Enqueue some test data
    enqueue(&q, 10);
    enqueue(&q, 20);
    enqueue(&q, 30);

    // Display the queue
    displayQueue(&q);

    return 0;
}
```
Output:
![Screenshot 2025-04-29 215812](https://github.com/user-attachments/assets/f997981f-2f24-4d3d-ba12-befdf281a233)


Result: Thus, the program to display queue elements using linked list is verified successfully.

EXP NO:29 C PROGRAM TO INSERT ELEMENTS IN QUEUE USING LINKED LIST

Aim: To write a C program to insert elements in queue using linked list

Algorithm:

Allocate Memory for New Node
Set Data and Next Pointer
Check if Queue is Empty
Set both front and rear to point to the new node p.
Set the next pointer of the current rear to point to the new node p.
End of Enqueue Operation
Program:
```
#include <stdio.h>
#include <stdlib.h>

// Node structure
struct Node {
    int data;
    struct Node* next;
};

// Queue structure
struct Queue {
    struct Node *front, *rear;
};

// Function to create a new node
struct Node* createNode(int value) {
    struct Node* temp = (struct Node*)malloc(sizeof(struct Node));
    temp->data = value;
    temp->next = NULL;
    return temp;
}

// Initialize an empty queue
void initQueue(struct Queue* q) {
    q->front = q->rear = NULL;
}

// Enqueue function (insert at rear)
void enqueue(struct Queue* q, int value) {
    struct Node* temp = createNode(value);

    if (q->rear == NULL) {
        q->front = q->rear = temp;
        printf("%d inserted into the queue.\n", value);
        return;
    }

    q->rear->next = temp;
    q->rear = temp;
    printf("%d inserted into the queue.\n", value);
}

// Display the queue
void displayQueue(struct Queue* q) {
    struct Node* temp = q->front;
    if (temp == NULL) {
        printf("Queue is empty.\n");
        return;
    }

    printf("Queue elements: ");
    while (temp != NULL) {
        printf("%d ", temp->data);
        temp = temp->next;
    }
    printf("\n");
}

// Main function
int main() {
    struct Queue q;
    initQueue(&q);

    int choice, value;

    while (1) {
        printf("\n--- Menu ---\n");
        printf("1. Enqueue (Insert)\n");
        printf("2. Display Queue\n");
        printf("3. Exit\n");
        printf("Enter your choice: ");
        scanf("%d", &choice);

        switch (choice) {
            case 1:
                printf("Enter value to insert: ");
                scanf("%d", &value);
                enqueue(&q, value);
                break;
            case 2:
                displayQueue(&q);
                break;
            case 3:
                printf("Exiting program.\n");
                exit(0);
            default:
                printf("Invalid choice. Try again.\n");
        }
    }

    return 0;
}
```


Output:

![Screenshot 2025-04-29 215614](https://github.com/user-attachments/assets/0f1698ce-b263-4030-9fb5-47790829dfdd)


Result: Thus, the program to insert elements in queue using linked list is verified successfully.

EXP NO:30 C FUNCTION TO FIND THE PEEK OF QUEUE USING LINKED LIST.

Aim:

The aim of this function is to retrieve the "peek" (the front element) of a queue implemented using a linked list

Algorithm:

Check if the queue is empty: o If the queue is empty (i.e., the front pointer is NULL), return an error or a message indicating that the queue is empty.
Access the front element: o If the queue is not empty, return the data stored in the front node of the linked list (i.e., the element at the head of the queue).
Program:

```
#include <stdio.h>
#include <stdlib.h>

// Node structure
struct Node {
    int data;
    struct Node* next;
};

// Queue structure
struct Queue {
    struct Node *front, *rear;
};

// Create a new node
struct Node* newNode(int value) {
    struct Node* temp = (struct Node*)malloc(sizeof(struct Node));
    temp->data = value;
    temp->next = NULL;
    return temp;
}

// Initialize an empty queue
void initQueue(struct Queue* q) {
    q->front = q->rear = NULL;
}

// Enqueue operation
void enqueue(struct Queue* q, int value) {
    struct Node* temp = newNode(value);

    if (q->rear == NULL) {
        q->front = q->rear = temp;
        return;
    }

    q->rear->next = temp;
    q->rear = temp;
}

// Peek operation: return front element without removing it
int peek(struct Queue* q) {
    if (q->front == NULL) {
        printf("Queue is empty.\n");
        return -1; // or some error indicator
    }
    return q->front->data;
}

// Dequeue operation (optional for demonstration)
void dequeue(struct Queue* q) {
    if (q->front == NULL) {
        printf("Queue is empty.\n");
        return;
    }

    struct Node* temp = q->front;
    q->front = q->front->next;

    if (q->front == NULL)
        q->rear = NULL;

    free(temp);
}

// Main function to demonstrate
int main() {
    struct Queue q;
    initQueue(&q);

    enqueue(&q, 10);
    enqueue(&q, 20);
    enqueue(&q, 30);

    printf("Front element (peek): %d\n", peek(&q));

    dequeue(&q);
    printf("Front element after one dequeue: %d\n", peek(&q));

    return 0;
}
```

Output:


![Screenshot 2025-04-29 214704](https://github.com/user-attachments/assets/adae885f-1619-4ea4-b3c4-8bbbcd63b58b)


Result:

Thus, the program to retrieve the "peek" (the front element) of a queue implemented using a linked list is verified successfully.
