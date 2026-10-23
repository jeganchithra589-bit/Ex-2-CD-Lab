# AIM
## To write a lex program to implement lexical analyzer to recognize a few patterns.
# ALGORITHM

1.	Start the program.

2.	Lex program consists of three parts.

     a.	Declaration %%

     b.	Translation rules %%

     c.	Auxilary procedure.

3.	The declaration section includes declaration of variables, maintest, constants and regular definitions.
4.	Translation rule of lex program are statements of the form

    a.	P1 {action}

    b.	P2 {action}

    c.	…

    d.	…

    e.	Pn {action}

5.	Write a program in the vi editor and save it with .l extension.

6.	Compile the lex program with lex compiler to produce output file as lex.yy.c. eg $ lex filename.l $ cc lex.yy.c
7.	Compile that file with C compiler and verify the output.

# Program

```
#include <stdio.h>
#include <ctype.h>
#include <string.h>

int main()
{
    char s[100];
    int i = 0;

    printf("Enter the input: ");
    fgets(s, sizeof(s), stdin);

    while (s[i] != '\0')
    {
        if (isspace(s[i]))
        {
            i++;
        }
        else if (isalpha(s[i]) || s[i] == '_')
        {
            printf("Identifier: ");
            while (isalnum(s[i]) || s[i] == '_')
                printf("%c", s[i++]);
            printf("\n");
        }
        else if (isdigit(s[i]))
        {
            printf("Number: ");
            while (isdigit(s[i]))
                printf("%c", s[i++]);
            printf("\n");
        }
        else if (strchr("+-*/=", s[i]))
        {
            printf("Operator: %c\n", s[i]);
            i++;
        }
        else
        {
            printf("Special Symbol: %c\n", s[i]);
            i++;
        }
    }

    return 0;
}
```

# INPUT

input a = 10 + 20

# OUTPUT

<img width="885" height="517" alt="image" src="https://github.com/user-attachments/assets/7b122954-430a-4b88-baa4-9526b829e729" />

# RESULT
## The lexical analyzer is implemented using lex and the output is verified.
