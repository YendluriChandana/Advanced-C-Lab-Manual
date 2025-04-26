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
