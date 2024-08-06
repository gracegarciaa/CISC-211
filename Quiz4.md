# Quiz 4

## My Code:
```
section .data
    ; define & initialize vars
    x dd 5          ; x = 5
    y dd 10         ; y = 10
    z dd 15         ; z = 15
    result dd 0     ; result var

section .text
    global _start

_start:
    ; load var address into registers
    mov eax, [x]    ; x --> eax
    mov ebx, [y]    ; y --> ebx
    mov ecx, [z]    ; z --> ecx

    ; call function
    call add_nums

    ; store into result variable
    mov [result], eax

    ; exit prog
    mov eax, 1      
    xor ebx, ebx    
    int 0x80       

add_numbers:
    add eax, ebx    ; eax = eax + ebx
    add eax, ecx    ; eax = eax + ecx

    ; returns: eax - result of x + y + z
    ret
```
