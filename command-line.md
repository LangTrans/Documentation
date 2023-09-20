# Command Line

## Usage

```bash
py langtrans.py <SoureFileName> <OutputFileName> <SyntaxRepr> <PatternRepr>
```

**SourceFileName** - File name of the source code written with new syntax

**OutputFileName** - File name of the source code you want to generate with original syntax

**SyntaxRepr** - File name of YAML file for [token extraction](implementation.md#token-extraction) without extension(.yaml)

**PatternRepr** - File name of YAML file with [template](implementation.md#template) of original language without extension

### **Compile**

```bash
py langtrans.py -c <SyntaxRepr> <PatternRepr> <compfile>
```

**compfile**

Name of the compiled file(without extension)

`filename.ltz` will be generated.

### **Run**

```bash
py langtrans.py -f <SoureFileName> <OutputFileName> <compfile>
```

### **Options**

* &#x20;**-h** - For help
* &#x20;**-v** - Verbose mode
* &#x20;**-y** - To execute ‘after’ command automatically
* &#x20;**-n** - To exit without executing ‘after’ command

### **Docs for token extraction file**

To generate documentation for [token extraction](implementation.md#syntax) file

```bash
py langtrans.py -d <SyntaxRepr> > filename.txt
```

