---
comments: true
title: Lua (5.1) for World of Warcraft (3.3.5a)
date: 2026-04-19 12:00:00
image:
    path: /assets/img/images_alphawow/LuaPreview.png
math: true
categories: [Machine Learning, Reinforcement Learning]
tags: [machine-learning, reinforcement-learning]
---

### Lua Naming Conventions Summary

|     **Category**     |               **Convention**               |
| :------------------: | :----------------------------------------: |
| **Local Variables**  |      `lowerCamelCase` or `snake_case`      |
| **Global Variables** |      `UpperCamelCase` (Use sparingly)      |
|    **Constants**     |           `SCREAMING_SNAKE_CASE`           |
|  **Boolean Flags**   |     Prefix with `is`, `has`, or `can`      |
|    **Functions**     |              `lowerCamelCase`              |
| **Private/Internal** |    Prefix with a single underscore `_`     |
| **Modules/Classes**  |              `UpperCamelCase`              |
|    **Instances**     |              `lowerCamelCase`              |
|  **Dummy Variable**  | Single underscore `_` (for unused returns) |
|   **Metamethods**    |     Double underscore `__` (Reserved)      |

### Reserved Keywords

|     **Category**     |                 **Keywords**                  |
| :------------------: | :-------------------------------------------: |
| **Logic & Literals** |  `and`, `or`, `not`, `true`, `false`, `nil`   |
|   **Control Flow**   |     `if`, `then`, `else`, `elseif`, `end`     |
|    **Iteration**     | `for`, `in`, `while`, `do`, `repeat`, `until` |
|    **Execution**     |         `function`, `return`, `break`         |
|      **Scope**       |                    `local`                    |


- World of Warcraft 3.3.5a does **NOT** support `goto` and `double-colon labels` such as `::top::`

### Types

There are eight basic types in Lua:

1. `nil`
2. `boolean`
3. `number`
4. `string`: immutable
5. `function`: functions are first-class values in Lua, which means that functions can be 
   - stored in variables
   - passed as arguments to other functions
   - returned as results
6. `userdata`: allows arbitrary C data to be stored in Lua variables. Default supported operations only have assignment and equality test.
7. `thread`
8. `table`

#### String

- Lua provide automatic conversions between numbers and strings at run time.

  ```lua
  -- 
  print("10" + 1)           --> 11
  print("10 + 1")           --> 10 + 1
  print("-5.3e-10"*"2")     --> -1.06e-09
  print("hello" + 1)        -- ERROR (cannot convert "hello")
  ```

- Concatenate strings with `..`

- `tonumber()` and `tostring()` are global functions

  ```lua
  line = io.read()     -- read a line
  n = tonumber(line)   -- try to convert it to a number
  if n == nil then
    error(line .. " is not a valid number")
  else
    print(n*2)
  end
  
  print(tostring(10) == "10")   --> true
  print(10 .. "" == "10")       --> true
  print(0 .. 1)									--> "01"
  ```

#### Table

1. Object-Oriented Nature
   - **Anonymity:** Tables are anonymous objects rather than fixed variables.
   - **Reference-Based:** Assignment (e.g., `b = a`) copies the reference to the table, not the data itself. Both variables point to the same memory address.
   - **Lifecycle:** Memory is managed via garbage collection; tables are deleted only when all references are removed (set to `nil`).
2. Indexing and Syntax
   - **Associative Flexibility:** Indices may consist of **any type** except `nil`.
   - **Literal vs Variable:**  
     - `a.x` is syntactic sugar for `a["x"]`, referencing the literal string "x".
     - `a[x]` evaluates the current value of the variable `x` to determine the index.
   - **Type Strictness:** Numeric keys and string keys are not interchangeable. `a[10]` and `a["10"]` represent distinct memory locations.
3. Data Structures
   - **Arrays:** Implemented using integer keys. By convention, Lua arrays are **1-indexed**.
   - **Packages:** Libraries (such as `io`) are represented as tables. Accessing `io.read` is functionally identical to indexing a table named `io` with the key `"read"`.
   - **Dynamic Scaling:** Tables lack a fixed size and expand automatically as new entries are assigned.

##### Table Iteration 

`pairs` vs `ipairs`

|    Feature    |            ipairs (Integer Pairs)            |           pairs (All Pairs)            |
| :-----------: | :------------------------------------------: | :------------------------------------: |
| **Key Types** |    Only positive integers ($1, 2, 3...$)     | Everything (Strings, numbers, objects) |
|   **Order**   | Guaranteed $(1 \rightarrow 2 \rightarrow 3)$ |            Random/Unordered            |
| **Stops At**  |            The first `nil` index             | Only when the entire table is finished |

