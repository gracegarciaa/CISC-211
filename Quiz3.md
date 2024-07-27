# Quiz 3 

## My Code:
```
section .data
    number  dd 5       ; Pre-defined number for which we want to calculate factorial
    result  dd 0       ; Variable to store the result of the factorial

section .text
    global _start

_start:
    mov eax, [number]  ; load num into EAX
    
    ; initialize result = 1
    mov ebx, 1         ; EBX holds result
    mov ecx, eax       ; ECX = loop ctr
    
factorial_loop:
    imul ebx           ; EAX = EAX * EBX
    ; ctr-1
    dec ecx            ; ECX - 1
    ; Check if ECX is zero
    jz done            ; if ECX = 0, go to done
    ; else, continue loop
    jmp factorial_loop ; repeat loop

done:
    mov [result], ebx  ; store result in corresponding var
    
    ; exit prog
    mov eax, 1        
    xor ebx, ebx      
    int 0x80           
```

