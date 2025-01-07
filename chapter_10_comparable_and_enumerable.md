## Comparable and Enumerable: Ready-Made Mixes

### Comparing Objects
- For example: `<`, `>`, `<=`, `==`, `>=`, `between`

### Working with Collections
- For example: `find_all`, `reject`, `map`, etc.

### Example: Custom Comparison

```ruby
class Steak
  attr_accessor :grade

  def > (other)
    grade_scores = {"Prime" => 3, "Choice" => 2, "Select" => 1}
    grade_scores[grade] > grade_scores[other.grade]
  end
end

first_steak = Steak.new
second_steak = Steak.new
first_steak.grade = "Prime"
second_steak.grade = "Choice"

if first_steak > second_steak
  puts "I take #{first_steak.grade}"
end
```

- The `grade_scores` hash object is created on each instantiation or call of the method. To improve, use "constants" instead.

### Improved Example Using Constants

```ruby
class MyClass
  GRADE_SCORES = {"Prime" => 3, "Choice" => 2, "Select" => 1}

  def my_method
    puts GRADE_SCORES
  end
end

MyClass.new.my_method
```

---

## Spaceship Operator (`<=>`)

The spaceship operator is equivalent to a combination of `<`, `==`, and `>`. It returns:

- `-1` if the expression on the left is less than the expression on the right
- `0` if the expressions are equal
- `1` if the expression on the left is greater than the expression on the right

### Example
- The object on the right can be any other argument.
```ruby
3 <=> 4  # -1
3 <=> 3  # 0
4 <=> 3  # 1
```