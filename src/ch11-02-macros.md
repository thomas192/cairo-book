# Macros

The Cairo language has some plugins that allow developers to simplify their code. They are called `inline_macros` and are a way of writing code that generates other code.

### `print!` and `println!` macros

Two macros are available for printing values:
- `println!` which prints on a new line 
- `print!` with inline printing
  
Both can be used with curly brackets as placeholders that hold a value in place:
- When printing the value of a variable, the variable name can go inside the curly brackets.
- When printing the result of evaluating an expression, use empty curly brackets in the format string, then follow the format string with a comma-separated list of expressions to print in each empty curly bracket placeholder in the same order.

### `consteval_int!` macro

In some situations, a developer might need to declare a constant that is the result of a computation of integers. To compute a constant expression and use its result at compile time, it is required to use the `consteval_int!` macro.

Here is an example of `consteval_int!`:

```rust
const a: felt252 = consteval_int!(2 * 2 * 2);
```

This will be interpreted as `const a: felt252 = 8;` by the compiler.

### `array!` macro

Please refer to the [Arrays](./ch03-01-arrays.md) page.

### `panic!`, `assert!` and `assert_eq!` macros macro

See [Unrecoverable Errors with panic](./ch10-01-unrecoverable-errors-with-panic.md) page.

### `format!` macro

The `format!` macro works like `println!`, but instead of printing the output to
the screen, it returns a  `ByteArray` with the contents. In the following
example, we perform string concatenation using either the `+` operator or the
`format!` macro.  The version of the code using `format!` is much easier to
read, and the code generated by the `format!` macro uses snapshots so that this
call doesn’t take ownership of any of its parameters.

```rust
{{#include ../listings/ch11-advanced-features/no_listing_06_format_macro/src/lib.cairo}}
```

### `write!` macro

The `write!` and `writeln!` are two macros which are used to emit the format string to a specified stream.
This macro takes 2 arguments:
- a Formatter, which is a struct containing a `ByteArray`, representing the pending result of formatting (the _stream_)
- the 'ByteArray' to append to the formatter
  
Calling this macro will append the provided `ByteArray` string to the formatter.
Example usage is:
```rust
{{#include ../listings/ch11-advanced-features/no_listing_07_write_macro/src/lib.cairo}}
```


