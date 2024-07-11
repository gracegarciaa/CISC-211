# Coding Practice

## Standard Deviation:
```
section .data
    array    db  60, 70, 90, 40, 65   ; arr of student scores
    count    equ $ - array            ; # of elements in arr
    mean     dd  0                    ; mean of arr
    sumsq    dd  0                    ; sum of squares

section .text
    global _start

_start:
    ; calc mean
    mov     ecx, count               ; ecx = # of elements
    xor     eax, eax                 ; clear eax for sum
    xor     edx, edx                 ; clear edx for index
    lea     esi, [array]             ; esi = start of arr
    
mean_loop:
    movzx   ebx, byte [esi + edx]    ; ebx = current element
    add     eax, ebx                 ; add current element to sum
    inc     edx                      ; increment index
    loop    mean_loop                ; loop until ecx = 0
    
    mov     ebx, count               ; ebx = # of elements
    mov     ecx, eax                 ; ecx = sum
    cdq                              ; clear edx, prepare for division
    idiv    ebx                      ; divide sum by # of elements
    mov     [mean], eax              ; store mean
    
    ; calc sum of squares
    xor     eax, eax                 ; clear eax for sum of squares
    xor     edx, edx                 ; clear edx for index
    lea     esi, [array]             ; esi = start of arr
    
sumsq_loop:
    movzx   ebx, byte [esi + edx]    ; ebx = current element
    sub     ebx, [mean]              ; subtract mean from current element
    imul    ebx, ebx                 ; square  difference
    add     eax, ebx                 ; add squared difference to sum
    inc     edx                      ; increment index
    loop    sumsq_loop               ; loop until all elements processed
    
    mov     [sumsq], eax             ; store sum of squares
    
    ; calc standard dev
    mov     ebx, count               ; ebx = # of elements
    mov     ecx, [sumsq]             ; ecx = sum of squares
    cdq                              ; clear edx
    idiv    ebx                      ; divide sum of squares by # of elements
    fsqrt                            ; calc sqrt 
    
    ; exit prog
    mov     eax, 1                  
    xor     ebx, ebx                 
    int     0x80                     
```

## Binary Conversion
```
575/2 = 287 R1
287/2 = 143 R1
143/2 = 71 R1
71/2 = 35 R1
35/2 = 17 R1
17/2 = 8 R1
8/2 = 4 R0
4/2 = 2 R0
2/2 = 1 R0
1/2 = 0 R1

575 = 1000111111 in binary
```

## Hexadecimal Conversion:
```
575/16 = 35 R15 (F)
35/16 = 2 R3
2/16 = 0 R 2

575 = 23F in hexidecimal
```

## Code Errors:
```
- need to declare 'result' in .data section
- resb 1 not usually used to hold a # directly
```

## Cache Memory:
```
Index	V	Tag	Data
1	    1	101	0111
0	    1	100	0000
3	    1	111	0101
```
