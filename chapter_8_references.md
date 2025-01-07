
### Ruby Objects and the Heap
- All Ruby objects live on the heap, managed manually.
- Ruby garbage-collects unused objects.
- References are used to locate objects on the heap.

---

### Hash Default Blocks
Hash default blocks allow for dynamic default values and can execute custom logic when a key is accessed for the first time.

#### Example: Using a Default Block
```ruby
# When the block is called later, it will receive a reference to the hash and the key being accessed
h = Hash.new do |hash, key|
  body = CelestialBody.new
  body.type = "planet"
  hash[key] = body
  body # Return the object
end

bodies['Mars'].name = "Mars"
p bodies['Mars'] # type = "planet", name = "Mars"

bodies['Europa'].name = "Europa"
bodies['Europa'].type = "Moon"
p bodies['Europa'] # type = "moon", name = "Europa"

bodies['Venus'].name = "Venus"
p bodies["Venus"] # type = "planet", name = "Venus"
```

**Note**: Ensure the block’s return value matches what is assigned to the hash. Mismatched return values can lead to different results on subsequent accesses.

---

### The Value of Expressions in Ruby
In Ruby, the value of an expression equals the value being assigned.

#### Example: Expression Value Assignment
```ruby
greeting = Hash.new do |hash, key|
  hash[key] = "Hi, #{key}"
end

p greeting["Kayla"] # "Hi, Kayla"
p greeting # {"Kayla" => "Hi, Kayla"}
```

#### Additional Example:
```ruby
p my_hash = {} # {}
p my_integer = 20 # 20
p my_hash["A"] = ['Apple'] # ["Apple"]
p my_array[0] = 245 # 245
```

---

### Putting It All Together
Here’s an example combining the discussed concepts:
```ruby
class CelestialBody
  attr_accessor :type, :name
end

bodies = Hash.new do |hash, key|
  body = CelestialBody.new
  body.type = "planet"
  hash[key] = body
end

bodies["Mars"].name = "Mars"
bodies["Europa"].name = "Europa"
bodies["Europa"].type = "Moon"
bodies["Venus"].name = "Venus"

p bodies 
# {
#   "Mars" => #<CelestialBody @type="planet", @name="Mars">, 
#   "Europa" => #<CelestialBody @type="moon", @name="Europa">,
#   "Venus" => #<CelestialBody @type="planet", @name="Venus">
# }
```

---

## Rule of Thumb for Hash Defaults
1. If your default is a **number**, use a **default object**.
2. If your default is **anything else**, use a **default block**.

### Default Object and Its Pitfall
Setting a default object for a hash causes all unassigned keys to return references to the same default object:
```ruby
h = Hash.new([])
h[:a] << 1
h[:b] << 2
p h # {}
p h[:c] # [1, 2]
```

**Solution**: Use a default block instead:
```ruby
h = Hash.new { [] }
h[:a] << 1
h[:b] << 2
p h # {}
p h[:c] # []
```