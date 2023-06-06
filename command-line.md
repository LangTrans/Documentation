# Command Line

## Usage

```bash
py langtrans.py <SoureFileName> <OutputFileName> <SyntaxRepr> <PatternRepr>
```

**SourceFileName** - Name of the file with source code to transpile

**OutputFileName** - Name of the file to output to

**SyntaxRepr** - File name of YAML file with [definition of tokens](implementation.md#token-extraction) (without .yaml extension)

**PatternRepr** - File name of YAML file with [template](implementation.md#template) of original language (without .yaml extension)

### **To Compile**

```bash
py langtrans.py -c <SyntaxRepr> <PatternRepr> <compfile>
```

**compfile**

Name of output file (without extension); compiles and generates `filename.ltz`.

### **To Run**

```bash
py langtrans.py -f <SoureFileName> <OutputFileName> <compfile>
```

### **Options**

* &#x20;**-h** - For help
* &#x20;**-v** - Verbose mode
* &#x20;**-y** - To execute ‘after’ command automatically
* &#x20;**-n** - To exit without executing ‘after’ command

### **Docs for token extraction file**

To generate documentation for [definition of tokens](implementation.md#syntax) file, run:

```bash
py langtrans.py -d <SyntaxRepr> > filename.txt
```

