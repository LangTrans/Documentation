---
description: How to run example?
---

# Getting Started

## Download

### Latest

Clone the repo

```bash
git clone https://github.com/LangTrans/LangTrans.git
```

or download source code in [releases](https://github.com/LangTrans/LangTrans/releases)

Go to LangTrans Folder

### Standalone (Alternate)

Go to [releases](https://github.com/LangTrans/LangTrans/releases) and download latest executable

## Create Source Code

Create a new file (`filename.ext`)&#x20;

```python
# Anonymous function
inc = (x) => x+1
# Lambda function
twice(x) = 2*x
# Print Done if x is defined other wise Failed
print((x||True)?"Done":"Failed")
# Single Line if and check x defined or not
print('x is not defined') if !x
# Pipe Syntax
1 -> inc
|> print
# Reverse Pipe
print<-inc<-inc<-1
# Arithmetic operations with functions 
print((inc+twice)(3))
#Scope syntax work like in javascript
#scope1#
print("Scope1")
print("Done")

#scope2#
print("Scope2")
print("Done")
```

Paste this code to `filename.ext`

## Transpile Code

### With YAML files

#### For source code

```bash
py langtrans.py filename.ext filename.py example/source example/target
```

#### Standalone

```bash
langtrans filename.ext filename.py example/source example/target
```

### With compiled syntax (Alternate Method)

#### Compile syntax

```bash
py langtrans.py -c example/source example/target py
```

`py.ltz`will be created

#### Generate code

```bash
py langtrans.py -f filename.ext filename.py py
```

`filename.py`will be generated. It contain the transpiled code

Run`filename.py`
