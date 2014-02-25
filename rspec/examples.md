### First `describe` what you are doing

Begin by using a `describe` for each of the methods you plan on defining,
passing the method’s name as the argument. For class method specs prefix a “.”
to the name, and for instance level specs prefix a “#”. This follows standard
Ruby documenting practices and will read well when output by the spec runner.

````
describe User do

  # for User.authenticate
  describe '.authenticate' do
  end
 
  describe '.admins' do
  end

  # for @user.authenticate
  describe '#admin?' do
  end
 
  describe '#name' do
  end
end
````

### Then establish the `context`

Write a `context` for each execution path through a method; literally
specifying the behavior of a method in a given context.

````
describe '#create' do
  context 'given valid credentials' do
  end
 
  context 'given invalid credentials' do
  end
end
````

Note the use of “given” in the argument to each `context`. It communicates the
context of receiving input. Another great word to use in a context for
describing conditional driven behavior is “when”.

````
describe '#destroy' do
   context 'when logged in' do
   end
 
   context 'when not logged in' do
   end
 end
````

### `it` only expects one thing

By striving to only having one expectation per example, you increase the
readability of your specs. Breaking out the expectations into separate
examples clearly defines the behavior and results in easier to maintain
examples:

````
describe UsersController do
 
  describe '#create' do
    it 'creates a new user' do
      User.count.should == @count + 1
    end
 
    it 'sets a flash message' do
      flash[:notice].should be
    end
 
    it "redirects to the new user's profile" do
      response.should redirect_to(user_path(assigns(:user)))
    end
  end
end
````

Write examples by starting with a present tense verb that describes the behavior.

````
it 'creates a new user' do ... end
 
it 'sets a flash message' do ... end
 
it 'redirects to the home page' do ... end
````

Finally, don’t begin examples names with the word ‘should’.  It’s redundant and
results in hard to read spec output.

### Run specs to confirm readability

Always run your specs with the ‘–format’ option set to ‘documentation’
(`--format documentation` or `-f d`)

````
$ rspec spec/controllers/users_controller_spec.rb --format documentation
````

````
UsersController
  #create
    creates a new user
    sets a flash message
    redirects to the new user's profile
  #show
    finds the given user
    displays its profile
    responds to JSON
  #destroy
    deletes the given user
    sets a flash message
    redirects to the home page
````

Continue to rename your examples until this output reads like clear conversation.

### Use mocks and stubs over factories

Factories hit the database when it's not necessary. 

````
# wrong
context 'when user is valid' do
  before do
    user = Factory.create(:valid_user)
  end

  it 'sets flash notice' do
    flash[:notice].should be
  end
end

# correct
context 'when user is valid' do
  before do
    user = mock_model(User)
    user.stub(:valid?).and_return(true)
  end

  it 'sets flash notice' do
    flash[:notice].should be
  end
end
````

### Conclusion

As you can see, all these practices revolve around writing clear specifications
readable by all developers. The ideal is to run all specs to not only pass but
to have their output completely define your application. Every little step
towards that goal helps, and we’re still learning better ways to get there.

### Sources

* http://blog.carbonfive.com/2010/10/21/rspec-best-practices/
* http://betterspecs.org/
