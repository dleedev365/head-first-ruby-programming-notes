## Blocks

- Blocks are a Ruby-specific concept that can get/update the value of local variables in the same scope as the block.
- A chunk of code associated with a method call. The method can invoke the block one or more times.
- **Block Syntax**:

  ```ruby
  # Multi-line
  take_this do |thing|
      puts "do/end block got #{thing}"
  end

  # Inline
  take_this { |thing| puts "do/end block got #{thing}" }
  ```

- **Example**:

  ```ruby
  # Method
  def my_method(my_block)
      <code>
      my_block.call
      <code>
  end

  # Block
  my_method do
      <code>
  end
  ```

- **Caveat**: A method can only take one block.
- **Convention**:
  - Single-line blocks: Use curly braces `{ ... }`.
  - Multi-line blocks: Use `do...end`.

## Yield

- A keyword that finds and invokes the block a method was called with.
- **Example**:
  ```ruby
  def twice
      yield
      yield
  end
  ```

## Arrays

- **`each` Method**:

  - Invokes a block for each item in an array.
  - **Example**:

    ```ruby
    # Example 1
    ["a", "b", "c"].each { |parameter| puts parameter } # Prints: a, b, c

    # Example 2
    def total(prices)
        amount = 0
        prices.each do |price|
            amount += price
        end
        amount # Returns amount
    end
    ```
