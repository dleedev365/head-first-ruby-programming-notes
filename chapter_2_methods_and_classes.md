# Ruby Syntax for Methods, Classes, and Inheritance

## Method Syntax

```ruby
def <function_name>(parameter_1, parameter_2, ...)
  <code>
end
```

- **Scope**: Methods are defined outside of any class and are included in the top-level execution environment.
- **Naming Conventions**:
  - Methods that return Boolean values end with `?`.
  - Methods with potentially surprising side effects end with `!`.
  - Leave parentheses off the method definition if there are no parameters.

### Optional Parameters

- Provide a default value for optional parameters by defining it after required parameters.
- Example:

```ruby
def use_headlights(brightness = "low-beam")
  # ...
end

# Method calls:
use_headlights
use_headlights("high-beam")
```

### Return Keyword

- Ruby doesn’t require an explicit `return` keyword in methods, but it can be used to terminate early.
- Example:

```ruby
def mileage(parameter_1, parameter_2)
  if <condition>
    return <value>
  end
  <code>
end
```

---

## Class Syntax

```ruby
class ClassName
  def method_name
    <code>
  end
end

# Instantiate a class and call a method:
c = ClassName.new
c.method_name
```

### Conventions

- **Class Names**: Must start with a capital letter.
- **Symbols**: Represent properties of a class that can’t be changed.
  - Example using `attr_accessor`:

```ruby
class Dog
  attr_accessor :name, :age

  def report_age
    puts "#{@name} is #{@age} years old"
  end
end
```

- **Manual Implementation of Accessors**:

```ruby
# attr_writer under the hood:
def name=(new_value)
  @name = new_value
end

# attr_reader under the hood:
def name
  @name
end

# attr_accessor combines both:
def name=(new_value)
  @name = new_value
end

def name
  @name
end
```

### Error Handling

- Use `raise` to stop execution, print an error message, and exit immediately if no further instructions are provided.
  - Example:

```ruby
raise "Something bad happened!"
```

---

## Inheritance Syntax

```ruby
# Car is a subclass and Vehicle is the superclass
class Car < Vehicle
  <code>
end
```

### Instance Variables

- Declared on the object level, not inherited from the superclass.
- Example:

```ruby
car = Car.new

car.instance_variables # prints nothing

car.odometer = 22914
car.gas_used = 728

car.instance_variables # prints @odometer and @gas_used
```

### `super` Keyword

- Calls a method of the same name in the superclass.
- Can pass arguments to `super`. If no arguments are provided, the superclass method will be called with the same arguments as the subclass method.
  - Example:

```ruby
class Friend < Person
  def greet_by_name(name)
    basic_greeting = super
    "#{basic_greeting}..."
  end
end
```

### Checking Inheritance

- Use `.superclass` to identify the inheritance hierarchy at the top level of an object.
