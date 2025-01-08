## Unit Testing: Code Quality Assurance

- Ruby's standard unit testing library is **MiniTest**.

---

## Creating Test Cases

```ruby
require 'minitest/autorun'

class TestSomething < Minitest::Test
    def test_true_assertion
        assert(true)
    end

    def test_false_assertion
        assert(false)
    end
end
```

- To run the test file: `ruby test_something.rb`
- **Convention**: Test method names should start with `test`, and the file name should follow the same convention (e.g., `test_<filename>.rb`).

---

## Testing a Class

### Example Directory Structure

```
project_root
|-- lib
|   |-- person.rb
|-- test
    |-- test_person.rb
```

### Implementation Code (`lib/person.rb`)

```ruby
class Person
    attr_accessor :name

    def introduction
        "Hello, my name is #{name}!"
    end
end
```

### Test Code (`test/test_person.rb`)

```ruby
require 'minitest/autorun'
require 'person'

class TestPerson < Minitest::Test
    def test_introduction
        person = Person.new
        person.name = "Bob"
        assert(person.introduction == "Hello, my name is Bob!")
    end
end
```

- To run the test: `ruby -I lib test/test_person.rb` from the project root directory.
  - `-I lib` adds the `lib` directory to Ruby's load path, allowing you to `require` files from it.

---

## Other Useful MiniTest Methods

- `assert_equal(A, B)`
- `assert_includes([A, B, C], A)`
- `assert_instance_of(String, "Apple")`
- `assert_raises(<exception_class>) { <block> }`

### Example: Testing Exception Handling

```ruby
assert_raises(ArgumentError) do
    raise ArgumentError, "That didn't work!"
end
```
