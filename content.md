# Ruby Gym: Think Fast

Suppose that your program has to deal with the object inside the variable `some_random_input`. If the object is:

* a `String`: downcase it and print it
* a `Time`: figure out the day of the week, downcased, and print
* an `Integer`: figure out whether it's odd or even and print (where X is the number)
    * `"X is odd"`, or
    * `"X is even"`
* a `Symbol`: downcase it and print it
* `nil`: print `"no object provided"`
* `true`: print `"you may pass"`
* `false`: print `"you may not pass"`
* a `Hash`: print the list of keys within the `Hash`, as an `Array`.

`if` statements are one of our most commonly used tools we use as developers for dealing with the unknown! [Pull up the lesson](https://learn.firstdraft.com/lessons/74) if you need a refresher.

Next, remember that there's a method called `.class` that we can call on any Ruby object to find out what kind of thing it is. We first met it way back in the `Integer` lesson.

```ruby
unpredictable_inputs = [
  "Hello!",
  Time.now,
  rand(100),
  :GOODBYE,
  nil,
  true,
  false,
  { :city => "Chicago", :state => "IL", :zip => 60654 }
]

some_random_input = unpredictable_inputs.sample
# write your program below
```
{: .repl #think_fast title="Think Fast" readonly_lines="[1,2,3,4,5,6,7,8,9,10,11,12,13]"}


```ruby
describe "Think Fast" do
  it "prints '40 is even' when the random number is '40'" do
    path = "/tmp/code.rb"
    allow_any_instance_of(Array).to receive(:sample).and_return(40)
    output = capture_stdout { require_relative(path) }
    expect(output).to match(/40 is even/i), "Expected output to be '40 is even', but was '#{output}'."
  end

  def capture_stdout
    old_stdout = $stdout
    $stdout = StringIO.new
    yield
    $stdout.string
  ensure
    $stdout = old_stdout
  end
end
```
{: .repl-test #think_fast_test_1 for="think_fast" title="Think Fast prints '40 is even' when the random number is '40'" points="1"}


```ruby
describe "Think Fast" do
  it "prints 'you may pass' input is 'true'" do
    path = "/tmp/code.rb"
  allow_any_instance_of(Array).to receive(:sample).and_return(true)
    output = capture_stdout { require_relative(path) }
    expect(output).to match(/you may pass/i), "Expected output to be 'you may pass', but was '#{output}'."
  end

  def capture_stdout
    old_stdout = $stdout
    $stdout = StringIO.new
    yield
    $stdout.string
  ensure
    $stdout = old_stdout
  end
end
```
{: .repl-test #think_fast_test_2 for="think_fast" title="Think Fast prints 'you may pass' input is 'true'" points="1"}


```ruby
describe "Think Fast" do
  it "prints 'you may not pass' input is 'false'" do
    path = "/tmp/code.rb"
    allow_any_instance_of(Array).to receive(:sample).and_return(false)
    output = capture_stdout { require_relative(path) }
    expect(output).to match(/you may not pass/i), "Expected output to be 'you may not pass', but was '#{output}'."
  end

  def capture_stdout
    old_stdout = $stdout
    $stdout = StringIO.new
    yield
    $stdout.string
  ensure
    $stdout = old_stdout
  end
end
```
{: .repl-test #think_fast_test_3 for="think_fast" title="Think Fast prints 'you may not pass' input is 'false'" points="1"}


```ruby
describe "Think Fast" do
  it "prints '[:city, :state, :zip]' input is a Hash" do
    path = "/tmp/code.rb"
    allow_any_instance_of(Array).to receive(:sample).and_return({ :city => "Chicago", :state => "IL", :zip => 60654 })
    output = capture_stdout { require_relative(path) }
    expect(output).to match(/\[:city, :state, :zip\]/i), "Expected output to be '[:city, :state, :zip]', but was '#{output}'."
  end

  def capture_stdout
    old_stdout = $stdout
    $stdout = StringIO.new
    yield
    $stdout.string
  ensure
    $stdout = old_stdout
  end
end
```
{: .repl-test #think_fast_test_4 for="think_fast" title="Think Fast prints '[:city, :state, :zip]' input is a Hash" points="1"}


```ruby
describe "Think Fast" do
  it "prints 'hello!' input is 'Hello!'" do
    path = "/tmp/code.rb"
    allow_any_instance_of(Array).to receive(:sample).and_return("Hello!")
    output = capture_stdout { require_relative(path) }
    expect(output).to match(/hello!/), "Expected output to be 'hello!', but was '#{output}'."
  end

  def capture_stdout
    old_stdout = $stdout
    $stdout = StringIO.new
    yield
    $stdout.string
  ensure
    $stdout = old_stdout
  end
end
```
{: .repl-test #think_fast_test_5 for="think_fast" title="Think Fast prints 'hello!' input is 'Hello!'" points="1"}


```ruby
describe "Think Fast" do
  it "prints ':goodbye' input is ':GOODBYE'" do
    path = "/tmp/code.rb"
    allow_any_instance_of(Array).to receive(:sample).and_return(:GOODBYE)
    output = capture_stdout { require_relative(path) }
    expect(output).to match(/:goodbye/), "Expected output to be ':goodbye', but was '#{output}'."
  end

  def capture_stdout
    old_stdout = $stdout
    $stdout = StringIO.new
    yield
    $stdout.string
  ensure
    $stdout = old_stdout
  end
end
```
{: .repl-test #think_fast_test_6 for="think_fast" title="Think Fast prints ':goodbye' input is ':GOODBYE'" points="1"}


```ruby
describe "Think Fast" do
  it "prints 'monday' input is a Time and the current day is a Monday" do
    path = "/tmp/code.rb"
    allow_any_instance_of(Array).to receive(:sample).and_return(Time.at(1594669445))
    output = capture_stdout { require_relative(path) }
    expect(output).to match(/monday/), "Expected output to be 'monday', but was '#{output}'."
  end

  def capture_stdout
    old_stdout = $stdout
    $stdout = StringIO.new
    yield
    $stdout.string
  ensure
    $stdout = old_stdout
  end
end
```
{: .repl-test #think_fast_test_7 for="think_fast" title="Think Fast prints 'monday' input is a Time and the current day is a Monday" points="1"}


```ruby
describe "Think Fast" do
  it "prints '5 is odd' when the random number is '5'" do
    path = "/tmp/code.rb"
    allow_any_instance_of(Array).to receive(:sample).and_return(5)
    output = capture_stdout { require_relative(path) }
    expect(output).to match(/5 is odd/i), "Expected output to be '5 is odd', but was '#{output}'."
  end

  def capture_stdout
    old_stdout = $stdout
    $stdout = StringIO.new
    yield
    $stdout.string
  ensure
    $stdout = old_stdout
  end
end
```
{: .repl-test #think_fast_test_8 for="think_fast" title="Think Fast prints '5 is odd' when the random number is '5'" points="1"}
