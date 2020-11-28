# bomb lab
# [GDB Cheatsheet](http://users.ece.utexas.edu/~adnan/gdb-refcard.pdf)
# [GDB Cheatsheet 2](https://darkdust.net/files/GDB%20Cheat%20Sheet.pdf)
# phase_1
## Check Assembly Code of Main function
```bash
# objdump -d bomb
400da0: 53                           	pushq	%rbx
  400da1: 83 ff 01                     	cmpl	$1, %edi
  400da4: 75 10                        	jne	16 <main+0x16>
  400da6: 48 8b 05 9b 29 20 00         	movq	2107803(%rip), %rax
  400dad: 48 89 05 b4 29 20 00         	movq	%rax, 2107828(%rip)
  400db4: eb 63                        	jmp	99 <main+0x79>
  400db6: 48 89 f3                     	movq	%rsi, %rbx
  400db9: 83 ff 02                     	cmpl	$2, %edi
  400dbc: 75 3a                        	jne	58 <main+0x58>
  400dbe: 48 8b 7e 08                  	movq	8(%rsi), %rdi
  400dc2: be b4 22 40 00               	movl	$4203188, %esi
  400dc7: e8 44 fe ff ff               	callq	-444 <fopen@plt>
  400dcc: 48 89 05 95 29 20 00         	movq	%rax, 2107797(%rip)
  400dd3: 48 85 c0                     	testq	%rax, %rax
  400dd6: 75 41                        	jne	65 <main+0x79>
  400dd8: 48 8b 4b 08                  	movq	8(%rbx), %rcx
  400ddc: 48 8b 13                     	movq	(%rbx), %rdx
  400ddf: be b6 22 40 00               	movl	$4203190, %esi
  400de4: bf 01 00 00 00               	movl	$1, %edi
  400de9: e8 12 fe ff ff               	callq	-494 <__printf_chk@plt>
  400dee: bf 08 00 00 00               	movl	$8, %edi
  400df3: e8 28 fe ff ff               	callq	-472 <exit@plt>
  400df8: 48 8b 16                     	movq	(%rsi), %rdx
  400dfb: be d3 22 40 00               	movl	$4203219, %esi
  400e00: bf 01 00 00 00               	movl	$1, %edi
  400e05: b8 00 00 00 00               	movl	$0, %eax
  400e0a: e8 f1 fd ff ff               	callq	-527 <__printf_chk@plt>
  400e0f: bf 08 00 00 00               	movl	$8, %edi
  400e14: e8 07 fe ff ff               	callq	-505 <exit@plt>
  400e19: e8 84 05 00 00               	callq	1412 <initialize_bomb>
  400e1e: bf 38 23 40 00               	movl	$4203320, %edi
  400e23: e8 e8 fc ff ff               	callq	-792 <puts@plt>
  400e28: bf 78 23 40 00               	movl	$4203384, %edi
  400e2d: e8 de fc ff ff               	callq	-802 <puts@plt>
  400e32: e8 67 06 00 00               	callq	1639 <read_line>
  400e37: 48 89 c7                     	movq	%rax, %rdi
  400e3a: e8 a1 00 00 00               	callq	161 <phase_1>
  400e3f: e8 80 07 00 00               	callq	1920 <phase_defused>
  400e44: bf a8 23 40 00               	movl	$4203432, %edi
  400e49: e8 c2 fc ff ff               	callq	-830 <puts@plt>
  400e4e: e8 4b 06 00 00               	callq	1611 <read_line>
  400e53: 48 89 c7                     	movq	%rax, %rdi
  400e56: e8 a1 00 00 00               	callq	161 <phase_2>
  400e5b: e8 64 07 00 00               	callq	1892 <phase_defused>
  400e60: bf ed 22 40 00               	movl	$4203245, %edi
  400e65: e8 a6 fc ff ff               	callq	-858 <puts@plt>
  400e6a: e8 2f 06 00 00               	callq	1583 <read_line>
  400e6f: 48 89 c7                     	movq	%rax, %rdi
  400e72: e8 cc 00 00 00               	callq	204 <phase_3>
  400e77: e8 48 07 00 00               	callq	1864 <phase_defused>
  400e7c: bf 0b 23 40 00               	movl	$4203275, %edi
  400e81: e8 8a fc ff ff               	callq	-886 <puts@plt>
  400e86: e8 13 06 00 00               	callq	1555 <read_line>
  400e8b: 48 89 c7                     	movq	%rax, %rdi
  400e8e: e8 79 01 00 00               	callq	377 <phase_4>
  400e93: e8 2c 07 00 00               	callq	1836 <phase_defused>
  400e98: bf d8 23 40 00               	movl	$4203480, %edi
  400e9d: e8 6e fc ff ff               	callq	-914 <puts@plt>
  400ea2: e8 f7 05 00 00               	callq	1527 <read_line>
  400ea7: 48 89 c7                     	movq	%rax, %rdi
  400eaa: e8 b3 01 00 00               	callq	435 <phase_5>
  400eaf: e8 10 07 00 00               	callq	1808 <phase_defused>
  400eb4: bf 1a 23 40 00               	movl	$4203290, %edi
  400eb9: e8 52 fc ff ff               	callq	-942 <puts@plt>
  400ebe: e8 db 05 00 00               	callq	1499 <read_line>
  400ec3: 48 89 c7                     	movq	%rax, %rdi
  400ec6: e8 29 02 00 00               	callq	553 <phase_6>
  400ecb: e8 f4 06 00 00               	callq	1780 <phase_defused>
  400ed0: b8 00 00 00 00               	movl	$0, %eax
  400ed5: 5b                           	popq	%rbx
  400ed6: c3                           	retq
  400ed7: 90                           	nop
  400ed8: 90                           	nop
  400ed9: 90                           	nop
  400eda: 90                           	nop
  400edb: 90                           	nop
  400edc: 90                           	nop
  400edd: 90                           	nop
  400ede: 90                           	nop
  400edf: 90                           	nop
```

