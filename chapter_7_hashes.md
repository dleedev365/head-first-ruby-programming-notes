## Hashes (Labelling Data)

- **Syntax example**:
    ```ruby
    # key/value assignment
    {"key" => "value"}

    # creates a default hash object
    h = Hash.new()
    ```

- **Only `nil` is falsy in Ruby**:
    - For example, the following code will throw a compile error:
    ```ruby
    hash[<undefined_hash_key>] += 1
    ```

- **Symbol keys are more efficient than string keys** (for hash parameter keys):
    - For example:
    ```ruby
    def area(options)
        options[:length] * options[:width]
    end

    put area({:length => 2, :width => 1})
    ```

    - You can omit curly braces and use the shorthand arrow syntax (by keeping the hash parameter last):
    ```ruby
    candidate = Candidate.new("name", age: 32, occupation: "Engineer", hobby: "Climbing")
    ```

- **From version 2, "keyword" arguments were introduced** to prevent typos in hash arguments:
    - For example:
    ```ruby
    def welcome(greeting: "default value", name: nil)
        # code block
    end
    ```

    - To make hash arguments optimal, provide default values wherever possible. If not, refactor or handle missing values accordingly.

- **From version 2.1, "required" keyword arguments were added**:
    - This feature allows you to enforce that certain arguments must be provided when calling a method.
    ```ruby
    def greet(name:, greeting: "Hello")
        puts "#{greeting}, #{name}!"
    end

    greet(name: "Alice")  # Works
    greet(greeting: "Hi") # Throws error: missing required argument 'name'
    ```
