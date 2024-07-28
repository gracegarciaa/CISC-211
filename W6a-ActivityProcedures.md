# Activity Procedures

## My Code:
```
section .data
    newline db 0xA        ; new line

section .text
    global _start

_start:
    mov ecx, 65 ; initialize loop var to ASCII value 'A'

print_loop:
    ; print current char
    mov eax, 4       
    mov ebx, 1        
    mov edx, 1 ; num bytes to write (1)
    mov [buffer], cl ; move current char into buffer
    lea esi, [buffer] ; load buffer address --> ESI
    int 0x80          

    ; print newline
    mov eax, 4        
    mov ebx, 1         
    lea edx, [newline] ; newline address
    mov edx, 1        
    int 0x80          

    inc cl ; move to next char
    cmp cl, 91 ; compare current char w/ 'Z' + 1
    jl print_loop ; loop if char < 'Z' + 1

    ; exit prog
    mov eax, 1        
    xor ebx, ebx      
    int 0x80          

section .bss
    buffer resb 1 ; reserve 1 byte for char buffer
```

## Flowchart:
[click here] (https://drive.google.com/file/d/1bDEWQIPggj_lOd1TsWZJqVtCA9RnBgz4/view?usp=sharing)

## Challenges:
The most difficult about this activity was the loops for me, they're fairly different from loops in java so I feel like I'm still trying to get used to them.
