# VLSI_RISC-V_Internship


## Task 1

Writing the code for sum of first n natural numbers and compiling  it with gcc compiler


![Screenshot 2024-12-23 193505](https://github.com/user-attachments/assets/c0d48825-af7e-4849-b3f0-0a79efd75959)

Next we will compile the code 'Karthik.c' in the RISC-V compiler.

Using option '-O1'


![Screenshot 2024-12-23 193505](https://github.com/user-attachments/assets/e15068fb-4d26-45e1-81f8-85d7838f133f)


The address of the main section is 10184(Hex) and we got 11 instructions.

![Screenshot 2024-12-23 120531](https://github.com/user-attachments/assets/b03f8d19-353c-4ee6-b21e-0ac9b6f14342)

Using option '-Ofast'


![Screenshot 2024-12-23 193533](https://github.com/user-attachments/assets/daf64f20-2f0b-44b6-a035-2c4b228079e9)

The address of the main section is 100B0(Hex) and we got 11 instructions.

![Screenshot 2024-12-23 121009](https://github.com/user-attachments/assets/eef49bd5-903d-4e00-bc37-c7c9c1ef08f3)


## Task 2

Simulation using Spike Tool

![image](https://github.com/user-attachments/assets/0498acd6-e3f4-4b28-b588-c4ad9208f986)

Assembly language code of the  **Karthik.c**

![Screenshot 2024-12-27 233158](https://github.com/user-attachments/assets/93744059-1723-4cf5-bd5b-109b7f423fb5)

Debugging using Spike Tool

![Screenshot 2024-12-27 234223](https://github.com/user-attachments/assets/bf5c8694-9e93-4622-bf44-69272f02c9fc)

![Screenshot 2024-12-27 234450](https://github.com/user-attachments/assets/3645e820-d77c-4547-a502-322aba5bdbec)


### Example 

Factorial code using recursion

```
#include<stdio.h>
 int Fact(int n);
int main() {
    int n;
    printf("Enter a positive integer: ");
    scanf("%d",&n);
    printf("Factorial of %d = %d", n, Fact(n));
    return 0;
}

 int Fact(int n) {
    if (n>=1)
        return n*Fact(n-1);
    else
        return 1;
}
```
Simulation of  **Factorial.c** by GCC complier & Spike tool

![Screenshot 2024-12-28 001554](https://github.com/user-attachments/assets/6ec93f23-8a3a-4f55-b57a-bb292dd017e6)

Assembly language code of the  **Factorial.c**

![Screenshot 2024-12-27 235736](https://github.com/user-attachments/assets/23cb3ce1-c835-4f2f-93b0-c4905ed2d49b)

The address of the main section is 100b0 (Hexadecimal) and got 34 instructions

Debugging using Spike Tool

![Screenshot 2024-12-27 235903](https://github.com/user-attachments/assets/23326adb-5a32-4d67-8c1a-55e9ef8d28bf)

