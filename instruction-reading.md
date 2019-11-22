| Line | Label | Instruction | Meaning |
| --- | --- | --- | --- |
| 1 |`value:`| |
| 2 | |        `.word   13`| `value` is of size word and has starting value 13|
| 3 |`negate:`| |
| 4 | |`sub     sp, sp, #8`| Decrement the stack pointer by 8 |
| 5 | |`str     r0, [sp, #4]`| Store register r0 to the stack position at stack pointer + 4|
| 6 | |`ldr  r3, [sp, #4]`| Load into register r3 the value of the stack pointer + 4|
| 7 | |`rsbs     r3, r3 #0`| the condition flags are updated on the result of the operation. subtracts the value of r3 from 2 and stores it back in r3 |
| 8 | |`movs    r0, r3`| Copy r3 to r0 |
| 9 | |` add     sp, sp, #8`| Add the value of 8 to stack pointer |
| 10 | |` bx      lr`| branch the exchange|
| 11 | |`main:`| |
| 12 | |` push    {r4, lr}`|Push registers r4 and `lr` onto the stack.|
| 13 |`ldr     r3, .L6`|Load the address that is generated in r3 to the label `.L6`|
| 14 | |`ldr     r3, [r3]`|Load the value at [r3] into r3.|
| 15 | |` cmp     r3, #0`|Compare the value of r3 with 0 |
| 16 | |`ble     .L4`| branch to '.L4' if less than|
| 17 | |` ldr     r3, .L6`| loads '.L6' into r3|
| 18 | |`ldr     r3, [r3]`| loads [r3] into r3|
| 19 | |` movs    r0, r3`|Copy r3 to r0 |
| 20 | |`bl      negate`| branch with link to 'negate' |
| 21 | |`movs    r2, r0`| Copy the value of r0 to r2.|
| 22 | |`ldr     r3, .L6`|same as line 17 |
| 23 | |`str     r2, [r3]`| Store r2 at [r3].|
| 24 |`.L4:` || |
| 25 | |`movs    r3, #0| Write 0 in r3. |
| 26 | | movs    r0, r3 | Copy r3 to r0 |
| 27 | |`pop     {r4, pc}`| Pop from the stack into r4 and `pc`.|
| 28 |`.L6:` | | |
| 29 | |`.word   value`| |

