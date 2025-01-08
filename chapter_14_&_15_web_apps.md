# Web Apps: Serving HTML

## Embedding Tags

- `<%= %>`: Output embedding tag. Used to display values.
- `<% %>`: Regular embedding tag. Ruby code inside this tag is evaluated but the result is not output directly to the HTML.

### Example

```html
<!DOCTYPE html>
<html>
  <body>
    <ul>
      <% [1, 2, 3].each do |number| %>
      <li><%= number %></li>
      <% end %>
    </ul>
  </body>
</html>
```

- The `erb` method loads a file from the `views` subdirectory with a name ending in `.erb`, evaluates any embedded Ruby code, and returns the result as a string.

---

# Saving and Loading Data: Keeping it Around

## Handling POST Requests

Example of handling a `POST` request:

```ruby
post('/movies/create') do
  @movie = Movie.new
  # Assign the contents of the form fields to the object's attributes
  @movie.title = params["title"]
  @movie.director = params["director"]
end
```

## Converting Objects to/from Strings with YAML

"YAML" stands for "YAML Ain't Markup Language" and is a standard for representing objects and other data in string form.

### Example of Using YAML

```ruby
require 'movie'
require 'yaml'

movie = Movie.new
movie.title = "Fight Club"
movie.director = "David Fincher"

puts YAML.chomp(movie)

movie_yaml = YAML.dump(movie) # Convert the movie object to YAML string
copy = YAML.load(movie_yaml)  # Convert the YAML string back to an object
puts copy.title, copy.director
```

## Saving Objects to a File with `YAML::Store`

`YAML::Store` allows saving Ruby objects to disk and loading them back.

### Example of Saving to YAML::Store

```ruby
require 'yaml/store'

# ".transaction" ensures no other programs can write to the file during the block's execution
store.transaction do
  store["My Key"] = "My Key Value"
  store["Key Two"] = "Value Two"
end
```

## Finding the Next Available ID

You can use the `root` method to return all the keys in the store as an array, find the highest key, and increment it by 1 for the next instance.

### Example of Finding the Next Available ID

```ruby
require 'yaml/store'

store = YAML::Store.new('empty+store.yml')
store.transaction do
  highest_id = store.roots.max || 0
  p highest_id + 1
end
```

---

# Loading All Movies in a Sinatra App

### Example of Loading and Managing Movies in a Sinatra App

```ruby
require 'sinatra'
require 'movie'
require 'movie_store'

store = MovieStore.new('movies.yaml')

get('/movies') do
  @movies = store.all
  erb :index  # Displays a list of all existing records
end

get('/movies/new') do
  erb :new  # Displays form to create a new record
end

post('/movies/create') do
  @movie = Movie.new
  @movie.title = params["title"]
  @movie.director = params["director"]

  store.save(@movie)
  redirect '/movies/new'  # Redirect to the new movie form after saving
end

get('/movies/:id') do
  id = params["id"].to_i  # Convert the string ID to an integer
  @movie = store.find(id)
  erb :show  # Displays the details of a specific movie
end
```
