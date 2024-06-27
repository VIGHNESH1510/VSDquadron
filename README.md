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
     __________

# TASK 2
## To write a C Program for Clock Divider Circuit And Compile it to RISC File
A Clock Divider Circuit is used to divide the operating frequency of the clock based on the Division Factor In relative to the Master Clock.
## The below image is the C Program for the Clock Divider Circuit along with its output value,

![WhatsApp Image 2024-06-25 at 16 39 08_c085d847](https://github.com/VIGHNESH1510/VSDquadron/assets/173612404/7b939c39-26a9-4b0a-8612-7d52c6d6e2f8)

## The Assembly code for the Clock Divider Circuit,

![WhatsApp Image 2024-06-25 at 16 39 06_1e5f4607](https://github.com/VIGHNESH1510/VSDquadron/assets/173612404/2d3b5771-8c12-4315-b58f-0d4518d3b0a9)

## The Reduced Assembly Code for the Clock Divider Circuit,

![WhatsApp Image 2024-06-25 at 16 39 06_f0126ef9](https://github.com/VIGHNESH1510/VSDquadron/assets/173612404/6d6327ca-4a32-448a-bc8c-7efff0dff4ae)
________

## TASK 3
## ANALYSES OF THE  C CODE USING THE SPIKE 
   + To compile the C code for clock Divider in risc using the **spike**, we use the commands

     ``` js
         riscv64-unknown-elf-gcc -Ofast -mabi=lp64 -march=rv64i -o clockdivider.o clockdivider.c
         spike pk clockdivider.o
     ```
     
  + we may verify the output of the risc compiler with the output of the C code
    
![Screenshot 2024-06-27 142805](https://github.com/VIGHNESH1510/VSDquadron/assets/173612404/0992ced2-0868-4bfe-a9c5-2d39dd365671)

+ To debug the Assembly code we use the command

``` js
    spike -d pk clockdivider.o
    until pc 0 100b0
```

+ To read the contents in instruction 

  ``` js
      reg 0 a0
  ```
![Screenshot 2024-06-27 123634](https://github.com/VIGHNESH1510/VSDquadron/assets/173612404/dd01ae40-fea6-45c3-be07-5911332ccc85)

  ______



