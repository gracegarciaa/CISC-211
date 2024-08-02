# Loops & Arrays

## My Code:

Part 1:
```
section .text
        global _start

_start:
        mov ebx,0       ; reset ebx = 0
label:
        inc ebx
        cmp ebx,10
        jl label        ;jump if less

        mov eax,1       
        xor ebx, ebx    
        int 0x80

; findings --> the code initializes the ebx register to 0 then increments it in a loop until it reaches 10. After the loop finishes, it exits the with code 0.
```

Part 2:
```
section .bss
sum resd 1        ; reserve space for sum

section .text
    global _start

_start:
    ; initialize vars
    mov eax, 0    ; Fibonacci(0)
    mov ebx, 1    ; Fibonacci(1)
    mov ecx, 10   ; ctr for first 10 fib nums
    mov edi, 0    ; hold sum of fib nums
    
    ; initialize sum
    mov [sum], edi
    
    ; calculate fib nums & sum
loop_fib:
    add edi, eax  ; add current fib to sum
    mov [sum], edi
    add eax, ebx  ; generate next num
    xchg eax, ebx ; swap eax & ebx to update sequence
    loop loop_fib ; loop until all 10 nums have been processed

   
    mov eax, 1    
    xor ebx, ebx  
    int 0x80      
```

Part 3:
```
section .data
    array:  dd 4, 8, 2, 10  ; define arr of ints 

section .text
    global _start

_start:
    ; initialize vars & registers

    ; find largest element in arr
    mov eax, [array]      ; load 1st element into eax
    mov ecx, 1            ; initialize ctr
    mov edx, eax          ; initialize edx to store max value

find_max_loop:
    cmp ecx, 4            ; compare loop counter w/ arr length (4 elements)
    jge end_find_max      ; if ecx >= 4 --> exit loop

    mov ebx, [array + ecx * 4]  ; load arr element into ebx
    cmp ebx, edx                ; compare ebx w/ edx (current max)
    jle skip_update             ; if ebx <= edx, don't update edx
    mov edx, ebx                ; update edx w/ ebx (new max)

skip_update:
    inc ecx               ; increment loop ctr
    jmp find_max_loop     ; go back to find_max_loop

end_find_max:
    ; ffter loop completes, edx should contain largest element in arr

    mov eax, 1    ; syscall num for exit
    xor ebx, ebx  ; exit status (0)
    int 0x80      ; syscall
```

## Flowchart:
[click here] (https://drive.google.com/file/d/1SQ7e-bsNJgCWsmjLGXxsn-Wa34aL4Xge/view?usp=sharing

## Challenges:
This lab was pretty straightforward, but I found the fibonacci numbers challenging because I had to figure out that the 11th number was 55.
