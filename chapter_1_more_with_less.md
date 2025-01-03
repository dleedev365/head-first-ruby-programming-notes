# How Ruby Programs Run

1. **Ruby script file (.rb)** → **Ruby interpreter** → **Execution**

---

# Ruby Basics

## Interactive Ruby (IRB)

- Ruby supports interactive programming via `irb` (Interactive Ruby Shell).
- You can type expressions directly and see the results immediately.

```ruby
$ irb
irb(main):001:0 > 1 + 2
=> 3

irb(main):002:0 > exit
```

---

## Key Features

- **Variables**: Ruby variables don't have types.
  - Naming convention: Use snake_case (all lowercase, separated by underscores).
- **Everything is an object**:

  - Example: `"Hello".upcase` → `"HELLO"`

- **Output Methods**:

  - `puts <string>`: Displays the string and adds a newline.
  - `print <string>`: Similar to `puts` but doesn’t add a newline.
  - Example:
    ```ruby
    puts "one", "two"  # Output: one\ntwo
    print "one", "two" # Output: onetwo
    ```
  - Both methods are "top-level" and can be called anywhere without specifying a receiver.
  - Parentheses are optional:
    ```ruby
    puts ("one", "two") # Same as puts "one", "two"
    ```

- **String Interpolation**: Embed variables or expressions within strings using `#{<variable>}`.

- **Inspect Method**: `.inspect` converts an object into a string representation (useful for debugging).
  - Shorthand: `p <variable>` (automatically calls `.inspect`).

---

## Common Methods

- `.chomp`: Removes a trailing newline character.
- `.methods`: Lists all available methods for an object.
- `.to_s`: Converts an object (e.g., number) to a string.
- `.to_i`: Converts a string to an integer.

---

## Control Structures

- Conditional statements or blocks must end with `end`.

- **Negation**:

  - `!<condition>` means "not `<condition>`".
  - `unless <condition>` is equivalent to `if not <condition>`.

- **Loops**:
  - `while <condition>` executes while the condition is true.
  - `until <condition>` executes until the condition becomes true.

### Example: Conditional Statement

```ruby
if light == "red"
  puts "Stop!"
else
  puts "Go!"
end
```
