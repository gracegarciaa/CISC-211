# Final Project

## Iterative:
```
// counter.c
#include <stdio.h>
#include <stdlib.h>
#include <time.h>

void count(int n) {
    FILE *file = fopen("counter_fun.txt", "a");
    if (file == NULL) {
        perror("Failed to open file");
        exit(EXIT_FAILURE);
    }

    for (int i = 0; i <= n; ++i) {
        fprintf(file, "%d\n", i);
    }

    fclose(file);
}

int main(int argc, char *argv[]) {
    if (argc != 2) {
        fprintf(stderr, "Usage: %s <number>\n", argv[0]);
        return EXIT_FAILURE;
    }

    int n = atoi(argv[1]);
    if (n <= 0) {
        fprintf(stderr, "Please provide a positive integer.\n");
        return EXIT_FAILURE;
    }

    count(n);

    return EXIT_SUCCESS;
}
```

```
gcc -o counter counter.c
```

```
time ./counter 20000 >> counter_fun.txt 2>&1
```

## Recursive:
```
// counter_rec.c
#include <stdio.h>
#include <stdlib.h>

void count_recursive(int n, int current) {
    if (current > n) {
        return;
    }
    
    FILE *file = fopen("counter_rec.txt", "a");
    if (file == NULL) {
        perror("Failed to open file");
        exit(EXIT_FAILURE);
    }

    fprintf(file, "%d\n", current);
    fclose(file);

    count_recursive(n, current + 1);
}

int main(int argc, char *argv[]) {
    if (argc != 2) {
        fprintf(stderr, "Usage: %s <number>\n", argv[0]);
        return EXIT_FAILURE;
    }

    int n = atoi(argv[1]);
    if (n <= 0) {
        fprintf(stderr, "Please provide a positive integer.\n");
        return EXIT_FAILURE;
    }

    count_recursive(n, 0);

    return EXIT_SUCCESS;
}
```

```
gcc -o counter_rec counter_rec.c
```

```
time ./counter_rec 20000 >> counter_rec.txt 2>&1
```

## Comparison:

# Iterative: 
This version has a fixed amount of stack space because it uses a loop, so I think it will be more efficient than the recursive version because you don't have to keep calling the function.

# Recursive:
With this version, each call adds a frams to the stack so this would be a lot less efficient when working with bigger numbers. Since we have to repeatedly call the function, I think this will make the program run a lot slower more often than not.

## Flowchart:
[click here] (insert link)

## Challenges:

