# Final Project

## Iterative:
```
; counter.asm
section .data
    filename db 'counter_fun.txt', 0
    filemode  db 0x41        
    buffer db '0000000000', 10 ; buffer for output & newline

section .bss
    file_descriptor resd 1   ; 

section .text
    global _start

_start:
    ; open file in append mode
    mov eax, 5              
    mov ebx, filename       
    mov ecx, filemode      
    mov edx, 0666          
    int 0x80                
    mov [file_descriptor], eax ; save file descriptor

    ; set ctr
    mov ecx, 20000        

print_loop:
    ; convert num --> str
    mov eax, ecx            ; load ctr val
    mov ebx, buffer + 10    ; end of buffer
    mov [ebx], 0           
    dec ebx                 ; move to last digit place

convert_loop:
    xor edx, edx            ; clear edx
    div dword [ten]         ; eax / 10
    add dl, '0'             ; convert to ASCII
    mov [ebx], dl           
    dec ebx                 ; move to next digit place
    test eax, eax           ; check if quotient = zero --> continue if not
    jnz convert_loop       

    ; write num to file
    mov eax, 4             
    mov ebx, [file_descriptor] 
    lea ecx, [ebx + 1]   
    mov edx, 10
    int 0x80              

    ; write newline to file
    mov eax, 4              
    mov ebx, [file_descriptor] 
    lea ecx, [buffer + 10] 
    mov edx, 1            
    int 0x80              

    dec ecx                 ; decrease ctr
    jnz print_loop          ; if != zero --> continue loop 

    ; close file
    mov eax, 6             
    mov ebx, [file_descriptor] 
    int 0x80               

    mov eax, 1            
    xor ebx, ebx           
    int 0x80                

section .data
ten dd 10                 
```

```
nasm -f elf32 -o counter.o counter.asm
ld -m elf_i386 -o counter counter.o
```

```
time ./counter >> counter_fun.txt 2>&1
```

## Recursive:
```
; counter_rec.asm
section .data
    filename db 'counter_rec.txt', 
    filemode  db 0x41        
    buffer db '0000000000', 10 ; buffer for output & newline

section .bss
    file_descriptor resd 1  

section .text
    global _start

_start:
    ; open file in append mode
    mov eax, 5              
    mov ebx, filename       
    mov ecx, filemode      
    mov edx, 0666         
    int 0x80               
    mov [file_descriptor], eax ; save file descriptor

    ; set ctr
    mov ecx, 20000          
    call print_counter

    ; close file
    mov eax, 6         
    mov ebx, [file_descriptor] 
    int 0x80               

    ; exit
    mov eax, 1              
    xor ebx, ebx           
    int 0x80                

; recursive function (print ctr)
print_counter:
    ; if ecx = 0 --> return
    test ecx, ecx
    jz .done

    ; call print_counter with ecx - 1
    push ecx                ; save current ct
    dec ecx                 ; decrease ctr
    call print_counter      
    pop ecx                

    ; convert cum --> str
    mov eax, ecx            ; load ctr val
    mov ebx, buffer + 10    ; end of buffer 
    mov [ebx], 0         
    dec ebx                 

convert_loop:
    xor edx, edx            ; clear edx 
    div dword [ten]         ; eax / 10
    add dl, '0'             ; convert to ASCII
    mov [ebx], dl         
    dec ebx                 ; move to next digit place
    test eax, eax           ; check if quotient = 0 --> continue if not
    jnz convert_loop       

    ; write num to file
    mov eax, 4            
    mov ebx, [file_descriptor]
    lea ecx, [ebx + 1]
    mov edx, 1             
    int 0x80               

    ; write newline to file
    mov eax, 4             
    mov ebx, [file_descriptor] 
    lea ecx, [buffer + 10] 
    mov edx, 1            
    int 0x80             

.done:
    ret

section .data
ten dd 10                 
```

```
nasm -f elf32 -o counter_rec.o counter_rec.asm
ld -m elf_i386 -o counter_rec counter_rec.o
```

```
time ./counter_rec >> counter_rec.txt 2>&1
```

## Comparison:

### Iterative: 
This version has a fixed amount of stack space because it uses a loop, so I think it will be more efficient than the recursive version because you don't have to keep calling the function.

### Recursive:
With this version, each call adds a frams to the stack so this would be a lot less efficient when working with bigger numbers. Since we have to repeatedly call the function, I think this will make the program run a lot slower more often than not.

## Flowchart:
[click here] (https://drive.google.com/file/d/1OgpX07aK60ROGSZwoqA8h8U5_l8rw4N7/view?usp=sharing)

## Video:
[click here] (insert link)
