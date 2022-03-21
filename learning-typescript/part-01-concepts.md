## Part 1 Concepts

### Chapter 1 From Javascript to Typescript

javascript was originally designed in days by Brendan Eich to be approchable and easyto use for websites. Javascript has maintain backwards compatibility for decades in varying environments, including browsers embedded applications and server runtimes. 

Problems with Javascript? 

- **Costly Freedom**: no restriction. You never know what is getting to be passed in as a parameter
- **Loose documentation:** nothing describes what parameters, function does. You can use JSDoc, however, it’s difficult in refactoring, can be wrong, describe complex object is annoying.

Typescript hence is introduced in 2010 by Microsoft and open sourced in 2012. Known as “superset of JavaScript” or “Javascript with Types”.

- It contains: type checker, compiler and language services (VS code)
- It provides extensive language services: say you type the name of a class, then by knowing the type of the class, you can also figure out the member of the class.

Typescript, however, is slower than javascript due to extra transpilation work done. 

> **Compiler:** is an umbrella term to describe a program that takes source code written in one language and produce a (or many) output file in some other language.
> 

 In practice we mostly use this term to describe a compiler such as gcc which takes in C code as input and produces a binary executable (machine code) as output.

> **Transpilers** are also known as source-to-source compilers. So in essence they are a **subset** of compilers which take in a source code file and convert it to another **source code file** in some other language or a different version of the same language.
> 

The ouput is generally understandable by a human. This output still has to go through a compiler or interpreter to be able to run on the machine.

Starting Locally, 

```bash
npm install -g typescript 
# Samething as 
# npm i -g typescript (g is global install flag)
```

Then do  the following to set up a setting file tsconfig.json file that declares the settings that TypeScript uses when analyzing your code. 

```bash
tsc --init
```

### **NOTE**

Creating a `index.ts` gave me an equivalent `index.js` file.

This is an important concept: even though there was a *type error* in our code, the *syntax* was still completely valid. The TypeScript compiler will still attempt to produce JavaScript from an input file’s syntax regardless of any type errors.

![Screen Shot 2022-03-19 at 12.50.27 PM.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/901ec8a2-417e-4c89-b19f-f7771d559c3a/Screen_Shot_2022-03-19_at_12.50.27_PM.png)

Running `tsc index.ts` gave me me a `index.js` file that actually corresponds to the index.ts file content. 

### Chapter 2. The Type System

A type is a description of what a JavaScript value shape might be. By shape I mean how a value looks and feels: its properties and methods, and what the built-int typeof operator would describe it as. 

Basic types in typescript (the basic 7 primitive types in typescript) 

```tsx
bigint
boolean
null 
number 
string 
symbol 
undefined 
```

When you do something like 

```tsx
let singer = "Aretha"
```

Tyescript will figure out that the initial value “Aretha” 

- TypeScript best practice is generally to refer to the lower-case names, such as `boolean` and `number`

**Type Inferences in Details:**

1. Reading in your code and understanding all the types and values in existence 
2. For each object, seeing what type its initial declaration indicates it may contain 
3. For each object, seeing all wyas its used later on 
4. Complaining to the user if an object usage doesnt match with this type 

Two most frequently seen errors is 

1. **Syntax:** blocking typeScript from being convereted to Javascript (incorrect javascript syntax) 
2. **Type:** something mismatched has been detected by the type checker

**Type Annotations**

```tsx
let rocker: string;
rocker = "Joan Jett"
```

Above is a code snippet of doing anontation. However, typescript knows how to infer type, thus in the following case 

```tsx
let rocker: string = "stuff"; // unnessecssary type annotation
```

### Chapter 3. Unions and Narrowing

**Unions:** Expanding a value’s allowed type to be two or more possible types 

- Typescript does this by using `I`
- `let thinker: boolena | string = false`
- Order does not matter
- function that exists for both/all the types will be allowed to be called

**Narrowing:** Reducing a value’s allowed type to not be one or more possible types 

- Done by doing checks/ or direct assignment; TypeScript will understand that while the variable may later receive a value of any of the union typed values
- One of the simplest ways to get TypeScript to narrow a variable’s value without assigning the value yourself is to do a if statement check, like

```tsx
if (typeof scientist === "string"){
	// Do sth
}
```