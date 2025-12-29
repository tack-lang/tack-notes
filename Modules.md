In Tack's module system, every file starts with a `mod` statement with the following syntax:
```
mod path.to.module;
```
This will allow exported items within the current file to be accessed at `path.to.module.item`. Multiple files can have the same module.
In order to export items, they must be marked with the `exp` keyword:
```
exp const EXPORTED_CONSTANT = 5;
```
Items can also be imported, allowing them to be accessed in the current scope:
```
mod path.to.other.module;

imp path.to.module.EXPORTED_CONSTANT;

// EXPORTED_CONSTANT can now be used.
```
Since imports are items, they can also be exported:
```
mod path.to.another.module;

exp imp path.to.module.EXPORTED_CONSTANT;

// path.to.another.module.EXPORTED_CONSTANT is now the same as path.to.module.EXPORTED_CONSTANT
```
Declaring a module implicitly imports all items inside of that module, including submodules. This may sound confusing, but this essentially just results in the following:
```
// file1.tck
mod program.module1;

exp const CONSTANT = 5;

// file2.tck
mod program;

imp module1.CONSTANT;
```
And the following:
```
// file1.tck
mod program;

exp const CONSTANT = 5;

// file2.tck
mod program;

// CONSTANT is valid in this scope.
```