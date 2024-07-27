# Activity Functions

## My Code:
```
section .data
    even_msg db 'even', 0xA, 0x0   ; displays if num = even
    odd_msg  db 'odd', 0xA, 0x0    ; displays if num = odd
    len_even  equ $ - even_msg      ; length of even msg
    len_odd   equ $ - odd_msg       ; length of odd msg

section .bss
    num resb 4                      ; reserves 4-byte space for num

section .text
    global _start

_start:
    ; Assign a number to the register
    mov eax, 7      ; example num
    
    call check_even_odd
    
    ; exit prog
    mov eax, 1     
    xor ebx, ebx   
    int 0x80      

check_even_odd:
    ; calc remainder for eax / 2
    mov ebx, 2     
    xor edx, edx    ; clear edx
    div ebx         ; eax = eax / ebx, edx = eax % ebx
    
    ; check if edx = 0
    cmp edx, 0      ; compare remainder w/ 0
    je even         ; if 0 --> num = even

    ; !0 --> num = odd
    ; print odd
    mov eax, 4     
    mov ebx, 1      
    mov ecx, odd_msg
    mov edx, len_odd
    int 0x80      
    ret             ; return

even:
    ; print even
    mov eax, 4      
    mov ebx, 1    
    mov ecx, even_msg
    mov edx, len_even
    int 0x80      
    ret             ; return
```

## Flowchart:
[click here] (https://drive.google.com/file/d/1tw7sFglaVeow32UI74EGQaEkSK8apG0J/view?usp=sharing)

## Challenges:

Overall this assignment was simple and easy to follow. It was interesting trying to find out how to display the messages, but not very difficult.
