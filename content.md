# Ruby Gym: Think Fast

<div class="alert alert-info">

Getting stuck with only partial credit on the tests? Remind yourself of how to write _flexible_ code that will pass for all tests at the same time with [this video](https://share.descript.com/view/x6XDEJNYGlp).
</div>

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

`if` statements are one of our most commonly used tools we use as developers for dealing with the unknown! [Pull up the lesson](https://learn.firstdraft.com/lessons/74-ruby-intro-conditionals) if you need a refresher.

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
{: .codeblock #think_fast title="Think Fast" readonly_lines="[1,2,3,4,5,6,7,8,9,10,11,12,13]"}


```ruby
describe "Think Fast" do
  it "prints '40 is even' when the random number is '40'" do
    allow_any_instance_of(Array).to receive(:sample).and_return(40)
    output = run_codeblock
    expect(output).to fuzzy_match("40 is even")
  end
end
```
{: .codeblock-test #think_fast_test_1 for="think_fast" title="Think Fast prints '40 is even' when the random number is '40'" points="1"}


```ruby
describe "Think Fast" do
  it "prints 'you may pass' input is 'true'" do
    allow_any_instance_of(Array).to receive(:sample).and_return(true)
    output = run_codeblock
    expect(output).to fuzzy_match("you may pass")
  end
end
```
{: .codeblock-test #think_fast_test_2 for="think_fast" title="Think Fast prints 'you may pass' input is 'true'" points="1"}


```ruby
describe "Think Fast" do
  it "prints 'you may not pass' input is 'false'" do
    allow_any_instance_of(Array).to receive(:sample).and_return(false)
    output = run_codeblock
    expect(output).to fuzzy_match("you may not pass")
  end
end
```
{: .codeblock-test #think_fast_test_3 for="think_fast" title="Think Fast prints 'you may not pass' input is 'false'" points="1"}


```ruby
describe "Think Fast" do
  it "prints '[:city, :state, :zip]' input is a Hash" do
    allow_any_instance_of(Array).to receive(:sample).and_return({ :city => "Chicago", :state => "IL", :zip => 60654 })
    output = run_codeblock
    expect(output).to fuzzy_match([:city, :state, :zip])
  end
end
```
{: .codeblock-test #think_fast_test_4 for="think_fast" title="Think Fast prints '[:city, :state, :zip]' input is a Hash" points="1"}


```ruby
describe "Think Fast" do
  it "prints 'hello!' input is 'Hello!'" do
    allow_any_instance_of(Array).to receive(:sample).and_return("Hello!")
    output = run_codeblock
    expect(output).to match("hello!")
  end
end
```
{: .codeblock-test #think_fast_test_5 for="think_fast" title="Think Fast prints 'hello!' input is 'Hello!'" points="1"}


```ruby
describe "Think Fast" do
  it "prints ':goodbye' input is ':GOODBYE'" do
    allow_any_instance_of(Array).to receive(:sample).and_return(:GOODBYE)
    output = run_codeblock
    expect(output).to fuzzy_match(:goodbye)
  end
end
```
{: .codeblock-test #think_fast_test_6 for="think_fast" title="Think Fast prints ':goodbye' input is ':GOODBYE'" points="1"}


```ruby
describe "Think Fast" do
  it "prints 'monday' input is a Time and the current day is a Monday" do
    # Note: Time.at(1594669445) returns Monday July 13th, 2020
    allow_any_instance_of(Array).to receive(:sample).and_return(Time.at(1594669445))
    output = run_codeblock
    expect(output).to fuzzy_match("monday")
  end
end
```
{: .codeblock-test #think_fast_test_7 for="think_fast" title="Think Fast prints 'monday' input is a Time and the current day is a Monday" points="1"}


```ruby
describe "Think Fast" do
  it "prints '5 is odd' when the random number is '5'" do
    allow_any_instance_of(Array).to receive(:sample).and_return(5)
    output = run_codeblock
    expect(output).to fuzzy_match("5 is odd")
  end
end
```
{: .codeblock-test #think_fast_test_8 for="think_fast" title="Think Fast prints '5 is odd' when the random number is '5'" points="1"}

- Approximately how long (in minutes) did this lesson take you to complete?
{: .free_text_number #time_taken title="Time taken" points="1" answer="any" }

