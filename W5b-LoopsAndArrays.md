# Loops & Arrays

## My Code:
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
