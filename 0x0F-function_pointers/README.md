./main 21 | udcli -64 -x -o 4005f6 int b);`
			- `op_div` : returns the result of the division of `a` by `b`. Prototype: `int op_div(int a, int b);`
			- `op_mod` : returns the remainder of the division of `a` by `b`. Prototype: `int op_mod(int a, int b);`

		&nbsp;
		- [3-get\_op\_functions.c](./3-get_op_func.c) : This file should contain the function that selects the correct function to perform the operation asked by the user. You’re not allowed to declare any other function.
			- Prototype: `int (*get_op_func(char *s))(int, int);`
			- Where `s` is the operator passed as argument to the program.
			- This function returns a pointer to the function that corresponds to the operator given as a parameter. Example: `get_op_func("+")` should return a pointer to the function `op_add`.
			- You are not allowed to use `switch` statements.
			- You are not allowed to use `for` or `do ... while` loops.
			- You are not allowed to use `goto`
			- You are not allowed to use `else`
			- You are not allowed to use more than one `if` statement in your code.
			- You are not allowed to use more than one `while` loop in your code.
			- if `s` does not match any of the 5 expected operators (`+`, `-`, `*`, `/`, `%`), return `NULL`
			- You are only allowed to use declare these two variables in this function:
				```c
				op_t ops[] = {
					{"+", op_add},
					{"-", op_sub},
					{"*", op_mul},
					{"/", op_div},
					{"%", op_mod},
					{NULL, NULL}
				};
				int i;
				```

		&nbsp;
		- [3-main.c](./3-main.c) : This file should contain your main function only.
			- You are not allowed to code any other function than `main` in this file.
			- You are not allowed to directly call `op_add`, `op_sub`, `op_mul`, `op_div` or `op_mod` from the `main` function.
			- You have to use `atoi` to convert arguments to `int`,
			- You are allowed to use a maximum of 3 `if` statements.
	- Compile the code this way: `gcc -Wall -pedantic -Werror -Wextra -std=gnu89 3-main.c 3-op_functions.c 3-get_op_func.c -o calc`
4. [Most hackers are young because young people tend to be adaptable. As long as you remain adaptable, you can always be a good hacker](./100-main_opcodes.c) : A program that prints [opcodes](https://en.wikipedia.org/wiki/Opcode) of its own main function.
	- Usage: `./main number_of_bytes`
	- Output format:
		- The opcodes should be printed in hexadecimal, lowercase.
		- Each opcode is two char long
		- Listing ends with a new line
		- See example:
			```sh
			[...]
			00000000004005f6 <main>:
			4005f6:   55                      push   rbp
			4005f7:   48 89 e5                mov    rbp,rsp
			4005fa:   48 83 ec 30             sub    rsp,0x30
			4005fe:   89 7d dc                mov    DWORD PTR [rbp-0x24],edi
			400601:   48 89 75 d0             mov    QWORD PTR [rbp-0x30],rsi
			400605:   83 7d dc 02             cmp    DWORD PTR [rbp-0x24],0x2
			400609:   74 14                   je     40061f <main+0x29>
			[...]

			# --------------------------------------------------------------- #

			00000000004005f6 55               push rbp                
			00000000004005f7 4889e5           mov rbp, rsp            
			00000000004005fa 4883ec30         sub rsp, 0x30           
			00000000004005fe 897ddc           mov [rbp-0x24], edi     
			0000000000400601 488975d0         mov [rbp-0x30], rsi     
			0000000000400605 837ddc02         cmp dword [rbp-0x24], 0x2
			0000000000400609 7414             jz 0x40061f
			```
	- You are allowed to use `printf` and `atoi`
	- You have to use `atoi` to convert the argument to an `int`
	- If the number of argument is not the correct one, print `Error`, followed by a new line, and exit with the status of `1`
	- If the number of bytes is negative, print `Error`, followed by a new line, and exit with the status of 2.
	- You do not have to compile with any flags.
	- **NOTE:** if you want to translate your opcodes to assembly instructions, you can use, for instance `udcli`.
	- Compile the code this way: `gcc -std=gnu89 100-main_opcodes.c -o main1`
	- Run code this way: `./main1 21`
	- Test case 1: `objdump -d -j.text -M intel main1`
		- Then note the starting address of `<main>`
	- Test case 2: `./main1 21 | udcli -64 -x -o 4005f6`
		- `4005f6` is the starting address of `<main>`
	- **Note 0:** `je` is equivalent to `jz`
	- **Note 1:** Depending on how you write your `main` function, and on which machine you compile your program, the opcodes (and by extension the assembly code) might be different than the above example.

