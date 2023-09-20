---
Description: Customize Programming Languages
---
  
# Welcome to LangTrans

LangTrans customizes any programming language. You can make your own syntax for any programming language.

## How it works?

LangTrans converts your syntax into the original syntax.&#x20;

Regular expressions(REGEX) extract tokens from your language. You should make a template of the original language syntax.&#x20;

LangTrans takes both as input and converts code written in the new syntax to the original syntax.


## FAQs:
  - question: What is the purpose of this implementation?
    answer: 
      This implementation aims to provide a customizable way to transform code syntax from one programming language to another. It involves token extraction, syntax template creation, and error linting to facilitate efficient and accurate code translation.
    
  - question: How do I customize the token extraction process?
    answer: 
      You can customize token extraction by defining regular expressions for each token you want to extract. These tokens represent specific elements in the code you're translating. You can also use modifiers like `unmatch`, `global`, `once`, and others to tailor the extraction process to your needs.
    
  - question: Can I reuse the same token extraction rules in different syntax templates?
    answer: 
      Yes, you can reuse the same token extraction rules by creating multiple `typeofsyntax` blocks that share the same pattern. You can differentiate them by using an underscore and a unique identifier, such as `_1typeofsyntax`.
    
  - question: How do I create syntax templates for the target language?
    answer: 
      Syntax templates are created using placeholders for the extracted tokens. Simply use the extracted token names within the template. For example, if you have an extracted token named `var`, you can use `<var>` in the syntax template to represent that token's value.
    
  - question: What is the purpose of the linting feature?
    answer: 
      The linting feature helps you identify and highlight potential errors in the translated code. By defining error patterns using regular expressions, you can automatically detect problematic code segments and provide associated error messages and help suggestions.
    
  - question: Can I define linting rules for specific code patterns?
    answer: 
      Yes, you can define linting rules both within `typeofsyntax` blocks to target specific code patterns related to that syntax and in the `outside` block to target general code patterns throughout the source code.
    
  - question: How do I handle errors related to the translated code?
    answer: 
      When linting identifies an error in the translated code, it will display the error message you defined in the linting rules. The associated help message provides guidance on how to resolve the error and improve the translation.
    
  - question: Is there a way to group similar `typeofsyntax` blocks together?
    answer: 
      Yes, you can use the `collections` setting to group similar `typeofsyntax` blocks. This grouping can be helpful when using the `call` and `next` features, as it allows you to reference and pass data between related syntax blocks.
    
  - question: How do I integrate this implementation into my workflow?
    answer: 
      After creating your custom token extraction rules, syntax templates, and linting rules, you can run the implementation on your source code. The `after` setting allows you to execute additional command-line commands after the translation process, enabling seamless integration into your development workflow.
    
  - question: How can I provide feedback or report issues with this implementation?
    answer: 
      We appreciate your feedback! You can report suggestions, and improvements in the [LangTrans Repos](https://langtrans.github.io/langtransrepos/), where you can connect with the community and contribute to the ongoing development of this implementation.
