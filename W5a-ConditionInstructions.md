# Condition Instructions

## My Code:
```
#!/bin/bash

# initialize var
num1=0
num2=0
num3=0
num4=0
num5=0

# generate sequence of even num up to 20
for (( i=2; i<=20; i+=2 )); do
    case $((i % 2)) in
        0)
            num1=$i
            ;;
        1)
            num2=$i
            ;;
    esac
done

# find largest num of the 5 initialized var
largest=$num1

if [ $num2 -gt $largest ]; then
    largest=$num2
fi

if [ $num3 -gt $largest ]; then
    largest=$num3
fi

if [ $num4 -gt $largest ]; then
    largest=$num4
fi

if [ $num5 -gt $largest ]; then
    largest=$num5
fi

# output largest num
echo "The largest number among $num1, $num2, $num3, $num4, and $num5 is: $largest"
```

## Flowchart:
[click here] (https://drive.google.com/file/d/17-UVJIa2ZiXJ1DgAZTolIN_0rn8To-Zm/view?usp=sharing)

## Challenges:
This lab was fairly straight forward so I did not have many challenges with it. However, I think I mostly struggle when it comes to syntax and using different programs with slightly different rules.
