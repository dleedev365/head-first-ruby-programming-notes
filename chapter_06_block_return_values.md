## Block Return Values

- **Ruby blocks return the value of the last expression they contain**:

  - The value is returned to the method as the result of the `yield` keyword.
  - **Example**:

    ```ruby
    def alert_if_true
      if yield
        puts "Block returned true!"
      else
        puts "Block returned false."
      end
    end

    alert_if_true { 2 + 2 == 5 } # prints "Block returned false."
    alert_if_true { 2 > 1 }      # prints "Block returned true!"
    ```

### Caveats

- **Avoid using `return` in blocks**:

  - The `return` keyword in a block exits the entire method where the block is defined, not just the block itself.
  - **Example (Incorrect)**:

    ```ruby
    def print_block_value
      puts yield
    end

    def other_method
      print_block_value { return 1 + 1 }
    end

    other_method # Doesn't print anything because the method exits when the block is defined.
    ```

  - **Correct Approach**:
    ```ruby
    def other_method
      print_block_value { 1 + 1 }
    end
    ```

- **Tip**: Always rely on the implicit return of the block for clear and expected behavior.
