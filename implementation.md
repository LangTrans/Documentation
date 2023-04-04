# Implementation

To customize you should extract tokens with regular expression. Then you should create the template of original language with token you extracted.

## Token Extraction

### Syntax

```yaml
typeofsynax:
    regex: regex (regex for token1) <var1> regex
    tokens: [token1,token2,token3]
    unmatch:
    - regex
    global: True
    once: True
    next: [other_typeofsyntax,$collection_name]
    token1:
        unmatch:
        - regex
        eachline: extra_here <line> extra_here
        replace:
        - [regex,"replacewith"]
        - ["regex here"]
        call: [other_typeofsyntax,$collection_name]
_1typeofsyntax:
    regex: regex2
    tokens: [token1,token2,token3]
#Code here(like above)
#...................
#...................
#...................
settings:
    collections:
        collection_name: [typeofsyntax1,typeofsyntax2]
    varfile: filename_without_extension
    variables:
        var1: regex1
        var2: regex2
        var3 : regex3
    after: #Command Line Commands
    errfile: # Base Name
    #after:
    #- Command One
    #- Command Two
    #after:
    #       windows: Command
    #       linux: Command
```



#### **typeofsyntax**

Name of syntax you wanted to match

**Eg.** arithmetic, loop etc.

If one type have same pattern but different regular expression to match.&#x20;

You can write `_<any character><typeofsyntax>` for next regex.

**Eg.** `_1typeofsyntax`

Both regex use one template

#### **regex**

Place where regular expression to match block of code..

Regular expression for tokens must be inside brackets.

> &#x20;`~` acts like `s*` in regular expression


#### **tokens**

Name of tokens you wanted to extract

#### **unmatch**

List of regex that should not be matched. It can be used in token option also

#### **global**

If it is False it works only after calling it otherwise it works normally.

#### **once**

If it is True it works only once

**next**

To pass converted syntax into another or same typeofsyntax

### **token1**

To modify token1 matched

> To add content in each line.

**eachline**  
`<line>` represents original content in eachline. It loops through every line.

**replace**  
Regular expression to match and replace or delete any unwanted content in token.  
To replace add a list with first item as regular expression to unwanted content and second item is the content you wanted to replace with.  
To delete add a list with regular expression only  

**call**  
To pass transformed to another typeofsyntax  
Write names of typeofsyntax inside array to call.  
Passes from left to right  

#### **settings block**

For setting variables, collections, after command


> **variables**  
You can make variables than can used inside **regular expression** by `<varname>`


> **varfile**  
Name of YAML file to import variables

> **info**  
Filename doesn't need extension (base name only)  

> **collections**  
Group of [typeofsyntax]s  
It can be used in call and next    
**Eg.** `$collection_name`


> **after**  
To run command line commands after translation.

## **Example**

```yaml
after: "black $target"
```

* $target - Location of translated file
* $source - Location of source file
* $current - Location of program


> **errfile**
YAML file with error definitions for **linting**


> **info**
> _regex_ _tokens_ should be in all typeofsyntax.  
Others are optional  

### Example

```yaml
shorthand:
  regex: <var>\+=<var>
  tokens: [var,num]
settings:
    variables:
        var: ([A-Za-z0-9_]+)
```

## Template

Template of syntax of target language

### Syntax

```yaml
typeofsyntax: "syntax1 <token1> middle syntax <token2> syntax3 <token3>"
```

**typeofsyntax**- Name of [typeofsyntax ](implementation.md#typeofsyntax)in [token extraction](implementation.md#token-extraction) file.

**token1,token2,token3** - Represents [tokens](implementation.md#tokens) extracted with regular expression in [token extraction file](implementation.md#token-extraction).

Write tokens inside template of original language(`<tokename>`)

### Example

```yaml
shorthand: (incf <var> <num>)
```

## Linting

To match error with regular expression.

If error is matched, part of code with error and error message will be displayed.

### Syntax

Syntax of error file

```yaml
typeofsyntax: # typeofsyntax block
    # Errors Block----------

    NameofError:
        #Error Details------
        regex: Regex
        msg: Error Message
        help: Help Message
        #-------------------

    NameofError1:
        #Error Details here

    # ----------------------

    # Outside Block---------
    outside:
        # Errors Block here
    #-----------------------

typeofsyntax1:
    #Errors Block here
    #Outside Block here

# Outside Block here
```

#### **typeofsyntax Block**

Block name is  name of [typeofsyntax ](implementation.md#typeofsyntax)in [token extraction](implementation.md#token-extraction) file. Regex is only matched inside text matched by [main regex](implementation.md#regex).

#### **Outside Block**

To match error regex in whole source code.

> For errors related to a typeofsyntax, outside block should be inside [typeofsyntax block](implementation.md#typeofsyntax-block).  
> For errors not related to any typeofsyntax, outside block should be used outside block


#### **NameofError**

Name of the error you want to match

**Eg.** TypeError, Syntax Error etc.

#### **Regex**&#x20;

Regular expression to match error part of code

#### **Error Message**

Details of error

#### **Help Message** (optional)

Steps to resolve the error

### Example

```yaml
fstring:
    Cannot_Quote:
        regex: '{(?:(?!\}).)*"'
        msg: "Can't use '\"' inside '{}'"
        help: Asign constant to a variable and add that variable to fstring
    Multiple_Curly:
        regex: '{(?:(?!}).)*{'
        msg: Cant't use nested curly brace
outside:
    Invalid_Object:
        regex: 'class <var>\((?:(?!\)).)*\n'
        msg: No Multiline
```


> You can share your syntax in [LangTrans Repos](https://langtrans.github.io/langtransrepos/)

