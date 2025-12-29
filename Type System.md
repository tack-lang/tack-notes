Tack's type system is rather complicated at times, but is also helpful.

# Values
In Tack, almost everything is a value, and every value has a type. **All types are values, but not all values are types.** The syntax `v: T` will be used to represent `v` being a value of type `T`. `v: T` means other things as well, but these are less important. The following statements are all true:
```
true: bool
'A': char
```

# Types
In Tack, a type is defined as anything in the `type` group. This includes `i32`, `f32`, `bool`, `char`, `void`, and other primitive types, but it also contains user-defined types, such as `struct { age: u32 }`, or `enum { Right, Left }`. However, all types are values, and all values have a type, which means that all of these values have types. All of the following statements are true:
```
i32: prim
f32: prim
bool: prim
char: prim
void: prim
struct { age: u32 }: struct
enum { Right, Left }: enum
```
However, we can go one step further. `prim` is a type, which makes it a value, which makes it have a type, and the same logic applies to `struct` and `enum`. All the following statements are true:
```
prim: prim
struct: prim
enum: prim
```

# Functions
Functions are another question. The syntax for function types is `func(Type1, Type2) RetType`. All the following statements are true:
```
func() void { println("Hello, world!"); }: func() void
func() void: func
func: prim
```

## Type equality
The syntax `T == G` will be used to denote that `T` is the same value as `G`. `T != G` denotes that `T` is not the same value as `G`. `typeof(v)` denotes the type of `v`. All the following statements are true:
```
func(x: i32) void { println(x) }: func(i32) void
func(y: i32) void { println(y) }: func(i32) void
func(x: i32) void { println(x) } != func(y: i32) void { println(y) }
typeof(func(x: i32) void { println(x) }) == typeof(func(y: i32) void { println(y) })
```
