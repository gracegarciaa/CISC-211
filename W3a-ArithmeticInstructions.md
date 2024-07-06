# Arithmetic Instructions

## My Code:
### result = -var1 * 10

```
section .data
    var1    dd  20       
    result  dd  0        ; result will be stored here

section .text
    global _start

_start:
    ; load var1 into eax
    mov eax, [var1]

    ; make eax negative (eax = -var1)
    neg eax

    ; multiply eax by 10 (eax = -var1 * 10)
    imul eax, 10

    ; store the result in memory location result
    mov [result], eax

    ; exit the program
    mov eax, 1        ; system call for exit
    xor ebx, ebx      ; exit status 0
    int 0x80          ; call kernel

section .bss
```

### result = var1 + var2 + var3 + var4

```
section .data
    var1    dd  10     
    var2    dd  20    
    var3    dd  30     
    var4    dd  40  

section .text
    global _start

_start:
    ; load var1, var2, var3, var4 into registers
    mov eax, [var1]   
    mov ebx, [var2]  
    mov ecx, [var3]   
    mov edx, [var4]   

    ; add var1,2,3,4 together
    add eax, ebx       ; eax += ebx (eax = var1 + var2)
    add eax, ecx       ; eax += ecx (eax = var1 + var2 + var3)
    add eax, edx       ; eax += edx (eax = var1 + var2 + var3 + var4)


    ; exit the program
    mov ebx, 0         ; exit status
    mov eax, 1         ; syscall number for exit
    int 0x80           ; make syscall

section .bss
```

### result = (-var1 * var2) +var3

```
section .data
    var1_addr   dd  0x11223344    ; example memory addresses
    var2_addr   dd  0x55667788    
    var3_addr   dd  0x99AABBCC    
    result_addr dd  0x0            ; memory address to store result (initialized to 0)

section .text
    global _start

_start:
    ; load var1 into register eax
    mov eax, dword [var1_addr]

    ; load var2 into register ebx
    mov ebx, dword [var2_addr]

    ; load var3 into register ecx
    mov ecx, dword [var3_addr]

    ; perform (-var1 * var2) + var3
    neg eax         ; negate var1 (eax = -var1)
    imul eax, ebx   ; multiply var2 with -var1 (eax = -var1 * var2)
    add eax, ecx    ; add var3 to the result (eax = (-var1 * var2) + var3)

    ; store the result back to memory
    mov dword [result_addr], eax

    ; exit program
    mov eax, 1      ; system call for exit
    xor ebx, ebx    ; return 0 status
    int 0x80        ; make syscall
```

### result = (var1 * 2)/(var2-3)

```
section .data
    var1_addr   dd  8      
    var2_addr   dd  5       
    result_addr dd  0       ; initialize result to 0

section .text
    global _start

_start:
    ; load var1 into register eax
    mov eax, dword [var1_addr]

    ; load var2 into register ebx
    mov ebx, dword [var2_addr]

    ; double var1 (eax = var1 * 2)
    shl eax, 1       

    ; (ebx = var2 - 3)
    sub ebx, 3       ; ebx = ebx - 3

    ; divide var1 * 2 by (var2 - 3)
    cdq              
    idiv ebx       

    ; store the result back to memory
    mov dword [result_addr], eax

    ; exit program
    mov eax, 1       ; system call for exit
    xor ebx, ebx     ; return 0 status
    int 0x80         ; make syscall

```

## Flowchart:
[click here] (https://drive.google.com/file/d/1wuI3gCXvi5aW4xVITkQJ21n22gPY6oU1/view?usp=sharing)

## Challenges:
The most challenging part about this assignment was learning how to apply the instructions to suit each equation. The first equation, for example, took me a little longer to figure out how to make a variable negative. So manipulating them was difficult for me in the beginning. But it slowly got easier over time.

