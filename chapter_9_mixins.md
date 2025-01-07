## Mixins: Mix it Up!
- Q. how do you deal with multiple, complex inheritance?
- Q. how to add a group of methods to multiple classes without using inheritance? via **Module**

---

### Module
- A module is an instance that can't be created
- For example, modules have the following syntax:
```ruby
    module ModuleName
        def first_method
            <code block>
        end
    end
```
- you can declare a class and "mix-in" modules to gain all the methods of modules in the class 
```ruby
    class MyClass
        include ModuleName_1
        include ModuleName_2
        include ModuleName_N
    end

    my_object = MyClass.new
    my_object.first_method
```
- when a module is used as a mixin, it generally describes an aspect of an object's behaviour. Thus, a convention is to use a description as the mixiin's name. (single adjective if applicable)
    - For example, a module named "commentable" can be named to "AcceptsComments"
- A class can only inherit from one superclass

---

### Mixins and Method Overriding
- When Ruby finds the method it's looking for on a class, it invokes the method and then stops looking. The same is true for mixins!
    - Ruby searches for instance methods in the modules and classes shown in a class's "ancestors" array
    - If the method is found in a class, it just invokes that method and ignores the same name in a mixin! (overriden by the class's method)
