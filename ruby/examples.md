Use spaces around operators, after commas, colons and semicolons,
around `{` and before `}`.

````
sum = 1 + 2
a, b = 1, 2
1 > 2 ? true : false; puts "Hi"
[1, 2, 3].each { |e| puts e }
````

No spaces after `(`, `[` or before `]`, `)`.

````
some(arg).other
[1, 2, 3].length
No spaces after !.

!array.include?(element)
````

Indent when as deep as case.

````
case
when song.name == "Misty"
  puts "Not again!"
when song.duration > 120
  puts "Too long!"
when Time.now.hour > 21
  puts "It's too late"
else
  song.play
end

case year
when 1850..1889 then "Blues"
when 1890..1909 then "Ragtime"
when 1910..1929 then "New Orleans Jazz"
when 1930..1939 then "Swing"
when 1940..1950 then "Bebop"
else "Jazz"
end
````

Use empty lines between defs and to break up a method into logical paragraphs.

````
def some_method
  data = initialize(options)

  data.manipulate!

  data.result
end

def some_method
  result
end
````

Use def self.method to define singleton methods. This makes the methods more
resistant to refactoring changes.

````
class TestClass
  # bad
  def TestClass.some_method
    # body omitted
  end

  # good
  def self.some_other_method
    # body omitted
  end
end
````

Avoid class << self except when necessary, e.g. single accessors and aliased
attributes.

````
class TestClass
  # bad
  class << self
    def first_method
      # body omitted
    end

    def second_method_etc
      # body omitted
    end
  end

  # good
  class << self
    attr_accessor :per_page
    alias_method :nwo, :find_by_name_with_owner
  end

  def self.first_method
    # body omitted
  end

  def self.second_method_etc
    # body omitted
  end
end
````

Indent the public, protected, and private methods as much the method definitions
they apply to. Leave one blank line above them.

````
class SomeClass
  def public_method
    # ...
  end

  private
  def private_method
    # ...
  end
end
````

Prefer string interpolation instead of string concatenation:

````
# bad
email_with_name = user.name + " <" + user.email + ">"

# good
email_with_name = "#{user.name} <#{user.email}>"
````

Prefer double-quoted strings. Interpolation and escaped characters will
always work without a delimiter change, and ' is a lot more common than "
in string literals.

````
# bad
name = 'Bozhidar'

# good
name = "Bozhidar"
````

Use Ruby 1.9 new Hash style

````
# bad
user = {
  :login => "defunkt",
  :name => "Chris Wanstrath",
  "followers-count" => 52390235
}

# good
user = {
  login: "defunkt",
  name: "Chris Wanstrath",
  "followers-count" => 52390235
}
````
