# Activity File Management

## My Code:
```
SECTION .text
global  _start
 
_start:
 
        mov     ecx, 0711o ; set all permissions to read, write, execute (octal format)
        mov     ebx, filename       ; filename we will create
        mov     eax, 8              ; invoke SYS_CREAT (kernel opcode 8)
        int     0x80                ; call the kernel

        mov     eax,1
        int     0x80

SECTION .data
filename db 'readme.txt', 0h    ; the filename to create
```

```
SECTION .data
    filename db 'quotes.txt', 0   ; filename
    contents1 db 'To be, or not to be, that is the question.', 0xA  ; 1st quote
    contents2 db 'A fool thinks himself to be wise, but a wise man knows himself to be a fool.', 0xA  ; 2nd quote
    contents3 db 'Better three hours too soon than a minute too late.', 0xA  ; 3rd quote
    contents4 db 'No legacy is so rich as honesty.', 0xA  ; 4th quote

SECTION .text
    global _start

_start:
    mov     ecx, 0711o ; set all permissions to read, write, execute 
    mov     ebx, filename       ; filename we will create
    mov     eax, 8              ; invoke SYS_CREAT (kernel opcode 8)
    int     0x80                ; call the kernel

    mov     eax,1
    int     0x80

    ; open file
    mov eax, 5          ; syscall number for sys_open
    mov ebx, filename   ; pointer to filename
    mov ecx, 0101o      ; flags: O_CREAT | O_WRONLY
    mov edx, 0777o      ; mode: rwxrwxrwx
    int 0x80            ; call kernel

    mov [fd_out], eax   ; store file descriptor

    ; write first 2 lines
    mov eax, 4          ; syscall number for sys_write
    mov ebx, [fd_out]   ; file descriptor
    mov ecx, contents1  ; pointer to 1st line
    mov edx, 50         ; num of bytes to write
    int 0x80            ; call kernel

    mov eax, 4          
    mov ebx, [fd_out]  
    mov ecx, contents2  
    mov edx, 93        
    int 0x80           

    ; use sys_lseek to move file pointer to end
    mov eax, 19         
    mov ebx, [fd_out]  
    mov ecx, 0          ; offset value = 0 
    mov edx, 2          ; ref position = 2 (end of file)
    int 0x80           

    ; write other 2 lines
    mov eax, 4          
    mov ebx, [fd_out]  
    mov ecx, contents3  ; pointer to 3rd line
    mov edx, 48       
    int 0x80           

    mov eax, 4          
    mov ebx, [fd_out]   
    mov ecx, contents4  ; pointer to 4th line
    mov edx, 35        
    int 0x80            

    ; close file
    mov eax, 6          
    mov ebx, [fd_out]  
    int 0x80            

    ; exit prog
    mov eax, 1          
    xor ebx, ebx      
    int 0x80           

SECTION .bss
    fd_out resb 1       ; reserve space for file descriptor
```

## Challenges:
For me, the most challenging part was appending the 3rd and 4th quote. It was mainly difficult dealing with the offset value and the reference position on top keeping track of the pointer.
