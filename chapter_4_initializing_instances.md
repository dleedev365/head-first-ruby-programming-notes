## Initializing Instances

- Format sequence (similar to C):

  - For example, `%4.3f`
    - `%` represents the start of the format sequence.
    - `4` (whole number) represents the minimum width of the entire number.
    - `3` (decimal number) represents the width after the decimal point.
    - `f` represents the format sequence type (in this example, `f` indicates it's a float).

- `initialize` method:

  - Allows a class instance and its instance variables to be safe to use before anyone else attempts to call methods on it.
  - Example:

    ```ruby
    class MyClass
        def initialize
            puts "Setting up new instance"
        end
    end
    ```

  - When `MyClass.new` is called, Ruby allocates memory to hold a new `MyClass` object, then calls the `initialize` instance method on that new object.
  - Example:

    ```ruby
    # Called before any other method. It's a great way to set default values for instance variables of a class.
    def initialize
        @name = <value>
        @salary = <value>
    end

    # OR

    # Parameters can be assigned default values to make them optional.
    def initialize(parameter_1, parameter_2)
        <code>
    end
    ```

  - Validation can also be placed in the `initialize` method as the first check of user inputs.

## `self` keyword

- It's optional
- Example:

  ```ruby
  class Employee
      attr_reader :name, :salary

      def print_pay_stub
          # If `self` is omitted, Ruby defaults the receiver to the current object (e.g., name).
          puts "Name: #{self.name}"

          # Resulting value will be a float because of 365.0 (making it 365 will result in a whole number).
          pay_for_period = (self.salary / 365.0) * 14
      end
  end
  ```

## Class Methods via Factory Pattern & Method

- Can be invoked directly on a class without the need for any instance of that class (similar to the `new` class method, e.g., `NewClass.new`).
- Example:

  ```ruby
  class MyClass
      def self.my_class_method(parameter_1, parameter_2)
          <code>
      end
  end

  # No need for:
  # instance = MyClass.new
  # instance.my_class_method

  MyClass.my_class_method(1, 2)
  ```

- With Factory Pattern (using the earlier Employee class example):

  ```ruby
  class HourlyEmployee < Employee
      def self.security_guard(name)
          HourlyEmployee.new(name, 19, 25, 20)
      end

      def self.cashier(name)
          HourlyEmployee.new(name, 12, 25, 25)
      end

      def self.janitor(name)
          HourlyEmployee.new(name, 10, 50, 20)
      end
  end

  angela = HourlyEmployee.security_guard("Angela Leather")
  angela.print_pay_stub
  ```
