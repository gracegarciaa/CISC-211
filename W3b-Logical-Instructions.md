# Logical Instructions

## My Code:
```
section .data
    operand db 0xAA  ; to test

section .text
    global _start

_start:
    mov al, [operand]   ; load operand into AL register
    test al, al         ; perform test instruction

    jz zero_detected    ; if zero flag is set --> AL == 0

    ; if not 0 --> perform other operations here
    mov ebx, 1          ; exit if not 0

    ; exit  program
    mov eax, 1          ; syscall number for exit
    int 0x80            ; call kernel

zero_detected:
    mov ebx, 0          ; exit if 0

    ; exit  program
    mov eax, 1          ; syscall number for exit
    int 0x80            ; call kernel
```

## Flowchart:
[click here] (https://drive.google.com/file/d/1lokkci9BNA7yzcOaujrvUoByNlnNi9cX/view?usp=sharing)

## Challenges:
I think the most difficult part about this assignment was that I had to do a lot of my own research on the logical instructions, which is how I ended up using the zero_detected method. It is generally just difficult for me when it comes to implementing in general.