## Solution
It's easy to figure out that the input is passed to the address `$rax` points to. We can also infer that when we call `phase_1` , the parameters passed to `strings_not_equal` are `$rdi` and `$rsi`. `$rdi` points to the data we input and `$rsi` points to the data we will compare with. We can print out the content at `$rsi` , which is the solution.

Solution is:
> Border relations with Canada have never been better.

# phase_2
## Check Assembly Code of phase_2 function
```
0000000000400efc phase_2:
  400efc: 55                            pushq %rbp
  400efd: 53                            pushq %rbx
  400efe: 48 83 ec 28                   subq  $40, %rsp
  400f02: 48 89 e6                      movq  %rsp, %rsi
  400f05: e8 52 05 00 00                callq 1362 <read_six_numbers>
  400f0a: 83 3c 24 01                   cmpl  $1, (%rsp)
  400f0e: 74 20                         je  32 <phase_2+0x34>
  400f10: e8 25 05 00 00                callq 1317 <explode_bomb>
  400f15: eb 19                         jmp 25 <phase_2+0x34>
  400f17: 8b 43 fc                      movl  -4(%rbx), %eax
  400f1a: 01 c0                         addl  %eax, %eax
  400f1c: 39 03                         cmpl  %eax, (%rbx)
  400f1e: 74 05                         je  5 <phase_2+0x29>
  400f20: e8 15 05 00 00                callq 1301 <explode_bomb>
  400f25: 48 83 c3 04                   addq  $4, %rbx
  400f29: 48 39 eb                      cmpq  %rbp, %rbx
  400f2c: 75 e9                         jne -23 <phase_2+0x1b>
  400f2e: eb 0c                         jmp 12 <phase_2+0x40>
  400f30: 48 8d 5c 24 04                leaq  4(%rsp), %rbx
  400f35: 48 8d 6c 24 18                leaq  24(%rsp), %rbp
  400f3a: eb db                         jmp -37 <phase_2+0x1b>
  400f3c: 48 83 c4 28                   addq  $40, %rsp
  400f40: 5b                            popq  %rbx
  400f41: 5d                            popq  %rbp
  400f42: c3                            retq
```
## Solution
We can see that a function called `read_six_numbers` get called, so we can infer that we need six numbers here. Please also remember `scanf` function use space as the default delimeter between inputs so we should use space between each number and the system will realize we are input multiple numbers here.

Analysing the code in `read_six_numbers`:
```
000000000040145c read_six_numbers:
  40145c: 48 83 ec 18                   subq  $24, %rsp
  401460: 48 89 f2                      movq  %rsi, %rdx
  401463: 48 8d 4e 04                   leaq  4(%rsi), %rcx
  401467: 48 8d 46 14                   leaq  20(%rsi), %rax
  40146b: 48 89 44 24 08                movq  %rax, 8(%rsp)
  401470: 48 8d 46 10                   leaq  16(%rsi), %rax
  401474: 48 89 04 24                   movq  %rax, (%rsp)
  401478: 4c 8d 4e 0c                   leaq  12(%rsi), %r9
  40147c: 4c 8d 46 08                   leaq  8(%rsi), %r8
  401480: be c3 25 40 00                movl  $4203971, %esi
  401485: b8 00 00 00 00                movl  $0, %eax
  40148a: e8 61 f7 ff ff                callq -2207 <__isoc99_sscanf@plt>
  40148f: 83 f8 05                      cmpl  $5, %eax
  401492: 7f 05                         jg  5 <read_six_numbers+0x3d>
  401494: e8 a1 ff ff ff                callq -95 <explode_bomb>
  401499: 48 83 c4 18                   addq  $24, %rsp
  40149d: c3                            retq
```
We can see that in `phase_2` we let `rsi=rsp`, and we let `movl $4203971, %esi`(`$4203981` points to the format string for input). When we return to `phase_2` at `400f0a`, we can infer that the function is trying to checking each number, and from `0x400f30` we can also infer that the function is checking each number a time, and make sure the current number is twice as the previous number.

