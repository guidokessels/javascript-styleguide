# JavaScript Style Guide

> "Programs are meant to be read by humans, and only incidentally for computers 
> to execute." - _Donald Knuth_

A style guide is a set of standards for the writing and design of code.
 
The goal of a style guide is that all code in any code-base should look like a single person typed 
it, even when many people are contributing to it. Consistency in code style and formatting makes 
code more readable, and thus more easier to maintain. 

## Goals

- Clear overview of rules
    - Commonly-agreed upon standards
    - Living document
- Style checker
    - Verify if style is correct
    - Runs via command line, integrated in build process
    - Run in editor (SublimeText, etc.)
    - Provide .editorconfig
- Style fixer: Automatically fix code (e.g., via CodePainter)

## Style Guide

### Indentation
Each indentation level is made up of four spaces. No tabs.

```javascript
//Good
if (true) {
    doSomething();
}
```

### Line Length
Each line should be no longer than 100 characters. If a line goes longer than 100 characters, it 
should be wrapped after an operator (comma, plus, etc.) The following line should be indented two
levels (eight spaces.)

```javascript
// Good
doSomething(argument1, argument2, argument3, argument4,
        argument5);

// Bad: Following line only indented four spaces
doSomething(argument1, argument2, argument3, argument4,
    argument5);

// Bad: Breaking before operator
doSomething(argument1, argument2, argument3, argument4
    , argument5);
```

### Primitive Literals
String should always use single quotes and should always be on a single line.

```javascript
// Good
var name = 'SpilGames';

// Bad: Double quotes
var name = "SpilGames";

// Bad: Wrapping to second line
var longString = 'This is a string spanning \
multiple lines.';
```

Number should be written as decimal integers, e-notation integers, hexadecimal integers, or 
floating-point decimals with at least one digit before and one digit after the decimal point. 
_Never_ use octal literals.

```javascript
// Good
var count = 10;
var price = 10.0;
var price = 10.00;
var num = 0xA2;
var num = 1e23;

// Bad: Hanging decimal point
var price = 10.;

// Bad: Leading decimal point
var price = .1;

// Bad: Octal (base 8) is deprecated
var num = 010;
```

The special value `null` should be used only in the following situations:

- To initialize a variable that may later be assigned an object value
- To compare against an initialized variable that may or may not have an object value
- To pass into a function where an object is expected
- To return from a function where an object is expected

Examples:

```javascript    
// Good
var person = null;

// Good
function getPerson() {
    if (condition) {
        return new Person("Nicholas");
    } else {
        return null;
    }
}

// Good
var person = getPerson();
if (person !== null){
    doSomething();
}

// Bad: Testing against uninitialized variable
var person;
if (person != null){
    doSomething();
}

// Bad: Testing to see if an argument was passed
function doSomething(arg1, arg2, arg3, arg4){
    if (arg4 != null){
        doSomethingElse();
    }
}
```

Never use the special value `undefined`. To see if a variable has been defined, use the `typeof`
operator:

```javascript
// Good
if (typeof variable == "undefined") {
    // do something
}

// Bad: Using undefined literal
if (variable == undefined) {
    // do something
}
```

### Operator Spacing
Operators with two operands must be preceded and followed by a single space to make
the expression clear. Operators include assignments and logical operators.

```javascript
// Good
var found = (values[i] === item);

// Good
if (found && (count > 10)) {
    doSomething();
}

// Good
for (i = 0; i < count; i++) {
    process(i);
}

// Bad: Missing spaces
var found = (values[i]===item);

// Bad: Missing spaces
if (found&&(count>10)) {
    doSomething();
}

// Bad: Missing spaces
for (i=0; i<count; i++) {
    process(i);
}
```

### Parentheses Spacing
When parentheses are used, there should be no white space immediately after the
opening paren or immediately before the closing paren.

```javascript
// Good
var found = (values[i] === item);

// Good
if (found && (count > 10)) {
    doSomething();
}

// Good
for (i = 0; i < count; i++) {
    process(i);
}

// Bad: Extra space after opening paren
var found = ( values[i] === item);

// Bad: Extra space before closing paren
if (found && (count > 10) ) {
    doSomething();
}

// Bad: Extra space around argument
for (i = 0; i < count; i++) {
    process( i );
}
```

### Object Literals
Object literals should have the following format:

- The opening brace should be on the same line as the containing statement.
- Each property-value pair should be indented one level with the first property appearing on the 
next line after the opening brace.
- Each property-value pair should have an unquoted property name, followed by a colon (no space 
preceding it), followed by the value.
- If the value is a function, it should wrap under the property name and should have a blank line 
both before and after the function.
- Additional empty lines may be inserted to group related properties or otherwise improve 
readability.
- The closing brace should be on a separate line.

Examples:

```javascript
// Good
var object = {
    key1: value1,
    key2: value2,

    func: function() {
        // do something
    },

    key3: value3
};

// Bad: Improper indentation
var object = {
                key1: value1,
                key2: value2
            };

// Bad: Missing blank lines around function
var object = {
    key1: value1,
    key2: value2,
    func: function() {
        // do something
    },
    key3: value3
};
```

When an object literal is passed to a function, the opening brace should be on the same
line as if the value is a variable. All other formatting rules listed earlier still apply.

```javascript
// Good
doSomething({
    key1: value1,
    key2: value2
});

// Bad: All on one line
doSomething({ key1: value1, key2: value2 });
```

### Comments
Make frequent use of comments to aid others in understanding your code. Use comments
when:

- Code is difficult to understand.
- The code might be mistaken for an error.
- Browser-specific code is necessary but not obvious.
- Documentation generation is necessary for an object, method, or property (use appropriate 
documentation comments).

#### Single-Line Comments
TODO

#### Multiline Comments
TODO

#### Comment Annotations
TODO

### Variable Declarations
TODO

### Function Declarations
TODO

### Naming
TODO

### Strict Mode
TODO

### Assignments
TODO

### Equality Operators
TODO

### Ternary Operators
TODO

### Statements
TODO

### White Space
TODO

### Things To Avoid
TODO


## Sources

A lot of content in this document originated from the following sources:

- ["Maintainable JavaScript" - _Nicolas C. Zakas_](http://shop.oreilly.com/product/0636920025245.do)
- http://addyosmani.com/blog/javascript-style-guides-and-beautifiers/
- https://github.com/rwaldron/idiomatic.js/
