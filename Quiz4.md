# Quiz 4

## My Code:
```
section .data
    ; define & initialize vars
    x dd 5          ; Integer x = 5
    y dd 10         ; Integer y = 10
    z dd 15         ; Integer z = 15
    result dd 0     ; Variable to store the result

section .text
    global _start

_start:
    ; load var address into registers
    mov eax, [x]    ; Load x into eax
    mov ebx, [y]    ; Load y into ebx
    mov ecx, [z]    ; Load z into ecx

    ; call function
    call add_nums

    ; store into result variable
    mov [result], eax

    ; exit prog
    mov eax, 1      
    xor ebx, ebx    
    int 0x80       

; add_nums function
; eax - x
; ebx - y
; ecx - z

add_numbers:
    ; add nums
    add eax, ebx    ; eax = eax + ebx
    add eax, ecx    ; eax = eax + ecx

    ; returns: eax - result of x + y + z
    ret
```