Solution is:
> 1 2 4 8 16 32

# phase_3
## Solution
`phase_3` also ask us to input 2 numbers, separated by a space.

Analysing the code in `phase_3`
```
0x0000000000400f43 <+0>:  sub    $0x18,%rsp
 0x0000000000400f47 <+4>: lea    0xc(%rsp),%rcx
 0x0000000000400f4c <+9>: lea    0x8(%rsp),%rdx
 0x0000000000400f51 <+14>:  mov    $0x4025cf,%esi
 0x0000000000400f56 <+19>:  mov    $0x0,%eax
 0x0000000000400f5b <+24>:  callq  0x400bf0 <__isoc99_sscanf@plt>
 0x0000000000400f60 <+29>:  cmp    $0x1,%eax
 0x0000000000400f63 <+32>:  jg     0x400f6a <phase_3+39>
 0x0000000000400f65 <+34>:  callq  0x40143a <explode_bomb>
 0x0000000000400f6a <+39>:  cmpl   $0x7,0x8(%rsp)
 0x0000000000400f6f <+44>:  ja     0x400fad <phase_3+106>
 0x0000000000400f71 <+46>:  mov    0x8(%rsp),%eax
 0x0000000000400f75 <+50>:  jmpq   *0x402470(,%rax,8)
 0x0000000000400f7c <+57>:  mov    $0xcf,%eax
 0x0000000000400f81 <+62>:  jmp    0x400fbe <phase_3+123>
 0x0000000000400f83 <+64>:  mov    $0x2c3,%eax
 0x0000000000400f88 <+69>:  jmp    0x400fbe <phase_3+123>
 0x0000000000400f8a <+71>:  mov    $0x100,%eax
 0x0000000000400f8f <+76>:  jmp    0x400fbe <phase_3+123>
 0x0000000000400f91 <+78>:  mov    $0x185,%eax
 0x0000000000400f96 <+83>:  jmp    0x400fbe <phase_3+123>
 0x0000000000400f98 <+85>:  mov    $0xce,%eax
 0x0000000000400f9d <+90>:  jmp    0x400fbe <phase_3+123>
 0x0000000000400f9f <+92>:  mov    $0x2aa,%eax
 0x0000000000400fa4 <+97>:  jmp    0x400fbe <phase_3+123>
 0x0000000000400fa6 <+99>:  mov    $0x147,%eax
 0x0000000000400fab <+104>: jmp    0x400fbe <phase_3+123>
 0x0000000000400fad <+106>: callq  0x40143a <explode_bomb>
 0x0000000000400fb2 <+111>: mov    $0x0,%eax
 0x0000000000400fb7 <+116>: jmp    0x400fbe <phase_3+123>
 0x0000000000400fb9 <+118>: mov    $0x137,%eax
 0x0000000000400fbe <+123>: cmp    0xc(%rsp),%eax
 0x0000000000400fc2 <+127>: je     0x400fc9 <phase_3+134>
 0x0000000000400fc4 <+129>: callq  0x40143a <explode_bomb>
 0x0000000000400fc9 <+134>: add    $0x18,%rsp
 0x0000000000400fcd <+138>: retq   
```
We can see that after calling `__isoc99_sscanf` at `0x400f5b`, we check if the input is grater than 1 by checking the return value in `$eax`. After that, we will also check if the first input(`8(%rsp)`) is greater than 7, if not, we will proceed to `jmpq` function. Note the expression here is `*0x402470(,%rax,8)`, this equals to `*(0x400270 + 8 * $rax)`, which is to retrieve the value stored at that specific location. In this case, we need to make sure the first number is 1, so that we can jump to `0x400fb9`.
The solution is:
> 1 311

# phase_4
## Solution
We take the same strategy, which is to examine the assembly code of `phase_4` and `func4`, we found that the function is asking for two numbers. We also find out that the first number should be 7 so that we can pass `cmpl %edi, %ecx` in `func4`, and we also find out that the second parameter should be 0 so that we can pass `phase_4`.

Solution is:
> 7 0

