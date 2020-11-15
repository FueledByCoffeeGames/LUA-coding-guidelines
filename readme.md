# Fueled By Coffee games Coding guidelines
#### Author: Joaquín josé von chong [AKA: FueledByCoff33]
#### Version: 1.0.0
#### Created: October 24, 2020
#### Last update: October 24, 2020
---
## Table of content:
  - [Introduction:](#introduction)
  - [File header documentation](#file-header-documentation)
  - [Coding standards Guidelines](#coding-standards-guidelines)
    - [Some words on programming style](#some-words-on-programming-style)
    - [Formatting](#formatting)
      - [Indentation](#indentation)
      - [Inline Multi Declaration](#inline-multi-declaration)
      - [Requiring statements](#require-statements)
    - [Naming](#naming)
      - [Casing](#casing)
      - [Variable naming](#variable-naming)
      - [Function naming](#function-naming)
      - [Module naming](#module-naming)
      - [Method naming](#method-naming)
      - [Private Method naming](#private-method-naming)





## Introduction:
Well written software offers many advantages. It will contain fewer bugs and will run
more efficiently than poorly written programs. Since software has a life cycle and much
of which revolves around maintenance, it will be easier for the original developer(s) and
future keepers of the code to maintain and modify the software as needed. This will lead
to increased productivity of the developer(s). The overall cost of the software is greatly
reduced when the code is developed and maintained according to software standards. 
<br>
It is important to note that standards are not fixed, but will evolve over time. Developers
are encouraged to provide feedback.


## File header documentation
File header documentation if done correctly, improves the readability of a module.
A software module should have a comment block at its beginning containing the following 
basic information:

- The name of the original author who wrote the module
- The date the file was created
- An overview of the purpose of the module.
- Last modification date
- semver version note
eg.
```lua
--- Author:Joaquin Jose von chong
--- Creation Date: D/M/Y
--- Description: This is a test
--- Last Modified: D/M/Y
--- version: 1.0.0
```
  
If the case of a document edited by other developer, the next information should be annexed and updated:

- The name of the last author making the edition.
- Updated las modification date
- Upped semver version note (eg. 0.1.0 -> 0.1.1). More of semver and how to use it [here](#https://semver.org/)
eg:
```lua
--- Author:Joaquin Jose von chong
--- Creation Date: D/M/Y
--- Description: This is a test
--- Last Modified: D/M/Y
--- version: 0.1.1
--- Edited By: Developer #2

```


## Coding standards Guidelines
#### Some words on programming style
Before applying these coding style guidelines, consider the words of warning taken from the [ Style Guide for Python Code](https://www.python.org/dev/peps/pep-0008/). which applies just as well to Lua or any programming language.

 Code is read much more often than it is written, and this style guide intends to improve the readability of code through consistency. Consistency is important, in increasing measure, with other projects, within a project, and within a single module or function. But most importantly: know when to be inconsistent, and use your best judgment -- sometimes the style guide just doesn't apply. It can be advisable to break a rule when applying the rule would make the code less readable.

Programming style is an art. There is some arbitrariness to the rules, but there are sound rationales for them. It is useful not only to provide sound advice on style but to understand the underlying rationale and human aspect of why the style recommendations are formed.
#### Formatting


###### Indentation:
Indenting often uses two spaces. This is followed in Programming in Lua, the Lua Reference Manual, Beginning Lua Programming, and the Lua users wiki. (Why this is the case, I don't know, but perhaps it is because Lua statements can tend to be deeply nested.) You'll see other common conventions (e.g. 3-4 spaces or tabs).

```lua
--- Bad
for i,v in ipairs(t) do
if type(v) == "string" then
print(v)
end
end

---Good 
for i,v in ipairs(t) do
  if type(v) == "string" then
    print(v)
  end
end
```
###### Inline multi declaration
inline multi declaration refers to declare multiple variables in a single line, eg.
```lua
  local x = 20,y = 20, z = 20
```
This practice is not permitted since it harms readability and makes variables easy to miss. Better way is to just to make a declaration per line
```lua
---Better way
local x = 20
local y = 20
local z = 20
```

###### Require statement:
All require statements must be a the top of the file
```lua
local OtherThing = require(script.Parent.OtherThing)
local AnotherOtherThing = require(script.Parent.AnotherOtherThing)
--- the rest of your code
```

#### Naming


###### Casing:
Declarations can be done in two types of casing depending on what you are declaring
<b>PascalCasing</b>, Where all first letters are capitalized and <b>camelCasing</b>, Where all first letters are capitalized except the first letter of the first word. eg.

```lua
---PascalCase
local MyPascalCasedVariable

--camelCase
local myCamelCasedVariable
```

###### Variable naming: 
Variable names should be [<b>camelCased</b>](#casing), also the should be as descriptive as possible without the use of cryptic abbreviations. We actually encourage the non-use of abbreviations. Don´t be afraid of long variable names. This allow a code reader to better know of the intent of the author and what is the purpose of that variable  (eg. PlayerPositionVector).

```lua
--- Wrong
local pmv = Cframe.new(1,2,5)
--- Good 
local PlayerPosVec = Cframe.new(1,2,5)
--- Even Better
local PlayerPositionVector = Cframe.new(1,2,5)
```


###### Function naming: 
Functions follow almost the same rule as variables but with a minor change in casing:
All functions must be [<b>PascalCased</b>](#casing).
(eg. A function that gets the current player list in the server)
```lua
--- Wrong
local func getPlayerList()
    return Players:PlayerList()
end 
--- Good
local func GetPlayerList()
    return Players:PlayerList()
end 
```


###### Module naming
Modules are modular pieces of code than can be imported in another file. You may think of a module as a class and the naming follows the same rules as functions
```lua

--- Wrong
local moduleName = {}

--- Good
local ModuleName = {}

```

###### Method naming: 
Methods follow almost the same rule as functions.
```lua
local Module = {}

--- Wrong
func Module:methodName()
    ...
end
--- Good
local func Module:MethodName()
    ...
end

```


###### Private method naming: 
LUA doesn't have such thing as private method but you can grammatically specify  
a private method adding a <b>"_"</b> as prefix, eg.

```lua
local Module = {}
func module._PrivateMethod()
  return 5
end 
func Module:MethodName(x)
    return self:_PrivateMethod + x
end

```
###### Require statement naming
When requiring a module the variable containing it must be [<b>PascalCased</b>](#casing)
Private methods are intended only for internal module usage usage.

