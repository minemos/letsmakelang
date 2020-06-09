# Compiler

**Changing some language(Source Code) to other(Object Code)**  
| Code | Mean |  
|---|:---:|
| Source Code | `Code(File etc..) that Before Compile` |  
| Object Code | `Code(File etc..) that After Compile` |

<br>

>For Example, in C  
>**Source Code** can be helloworld.c, **Object Code** can be helloworld.exe

<br>

## History

Long ago, Program was wirtten in **Assembly**.  
```assembly
org 100h
mov ax, 0b800h
mov ds, ax
mov cl, 'A'
mov ch, 11011111b
mov bx, 15eh
mov [bx], cx
ret
```
>Assembly Tutorial : https://github.com/gurugio/book_assembly_8086 

But **Assembly Code** was changed by cpu architecture, It cause many cost.  
~~coding -> deploy -> new cpu -> coding again~~  
So High-level Progamming Language was needed, In 1950 first High-level language and compiler came out

<br>

## How Compiler Working?

1. Syntax Parse

Breaking code from **Source Code** with each language syntax(Operator, Identifier etc..)  
Then make Abstract Syntax Tree(AST)

2. Optimization

Optimization from Abstract Syntax Tree(AST)  
(Finding unused variable, unreachable code etc..)

**Below Code is example for understanding. NOT REAL**
```javascript
let a = true;

if(a == false) console.log("a is false"); // can't reach
if(a == true) console.log("a is true"); // always reach here

console.log(3+(7*10)/10);
```
This code gonna be..
```javascript
console.log("a is true");

console.log(10);
```

3. Generate Object Code

Make Object Code After Optimization  
If Object Code is **Machine Language**, run hardware optimization like Register Allocation

![wikipedia picture](https://upload.wikimedia.org/wikipedia/commons/b/b0/Chaitin_et_al.%27s_iteravite_graph_coloring_based_register_allocator.png "From wikipedia")
>Register Allocation : https://en.m.wikipedia.org/wiki/Register_allocation

4. Linking(Only Machine Language)

Linker make one execute file with library
> Someone skip this in compiler. ~~I dont know why~~

<br>

### Etc

Native Compiler(Hosted Compiler) : Make Object Code execute in same environment(develop in window, compile to exe)

Cross Compiler : Make Object Code execute in different environment(develop in x86, compile to arm execute file)

Bytecode Compiler : Make Object Code run in Virtual Machine (like java)

JIT(Just In Time) Compile : Before execute, change Bytecode to Platform Machine Code
> Virtual Machine is slower than Platform Machine Code
