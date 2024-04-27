# Syntax for all loops in bash scripting

There are mainly 3 types of loops are present in bash scripting, They are,

- For loop
- While Loop
- Until Loop

## For Loop

There are diffenet types of for loops are present in bash script, They are

1. Simple for loop
2. Range based for loop
3. Array iteration for loops
4. C-Styled for loop
5. Infinite for loop

### 1. Simple for loop

**Syntax**

```bash
for <variable_name> in <list_of_items>;
do
    <some_commands>
done
```

**Sample Code**

```bash
#!/bin/bash
for i in 10 20 30
do
    echo $i
done
```

**sample Output**

![alt text](/images/Activity6/simpe_op.png)

### 2. Range based for loop

**Syntax**

```bash
for <variable_name> in <range_of_items>;
do
    <some_commands>
done
```

**Sample Code**

```bash
#!/bin/bash
for i in {1..10..2}
do
    echo $i
done
```

**Sample output**

![alt text](/images/Activity6/range_op.png)

### 3. Array iteration for loops

**Syntax**

```bash
for <variable_name> in <array_of_items>;
do
    <some_commands>
done
```

**Sample code**

```bash
#!/bin/bash
games=("cricket" "tennis" "vollyball" "basketball")
for game in ${games[@]}
do
    echo $game
done
```

**Sample output**

![alt text](/images/Activity6/array_op.png)

### 4. C-Styled for loop

**Syntax**

```bash
for (( <initialiser> ; <condition> ; <inc/dec> ))
do
    <some_commands>
done
```

**Sample Code**

```bash
#!/bin/bash
for (( i=0 ; i<5 ;i++ ))
do
    echo $i
done
```

**Sample screenshot**

![alt text](/images/Activity6/iterative_op.png)

### 5. Infinite for loop

**Syntax**

```bash
for (( ; ; ))
do
    <some_statements_with_break_condition>
done
```

**Sample code**

```bash
#!/bin/bash
n=4
for (( ; ; ));
do
	if [[ $n == 5 ]]
	then
		break
	fi
	((n++))
done
echo $n
```

**Smaple screenshot**

![alt text](/images/Activity6/infinite_op.png)

## While Loop

**Syntax**

```bash
while [[ <condition> ]];
do
    <statments>
done
```

**Sample code**

```bash
#!/bin/bash
n=0
while [[ n -lt 5 ]]
do
	echo $n
	(( n++ ))
done
```

**Smaple screenshot**

![alt text](/images/Activity6/iterative_op.png)

## Until Loop

```bash
until [[ <condition> ]];
do
    <statments>
done
```

**Sample code**

```bash
#!/bin/bashn=10
until [[ n -lt 5 ]]
do
	echo $n
	(( n-- ))
done
```

**Smaple screenshot**

![alt text](/images/Activity6/until_loop_op.png)
