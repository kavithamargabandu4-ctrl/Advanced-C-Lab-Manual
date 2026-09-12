EXP NO:1 C PROGRAM FOR ARRAY OF STRUCTURE TO CHECK ELIGIBILITY FOR THE VACCINE.

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
Program:
#include <stdio.h>

struct eligible
{
    int age;
    char n[50];
};

int main()
{
    struct eligible e[1];

    scanf("%d", &e[0].age);
    scanf("%s", e[0].n);

    if (e[0].age <= 6)
        printf("Vaccine Eligibility: No\n");
    else
        printf("Vaccine Eligibility: Yes\n");

    printf("Age: %d\n", e[0].age);
    printf("Name: %s\n", e[0].n);

    return 0;
}
Example Input

10
Kavitha
Output

Vaccine Eligibility: Yes
Age: 10
Name: Kavitha
Result: Thus, the program is verified successfully.
EXP NO:2 C PROGRAM FOR PASSING STRUCTURES AS FUNCTION ARGUMENTS AND RETURNING A STRUCTURE FROM A FUNCTION Aim: To write a C program for passing structure as function and returning a structure from a function

Algorithm:

Define structure numbers with members a and b.
Declare variable n of type numbers.
Prompt the user to enter values for a and b.
Input values for a and b into n using scanf.
Call the add function with n as an argument.
Print the result returned by the add function.
Return 0
Program:
#include <stdio.h>

struct numbers
{
    int a;
    int b;
};

struct numbers add(struct numbers n)
{
    struct numbers result;
    result.a = n.a + n.b;
    return result;
}

int main()
{
    struct numbers n, result;

    printf("Enter two numbers: ");
    scanf("%d %d", &n.a, &n.b);

    result = add(n);

    printf("Sum = %d", result.a);

    return 0;
}
Sample Output:
Enter two numbers: 10 20
Sum = 30

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
```c
#include <stdio.h>

int main()
{
    FILE *p;
    char name[50];

    printf("Enter the file name: ");
    scanf("%s", name);

    p = fopen(name, "w");

    if (p == NULL)
    {
        printf("File creation failed");
        return 1;
    }

    printf("File created successfully");
    printf("\nFile opened successfully");

    fclose(p);

    printf("\nFile closed successfully");

    return 0;
}
Example Output:


Enter the file name: sample.txt
File created successfully
File opened successfully
File closed successfully
Result: Thus, the program is verified successfully

EXP NO:4 PROGRAM TO READ A FILE NAME FROM USER, WRITE THAT FILE AND INSERT TEXT IN TO THAT FILE Aim: To write a C program to read, a file and insert text in that file Algorithm:

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
```c
#include <stdio.h>

int main()
{
    FILE *p;
    char name[50], text[100];
    int num, i;

    printf("Enter the file name: ");
    scanf("%s", name);

    printf("Enter the number of strings: ");
    scanf("%d", &num);

    p = fopen(name, "w");

    if (p == NULL)
    {
        printf("File opening failed");
        return 1;
    }

    printf("File opened successfully\n");

    for (i = 0; i < num; i++)
    {
        printf("Enter string %d: ", i + 1);
        scanf(" %[^\n]", text);
        fputs(text, p);
        fputs("\n", p);
    }

    fclose(p);

    printf("Data added successfully");

    return 0;
}
```
Example Output:


Enter the file name: sample.txt
Enter the number of strings: 3
File opened successfully
Enter string 1: Hello
Enter string 2: Welcome to C
Enter string 3: File handling
Data added successfully
The file sample.txt will contain:


Hello
Welcome to C
File handling
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

```c
#include <stdio.h>
#include <stdlib.h>

struct subject
{
    char name[50];
    int marks;
};

int main()
{
    struct subject *s;
    int n, i;

    printf("Enter the number of subjects: ");
    scanf("%d", &n);

    s = (struct subject *)malloc(n * sizeof(struct subject));

    if (s == NULL)
    {
        printf("Memory allocation failed");
        return 1;
    }

    for (i = 0; i < n; i++)
    {
        printf("Enter subject name: ");
        scanf("%s", s[i].name);

        printf("Enter marks: ");
        scanf("%d", &s[i].marks);
    }

    printf("\nStudent Details:\n");

    for (i = 0; i < n; i++)
    {
        printf("Subject: %s\n", s[i].name);
        printf("Marks: %d\n", s[i].marks);
    }

    free(s);

    return 0;
}
```
Example Output:


Enter the number of subjects: 3
Enter subject name: Maths
Enter marks: 90
Enter subject name: Physics
Enter marks: 85
Enter subject name: C
Enter marks: 95

Student Details:
Subject: Maths
Marks: 90
Subject: Physics
Marks: 85
Subject: C
Marks: 95

Result: Thus, the program is verified successfully

