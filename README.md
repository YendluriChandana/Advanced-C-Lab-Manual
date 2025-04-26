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
