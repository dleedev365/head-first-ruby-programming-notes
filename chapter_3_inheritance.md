# Ruby Syntax for Inheritance

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