##### Table Constructor

Constructors only affect their initialization

```lua
-- 1. Empty Constructor
data = {}

-- 2. Array/Sequence/List
days = {"Sunday", "Monday", "Tuesday", "Wednesday", "Thursday", "Friday", "Saturday"}
print(days[4])  						--> Wednesday

-- 3. Record (Dictionary/Object)
character = {
    name = "Metamagic",
    level = 80,
    class = "Paladin",
    is_hero = true
}
print(character.level)			--> 80

-- 4. Hybrid Table
mixed_data = {
    "First positional",     -- index [1]
    "Second positional",    -- index [2]
    status = "Active",      -- key "status"
    version = 3.35          -- key "version"
}

print(mixed_data[1])                    --> First positional
print(mixed_data.status)                --> Active

-- Misc. Semicolon can be used instead of a comma.
data = {x=10, y=45; "one", "two", "three"}
```

### Operators

#### Arithmetic Operators

- `+`, `-`, `*`, `/`
- `^`
  - Highest precedence of all operators
  - The syntax is part of the Lua core
  - The logic (functionality) is provided by the standard mathematical library, not the core itself

#### Relational Operators

- `<`, `>`, `<=`, `>=`, `==`, `~=`
  - `nil` is equal only to itself
  - Lua compares `tables`, `userdata`, and `functions` by reference
  - Lua compares strings in alphabetical order
  - Other types can be compared only for equality (and inequality)

#### Logical Operators

##### Truthiness Rules

- Considered `false`:  `false` and `nil`
- Considered `true`: everything else, including `0` and `""` (empty string)

| **Operator** |      **Logic**       |                       **Result**                       |
| :----------: | :------------------: | :----------------------------------------------------: |
|  **`and`**   | Short-cut evaluation | Returns the **first falsy** item OR the **last** item  |
|   **`or`**   | Short-cut evaluation | Returns the **first truthy** item OR the **last** item |
|  **`not`**   |    Unary operator    |      Always returns a boolean (`true` or `false`)      |

##### Precedence

- `^`
- `not`, `-` (unary)
- `*`, `/`
- `+`, `-`
- `..`
- `<`, `>`, `<=`, `>=`, `==`, `~=`
- `and`
- `or`

### Statements

```lua
-- 1. Assignment
str = "hello" .. "world"
a, b = 10, 2*13

-- value of b+2 is ignored
a, b = a+1, b+1, b+2

-- f() returns two results: a gets the first and b gets the second
a, b = f()

-- 2. Local Variables and Blocks
i = 10         		-- global variable
local j = 1    		-- local variable

x = 10
local i = 1        -- local to this line itself (chunck)

while i<=x do
  local x = i*2    -- local to the while body
  print(x)         --> 2, 4, 6, 8, ...
  i = i + 1
end

if i > 20 then
  local x          -- local to the "then" body
  x = 20
  print(x + 2)
else
  print(x)         --> 10  (the global one)
end

print(x)           --> 10  (the global one)

-- 3. A common idiom
local foo = foo
--[[
	1. speeds up access to foo;
	2. preserve the original value of foo.
]]--
```

#### Control Structures

```lua
-- 1. selection
if op == "+" then
    r = a + b
  elseif op == "-" then
    r = a - b
  elseif op == "*" then
    r = a*b
  elseif op == "/" then
    r = a/b
  else
    error("invalid operation")
end

-- 2. while
local i = 1
while a[i] do
  print(a[i])
  i = i + 1
end

-- 3. repeat-until
repeat
  line = io.read()
until line ~= ""
print(line)

-- 4. numeric for
for var=exp1, exp2, exp3 do
  something
end
-- exp1: from value
-- exp2: to value
-- exp3: step value; default to 1; optional

-- 5. generic for
for i, v in ipairs(a) do 
  print(v) 
end
-- traverse all values returned by an iterator function
```

### Functions

```lua
function <identifier> (<param_1>, ..., <param_x>)
  something
end

-- Vararg Expression ...
function <identifier> (...)
  something
end
```

|   **Syntax**   | **Description** |                 **Effect**                  |
| :------------: | :-------------: | :-----------------------------------------: |
|     `f()`      |   Normal call   |    Returns all values ($0, 1,$ or many).    |
|    `(f())`     |  Wrapped call   |         Returns exactly one value.          |
|  `return f()`  |    Tail call    |      Passes all return values through.      |
| `return (f())` |  Forced single  | Only passes the first return value through. |

#### Closures

