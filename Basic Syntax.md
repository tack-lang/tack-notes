This is a basic primer in Tack's syntax, not an in-depth explanation. For a formal grammar, see [formal.ebnf](https://github.com/tack-lang/tackc/tree/master/crates/tackc_parser/formal.ebnf).

Every Tack file must start with a `mod` statement. For an explanation of the module system, see [[Modules]].
`mod path.to.module;`

## Function declarations
```
func func_name(arg1: Type1, arg2: Type2) RetType {
	
}
```

## Statements
Tack doesn't have many statements, as it's a mostly expression-based language. However, it does have statements for variable declarations and assignments:
```
let s = 5;
s = 1;
```

## Expressions
In Tack, most things are expressions.

### Operations
```
5 + 2;
1 - 3;
2 * 5;
3 / 1;
```

### Function calls
```
function(arg1, arg2);
```

### If statements
```
if cond {
	function();
}
```
Blocks in if statements (not if-else statements) must evaluate to `void`.

### If-else statements
```
if cond {
	function()
} else {
	other_function()
}
```
Blocks in if-else statements must evaluate to the same type.

### While loops
```
while cond {
	function();
}
```
Blocks in while loops also must evaluate to `void`.

### For loops
```
for i in iter {
	function();
}
```
Tack has Rust-like iterators, and uses them inside for loops. Blocks in while loops also must evaluate to `void`.