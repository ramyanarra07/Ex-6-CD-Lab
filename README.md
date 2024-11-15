# Ex-6-IMPLEMENTATION-OF-THE-BACK-END-OF-THE-COMPILER-
IMPLEMENTATION OF THE BACK END OF THE COMPILER 
# Date : 10-11-2024
# Developed by: NARRA RAMYA
# Register number: 212223040128
# Aim :
To write a program to implement the back end of the compiler.
# ALGORITHM
1. Start the program.
2. Get the three variables from statements and stored in the text file k.txt.
3. Compile the program and give the path of the source file.
4. Execute the program.
5. Target code for the given statement is produced.
6. Stop the program.
# PROGRAM
k.txt
```
X=b-c
Y=b-d
Z=b+c
D=b-c
D=b+c
```
EX6.c
```
#include <stdio.h>
#include <string.h>

int main() {
    char line[50], op1[5], op2[5], res[5], op;
    FILE *fp = fopen("k.txt", "r");
    
    if (fp == NULL) {
        printf("Error opening file.\n");
        return 1;
    }

    printf("Statement\tTarget Code\n");

    int reg = 0;
    while (fgets(line, sizeof(line), fp)) {
        sscanf(line, "%[^=]=%[^+-]%c%s", res, op1, &op, op2);

        printf("%s=%s%c%s\t", res, op1, op, op2);
        
        if (op == '-') {
            printf("MOV %s,R%d SUB %s SUB %s,R%d\n", op1, reg, op1, op2, reg);
        } else if (op == '+') {
            printf("MOV %s,R%d ADD %s ADD %s,R%d\n", op1, reg, op1, op2, reg);
        }
        reg++;
    }
    
    fclose(fp);
    return 0;
}

```
# OUTPUT
![image](https://github.com/user-attachments/assets/713328f8-bbed-447d-bc80-1c29d8fa59ae)

# Result
The back end of the compiler is implemented successfully, and the output is verified.
