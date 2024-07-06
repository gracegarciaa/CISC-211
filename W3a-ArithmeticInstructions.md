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

## Flowchart:
[click here] (insert link)

## Challenges:

