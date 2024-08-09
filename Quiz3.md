# Quiz 3 

## My Code:
```
section .data
    number dq 5              ; num to compute fact of
    result dq 1              ; result var

section .text
    global _start

_start:
    ; load numb into rax reg
    mov rax, [number]        ; rax = num
    mov rbx, rax            ; loop ctr
    mov rcx, 1              ; initial result)

factorial_loop:
    imul rcx, rbx           ; rcx = rcx * rbx
    dec rbx                 ; decrement rbx
    jnz factorial_loop      ; if rbx != 0 --> continue loop

    ; store result in mem
    mov [result], rcx

    ; exit prog
    mov rax, 60            
    xor rdi, rdi           
    syscall
```
