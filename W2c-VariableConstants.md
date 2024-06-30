# Variables & Constants

## My Code:
```
section .text
        global _start

_start:
        ;use this space for the main body of your program
   	;======== write your code below ===========
   			    ; Load var1 into eax
    mov eax, [var1]

    ; Load var2 into ebx
    mov ebx, [var2]

    ; Add var1 and var2
    add eax, ebx

    ; Store the result in result variable
    mov [result], eax

    ; Print the result
    mov eax, 4           ; syscall number for sys_write
    mov ebx, 1           ; file descriptor 1 (stdout)
    mov ecx, result      ; pointer to the result variable
    mov edx, 4           ; message length (4 bytes for a dword)
    int 0x80             ; make syscall
   	;======== write your code above ===========
        
        mov eax,1	;set eax register to 1 (do not remove this line)
        int 0x80	;interrupt 0x80 (do not remove this line)

segment .bss
        ;use this space for uninitialized variable (result)

segment .data
	;use this space for initialized variables (var1 and var2)

; Exit the program
    mov eax, 1           ; syscall number for sys_exit
    xor ebx, ebx         ; exit status 0
    int 0x80             ; make syscall
```

## Flowchart:
[click here] (https://drive.google.com/file/d/1OL70pMT824nTxboUkvQraIknhl9IEBVf/view?usp=sharing)

## Challenges:
I think my biggest challenges with learning assembly is that the commands are similar yet still different from when we wrote java in intellijay. I'm still getting used to the syntax and just the process of running the code in general.
