# simplif-ai

> A pseudolanguage to describe code for LLMs

## simplif-ai v0.1.2

### Overview

simplif-ai is a language designed for efficient token usage and easy transpilation into other programming languages, such as JavaScript, TypeScript, JSX/TSX, and Python. It is particularly suitable for usage with large language models (LLMs) like GPT-4.

### Syntax

#### Keywords and Symbols

- `imp`: Import multiple modules in one statement.
- `func`: Declare a function.
- `obj`: Declare an object type.
- `arr`: Declare an array type.
- `val`: Declare a value.
- `int`: Declare an integer type.
- `str`: Declare a string type.
- `bool`: Declare a boolean type.
- `ret`: Return a value.
- `exp`: Export a module or value.
- `key`: Define a key for elements in an array.
- `if`: Conditional statement.
- `else`: Alternate branch for a conditional statement.
- `for`: Iterate over a range or collection.
- `while`: Loop while a condition is true.
- `try`: Enclose a block of code that might raise an exception.
- `catch`: Handle exceptions raised in the try block.
- `throw`: Raise an exception.
- `class`: Define a class.
- `extends`: Inherit properties and methods from another class.
- `struct`: Define a constructor method for a class.
- `super`: Call the constructor of the parent class.

#### Delimiters

- `;`: End a statement, expression, or function.

### Language Features

- Compact syntax and efficient token usage.
- Declarative naming conventions.
- Transpiles to JavaScript, TypeScript, JSX/TSX, and Python with best practices.
- Can be used for a wide range of programming tasks, including array manipulations, filtering, sorting, and object-oriented programming.

### Transpilation

To transpile simplif-ai code into another programming language, call the `transpile` function with the desired output language as an argument.

Examples:

```
transpile(tsx)

imp React,useState,useMemo
func ComplexArray():obj arr[obj]data=[{id:1,val:15},{id:2,val:2},{id:3,val:7},{id:4,val:30},{id:5,val:4}]
arr[obj]filtered=useMemo(()=>data.filter(i=>i.val>5).sort((a,b)=>if(a.id%2===0&b.id%2===0)ret a.val-b.val
if(a.id%2!==0&b.id%2!==0)ret b.val-a.val ret a.id%2===0?-1:1);,[data])
ret div(ul(filtered.map((i)=>li(key(i.id),'ID: '+i.id+', Value: '+i.val)));)
exp default ComplexArray

```

GPT-3.5-turbo

```tsx
import React, { useState, useMemo } from "react";

function ComplexArray() {
  const data = [
    { id: 1, val: 15 },
    { id: 2, val: 2 },
    { id: 3, val: 7 },
    { id: 4, val: 30 },
    { id: 5, val: 4 },
  ];

  const filtered = useMemo(
    () =>
      data
        .filter((i) => i.val > 5)
        .sort((a, b) =>
          a.id % 2 === 0 && b.id % 2 === 0
            ? a.val - b.val
            : a.id % 2 !== 0 && b.id % 2 !== 0
            ? b.val - a.val
            : a.id % 2 === 0
            ? -1
            : 1
        ),
    [data]
  );

  return (
    <div>
      <ul>
        {filtered.map((i) => (
          <li key={i.id}>
            {"ID: " + i.id + ", Value: " + i.val}
          </li>
        ))}
      </ul>
    </div>
  );
}

export default ComplexArray;
```
