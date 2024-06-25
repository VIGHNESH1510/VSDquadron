# TASK 1
## INSTALLATION OF LEAFPAD

  ![Screenshot (246)](https://github.com/VIGHNESH1510/VSDquadron/assets/173612404/1a8e93c0-b6fa-4997-b354-19470a26b43e)


## TO WRITE A C CODE TO FIND THE SUM OF N NUMBERS
   + open the ubunto terminal.
   + type the command **leafpad filename.c &** to open the leafpad.
   + write the c code to find the sum of N numbers.
   + for compiling, use the command **gcc filename.c** and the output can be displayed using the command **./a.out**.
     
     ![image](https://github.com/VIGHNESH1510/VSDquadron/assets/173612404/0d0b9cb8-f300-41ac-8e4f-1569828e57d0)

     
## CONVERSION OF C CODE TO INSTRUCTION SET
   + to create a  O file use the command **riscv64-unknown-elf-gcc -O1 -mabi=lp64 -march=rv64i -o sum1ton.o sum1ton.c**
   + and then type **ls -ltr sum1ton.o**
   + we can the see the instruction set using the command **risc64-unknown-elf-objdump -d sum1ton.o**

     ![Screenshot (255)](https://github.com/VIGHNESH1510/VSDquadron/assets/173612404/f56cca63-b262-433b-aba4-7b895487db30)

     when we replace the **-O1** with **Ofast** we can observe that the number of instructions set will be reduced.

     ![Screenshot (258)](https://github.com/VIGHNESH1510/VSDquadron/assets/173612404/36a73ba3-18ba-45d1-a039-6427b900744b)


