# Compilers
Projects developed under the Compilers college chair during the 2018/2019 school year

## Project 1) Abstract syntax trees (ASTs)

Summary: Building ASTs for a language of arithmetic expressions involving integers. We start with "programs" defined by a single expression made of numbers and sum (+) operations.  
After parsing, the AST for a program is visited/interpreted to print values for expressions.

## Project 2) C to Assembly

Summary: Extend the previous project to work not only with numbers and sum operators and well as with a whole subset of the C language, including variable declaration and assignment, relational operators, loops, IO operations, etc. 
After this, the challenge is to convert a file written with a subset of the subset of the C code into a set of assemly instructions, kind of like a compiler, and return a working MIPS file as output.

Along with all the files regarding the work itself, I have added some files (example1.txt, example2.txt, etc...), which are some examples tested by us that exemplify the functioning of the parser, as well as the printing of the respective abstract syntax trees.

For example, by running the program for the following C code:

```C
fun main(){
int x = 0;
 while(x < 4) {
  while( y <= 5 && 4 > 3 ){
   scanf("%f",x);
   if(x - 4 >= y - 2){
     k = k + 12;
   }
   x = x + 1;
   int y = y + 1;
   printf("%d",x);
  }
 }
}
```

Returns the corresponding assembly code:
```assembly
.data
x: .word 4
y: .word 4

.text
li $a0,1
addiu $sp, $sp, -4
sw $a0, 0($sp)
lw $a0, 0($sp)
addiu $sp, $sp, 4
sw $a0, x
li $a0,5
addiu $sp, $sp, -4
sw $a0, 0($sp)
lw $a0, 0($sp)
addiu $sp, $sp, 4
sw $a0, y
Label_1:
lw $a0, x
addiu $sp, $sp, -4
sw $a0, 0($sp)
li $a0,20
addiu $sp, $sp, -4
sw $a0, 0($sp)
lw $t1, 0($sp)
addiu $sp, $sp, 4
lw $t0, 0($sp)
addiu $sp, $sp, 4
slt $a0, $t0, $t1
subu $a1, $t0, $t1
sltu $a1, $zero, $a1
xori $a1, $a1, 1
or $a0, $a0, $a1
addiu $sp, $sp, -4
sw $a0, 0($sp)
lw $a0, 0($sp)
addiu $sp, $sp, 4
beq $a0, $zero, Label_2
lw $a0, x
addiu $sp, $sp, -4
sw $a0, 0($sp)
li $a0,2
addiu $sp, $sp, -4
sw $a0, 0($sp)
lw $t1, 0($sp)
addiu $sp, $sp, 4
lw $a0, 0($sp)
addiu $sp, $sp, 4
div $a0, $t1
mfhi $a0
addiu $sp, $sp, -4
sw $a0, 0($sp)
li $a0,0
addiu $sp, $sp, -4
sw $a0, 0($sp)
lw $t1, 0($sp)
addiu $sp, $sp, 4
lw $a0, 0($sp)
addiu $sp, $sp, 4
subu $a0, $a0, $t1
sltu $a0, $zero, $a0
xori $a0, $a0, 1
addiu $sp, $sp, -4
sw $a0, 0($sp)
lw $a0, 0($sp)
addiu $sp, $sp, 4
beq $a0, $zero, Label_3
lw $a0, x
li $v0, 1
syscall
j Label_4
Label_3:
lw $a0, y
li $v0, 1
syscall
Label_4:
lw $a0, x
addiu $sp, $sp, -4
sw $a0, 0($sp)
li $a0,1
addiu $sp, $sp, -4
sw $a0, 0($sp)
lw $t1, 0($sp)
addiu $sp, $sp, 4
lw $a0, 0($sp)
addiu $sp, $sp, 4
add $a0, $a0, $t1
addiu $sp, $sp, -4
sw $a0, 0($sp)
lw $a0, 0($sp)
addiu $sp, $sp, 4
sw $a0, x
j Label_1
Label_2:
li $v0, 10
syscall
```
