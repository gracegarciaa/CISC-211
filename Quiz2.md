# Quiz 2

## My Code:
```
section .data
    a dd 5      ; a = 5
    b dd 10     ; b = 10
    c dd 2      ; c = 2
    d dd 3      ; d = 3
    x dd 0      ; x = 0 

section .text
    global _start

_start:
    mov eax, [a]  ; a --> eax
    mov ebx, [b]  ; b --> ebx
    imul eax, ebx ; eax = a * b
    
    mov ecx, [c]  ; c --> ecx
    mov edx, [d]  ; d --> edx
    imul ecx, edx ; ecx = c * d

    add eax, ecx  ; eax = (a * b) + (c * d)

    mov [x], eax  ; store result in x

    ; exit prog 
    mov eax, 1    
    xor ebx, ebx  
    int 0x80     
```
