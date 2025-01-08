# Exceptions: Handling the Unexpected

- Avoid using "method return values" for error messages or as a replacement for the `raise` method.
  - The `raise` method creates an exception object/class that represents an error.
  - If not handled, exceptions will halt program execution.
- For graceful error handling or rejection, use the `rescue` keyword.

---

## Using `rescue` for Exception Handling

### Syntax

```ruby
begin
    <code block>
    raise "Error Found!" # Creates an error object with a "message" attribute
rescue
    puts "Handling Error"
end
```

### Key Points

- Wrap code that might raise exceptions within a `begin`/`end` block and add one or more `rescue` clauses.
- Once the `rescue` clause completes, code execution continues normally after the `begin`/`end` block.

**Example:**

```ruby
begin
    raise "oops!"
rescue => my_exception # Store the exception in a variable
    puts my_exception.message
end
```

- Multiple `rescue` blocks can handle different types of exceptions.

---

## Additional Details

### Custom Exception Classes

- By default, the `raise` method creates an instance of the `RuntimeError` class.
- To specify a different exception class, use the syntax:  
  `raise <ClassName>, <exception_message>`

### Retrying After an Exception

- The `retry` keyword allows you to reattempt execution from the start of the `begin`/`end` block.

**Example:**

```ruby
begin
    <code block>
rescue ZeroDivisionError
    puts "Error: Division by zero detected!"
    portion = 1
    retry # Restarts execution from the beginning of the block
end
```

### Ensuring Execution with `ensure`

- The `ensure` clause runs regardless of whether an exception occurs or not.

**Example:**

```ruby
begin
    <code block>
rescue
    <handle error>
ensure
    puts "This will always run!"
end
```
