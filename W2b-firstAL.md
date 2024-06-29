# First Assembly Language Program

## My Code:
```
section .data
    message1 db 'I came, ', 0
    message2 db 'I saw, ', 0
    message3 db 'I conquered.', 0

section .text
    global _start

_start:
; Print New Line message1
    mov eax, 4       ; syscall number for sys_write
    mov ebx, 1       ; file descriptor 1 (stdout)
    mov ecx, message1 ; pointer to the message
    mov edx, 8       ; message length
    int 0x80         ; make syscall
; Print New Line message2
    mov eax, 4       ; syscall number for sys_write
    mov ebx, 1       ; file descriptor 1 (stdout)
    mov ecx, message2 ; pointer to the message
    mov edx, 8       ; message length
    int 0x80         ; make syscall
; Print New Line message3
    mov eax, 4       ; syscall number for sys_write
    mov ebx, 1       ; file descriptor 1 (stdout)
    mov ecx, message3 ; pointer to the message
    mov edx, 12      ; message length
    int 0x80         ; make syscall

    ; Exit the program
    mov eax, 1       ; syscall number for sys_exit
    xor ebx, ebx     ; exit status 0
    int 0x80         ; make syscall
```

## Flowchart:
[click here] (https://drive.google.com/file/d/1xgi83xrAAUf00ci1JURQzf98mitIjnkJ/view?usp=sharing)
